---
product: campaign
title: Atualização da estrutura do banco de dados
description: Atualização da estrutura do banco de dados
feature: Configuration
role: Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
TQID: https://experienceleague.adobe.com/y4P6bZcEyVIdfI4LHMivPIRVzb1Z4sV7ewISWqk29F0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 137
ht-degree: 8%

---

# Atualização da estrutura do banco de dados{#updating-the-database-structure}



Para aplicar as modificações feitas nos esquemas, inicie o assistente de atualização de banco de dados. Este assistente pode ser acessado via **[!UICONTROL Tools > Advanced > Update database structure]**. Ele verifica se a estrutura física do banco de dados corresponde à sua descrição lógica e executa os scripts de atualização SQL.

![](assets/d_ncs_integration_schema_update.png)

Os módulos no banco de dados são automaticamente preenchidos e ativados.

![](assets/d_ncs_integration_schema_update_select.png)

As opções **[!UICONTROL Add stored procedures]** e **[!UICONTROL Import initialization data]** são usadas para iniciar os scripts SQL iniciais e os pacotes de dados executados quando o banco de dados é criado.

É possível importar um conjunto de dados de um pacote de dados externo. Para fazer isso, selecione **[!UICONTROL Import a package]** e insira o arquivo XML do pacote.

Siga as etapas e exiba o script SQL de atualização do banco de dados:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Está em um campo de edição e pode ser modificado para excluir ou adicionar o código SQL.

Em seguida, inicie a atualização do banco de dados:

![](assets/d_ncs_integration_schema_update3.png)
