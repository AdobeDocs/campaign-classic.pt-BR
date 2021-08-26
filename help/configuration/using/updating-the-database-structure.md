---
product: campaign
title: Atualização da estrutura do banco de dados
description: Atualização da estrutura do banco de dados
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# Atualização da estrutura do banco de dados{#updating-the-database-structure}

![](../../assets/v7-only.svg)

Para aplicar as modificações feitas nos schemas, inicie o assistente de atualização do banco de dados. Este assistente pode ser acessado por meio de **[!UICONTROL Tools > Advanced > Update database structure]** . Verifica se a estrutura física do banco de dados corresponde à sua descrição lógica e executa os scripts de atualização SQL.

![](assets/d_ncs_integration_schema_update.png)

Os módulos no banco de dados são automaticamente preenchidos e ativados.

![](assets/d_ncs_integration_schema_update_select.png)

As opções **[!UICONTROL Add stored procedures]** e **[!UICONTROL Import initialization data]** são usadas para iniciar os scripts SQL iniciais e os pacotes de dados executados quando o banco de dados é criado.

É possível importar um conjunto de dados de um pacote de dados externo. Para fazer isso, selecione **[!UICONTROL Import a package]** e insira o arquivo XML do pacote.

Siga as etapas e exiba o script SQL de atualização do banco de dados:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Isso está em um campo de edição e pode ser modificado para excluir ou adicionar código SQL.

Em seguida, inicie a atualização do banco de dados:

![](assets/d_ncs_integration_schema_update3.png)
