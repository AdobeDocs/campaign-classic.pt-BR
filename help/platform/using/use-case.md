---
product: campaign
title: Caso de uso
description: Caso de uso
feature: Subscriptions, Email, Data Management
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 96%

---

# Caso de uso{#use-case}



## Criar um filtro no formato do email dos assinantes {#creating-a-filter-on-the-email-format-of-subscribers}

Este caso de uso demonstrará como criar um filtro para classificar assinaturas de informativo com base no formato do email do recipient.

Para fazer isso, precisamos usar um filtro predefinido: esses filtros estão vinculados a um tipo de documento e são acessados por meio do nó **[!UICONTROL Administration > Configuration > Predefined filters]**. Esses filtros de dados podem ser usados para cada tipo de editor (ou documento) no aplicativo.

Os filtros de dados são criados da mesma maneira que os filtros predefinidos, mas há um campo adicional para selecionar o tipo de documento no qual o filtro será aplicado.

Siga as etapas abaixo:

1. Crie um novo filtro através do nó **[!UICONTROL Administration > Configuration > Predefined filters]**.
1. Clique no ícone **[!UICONTROL Select link]** para selecionar o documento relacionado:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Selecione o esquema de subscrição (nms:subscription) e clique em **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Clique em **[!UICONTROL Edit link]** para exibir os campos do documento selecionado.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   É possível visualizar o conteúdo do documento selecionado:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Você pode acessar esses campos para definir condições de filtro no corpo do editor de filtro. Um filtro de aplicativo é definido exatamente da mesma maneira como um filtro avançado. Consulte [Criar um filtro avançado](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Crie um novo filtro em assinaturas para exibir somente assinaturas com um formato do email indefinido:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Clique em **[!UICONTROL Save]** para adicionar um filtro aos filtros predefinidos desse tipo de lista.
1. Agora é possível usar esse filtro na guia **[!UICONTROL Subscriptions]** do perfil do recipient e também acessar o filtro “Formato de email desconhecido”, clicando no botão **[!UICONTROL Filters]**.

   ![](assets/s_ncs_user_filter_on_events.png)

   O nome do filtro atual é exibido acima da lista. Para cancelar o filtro, clique no ícone **[!UICONTROL Delete this filter]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
