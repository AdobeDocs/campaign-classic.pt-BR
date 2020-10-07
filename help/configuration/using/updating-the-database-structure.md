---
title: Atualização da estrutura do banco de dados
seo-title: Atualização da estrutura do banco de dados
description: Atualização da estrutura do banco de dados
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 11%

---


# Atualização da estrutura do banco de dados{#updating-the-database-structure}

Para aplicar as modificações feitas nos schemas, inicie o assistente de atualização do banco de dados. Este assistente pode ser acessado via **[!UICONTROL Tools > Advanced > Update database structure]** . Ele verifica se a estrutura física do banco de dados corresponde à sua descrição lógica e executa os scripts de atualização do SQL.

![](assets/d_ncs_integration_schema_update.png)

Os módulos no banco de dados são automaticamente preenchidos e ativados.

![](assets/d_ncs_integration_schema_update_select.png)

As **[!UICONTROL Add stored procedures]** opções e **[!UICONTROL Import initialization data]** são usadas para iniciar os scripts SQL iniciais e os pacotes de dados executados quando o banco de dados é criado.

É possível importar um conjunto de dados de um pacote de dados externo. Para fazer isso, selecione **[!UICONTROL Import a package]** e insira o arquivo XML do pacote.

Siga as etapas e visualização o script SQL de atualização do banco de dados:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Isso está em um campo de edição e pode ser modificado para excluir ou adicionar o código SQL.

Em seguida, inicie a atualização do banco de dados:

![](assets/d_ncs_integration_schema_update3.png)

