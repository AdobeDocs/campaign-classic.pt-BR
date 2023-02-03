---
product: campaign
title: Recomendações específicas do RDBMS
description: Recomendações específicas do RDBMS
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 98b338ddf0da184363c599d74aeb98ed7f6303ce
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 4%

---

# Recomendações específicas do RDBMS{#rdbms-specific-recommendations}

![](../../assets/v7-only.svg)

Para ajudar você a configurar planos de manutenção, esta seção lista algumas recomendações e práticas recomendadas adaptadas aos vários mecanismos RDBMS compatíveis com a Adobe Campaign. No entanto, estas são apenas recomendações. Cabe a você adaptá-los às suas necessidades, de acordo com o procedimento e as restrições internas. O administrador do banco de dados tem a responsabilidade de criar e executar esses planos.

## PostgreSQL {#postgresql}

### Detecção de tabelas grandes {#detecting-large-tables}

1. Você pode adicionar a seguinte exibição ao banco de dados:

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

1. Você pode executar esta consulta para detectar tabelas e índices grandes:

   ```
   SELECT * FROM uvSpace;
   ```

   Como alternativa, execute esta consulta, por exemplo, para ver todos os tamanhos de índice coletivamente:

   ```
   SELECT
      tablename,
      sum(size_mbytes) AS "sizeMB_all",
      (
         SELECT sum(size_mbytes)
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_data",
      (
         SELECT sum(size_mbytes)
         FROM uvspace 
         AS uv2 
         WHERE
            INDEXNAME IS NOT NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_index",
      (
         SELECT ROW_COUNT
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS ROWS FROM uvspace AS uv1
      GROUP BY tablename
      ORDER BY 2 DESC
   ```

### Manutenção simples {#simple-maintenance}

No PostgreSQL, você pode usar estas palavras-chave típicas:

* VÁCUO (COMPLETO, ANÁLISE, VERBOR)

Para executar a operação VACUUM e analisar e cronometrar, use a sintaxe a seguir:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

Recomendamos que você não omita a declaração ANALYZE. Caso contrário, a tabela vazia fica sem nenhuma estatística. O motivo é que uma nova tabela é criada e a antiga é excluída. Como resultado, a ID de objeto (OID) da tabela muda, mas nenhuma estatística é calculada. Consequentemente, você enfrentará problemas de desempenho imediatamente.

