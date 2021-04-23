---
solution: Campaign Classic
product: campaign
title: Publicação de template
description: Publicação de template
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1e09381d-af20-4309-8769-47f0d5e8dd64
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '226'
ht-degree: 100%

---

# Desfazer a publicação de template{#template-unpublication}

Depois que um modelo de mensagem é publicado nas instâncias de execução, você pode desfazer a publicação. Para obter mais informações sobre o processo de publicação do modelo, consulte [esta seção](../../message-center/using/template-publication.md).

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

   Eles não aparecem mais na pasta **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** (consulte [esta seção](../../message-center/using/template-publication.md)).

* Quando a publicação de um modelo for desfeita, você poderá excluí-lo da instância de controle.

   Para fazer isso, selecione-o na lista e clique no botão **[!UICONTROL Delete]** na parte superior direita da tela.
