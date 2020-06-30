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
translation-type: ht
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: ht
source-wordcount: '205'
ht-degree: 100%

---


# Desfazer a publicação de template{#template-unpublication}

Depois que um template de mensagem é publicado nas instâncias de execução, você pode desfazer a publicação.

Na verdade, um template publicado ainda pode ser chamado. Portanto, se você não estiver mais usando um template de mensagem, é recomendável desfazer a publicação. Dessa forma, você pode evitar o envio de uma mensagem transacional indesejada por engano. Por exemplo, você publicou um template de mensagem que só usa para campanhas de Natal. Talvez você queira desfazer a publicação depois que o período de Natal acabar e publicá-lo novamente no próximo ano.

Além disso, não é possível excluir um template de mensagem transacional que tenha o status **[!UICONTROL Published]**. Você deve desfazer a publicação primeiro.

Para desfazer a publicação de um template de mensagem transacional, siga as etapas abaixo.

1. Na instância de controle, vá para a pasta **[!UICONTROL Message Center > Transactional message templates]** da árvore.
1. Selecione o template do qual você deseja desfazer a publicação.
1. Clique em **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Clique em **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

O status do template de mensagem transacional muda de **[!UICONTROL Published]** para **[!UICONTROL Being edited]**.

Depois de desfazer a publicação:

* Ambos os templates de mensagem (aplicados a eventos de tipo em lote e em tempo real) são excluídos de cada instância de execução. Eles não aparecem mais na pasta **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]**.

* Quando a publicação de um template for desfeita, você poderá excluí-lo da instância de controle, se necessário. Para fazer isso, selecione-o na lista e clique no botão **[!UICONTROL Delete]** na parte superior direita da tela.