Este é um exemplo típico de um plano de manutenção SQL a ser executado regularmente:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
```

>[!NOTE]
>
>* O Adobe recomenda começar com tabelas menores: assim, se o processo falhar em grandes tabelas (quando o risco de falha é maior), pelo menos parte da manutenção foi concluída.
>* O Adobe recomenda adicionar as tabelas específicas ao seu modelo de dados, que podem estar sujeitas a atualizações significativas. Pode ser o caso para **NmsRecipient** se você tiver grandes fluxos diários de replicação de dados.
>* A instrução VACUUM bloqueará a tabela, que pausa alguns processos enquanto a manutenção é realizada.
>* Para tabelas muito grandes (normalmente acima de 5 Gb), a instrução VACUUM FULL pode tornar-se bastante ineficiente e demorar muito tempo. O Adobe não recomenda usá-lo para o **YyNmsBroadLogXxx** tabela.
>* Essa operação de manutenção pode ser implementada por um workflow do Adobe Campaign, usando um **[!UICONTROL SQL]** atividade . Para obter mais informações, consulte [esta seção](../../workflow/using/architecture.md). Certifique-se de programar a manutenção para um tempo de baixa atividade que não colidir com a janela de backup.
>


### Reconstrução de um banco de dados {#rebuilding-a-database}

O PostgreSQL não fornece uma maneira fácil de executar uma recriação de tabela online, pois a instrução VACUUM FULL bloqueia a tabela, impedindo assim a produção regular. Isso significa que a manutenção deve ser executada quando a tabela não for usada. É possível:

* executar a manutenção quando a plataforma Adobe Campaign for interrompida,
* pare os vários subserviços do Adobe Campaign que provavelmente gravarão na tabela que está sendo recriada (**nlserver stop wfserver instance_name** para interromper o processo do workflow).

Veja um exemplo de desfragmentação de tabela usando funções específicas para gerar o DDL necessário. O SQL a seguir permite criar duas novas funções: **GenRebuildTablePart1** e **GenRebuildTablePart2**, que pode ser usada para gerar a DDL necessária para recriar uma tabela.

* A primeira função permite criar uma tabela de trabalho (** _tmp** aqui) que é uma cópia da tabela original.
* A segunda função exclui a tabela original e renomeia a tabela de trabalho e seus índices.
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

O exemplo a seguir pode ser usado em um workflow para recriar as tabelas necessárias em vez de usar a variável **vácuo/reconstrução** comando:

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
1. Vá para o **[!UICONTROL Management > Maintenance Plans]** , clique com o botão direito do mouse e escolha **[!UICONTROL Maintenance Plan Wizard]**.
1. Clique em **[!UICONTROL Next]** quando a primeira página aparece.
1. Selecione o tipo de plano de manutenção que deseja criar (programações separadas para cada tarefa ou programação única para o plano inteiro) e clique no botão **[!UICONTROL Change...]** botão.
1. No **[!UICONTROL Job schedule properties]** selecione as configurações de execução desejadas e clique em **[!UICONTROL OK]**, depois clique em **[!UICONTROL Next]**.
1. Selecione as tarefas de manutenção que deseja executar e clique em **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >Recomendamos executar pelo menos as tarefas de manutenção mostradas abaixo. Você também pode selecionar a tarefa de atualização de estatísticas, embora ela já tenha sido executada pelo workflow de limpeza do banco de dados.

1. Na lista suspensa, selecione o banco de dados no qual deseja executar o **[!UICONTROL Database Check Integrity]** tarefa.
1. Selecione o banco de dados e clique em **[!UICONTROL OK]**, depois clique em **[!UICONTROL Next]**.
1. Configure o tamanho máximo alocado para o banco de dados e clique em **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >Se o tamanho do banco de dados exceder esse limite, o plano de manutenção tentará excluir dados não utilizados para liberar espaço.

1. Reorganize ou recrie o índice:

   * Se a taxa de fragmentação do índice estiver entre 10% e 40%, recomenda-se uma reorganização.

      Escolha quais bancos de dados e objetos (tabelas ou exibições) você deseja reorganizar e clique em **[!UICONTROL Next]**.

      >[!NOTE]
      >
      >Dependendo da sua configuração, você pode escolher as tabelas selecionadas anteriormente ou todas as tabelas no seu banco de dados.

   * Se a taxa de fragmentação do índice for superior a 40%, é recomendável reconstruir.

      Selecione as opções que deseja aplicar à tarefa de reconstrução de índice e clique em **[!UICONTROL Next]**.

      >[!NOTE]
      >
      >O processo de recriação de índice é mais restritivo em termos de uso do processador e bloqueia os recursos do banco de dados. Selecione o **[!UICONTROL Keep index online while reindexing]** se desejar que o índice esteja disponível durante a reconstrução.

1. Selecione as opções que deseja exibir no relatório de atividade e clique em **[!UICONTROL Next]**.
1. Verifique a lista de tarefas configuradas para o plano de manutenção e clique em **[!UICONTROL Finish]**.

   É exibido um resumo do plano de manutenção e os status de suas várias etapas.

1. Depois de concluir o plano de manutenção, clique em **[!UICONTROL Close]**.
1. No explorador do Microsoft SQL Server, clique duas vezes no botão **[!UICONTROL Management > Maintenance Plans]** pasta.
1. Selecione o plano de manutenção do Adobe Campaign: as várias etapas são detalhadas em um workflow.

   Observe que um objeto foi criado na variável **[!UICONTROL SQL Server Agent > Jobs]** pasta. Esse objeto permite iniciar o plano de manutenção. No nosso exemplo, há apenas um objeto, pois todas as tarefas de manutenção fazem parte do mesmo plano.

   >[!IMPORTANT]
   >
   >Para que esse objeto seja executado, o agente do Microsoft SQL Server deve estar habilitado.

**Configurar um banco de dados separado para tabelas de trabalho**

>[!NOTE]
>
>Essa configuração é opcional.

A opção **WdbcOptions_TempDbName** permite configurar um banco de dados separado para tabelas de trabalho no Microsoft SQL Server. Isso otimiza os backups e a replicação.

Essa opção pode ser usada se desejar que as tabelas de trabalho (por exemplo, as tabelas criadas durante a execução de um workflow) sejam criadas em outro banco de dados.

Ao definir a opção como &quot;tempdb.dbo.&quot;, as tabelas de trabalho são criadas no banco de dados temporário padrão do Microsoft SQL Server. O administrador do banco de dados precisa permitir acesso de gravação ao banco de dados tempdb.

Se a opção estiver definida, ela será usada em todos os bancos de dados do Microsoft SQL Server configurados no Adobe Campaign (banco de dados principal e contas externas). Observe que se duas contas externas compartilharem o mesmo servidor, podem ocorrer conflitos (já que o tempdb é exclusivo). Da mesma forma, se duas instâncias do Campaign usarem o mesmo servidor MSSQL, poderá haver conflitos se usarem o mesmo tempdb.
