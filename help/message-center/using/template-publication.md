---
solution: Campaign Classic
product: campaign
title: Publicação de template
description: publicação de templates de mensagem transacionais
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 98%

---


# Publicação de template{#template-publication}

Quando o template de mensagem criado na instância de controle está concluído, é possível publicá-lo em todas as instâncias de execução. A publicação permite criar automaticamente dois templates de mensagem na instância de execução, o que permitirá enviar mensagens vinculadas a eventos batch e em tempo real.

>[!IMPORTANT]
>
>Lembre-se de publicar o template sempre que fizer alterações nele para que essas alterações sejam efetivas durante o delivery de mensagens transacionais.

>[!NOTE]
>
>Ao publicar templates de mensagem transacional, as regras de tipologia são publicadas automaticamente nas instâncias de execução.

1. Na instância de controle, vá para a pasta **[!UICONTROL Message Center > Transactional message templates]** da árvore.
1. Selecione o template que deseja publicar em suas instâncias de execução.
1. Clique em **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Quando a publicação estiver concluída, ambos os templates de mensagem que serão aplicados em eventos batch e em tempo real são criados na árvore da instância de produção na pasta **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Se você substituir um campo existente do template de mensagem transacional, como o endereço do remetente, com um valor vazio, o campo correspondente na instância de execução não será atualizado uma vez que a mensagem transacional seja publicada novamente. Ele ainda conterá o valor anterior. No entanto, se você adicionar um valor não vazio, o campo correspondente será atualizado como normal após a próxima publicação.
