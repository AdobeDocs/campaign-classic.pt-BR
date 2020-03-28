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
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Publicação de template{#template-publication}

Quando o template de mensagem criado na instância de controle está concluído, é possível publicá-lo em todas as instâncias de execução. A publicação permite criar automaticamente dois templates de mensagem na instância de execução, o que permitirá enviar mensagens vinculadas a eventos batch e em tempo real.

>[!CAUTION]
>
>Lembre-se de publicar o template sempre que fizer alterações nele para que essas alterações sejam efetivas durante o delivery de mensagens transacionais.

>[!NOTE]
>
>Ao publicar templates de mensagem transacional, as regras de tipologia são publicadas automaticamente nas instâncias de execução.

1. Na instância de controle, vá para a pasta **[!UICONTROL Message Center > Transactional message templates]** da árvore.
1. Selecione o template que deseja publicar em suas instâncias de execução.
1. Clique em **[!UICONTROL Publication]**.

   ![](assets/messagecenter_publish_model_008.png)

Uma vez concluída a publicação, ambos os modelos de mensagem a serem aplicados em eventos de tipo em lote e em tempo real são criados na árvore da instância de produção na pasta **[!UICONTROL Administration > Production > Message Center > Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Se você substituir um campo existente do template de mensagem transacional, como o endereço do remetente, com um valor vazio, o campo correspondente na instância de execução não será atualizado uma vez que a mensagem transacional seja publicada novamente. Ele ainda conterá o valor anterior. No entanto, se você adicionar um valor não vazio, o campo correspondente será atualizado como normal após a próxima publicação.

