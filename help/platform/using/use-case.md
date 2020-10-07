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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 91%

---


# Caso de uso{#use-case}

## Criação de um filtro no formato de email dos assinantes {#creating-a-filter-on-the-email-format-of-subscribers}

Este caso de uso irá demonstrar como criar um filtro para classificar assinaturas de boletim informativo com base no formato do email do destinatário.

Para fazer isso, precisamos usar um filtro predefinido: esses filtros estão vinculados a um tipo de documento e são acessados por meio do nó **[!UICONTROL Administration > Configuration > Predefined filters]**. Esses filtros de dados podem ser usados para cada tipo de editor (ou documento) no aplicativo.

Os filtros de dados são criados da mesma maneira que os filtros predefinidos, mas há um campo adicional para selecionar o tipo de documento no qual o filtro será aplicado.

Siga as etapas abaixo:

1. Create a new filter via the **[!UICONTROL Administration > Configuration > Predefined filters]** node.
1. Click the **[!UICONTROL Select link]** icon to select the concerned document:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Selecione o esquema de subscrição (nms:subscription) e clique em **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Clique em **[!UICONTROL Edit link]** para exibir os campos do documento selecionado.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   É possível visualizar o conteúdo do documento selecionado:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Você pode acessar esses campos para definir condições de filtro no corpo do editor de filtro. Um filtro de aplicativo é definido exatamente da mesma maneira como um filtro avançado. Consulte [Criar um filtro avançado](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Crie um novo filtro em assinaturas para exibir somente assinaturas com um formato de email indefinido:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Clique em **[!UICONTROL Save]** para adicionar um filtro aos filtros predefinidos desse tipo de lista.
1. Agora você pode usar esse filtro na guia **[!UICONTROL Subscriptions]** do perfil do recipient e também acessar o filtro &quot;Unknown e-mail format&quot; clicando no botão **[!UICONTROL Filters]**.

   ![](assets/s_ncs_user_filter_on_events.png)

   O nome do filtro atual é exibido acima da lista. To cancel the filter, click the **[!UICONTROL Delete this filter]** icon.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

