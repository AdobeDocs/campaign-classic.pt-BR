---
title: Criação de um template de delivery
seo-title: Criação de um template de delivery
description: Criação de um template de delivery
seo-description: null
page-status-flag: never-activated
uuid: 8ceae1ec-9e02-4809-aa8b-1e6bd7790950
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 0e67d9dd-3ee8-4c06-98a4-3a2c644b6c0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a5711c4478f8378c079fec4792ecbb95266ad4b
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 77%

---


# Criação de um template de delivery{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso em vídeo](#delivery-template-video)

## Conversão de um delivery existente para um template {#converting-an-existing-delivery-to-a-template}

Um delivery pode ser convertido em um template para novas ações de delivery repetidas. Para converter um delivery em um template, selecione-o na lista de delivery, acessível por meio do nó **[!UICONTROL Campaign management]** da árvore.

Right-click and select **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Essa ação cria um template de delivery a partir do delivery selecionado. Você deve inserir a pasta onde ele é salvo (no campo **[!UICONTROL Folder]**), bem como a pasta onde os deliveries criados com base neste template são criados (no campo **[!UICONTROL Execution folder]**).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Para obter mais informações sobre o modo de configuração, consulte [Vincular o template a um delivery](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Criação de um novo modelo {#creating-a-new-template}

Para configurar um template de delivery, siga as seguintes etapas:

1. Abra o Campaign Explorer.
1. Na pasta **Resources**, selecione **Templates** e depois **Delivery templates**.

   ![](assets/delivery_template_1.png)

1. Clique em **New** na barra de ferramentas para criar um novo template de delivery.

   ![](assets/delivery_template_2.png)

1. Modifique o **Label** e o **Internal name** da pasta.
1. Salve seu template e abra-o novamente.
1. Clique no botão **Properties** e modifique os valores de acordo com suas necessidades.

   ![](assets/delivery_template_3.png)

1. Na guia **General**, confirme ou altere os locais selecionados nos menus suspensos **Execution folder**, **Folder**, e **Routing.**

   ![](assets/delivery_template_4.png)

1. Complete a categoria **Email parameters** com o assunto do email e o público alvo.
1. Adicione seu **HTML** content para personalizar seu template, você pode exibir um link de mirror page e um link de unsubscription.
1. Selecione a guia **Preview.** No menu suspenso **Test personalization**, selecione **Recipient** para visualizar seu template como o perfil escolhido.

   ![](assets/delivery_template_5.png)

1. Clique em **Save**. Seu template está pronto para ser usado em um delivery.

>[!NOTE]
>
>Para evitar erros de configuração, recomendamos que você duplique um modelo nativo e altere suas propriedades em vez de criar um novo template.

## Como configurar um template do delivery {#delivery-template-video}

O vídeo a seguir demonstra como configurar um modelo para um delivery ad hoc.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

## Como configurar propriedades de templates do delivery

O vídeo a seguir mostra como definir as propriedades do template do delivery e explica cada propriedade em detalhes.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

## Como implantar um template do delivery ad-hoc

Este vídeo explica como implantar um template do delivery de email ad-hoc e explica a diferença entre um delivery de email e um fluxo de trabalho de delivery.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)
