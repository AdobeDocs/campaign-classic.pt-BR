---
title: Caso de uso
seo-title: Caso de uso
description: Caso de uso
seo-description: null
page-status-flag: never-activated
uuid: d4c76fdf-d562-4151-93ec-08b4f6563440
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: fbc38e33-60a6-4d21-a598-312293d168fb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Caso de uso{#use-case}

## Criação de um filtro no formato de email dos assinantes {#creating-a-filter-on-the-email-format-of-subscribers}

Este caso de uso irá demonstrar como criar um filtro para classificar assinaturas de boletim informativo com base no formato do email do destinatário.

To do this, we need to use a predefined filer: these filters are linked to a document type and are accessed via the **[!UICONTROL Administration > Configuration > Predefined filters]** node. Esses filtros de dados podem ser usados para cada tipo de editor (ou documento) no aplicativo.

Os filtros de dados são criados da mesma maneira que os filtros predefinidos, mas há um campo adicional para selecionar o tipo de documento no qual o filtro será aplicado.

Siga as etapas abaixo:

1. Crie um novo filtro pelo **[!UICONTROL Administration > Configuration > Predefined filters]** nó.
1. Click the **[!UICONTROL Select link]** icon to select the concerned document:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Select the subscription schema (nms:subscription) and click **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Click **[!UICONTROL Edit link]** to view the fields of the selected document.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   É possível visualizar o conteúdo do documento selecionado:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Você pode acessar esses campos para definir condições de filtro no corpo do editor de filtro. Um filtro de aplicativo é definido exatamente da mesma maneira como um filtro avançado. See [Creating an advanced filter](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Crie um novo filtro em assinaturas para exibir somente assinaturas com um formato de email indefinido:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Click **[!UICONTROL Save]** to add a filter to the pre-defined filters for this type of list.
1. You can now use this filter in the **[!UICONTROL Subscriptions]** tab of the recipient profile; you can access the &quot;Unknown e-mail format&quot; filter by clicking the **[!UICONTROL Filters]** button.

   ![](assets/s_ncs_user_filter_on_events.png)

   O nome do filtro atual é exibido acima da lista. Para cancelar o filtro, clique no **[!UICONTROL Delete this filter]** ícone.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

