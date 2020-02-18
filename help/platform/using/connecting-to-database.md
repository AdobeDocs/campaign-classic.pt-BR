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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4969c5e56f1911b3abfd770ca4f8f5ed25784a52

---


# Conexão com o banco de dados {#connecting-to-the-database}

Para habilitar uma conexão com o banco de dados externo, você deve indicar os parâmetros de conexão, ou seja, a fonte de dados direcionada e o nome da tabela com os dados que exigem carregamento.

>[!CAUTION]
>
>O usuário do Adobe Campaign precisa de direitos específicos para o banco de dados externo e o servidor de aplicativos do Adobe Campaign para processar dados de um banco de dados externo. Para obter mais informações, consulte a seção Direitos [de acesso ao banco de dados](#remote-database-access-rights) remoto.
>
>Para evitar mau funcionamento, os operadores que acessam dados compartilhados remotos devem trabalhar em espaços separados.

## Criação de uma conexão compartilhada {#creating-a-shared-connection}

Para habilitar uma conexão com um banco de dados externo compartilhado, desde que essa conexão esteja ativa, o banco de dados pode ser acessado pelo Adobe Campaign.

1. The configuration must be defined beforehand via the **[!UICONTROL Administration > Platform > External accounts]** node.
1. Clique no **[!UICONTROL New]** botão e selecione o **[!UICONTROL External database]** tipo.
1. Define the **[!UICONTROL Connection]** parameters of the external database.

   For connections to an **ODBC** type database the **[!UICONTROL Server]** field must contain the name of the ODBC data source and not the server name. Além disso, algumas configurações adicionais podem ser necessárias, dependendo dos bancos de dados usados. Consulte a seção Configurações [específicas por tipo](#specific-configurations-by-database-type) de banco de dados.

1. Once the parameters are entered, click the **[!UICONTROL Test the connection]** button to approve them.

   ![](assets/wf-external-account-create.png)

1. If necessary, uncheck the **[!UICONTROL Enabled]** option to disable access to this database without deleting its configuration.
1. Para permitir que o Adobe Campaign acesse esse banco de dados, você deve implantar as funções SQL. Clique na **[!UICONTROL Parameters]** guia e no **[!UICONTROL Deploy functions]** botão.

   ![](assets/wf-external-account-functions.png)

You can define specific work tablespaces for the tables and for the index in the **[!UICONTROL Parameters]** tab.

## Como criar uma conexão temporária {#creating-a-temporary-connection}

Você pode definir diretamente uma conexão com um banco de dados externo a partir de atividades do workflow. Nesse caso, ele estará em um banco de dados externo local, reservado para ser usado em um workflow atual, ou seja, não será salvo nas contas externas. Esse tipo de conexão pontual pode ser criada em diferentes atividades do fluxo de trabalho, especialmente **[!UICONTROL Query]** a atividade, a **[!UICONTROL Data loading (RDBMS)]**, a **[!UICONTROL Enrichment]** atividade ou a **[!UICONTROL Split]** atividade.

>[!CAUTION]
>
>Esse tipo de configuração não é recomendado, mas pode ser utilizado periodicamente para coletar dados. No entanto, você deve criar uma conta externa, conforme apresentada na seção [Criação de uma conexão compartilhada](#creating-a-shared-connection).

Por exemplo, na atividade de query, as etapas para criar uma conexão periódica com um banco de dados externo são as seguintes:

1. Clique no link **[!UICONTROL Add data...]** e selecione as **[!UICONTROL External data]** opções.
1. Selecione a **[!UICONTROL Locally defining the data source]** opção.

   ![](assets/wf_add_data_local_external_data.png)

1. Selecione o mecanismo de banco de dados do Target na lista suspensa. Digite o nome do servidor e forneça os parâmetros de autenticação.

   Especifique também o nome do banco de dados externo.

   ![](assets/wf_add_data_local_external_data_param.png)

   Clique no botão **[!UICONTROL Next]**.

1. Selecione a tabela onde os dados estão armazenados.

   Você pode inserir o nome da tabela diretamente no campo correspondente ou clicar no ícone edição para acessar a lista das tabelas do banco de dados.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Click the **[!UICONTROL Add]** button to define one or several reconciliation fields between the external database data and the data in the Adobe Campaign database. Os **[!UICONTROL Edit expression]** ícones do **[!UICONTROL Remote field]** e **[!UICONTROL Local field]** fornecem acesso à lista de campos de cada uma das tabelas.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Se necessário, especifique uma condição de filtragem e o modo de classificação de dados.
1. Selecione os dados adicionais a serem coletados no banco de dados externo. To do this, double click on the fields(s) that you want to add to display them in the **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   Clique **[!UICONTROL Finish]** para confirmar esta configuração.

## Conexão segura {#secure-connection}

>[!NOTE]
>
>A conexão segura só está disponível para o PostgreSQL.

Você pode proteger o acesso a um banco de dados externo ao configurar uma conta FDA externa.

Para fazer isso, adicione &quot;**:ssl**&quot; após o endereço e o endereço do servidor da porta usada. Por exemplo: **192.168.0.52:4501:ssl**.

Os dados serão enviados por meio do protocolo SSL seguro.

## Configurações adicionais {#additional-configurations}

Se necessário, você pode criar o schema para processamento de dados em um banco de dados externo. Da mesma forma, o Adobe Campaign permite definir o mapeamento nos dados em uma tabela externa. Essas configurações são gerais e não se aplicam exclusivamente aos workflows.

>[!NOTE]
>
>Para obter mais informações sobre como criar schemas no Adobe Campaign e definir um novo mapeamento de dados, consulte [esta página](../../configuration/using/about-schema-edition.md).