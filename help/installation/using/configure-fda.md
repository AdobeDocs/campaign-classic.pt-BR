---
solution: Campaign Classic
product: campaign
title: Configurar conectores FDA
description: Saiba mais sobre as etapas de configuração para FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 70%

---


# Configuração de conectores FDA {#specific-configurations-by-database-type}

Dependendo dos bancos de dados externos que você deseja acessar do Adobe Campaign, você precisará realizar algumas configurações específicas. Essas configurações envolvem basicamente a instalação de drivers e a declaração de variáveis de ambiente pertencentes a cada RDBMS no servidor do Adobe Campaign.

Como regra geral, você precisa instalar a camada de cliente correspondente no banco de dados externo no servidor do Adobe Campaign.

>[!NOTE]
>
>Versões compatíveis são listadas na [Matriz de Compatibilidade do Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).


## Etapas de configuração {#fda-configuration-steps}

Para configurar o acesso a um banco de dados externo com FDA, as etapas de configuração são:

1. Instalar os drivers que correspondem ao banco de dados no servidor do Adobe Campaign. Os drivers estão listados nas páginas específicas do banco de dados [listadas abaixo](#fda-specific-configuration).
1. [Criar e configurar uma conta externa](../../installation/using/connecting-to-database.md) que permita estabelecer a conexão entre o Adobe Campaign e o banco de dados externo. Para obter mais informações sobre contas externas na Campanha, consulte [esta página](../../installation/using/external-accounts.md).
1. [Criar o schema](../../installation/using/creating-data-schema.md) do banco de dados externo no Adobe Campaign. Isso permite reconhecer a estrutura de dados do banco de dados externo.
1. Se necessário, [crie um novo target mapping](../../installation/using/defining-data-mapping.md) a partir do schema criado anteriormente. Isso é necessário se os recipient de seus delivery forem provenientes do banco de dados externo. Essa implementação traz limitações relacionadas à personalização da mensagem.

Após a criação do schema de dados, é possível processar os dados nos workflows do Adobe Campaign. Para obter mais informações, consulte [esta seção](../../workflow/using/accessing-an-external-database--fda-.md).

## Configuração específica do banco de dados {#fda-specific-configuration}

Dependendo dos bancos de dados externos que você deseja acessar do Adobe Campaign, você precisará realizar algumas configurações específicas. Essas configurações envolvem basicamente a instalação de drivers e a declaração de variáveis de ambiente pertencentes a cada RDBMS no servidor do Adobe Campaign.

Siga os links abaixo para saber mais:

* [azure synapse](../../installation/using/configure-fda-synapse.md)

* [Snowflake](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [Netezza](../../installation/using/configure-fda-netezza.md)

* [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
