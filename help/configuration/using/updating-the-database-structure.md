---
product: campaign
title: Atualização da estrutura do banco de dados
description: Atualização da estrutura do banco de dados
feature: Configuration
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# Atualização da estrutura do banco de dados{#updating-the-database-structure}



Para aplicar as modificações feitas nos esquemas, inicie o assistente de atualização de banco de dados. Este assistente pode ser acessado via **[!UICONTROL Tools > Advanced > Update database structure]** . Ele verifica se a estrutura física do banco de dados corresponde à sua descrição lógica e executa os scripts de atualização SQL.

![](assets/d_ncs_integration_schema_update.png)

Os módulos no banco de dados são automaticamente preenchidos e ativados.

![](assets/d_ncs_integration_schema_update_select.png)

A variável **[!UICONTROL Add stored procedures]** e **[!UICONTROL Import initialization data]** As opções são usadas para iniciar os scripts SQL iniciais e os pacotes de dados executados quando o banco de dados é criado.

É possível importar um conjunto de dados de um pacote de dados externo. Para fazer isso, selecione **[!UICONTROL Import a package]** e insira o arquivo XML do pacote.

Siga as etapas e exiba o script SQL de atualização do banco de dados:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Está em um campo de edição e pode ser modificado para excluir ou adicionar o código SQL.

Em seguida, inicie a atualização do banco de dados:

![](assets/d_ncs_integration_schema_update3.png)
