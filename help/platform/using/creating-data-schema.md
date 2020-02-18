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
source-git-commit: 9a26ec7ed1c8463270ac9f97079f49e00d5b258e

---


# Criação do schema de dados {#creating-the-data-schema}

Para criar um esquema em um banco de dados externo:

1. Clique no **[!UICONTROL New]** botão acima da lista de esquemas de dados e escolha **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Insira um nome e uma descrição para o schema e selecione a conta externa que habilitará a conexão com o banco de dados. Isso permite o acesso à lista de tabelas disponíveis na base externa. Escolha a tabela que contém os dados a serem coletados.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Click **[!UICONTROL OK]** to confirm. O Adobe Campaign detecta automaticamente a estrutura da tabela selecionada e gera o schema lógico. Observe que o Adobe Campaign não gera links.

1. Click **[!UICONTROL Save]** to confirm creation.

   >[!CAUTION]
   >
   >Com Floco de neve, uma chave primária é obrigatória.

   ![](assets/wf_new_schema_generate_fda.png)

Os índices são criados automaticamente ao mapear uma tabela (mapeamento padrão ou FDA).
