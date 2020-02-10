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
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Criação de seed addresses{#creating-seed-addresses}

Seed addresses are not managed via standard profiles and targets, but in a dedicated node of the Adobe Campaign hierarchy **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Você pode criar subpastas para organizar os seed addresses. Para fazer isso, clique com o botão direito do mouse no **[!UICONTROL Seed addresses]** nó e selecione **[!UICONTROL Create a new 'Seed addresses' folder]**. Name the sub-folder and then press **[!UICONTROL Enter]** to validate. Agora você pode criar ou copiar seed addresses para esta subpasta. For more on this, refer to [Defining addresses](#defining-addresses).

O Adobe Campaign também permite criar templates de seed addresses que são importados para deliveries ou campanhas e adaptados com base nas necessidades específicas dos deliveries e campanhas relacionadas. Consulte [Criação de modelos](#creating-seed-address-templates)de endereço semente.

## Definição de endereços {#defining-addresses}

Para criar seed addresses, siga as etapas abaixo:

1. Click the **[!UICONTROL New]** button above the list of seed addresses.
1. Enter the data linked to the address in the matching fields from the **[!UICONTROL Recipient]** tab. Os campos disponíveis correspondem aos campos padrão nos perfis dos recipients do delivery (tabela nms:recipient): sobrenome, nome, email, etc.

   >[!NOTE]
   >
   >O rótulo do endereço é preenchido automaticamente com o sobrenome e o nome que você definiu.
   >
   >Não é necessário inserir todos os campos de cada guia ao criar um seed address. Todos os elementos de personalização ausentes são inseridos aleatoriamente durante o delivery.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. In the **[!UICONTROL Seed fields]** tab, enter the values that will be inserted in the delivery logs during the analysis phase (in the **[!UICONTROL nms:broadLog]** table).
1. In the **[!UICONTROL Additional data]** tab, enter the personalization data used for the deliveries created in the Datamanagement workflows and which you want to assign a specific value to.

## Criação de templates de seed address {#creating-seed-address-templates}

Para criar templates de endereço que serão importados e podem ser modificados para cada delivery, o processo é o mesmo que definir um novo seed address. A única diferença é que os templates de seed address devem ser armazenados em uma pasta do tipo &#39;template&#39;.

Para definir uma pasta de template, siga o seguinte processo:

1. Create a new **[!UICONTROL Seed addresses]** type folder, right-click the folder then select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Clique na **[!UICONTROL Restriction]** guia e adicione a seguinte condição de filtragem: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Os endereços armazenados nesta pasta agora podem ser usados como templates de endereço. You can import them into deliveries or campaigns and adapt them based on the specific needs of the concerned deliveries and campaigns (see [Adding seed addresses](../../delivery/using/adding-seed-addresses.md)).
