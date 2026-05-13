---
product: campaign
title: Criação do schema de dados para FDA
description: Saiba como criar o esquema de dados para FDA
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
TQID: https://experienceleague.adobe.com/eC7jDm92g943ymcfEQjaeevS7qzIJWJR0zCtnP2Ny7o
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 189
ht-degree: 46%

---

# Criação do schema de dados {#creating-the-data-schema}



Para criar um esquema em um banco de dados externo:

1. Clique no botão **[!UICONTROL New]** acima da lista dos esquemas de dados e escolha **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Insira um **[!UICONTROL Namespace]** e **[!UICONTROL Name]** para o esquema e selecione o **[!UICONTROL External account]** que habilitará a conexão com o banco de dados. Isso permite o acesso à lista de tabelas disponíveis na base externa.

   ![](assets/wf_new_schema_select_table_fda.png)

1. No campo **[!UICONTROL Table name]**, escolha a tabela que contém os dados a serem coletados.

   Com o Snowflake, você pode selecionar aqui suas visualizações se o usuário do banco de dados tiver recebido os privilégios corretos. Observe que, ao usar visualizações, o Adobe Campaign não poderá gerar automaticamente o esquema XML. Você mesmo terá que criá-lo. Para obter mais informações sobre exibições, consulte a [documentação do Snowflake](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Clique em **[!UICONTROL OK]** para confirmar. O Adobe Campaign detecta automaticamente a estrutura da tabela selecionada e gera o esquema lógico. Observe que o Adobe Campaign não gera links.

1. Clique em **[!UICONTROL Save]** para confirmar a criação.

   >[!CAUTION]
   >
   >Com o Snowflake, uma chave primária é obrigatória.

   ![](assets/wf_new_schema_generate_fda.png)

Os índices são criados automaticamente ao mapear uma tabela (mapeamento padrão ou FDA).
