---
product: campaign
title: 'Publicar modelos de mensagem '
description: Saiba mais sobre a publicação e o cancelamento da publicação de modelo de mensagem transacional no Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '494'
ht-degree: 100%

---

# Publicar modelos de mensagem {#publishing-template-messages}

## Publicação de modelo {#template-publication}

Quando o [modelo de mensagem](../../message-center/using/creating-the-message-template.md) criado na instância de controle for concluído e você tiver [testado](../../message-center/using/testing-message-templates.md), será possível publicá-lo. Esse processo também o publicará em todas as instâncias de execução.

A publicação permite criar automaticamente **dois modelos de mensagem** na instância de execução, que permitirá enviar mensagens vinculadas a **eventos em tempo real** e **eventos em lote**.

>[!NOTE]
>
>Ao publicar modelos de mensagem transacional, as regras de tipologia são publicadas automaticamente nas instâncias de execução.

>[!IMPORTANT]
>
>Sempre que fizer alterações em um modelo, publique-o novamente para que essas alterações estejam em vigor durante a entrega da mensagem transacional.

1. Na instância de controle, vá para a pasta **[!UICONTROL Message Center > Transactional message templates]** da árvore.
1. Selecione o template que deseja publicar em suas instâncias de execução.
1. Clique em **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Quando a publicação estiver concluída, ambos os templates de mensagem que serão aplicados em eventos batch e em tempo real são criados na árvore da instância de produção na pasta **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

Depois que um modelo for publicado, se o evento correspondente for acionado, a instância de execução receberá o evento, o vinculará ao modelo transacional e enviará a mensagem transacional correspondente a cada recipient. Para obter mais informações, consulte [Processamento de evento](../../message-center/using/about-event-processing.md).

>[!NOTE]
>
>Se você substituir um campo existente do template de mensagem transacional, como o endereço do remetente, com um valor vazio, o campo correspondente na instância de execução não será atualizado uma vez que a mensagem transacional seja publicada novamente. Ele ainda conterá o valor anterior.
>
>No entanto, se você adicionar um valor não vazio, o campo correspondente será atualizado como normal após a próxima publicação.

## Cancelar a publicação do modelo {#template-unpublication}

Depois que um modelo de mensagem é publicado nas instâncias de execução, você pode desfazer a publicação. Para obter mais informações sobre o processo de publicação do modelo, consulte [esta seção](#template-publication).

* Na verdade, um modelo publicado ainda poderá ser chamado se o evento correspondente for acionado: se você não estiver mais usando um modelo de mensagem, será recomendável desfazer a publicação. Dessa forma, você pode evitar o envio de uma mensagem transacional indesejada por engano.

   Por exemplo, você publicou um template de mensagem que só usa para campanhas de Natal. Talvez você queira desfazer a publicação depois que o período de Natal acabar e publicá-lo novamente no próximo ano.

* Além disso, não é possível excluir um template de mensagem transacional que tenha o status **[!UICONTROL Published]**. Você deve desfazer a publicação primeiro.

>[!NOTE]
>
>Esse recurso está disponível a partir da versão 20.2 do Campaign.

Para desfazer a publicação de um template de mensagem transacional, siga as etapas abaixo.

1. Na instância de controle, acesse a pasta **[!UICONTROL Message Center > Transactional message templates]** da árvore.
1. Selecione o template do qual você deseja desfazer a publicação.
1. Clique em **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Clique em **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

O status do template de mensagem transacional muda de **[!UICONTROL Published]** para **[!UICONTROL Being edited]**.

Depois de desfazer a publicação:

* Ambos os modelos de mensagem (aplicados a eventos de tipo em lote e em tempo real) são excluídos de cada instância de execução.

   Eles não aparecem mais na pasta **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** (consulte [esta seção](#template-publication)).

* Quando a publicação de um modelo for desfeita, você poderá excluí-lo da instância de controle.

   Para fazer isso, selecione-o na lista e clique no botão **[!UICONTROL Delete]** na parte superior direita da tela.
