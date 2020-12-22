---
solution: Campaign Classic
product: campaign
title: Publicação de template
description: Publicação de template de mensagem transacional
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 45%

---


# Publicação de template{#template-publication}

Quando o modelo de mensagem criado na instância de controle estiver concluído, você poderá publicá-lo. Esse processo também o publicará em todas as instâncias de execução.

A publicação permite que você crie automaticamente dois modelos de mensagem no instância de execução, o que permitirá que você envie mensagens vinculadas a eventos batch e mensagens em tempo real.

>[!NOTE]
>
>Ao publicar templates de mensagem transacionais, as regras de tipologia também são publicadas automaticamente nas instâncias de execução.

>[!IMPORTANT]
>
>Sempre que fizer alterações em um modelo, certifique-se de publicá-lo novamente para que essas alterações sejam eficazes durante o delivery do mensagen transacional.

1. Na instância de controle, vá para a pasta **[!UICONTROL Message Center > Transactional message templates]** da árvore.
1. Selecione o template que deseja publicar em suas instâncias de execução.
1. Clique em **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Quando a publicação estiver concluída, ambos os templates de mensagem que serão aplicados em eventos batch e em tempo real são criados na árvore da instância de produção na pasta **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

Depois que um modelo é publicado, se o evento correspondente for acionado, a instância de execução receberá o evento, vinculará-o ao modelo transacional e enviará o mensagen transacional correspondente a cada recipient.

>[!NOTE]
>
>Se você substituir um campo existente do template de mensagem transacional, como o endereço do remetente, com um valor vazio, o campo correspondente na instância de execução não será atualizado uma vez que a mensagem transacional seja publicada novamente. Ele ainda conterá o valor anterior.
>
>No entanto, se você adicionar um valor não vazio, o campo correspondente será atualizado como normal após a próxima publicação.
