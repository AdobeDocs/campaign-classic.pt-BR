---
title: Publicação de template
seo-title: Publicação de template
description: Publicação de template
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---


# Cancelamento da publicação do modelo{#template-unpublication}

Depois que um modelo de mensagem é publicado nas instâncias de execução, ele pode ser despublicado.

Na verdade, um modelo publicado ainda pode ser chamado. Portanto, se você não estiver mais usando um modelo de mensagem, é recomendável cancelar a publicação. Isto é para evitar enviar um mensagen transacional indesejado por engano. Por exemplo, você publicou um modelo de mensagem que só usa para campanhas de Natal. Talvez você queira desfazer a publicação depois que o período de Natal acabar e publicá-lo novamente no próximo ano.

Além disso, não é possível excluir um template de mensagem transacional que tenha o **[!UICONTROL Published]** status. Você deve cancelar a publicação primeiro.

Para cancelar a publicação de um template de mensagem transacional, siga as etapas abaixo.

1. In the control instance, go to the **[!UICONTROL Message Center > Transactional message templates]** folder of the tree.
1. Selecione o modelo que deseja cancelar a publicação.
1. Clique em **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Clique em **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

O status do template de mensagem transacional muda de **[!UICONTROL Published]** volta para **[!UICONTROL Being edited]**.

Após a conclusão da publicação:

* Ambos os modelos de mensagem (aplicados a eventos de tipo em lote e em tempo real) são excluídos de cada instância de execução. Eles não aparecem mais na **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** pasta.

* Quando um modelo não for publicado, você poderá excluí-lo da instância de controle, se necessário. Para fazer isso, selecione-o na lista e clique no **[!UICONTROL Delete]** botão na parte superior direita da tela.