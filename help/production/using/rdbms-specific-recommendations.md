---
solution: Campaign Classic
product: campaign
title: Recomendações específicas do RDBMS
description: Recomendações específicas do RDBMS
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 3%

---


# Recomendações específicas do RDBMS{#rdbms-specific-recommendations}

Para ajudá-lo a configurar planos de manutenção, esta seção lista algumas recomendações/práticas recomendadas adaptadas aos vários mecanismos RDBMS suportados pela Adobe Campaign. No entanto, estas são apenas recomendações. Cabe a você adaptá-los às suas necessidades, de acordo com o seu procedimento interno e as suas limitações. O administrador do banco de dados é responsável pela criação e execução desses planos.

## PostgreSQL {#postgresql}

### Detecção de tabelas grandes {#detecting-large-tables}

1. Você pode adicionar a seguinte visualização ao banco de dados:

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. A execução do seguinte comando permite que você localize tabelas e índices grandes:

   ```
   select * from uvSpace;
   ```

### Manutenção simples {#simple-maintenance}

Em PostgreSQL, os comandos típicos que você pode usar são **vácuo completo** e **reindex**.

Este é um exemplo típico de um plano de manutenção SQL a ser executado regularmente usando estes dois comandos:

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;
```

>[!NOTE]
>
>* O Adobe recomenda iniciar com tabelas menores: desta forma, se o processo falhar em grandes tabelas (se o risco de falha for maior), pelo menos parte da manutenção foi concluída.
>* O Adobe recomenda adicionar as tabelas específicas ao seu modelo de dados, que podem estar sujeitas a atualizações significativas. Esse pode ser o caso de **NmsRecipient** se você tiver grandes fluxos diários de replicação de dados.
>* Os comandos **vácuo** e **re-index** bloquearão a tabela, que pausa alguns processos enquanto a manutenção é realizada.
>* Para tabelas muito grandes (normalmente acima de 5 Gb), **vácuo cheio** pode tornar-se bastante ineficiente e levar muito tempo. O Adobe não recomenda usá-lo para a tabela **YyyNmsBroadLogXxx**.
>* Esta operação de manutenção pode ser implementada por um fluxo de trabalho da Adobe Campaign, usando uma atividade **[!UICONTROL SQL]** (para obter mais informações, consulte [esta seção](../../workflow/using/architecture.md)). Certifique-se de programar a manutenção para um tempo de atividade baixo que não colidir com a janela de backup.
>



### Reconstrução de um banco de dados {#rebuilding-a-database}

O PostgreSQL não fornece uma maneira fácil de executar uma recriação de tabela online, pois **vácuo cheio** bloqueia a tabela, impedindo assim a produção regular. Isso significa que a manutenção deve ser realizada quando a tabela não for usada. É possível:

* executar a manutenção quando a plataforma Adobe Campaign for parada,
* pare os vários subserviços do Adobe Campaign que provavelmente gravarão na tabela que está sendo recriada (**nlserver stop wfserver instance_name** para interromper o processo de fluxo de trabalho).

Este é um exemplo de desfragmentação de tabela usando funções específicas para gerar a DDL necessária. O SQL a seguir permite criar duas novas funções: **GenRebuildTablePart1** e **GenRebuildTablePart2**, que podem ser usadas para gerar a DDL necessária para recriar uma tabela.

* A primeira função permite criar uma tabela de trabalho (** _tmp** aqui) que é uma cópia da tabela original.
* A segunda função então exclui a tabela original e renomeia a tabela de trabalho e seus índices.
* Usar duas funções em vez de uma significa que, se a primeira falhar, você não corre o risco de excluir a tabela original.

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

O exemplo a seguir pode ser usado em um fluxo de trabalho para recriar as tabelas necessárias, em vez de usar o comando **vácuo/rebuild**:

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

## Oracle {#oracle}

Entre em contato com o administrador do banco de dados para saber mais sobre os procedimentos mais adequados para a sua versão do Oracle.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Para o Microsoft SQL Server, você pode usar o plano de manutenção detalhado em [esta página](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

O exemplo abaixo diz respeito ao Microsoft SQL Server 2005. Se estiver usando outra versão, entre em contato com o administrador do banco de dados para saber mais sobre os procedimentos de manutenção.

1. Primeiro, conecte-se ao Microsoft SQL Server Management Studio com um logon com direitos de administrador.
1. Vá para a pasta **[!UICONTROL Management > Maintenance Plans]**, clique com o botão direito do mouse nela e escolha **[!UICONTROL Maintenance Plan Wizard]**
1. Clique em **[!UICONTROL Next]** quando a primeira página aparecer.
1. Selecione o tipo de plano de manutenção que deseja criar (programações separadas para cada tarefa ou programação única para o plano inteiro) e clique no botão **[!UICONTROL Change...]**.
1. Na janela **[!UICONTROL Job schedule properties]**, selecione as configurações de execução desejadas e clique em **[!UICONTROL OK]** e, em seguida, clique em **[!UICONTROL Next]** .
1. Selecione as tarefas de manutenção que deseja executar e clique em **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >Recomendamos executar pelo menos as tarefas de manutenção mostradas abaixo. Você também pode selecionar a tarefa de atualização de estatísticas, embora ela já seja realizada pelo fluxo de trabalho de limpeza do banco de dados.

1. Na lista suspensa, selecione o banco de dados no qual deseja executar a tarefa **[!UICONTROL Database Check Integrity]**.
1. Selecione o banco de dados e clique em **[!UICONTROL OK]** e, em seguida, clique em **[!UICONTROL Next]** .
1. Configure o tamanho máximo alocado para o banco de dados e clique em **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >Se o tamanho do banco de dados exceder esse limite, o plano de manutenção tentará excluir os dados não utilizados para liberar espaço.

1. Reorganize ou recrie o índice:

   * Se a taxa de fragmentação do índice estiver entre 10% e 40%, recomenda-se uma reorganização.

      Escolha quais bancos de dados e objetos (tabelas ou visualizações) você deseja reorganizar e clique em **[!UICONTROL Next]**.

      >[!NOTE]
      >
      >Dependendo da sua configuração, você pode escolher as tabelas selecionadas anteriormente ou todas as tabelas no banco de dados.

   * Se a taxa de fragmentação do índice for superior a 40%, é recomendável reconstruir.

      Selecione as opções que deseja aplicar à tarefa de reconstrução de índice e clique em **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >O processo de recriação de índice é mais restritivo em termos de uso do processador e bloqueia os recursos do banco de dados. Clique na opção **[!UICONTROL Keep index online while reindexing]** se desejar que o índice esteja disponível durante a reconstrução.

1. Selecione as opções que deseja exibir no relatório de atividade e clique em **[!UICONTROL Next]** .
1. Verifique a lista do tarefa configurado para o plano de manutenção e clique em **[!UICONTROL Finish]**.

   Será exibido um resumo do plano de manutenção e dos status de suas várias etapas.

1. Quando o plano de manutenção estiver concluído, clique em **[!UICONTROL Close]** .
1. No Microsoft SQL Server Explorer, clique com o duplo na pasta **[!UICONTROL Management > Maintenance Plans]**.
1. Selecione o plano de manutenção da Adobe Campaign: as várias etapas são detalhadas em um fluxo de trabalho.

   Observe que um objeto foi criado na pasta **[!UICONTROL SQL Server Agent > Jobs]**. Esse objeto permite que você start o plano de manutenção. No nosso exemplo, existe apenas um objeto, uma vez que todas as tarefas de manutenção fazem parte do mesmo plano.

   >[!IMPORTANT]
   >
   >Para que esse objeto seja executado, o agente do Microsoft SQL Server deve estar habilitado.

**Configurar um banco de dados separado para tabelas de trabalho**

>[!NOTE]
>
>Essa configuração é opcional.

A opção **WdbcOptions_TempDbName** permite configurar um banco de dados separado para tabelas de trabalho no Microsoft SQL Server. Isso otimiza os backups e a replicação.

Essa opção pode ser usada se você quiser que tabelas de trabalho (por exemplo, as tabelas criadas durante a execução de um fluxo de trabalho) sejam criadas em outro banco de dados.

Quando você define a opção como &quot;tempdb.dbo.&quot;, as tabelas de trabalho serão criadas no banco de dados temporário padrão do Microsoft SQL Server. O administrador do banco de dados precisa permitir acesso de gravação ao banco de dados tempdb.

Se a opção estiver definida, ela será usada em todos os bancos de dados do Microsoft SQL Server configurados no Adobe Campaign (banco de dados principal e conta externa). Observe que se duas contas externas compartilham o mesmo servidor, podem ocorrer conflitos (já que o tempdb será único). Da mesma forma, se duas instâncias de Campanha usarem o mesmo servidor MSSQL, poderá haver conflitos se usarem o mesmo tempdb.
