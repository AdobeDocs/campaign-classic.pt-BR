---
title: Gestão de Dados SQL
seo-title: Gestão de Dados SQL
description: Gestão de Dados SQL
seo-description: null
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Gestão de Dados SQL{#sql-data-management}

A atividade de **Gestão de Dados SQL** permite escrever seus próprios scripts SQL para criar e preencher tabelas de trabalho.

## Pré-requisitos {#prerequisites}

Antes de configurar a atividade, verifique se os pré-requisitos a seguir estão sendo cumpridos:

* A atividade está disponível somente para fontes de dados remotas. O pacote **[!UICONTROL FDA]** (Federated Data Access) deve, portanto, ser instalado em sua instância (consulte [esta seção](../../platform/using/about-fda.md)).
* O schema de saída deve existir no banco de dados e ser vinculado a um banco de dados do FDA (para obter mais informações sobre schemas de dados, consulte [esta seção](../../configuration/using/about-schema-reference.md)).
* O operador que executa o fluxo de trabalho deve ter o item **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** nomeado corretamente. Para saber mais sobre direitos nomeados, consulte [esta seção](../../platform/using/access-management.md#named-rights).

## Configurando a atividade de gestão de dados SQL {#configuring-the-sql-data-management-activity}

1. Especifique a atividade **[!UICONTROL Label]**.
1. Selecione a **[!UICONTROL External account]** a ser utilizada e selecione o **[!UICONTROL Outbound schema]** vinculado a esta conta externa.

   >[!CAUTION]
   >
   >O schema de saída está fixo e não pode ser editado.

1. Adicione o script SQL.

   >[!CAUTION]
   >
   >É a responsabilidade do gravador de script SQL garantir que o script SQL esteja funcional e que suas referências (nomes de campos, etc.) estejam de acordo com o schema de saída.

   Para carregar um código SQL existente, selecione a opção **[!UICONTROL The SQL script is contained in an entity stored in the database]**. Os scripts SQL devem ser criados e armazenados no menu **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]**.

   Caso contrário, digite ou copie e cole o script SQL na área dedicada.

   ![](assets/sql_datamanagement.png)

   A atividade permite usar as seguintes variáveis no script:

   * **activity.tableName**: nome SQL da tabela de trabalho de saída
   * **task.incomingTransitionByName(&#39;name&#39;).tableName**: nome SQL da tabela de trabalho transmitida pela transição recebida a ser utilizada (a transição é identificada pelo próprio nome).

      >[!NOTE]
      >
      >O valor (&#39;name&#39;) corresponde ao **[!UICONTROL Name]** campo das propriedades de transição.

1. Se o script SQL já tiver comandos para criar uma tabela de trabalho de saída, desmarque a opção **[!UICONTROL Automatically create work table]**. Caso contrário, uma tabela de trabalho será criada automaticamente quando o workflow for executado.
1. Clique em **[!UICONTROL Ok]** para confirmar a configuração da atividade.

A atividade está configurada agora. Ela está pronta para ser executada no workflow

>[!CAUTION]
>
>Ao executar a atividade, os registros de transição de saída são somente indicativos. Pode variar de acordo com o nível de complexidade do script SQL.
>  
>Se a atividade for reiniciada, todo o script será executado desde o seu início, independentemente do status de execução.

## Exemplos de script SQL {#sql-script-samples}

>[!NOTE]
>
>Os exemplos de script nesta seção dever ser executados em PostgreSQL.

O script abaixo permite criar uma tabela de trabalho e inserir dados nesta mesma tabela de trabalho:

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

O script abaixo permite executar uma operação CTAS (CREATE TABLE AS SELECT) e criar um índice de tabela de trabalho:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

O script abaixo permite mesclar duas tabelas de trabalho:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

