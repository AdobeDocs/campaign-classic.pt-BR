---
title: Criação de seed addresses
seo-title: Criação de seed addresses
description: Criação de seed addresses
seo-description: null
page-status-flag: never-activated
uuid: 0dae107a-7b53-4096-93c3-9517b402cbc9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 6dad49af-4818-471b-9df1-057cc6b9a68a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6483c3e2e9fd3a2951b2bc8bf6d8a3350361e86f
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 75%

---


# Criação de seed addresses{#creating-seed-addresses}

Seed addresses are not managed via standard profiles and targets, but in a dedicated node of the Adobe Campaign hierarchy **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Você pode criar subpastas para organizar os seed addresses. To do this, right-click the **[!UICONTROL Seed addresses]** node and select **[!UICONTROL Create a new 'Seed addresses' folder]**. Nomeie a subpasta e pressione **[!UICONTROL Enter]** para validar. Agora você pode criar ou copiar seed addresses para esta subpasta. Para obter mais informações, consulte [Definindo addresses](#defining-addresses).

O Adobe Campaign também permite criar templates de seed addresses que são importados para deliveries ou campanhas e adaptados com base nas necessidades específicas dos deliveries e campanhas relacionadas. Consulte [Criação de templates de seed address](#creating-seed-address-templates).

## Definição de endereços {#defining-addresses}

Para criar seed addresses, siga as etapas abaixo:

1. Clique no botão **[!UICONTROL New]** acima da lista de seed addresses.
1. Insira os dados vinculados ao endereço nos campos correspondentes da guia **[!UICONTROL Recipient]**. Os campos disponíveis correspondem aos campos padrão nos perfis dos recipients do delivery (tabela nms:recipient): sobrenome, nome, email, etc.

   >[!NOTE]
   >
   >O rótulo do endereço é preenchido automaticamente com o sobrenome e o nome que você definiu.
   >
   >Não é necessário inserir todos os campos de cada guia ao criar um seed address. Todos os elementos de personalização ausentes são inseridos aleatoriamente durante o delivery.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Na guia **[!UICONTROL Seed fields]**, insira os valores que serão inseridos nos logs de delivery durante a fase de análise (na tabela **[!UICONTROL nms:broadLog]**).

1. In the **[!UICONTROL Additional data]** tab, enter the personalization data used for the deliveries created in the Data management workflows and which you want to assign a specific value to.

   >[!NOTE]
   >
   >Verifique se dados adicionais do público alvo foram definidos com um alias que começa com &#39;@&#39; na **[!UICONTROL Enrichment]** atividade. Caso contrário, você não poderá usá-los corretamente com seus seeds addresses na atividade do delivery.

## Criação de templates de seed address {#creating-seed-address-templates}

Para criar templates de endereço que serão importados e podem ser modificados para cada delivery, o processo é o mesmo que definir um novo seed address. A única diferença é que os templates de seed address devem ser armazenados em uma pasta do tipo &#39;template&#39;.

Para definir uma pasta de template, siga o seguinte processo:

1. Create a new **[!UICONTROL Seed addresses]** type folder, right-click the folder then select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Clique na guia **[!UICONTROL Restriction]** e adicione a seguinte condição de filtragem: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Os endereços armazenados nesta pasta agora podem ser usados como templates de endereço. Você pode importá-los para deliveries ou campanhas e adaptá-los com base nas necessidades específicas de deliveries e campanhas relacionadas (consulte[Adição de seed addresses](../../delivery/using/adding-seed-addresses.md)).
