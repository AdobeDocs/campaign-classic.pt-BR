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
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# Direitos de acesso ao banco de dados remoto {#remote-database-access-rights}

Primeiro, para que o usuário possa realizar operações em um banco de dados externo por meio do FDA, esse último deve ter um direito nomeado específico no Adobe Campaign.

1. Selecione o **[!UICONTROL Administration > Access Management > Named Rights]** nó no Adobe Campaign explorer.
1. Crie um novo direito especificando o rótulo escolhido.
1. The **[!UICONTROL Name]** field must take the following format **user:base@server**, where :

   * **user** corresponde ao nome do usuário no banco de dados externo.
   * **base** corresponde ao nome do banco de dados externo.
   * **server** corresponde ao nome do servidor de banco de dados externo.

      >[!NOTE]
      >
      >A parte **:base** é opcional no Oracle.

1. Save the named right then link it to your chosen user from the **[!UICONTROL Administration > Access Management > Operators]** node of the Adobe Campaign explorer.

Em seguida, para processar os dados contidos em um banco de dados externo, o usuário do Adobe Campaign deve ter pelo menos direitos &quot;Write&quot; no banco de dados. Assim, ele poderá criar worktables. Eles são excluídos automaticamente pelo Adobe Campaign.

Em geral, são necessários os seguintes direitos:

* **CONNECT**: conexão ao banco de dados remoto,
* **READ Data**: acesso somente leitura a tabelas com dados do cliente,
* **READ &#39;MetaData&#39;**: acesso aos catálogos de dados do servidor para obter a estrutura da tabela,
* **LOAD**: carregamento em massa em tabelas de trabalho (necessário ao trabalhar em coleções e associações),
* **CREATE/DROP** para **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **EXPLAIN** (recomendado): para monitorar desempenhos em caso de problemas,
* **WRITE Data** (dependendo do cenário de integração).

>[!NOTE]
>
>O administrador do banco de dados precisa combinar esses direitos com os direitos específicos de cada mecanismo de banco de dados. Para obter mais informações, consulte os [direitos específicos do RDBMS](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html).