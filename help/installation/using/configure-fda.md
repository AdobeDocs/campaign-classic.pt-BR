---
product: campaign
title: Configurar conectores FDA
description: Saiba mais sobre as etapas de configuração do FDA
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 41%

---

# Configuração de conectores FDA {#specific-configurations-by-database-type}



Dependendo dos bancos de dados externos que você deseja acessar do Adobe Campaign, você precisará realizar algumas configurações específicas. Essas configurações envolvem basicamente a instalação de drivers e a declaração de variáveis de ambiente pertencentes a cada RDBMS no servidor do Adobe Campaign.

Como regra geral, você precisa instalar a camada de cliente correspondente no banco de dados externo no servidor do Adobe Campaign.

>[!NOTE]
>
>Versões compatíveis são listadas na [Matriz de Compatibilidade do Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

## Etapas de configuração {#fda-configuration-steps}

Para definir o acesso a um banco de dados externo com FDA, as etapas de configuração são:

1. Instale os drivers e configure a conta externa que corresponde ao banco de dados no servidor do Adobe Campaign. Consulte as páginas específicas do banco de dados [listado abaixo](#fda-specific-configuration)
1. Teste a conta externa ou crie uma conexão temporária entre o Adobe Campaign e o banco de dados externo. [Saiba mais](../../installation/using/connecting-to-database.md)
1. Criar o schema do banco de dados externo no Adobe Campaign. Isso permite identificar a estrutura de dados do banco de dados externo. [Saiba mais](../../installation/using/creating-data-schema.md)
1. Se necessário, crie um novo target mapping do schema criado anteriormente. Isso é necessário se os recipients dos seus deliveries vierem do banco de dados externo. Essa implementação vem com limitações relacionadas à personalização da mensagem. [Saiba mais](../../installation/using/defining-data-mapping.md)

Após a criação do schema de dados, é possível processar os dados nos workflows do Adobe Campaign. Para obter mais informações, consulte [esta seção](../../workflow/using/accessing-an-external-database--fda-.md).

## Configuração específica do banco de dados {#fda-specific-configuration}

Dependendo dos bancos de dados externos que você deseja acessar do Adobe Campaign, você precisará realizar algumas configurações específicas. Essas configurações envolvem basicamente a instalação de drivers e a declaração de variáveis de ambiente pertencentes a cada RDBMS no servidor do Adobe Campaign e a configuração da conta externa.

Siga os links abaixo para saber mais:

* Conectar o Campaign e [Azure synapse](../../installation/using/configure-fda-synapse.md)
* Conectar o Campaign e [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Conectar o Campaign e [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Conectar o Campaign e [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)
* Conectar o Campaign e [Netezza](../../installation/using/configure-fda-netezza.md)
* Conectar o Campaign e [Oracle](../../installation/using/configure-fda-oracle.md)
* Conectar o Campaign e [PostgreSQL](../../installation/using/configure-fda-postgresql.md)
* Conectar o Campaign e [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Conectar o Campaign e [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Conectar o Campaign e [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Conectar o Campaign e [Teradata](../../installation/using/configure-fda-teradata.md)
* Conectar o Campaign e [Verticas analytics](../../installation/using/configure-fda-vertica.md)
