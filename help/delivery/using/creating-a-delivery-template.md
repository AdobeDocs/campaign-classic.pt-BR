---
product: campaign
title: Criar um modelo da entrega
description: Criar um modelo da entrega
feature: Delivery Templates
hide: true
role: User
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
TQID: https://experienceleague.adobe.com/5rlrthjXAnU8yfU1z67u-7uD0Z-pRfm0-Or5q7PBs-Q
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 391
ht-degree: 100%

---

# Criação de um modelo da entrega{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [Conheça este recurso no vídeo](#delivery-template-video)

## Conversão de uma entrega existente em um modelo {#converting-an-existing-delivery-to-a-template}

Uma entrega pode ser convertida em um modelo para novas ações de entrega repetidas. Para converter uma entrega em um modelo, selecione-a na lista de entrega, acessível por meio do nó **[!UICONTROL Campaign management]** da árvore.

Clique com o botão direito do mouse e selecione **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Essa ação cria um modelo de entrega a partir da entrega selecionada. Você deve inserir a pasta onde ele é salvo (no campo **[!UICONTROL Folder]**), bem como a pasta onde as entregas criadas com base neste modelo são criadas (no campo **[!UICONTROL Execution folder]**).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Para obter mais informações sobre o modo de configuração, consulte [Vincular o modelo a uma entrega](creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Criação de um novo modelo {#creating-a-new-template}

>[!NOTE]
>
>Para evitar erros de configuração, a Adobe recomenda que você duplique um modelo nativo e personalize suas configurações ao invés de criar um novo modelo.

Para configurar um modelo de entrega, siga as seguintes etapas:

1. Abra o Campaign Explorer.
1. Na pasta **Resources**, selecione **Templates** e depois **Templates de entrega**.

   ![](assets/delivery_template_1.png)

1. Clique em **Novo** na barra de ferramentas para criar um novo modelo de entrega, ou **Duplique** um modelo existente.

   ![](assets/delivery_template_2.png)

1. Modifique o **Label** e o **Internal name** da pasta.
1. Salve seu modelo e abra-o novamente.
1. Clique no botão **Properties** e modifique os valores de acordo com suas necessidades.

   ![](assets/delivery_template_3.png)

1. Na guia **General**, confirme ou altere os locais selecionados nos menus suspensos **Execution folder**, **Folder**, e **Routing.**

   ![](assets/delivery_template_4.png)

1. Complete a categoria **Email parameters** com o assunto do email e a população de destino.
1. Adicione seu **HTML** content para personalizar seu modelo, você pode exibir um link de mirror page e um link de unsubscription.
1. Selecione a guia **Preview.** No menu suspenso **Test personalization**, selecione **Destinatário** para visualizar seu modelo como o perfil escolhido.

   ![](assets/delivery_template_5.png)

1. Clique em **Save**. Seu modelo está pronto para ser usado em uma entrega.


## Tutoriais em vídeo {#delivery-template-video}

### Como configurar um modelo de entrega

O vídeo a seguir mostra como configurar um modelo para uma entrega ad hoc.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

### Como configurar propriedades de modelos de entrega

O vídeo a seguir mostra como definir as propriedades do modelo de entrega e explica em detalhes cada propriedade.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

### Como implantar um modelo de entrega ad-hoc

Este vídeo explica como implantar um modelo de entrega de email ad-hoc, bem como a diferença entre uma entrega de email e um fluxo de trabalho de entrega.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
