---
product: campaign
title: Criação do schema de dados para FDA
description: Saiba como criar o schema de dados para FDA
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 46%

---

# Criação do schema de dados {#creating-the-data-schema}

![](../../assets/v7-only.svg)

Para criar um schema em um banco de dados externo:

1. Clique no botão **[!UICONTROL New]** acima da lista dos schemas de dados e escolha **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Insira um **[!UICONTROL Namespace]** e  **[!UICONTROL Name]** para o schema e selecione o **[!UICONTROL External account]** que habilitará a conexão com o banco de dados. Isso permite o acesso à lista de tabelas disponíveis na base externa.

   ![](assets/wf_new_schema_select_table_fda.png)

1. No **[!UICONTROL Table name]** escolha a tabela que contém os dados a serem coletados.

   Com o Snowflake, você pode selecionar aqui suas exibições se o usuário do banco de dados tiver recebido os privilégios corretos. Observe que, ao usar exibições, o Adobe Campaign não poderá gerar automaticamente o esquema XML, você terá que criá-lo sozinho. Para obter mais informações sobre visualizações, consulte [Documentação do Snowflake](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Clique em **[!UICONTROL OK]** para confirmar. O Adobe Campaign detecta automaticamente a estrutura da tabela selecionada e gera o schema lógico. Observe que o Adobe Campaign não gera links.

1. Clique em **[!UICONTROL Save]** para confirmar a criação.

   >[!CAUTION]
   >
   >Com o Snowflake, uma chave primária é obrigatória.

   ![](assets/wf_new_schema_generate_fda.png)

Os índices são criados automaticamente ao mapear uma tabela (mapeamento padrão ou FDA).
