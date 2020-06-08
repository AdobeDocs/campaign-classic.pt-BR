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
source-git-commit: 1486e897a125520c51661db3030c62ab380fb173
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 68%

---


# Publicação de template{#template-publication}

Quando o template de mensagem criado na instância de controle está concluído, é possível publicá-lo em todas as instâncias de execução. A publicação permite que você crie automaticamente dois modelos de mensagem na instância de execução, o que permitirá que você envie mensagens vinculadas a eventos batch e mensagens em tempo real.

>[!IMPORTANT]
>
>Lembre-se de publicar o template sempre que fizer alterações nele para que essas alterações sejam efetivas durante o delivery de mensagens transacionais.

>[!NOTE]
>
>Ao publicar templates de mensagem transacional, as regras de tipologia são publicadas automaticamente nas instâncias de execução.

1. In the control instance, go to the **[!UICONTROL Message Center > Transactional message templates]** folder of the tree.
1. Selecione o template que deseja publicar em suas instâncias de execução.
1. Clique em **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Once publication is complete, both message templates to be applied to batch and real-time type events are created in the tree of the production instance in the **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** folder.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Se você substituir um campo existente do template de mensagem transacional, como o endereço do remetente, com um valor vazio, o campo correspondente na instância de execução não será atualizado uma vez que a mensagem transacional seja publicada novamente. Ele ainda conterá o valor anterior. No entanto, se você adicionar um valor não vazio, o campo correspondente será atualizado como normal após a próxima publicação.
