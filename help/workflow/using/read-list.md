---
title: Lista de leitura
seo-title: Lista de leitura
description: Lista de leitura
seo-description: null
page-status-flag: never-activated
uuid: 34e28675-f28b-407f-8d60-41a5383af0db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 96a7aea4-4799-4ac7-8dff-666b075a1c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Lista de leitura{#read-list}

Os dados processados em um workflow podem vir de listas em que os dados foram preparados ou estruturados antecipadamente (após uma segmentação ou carregamento de arquivo anterior).

The **[!UICONTROL Read list]** activity lets you copy the data from a list in the workflow worktable, like data from a query. Ele é então acessível através do workflow.

The list to be processed can be specified explicitly, computed by a script or localized dynamically, according to options selected and parameters defined in a **[!UICONTROL Read list]** activity.

![](assets/list_edit_select_option_01.png)

Se a lista não for especificada explicitamente, você deve fornecer uma lista para ser usada como template para descobrir sua estrutura.

![](assets/s_advuser_list_template_select.png)

Once the list selection has been configured, you can add a filter using the **[!UICONTROL Edit query]** option to keep one part of the population for the next workflow.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>Para poder criar um filtro em uma atividade de lista de leitura, a lista relevante deve ser um tipo de &quot;arquivo&quot;.

The lists can be created directly in Adobe Campaign via the **[!UICONTROL Profiles and Targets > Lists]** link of the home page. They can also be created in a workflow using the **[!UICONTROL List update]** activity.

**Exemplo: Excluir uma lista de endereços de envio**

O exemplo a seguir permite usar uma lista de endereços de email para excluir do target de delivery de email.

![](assets/s_advuser_list_read_sample_1.png)

Os perfis contidos na pasta **Novos Contatos** devem ser target de uma ação de delivery. Os endereços de email a serem excluídos do target são armazenados em uma lista externa. Em nosso exemplo, somente as informações sobre endereços de email são necessárias para exclusão.

1. O query de seleção da pasta **Novos Contatos** permite carregar os endereços de email dos perfis selecionados para habilitar o alinhamento com as informações na lista.

   ![](assets/s_advuser_list_read_sample_0.png)

1. Aqui, a lista é armazenada na pasta **Listas** e seu rótulo é calculado.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Para excluir os endereços de email da lista externa do target principal, você deve configurar a atividade de exclusão e especificar que a pasta **New Contacts** contém os dados a serem mantidos. Os dados conjuntos entre esse conjunto e qualquer outro conjunto de entrada da atividade de exclusão serão excluídos do target.

   ![](assets/s_advuser_list_read_sample_3.png)

   As regras de exclusão são configuradas na seção central da ferramenta de edição. Click the **[!UICONTROL Add]** button to define the type of exclusion to be applied.

   Você pode definir várias exclusões dependendo do número de transições de entrada da atividade.

1. In the **[!UICONTROL Exclusion set]** field, select the **[!UICONTROL Read list]** activity: the data in this activity is to be excluded from the main set.

   No nosso exemplo, temos uma exclusão em junções: os dados contidos na lista serão reconciliados com os dados do conjunto principal através do campo com o endereço de email. Para configurar a junção, selecione **[!UICONTROL Joins]** no **[!UICONTROL Change dimension]** campo.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Em seguida, selecione o campo correspondente ao endereço de email nos dois conjuntos (Origem e Destino). As colunas serão vinculadas e os recipients cujo endereço de email estiver na lista de endereços importados serão excluídos do target.

