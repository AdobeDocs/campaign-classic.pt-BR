---
title: Acesso a um banco de dados externo
seo-title: Acesso a um banco de dados externo
description: Acesso a um banco de dados externo
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '273'
ht-degree: 100%

---


# Opções adicionais {#additional-options}

<!--

## HTTP relay to a remote instance {#http-relay-to-a-remote-instance}

You can access external databases configured in remote instances using the HTTP protocol.

>[!NOTE]
>
>Not all SQL data types are supported by this feature. Blob data types are not supported at all. It is possible that other data types may not work depending on the targeted database (Timestamp on Microsoft SQL Server, for example). Please contact Adobe support for more information.

This simplifies transferring and synchronizing data between two instances. It also enables you to sidestep any tunneling between an instance and a remote database as well as the installation of the client layers to access this database. The destination instance can be a hosted instance.

>[!CAUTION]
>
>This option is only for facilitating data replication flows (ETL).   
>
>For example, it allows a cloud-hosted instance to have direct access to the data in an "on-premise" hosted database. However, it is not intended to allow targeting to be carried on an "on-premise" hosted database directly from the cloud.

To do this, you must configure the external accounts of the two instances so that the local instance can communicate with the remote instance using the HTTP protocol:

* Local instance: select the new **[!UICONTROL HTTP relay to a remote database]** connection type.

  In case of bulk load data transfer, also specify the buffer size. Select the compression option if you want to reduce the size of the transferred data.

  The **[!UICONTROL Data source]** must be defined with the following syntax: "nms:extAccount : `<internal_name_of_the_external_account>`"

  ![](assets/fda_over_http_1.png)

  >[!NOTE]
  >
  >We recommend that you use an HTTPS connection.

* Remote instance: in the FDA external account of the database accessed via the HTTP relay, check the Target of an **[!UICONTROL 'HTTP relay to a remote database' account option]**.

  ![](assets/fda_over_http_2.png)

The following example shows the new possible operating mode:

![](assets/schema_fda_over_http_2.png)

>[!CAUTION]
>
>The default database of the remote instance must be accessed via an external account as well.

This operating method avoids that the cleanup workflow of each instance deletes the work tables of the databases that use the instance as relay.

Thus, in the previous example, the cleanup workflow of the remote instance will not perform any action on the red FDA database as it is used by the local instance.

-->

## Criação direta de schemas temporários {#directly-creating-temporary-schemas}

Se você deseja gerenciar vários acessos a um banco de dados externo do FDA, uma nova opção permite criar um schema de trabalho diretamente ao configurar uma conta externa.

>[!NOTE]
>
>Essa opção funciona somente com PostgreSQL.

![](assets/fda_work_table.png)

## Otimização da personalização de e-mail com dados externos {#optimizing-email-personalization-with-external-data}

Na build 8740, agora a opção **[!UICONTROL Prepare the personalization data with a workflow]** está disponível na guia **[!UICONTROL Analysis]** das propriedades de delivery.

Durante a análise de delivery, essa opção cria e executa automaticamente um workflow que armazena todos os dados vinculados ao Target em uma tabela temporária, incluindo dados de tabelas vinculadas na FDA.

Ao selecionar essa opção, é possível obter um aumento significativo no desempenho para executar a personalização.

## Uso de dados de um banco de dados externo em um workflow {#using-data-from-an-external-database-in-a-workflow}

Em várias atividades de workflow do Adobe Campaign, você pode usar os dados armazenados em um banco de dados externo.

### Filtragem em dados externos {#filtering-on-external-data}

A atividade query permite adicionar dados externos e usá-los nas configurações de filtro definidas.

Para obter mais informações, consulte a seção [Query](../../workflow/using/targeting-data.md#selecting-data).

### Criação de subconjuntos {#creating-sub-sets}

A atividade dividida permite criar subconjuntos. Você pode usar dados externos para definir os critérios de filtragem a serem usados.

Para obter mais informações, consulte a seção [Split](../../workflow/using/split.md).

### Carregamento de banco de dados externo {#loading-external-database}

Você pode utilizar os dados externos no carregamento de dados (RDBMS). Essa atividade é apresentada na seção [Carregamento de dados](../../workflow/using/data-loading--rdbms-.md).

### Adição de informações e links {#adding-information-and-links}

A atividade de enriquecimento permite incluir dados adicionais na mesa de trabalho do workflow, como também links para uma tabela externa. Por esse motivo, é possível explorar os dados de um banco de dados externo. Essa atividade é apresentada na seção [Enriquecimento](../../workflow/using/enrichment.md) .
<!--

## Cloud Messaging - FDA synchronization {#cloud-messaging---fda-synchronization}

When the Cloud Messaging server and the Marketing server have not been synchronized for a long period, the volume of missing broadlogs on the Marketing server can be significant. To optimize broadlog synchronization via the FDA, the **NmsMidSourcing_LogsPeriodHour** option has been added. This allows a maximum period (expressed in hours) to be specified as to limit the number of broadlogs recovered every time the synchronization workflow is executed.

The option is to be added in the console, in the **[!UICONTROL Administration > Options]** node.

>[!CAUTION]
>
>This option must **only** be used for synchronizing a significant volume of broadlogs via the FDA.

>[!NOTE]
>
>The option is only taken into account if a last recovery date exists (**NmsMidSourcing_LastBroadLog_&#42;** option).

## Message Center - Read access on the XtkFolder table {#message-center---read-access-on-the-xtkfolder-table}

From build 8141 and above, manual action is necessary if Message Center uses the FDA as an archiving mode.

You need to grant read access on the XtKFolder table to the user linked with the external FDA account.

For a PostgreSQL database for example, the command is as follows:

```
GRANT SELECT ON XtkFolder TO DBUSER;
```

This user must have read access to the following tables:

* NmsBroadLogRtEvent
* NmsBroadLogBatchEvent
* NmsTrackingLogRtEvent
* NmsTrackingLogBatchEvent
* NmsRtEvent
* NmsBatchEvent
* NmsBroadLogMsg
* NmsTrackingUrl
* NmsDelivery
* NmsWebTrackingLog

>[!NOTE]
>
>This modification deletes the "Permission denied for relation xtkfolder" error message.

If the working schema selected in the external FDA account is not the out-of-the-box Neolane account, then this modification to the access rights is not necessary.

-->

