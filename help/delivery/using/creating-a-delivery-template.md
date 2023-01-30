---
product: campaign
title: Criar um modelo da entrega
description: Criar um modelo da entrega
feature: Delivery Templates
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
source-git-commit: 65e80f16a6beaee89b51636017c42766589e179e
workflow-type: ht
source-wordcount: '383'
ht-degree: 100%

---

# Criação de um modelo da entrega{#creating-a-delivery-template}

![](../../assets/common.svg)

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](#delivery-template-video)

## Conversão de uma entrega existente em um modelo {#converting-an-existing-delivery-to-a-template}

Uma entrega pode ser convertida em um modelo para novas ações de entrega repetidas. Para converter uma entrega em um template, selecione-a na lista de entrega, acessível por meio do nó **[!UICONTROL Campaign management]** da árvore.

Clique com o botão direito do mouse e selecione **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Essa ação cria um template de entrega a partir da entrega selecionada. Você deve inserir a pasta onde ele é salvo (no campo **[!UICONTROL Folder]**), bem como a pasta onde os deliveries criados com base neste template são criados (no campo **[!UICONTROL Execution folder]**).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Para obter mais informações sobre o modo de configuração, consulte [Vincular o modelo a uma entrega](creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Criação de um novo modelo {#creating-a-new-template}

>[!NOTE]
>
>Para evitar erros de configuração, a Adobe recomenda que você duplique um modelo nativo e personalize suas configurações ao invés de criar um novo modelo.

Para configurar um template de entrega, siga as seguintes etapas:

1. Abra o Campaign Explorer.
1. Na pasta **Resources**, selecione **Templates** e depois **Templates de entrega**.

   ![](assets/delivery_template_1.png)

1. Clique em **Novo** na barra de ferramentas para criar um novo modelo de entrega, ou **Duplique** um modelo existente.

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

1. Clique em **Save**. Seu template está pronto para ser usado em uma entrega.


## Tutoriais em vídeo {#delivery-template-video}

### Como configurar um template de entrega

O vídeo a seguir mostra como configurar um modelo para uma entrega ad hoc.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

### Como configurar propriedades de templates de entrega

O vídeo a seguir mostra como definir as propriedades do template de entrega e explica em detalhes cada propriedade.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

### Como implantar um template de entrega ad-hoc

Este vídeo explica como implantar um template de entrega de email ad-hoc, bem como a diferença entre uma entrega de email e um workflow de entrega.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
