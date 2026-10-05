---
product: campaign
title: Criar modelos de mensagem transacional
description: Saiba como criar um modelo de mensagem transacional no Adobe Campaign Classic
feature: Transactional Messaging, Message Center, Templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
TQID: 'https://experienceleague.adobe.com/lVjiHCruVE2IpwsTkjcNtccmpoSF1aeZ-PFRjcIwf7g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: baf8e746-117b-5e73-b179-0a83edc0295f
    internal-label: Templates
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 100%
---
# Criar modelos de mensagem transacional {#creating-the-message-template}



Para garantir que cada evento possa ser alterado em uma mensagem personalizada, você precisa criar um modelo de mensagem para corresponder a cada tipo de evento.

>[!IMPORTANT]
>
>Os tipos de evento precisam ser criados previamente. Para obter mais informações, consulte [Criar tipos de evento](../../message-center/using/creating-event-types.md).

Os modelos de mensagem transacional contêm as informações necessárias para personalizar a mensagem transacional. Você também pode usar modelos para testar a pré-visualização da mensagem e enviar provas usando seed addresses antes de entregar ao target final. Para obter mais informações, consulte [Testar modelos de mensagem transacional](../../message-center/using/testing-message-templates.md).

## Criar o modelo de mensagem {#creating-message-template}

1. Acesse a pasta **[!UICONTROL Message Center >Transactional message templates]** da árvore do Adobe Campaign.

1. Clique com o botão direito do mouse na lista de modelos de mensagem transacional e selecione **[!UICONTROL New]** no menu suspenso ou clique no botão **[!UICONTROL New]** acima da lista de modelos de mensagem transacional.

   ![](assets/messagecenter_create_model_001.png)

1. Na janela da entrega, selecione o modelo da entrega apropriado para o canal que deseja usar.

   ![](assets/messagecenter_create_model_002.png)

1. Altere seu rótulo se necessário.

1. Selecione o tipo de evento que corresponda à mensagem a ser enviada.

   ![](assets/messagecenter_create_model_003.png)

   Os tipos de eventos precisam ser criados previamente no console. Para obter mais informações, consulte [Criar tipos de evento](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >Um tipo de evento não pode estar vinculado a mais de um modelo.

1. Insira uma natureza e uma descrição e clique em **[!UICONTROL Continue]** para criar o corpo da mensagem (consulte [Criar o conteúdo da mensagem](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## Criar o conteúdo da mensagem {#creating-message-content}

A definição do conteúdo da mensagem transacional é a mesma para entregas comuns no Adobe Campaign. Por exemplo, para uma entrega de email, você pode criar conteúdo em formato HTML ou texto, adicionar anexos ou personalizar o objeto da entrega. Para obter mais informações, consulte o capítulo [Entrega de email](../../delivery/using/about-email-channel.md).

>[!IMPORTANT]
>
>As imagens incluídas na mensagem devem ser acessíveis publicamente. O Adobe Campaign não fornece nenhum mecanismo de carregamento de imagem para mensagens transacionais.\
>Ao contrário do JSSP ou webApp, `<%=`não tem nenhum escape padrão.
>
>Nesse caso, você precisa escapar cada dado que vem do evento corretamente. Este escape depende da forma como esse campo é usado. Por exemplo, dentro de uma URL, use encodeURIComponent. Para ser exibido no HTML, você pode usar escapeXMLString.

Após definir o conteúdo da mensagem, você pode integrar as informações do evento no corpo da mensagem e personalizá-lo. As informações do evento são inseridas no corpo do texto graças às tags de personalização.

![](assets/messagecenter_create_content_001.png)

* Todos os campos de personalização vêm da carga.
* É possível referenciar um ou vários blocos de personalização em uma mensagem transacional. O conteúdo do bloco será adicionado ao conteúdo de entrega durante a publicação para a instância de execução.

Para inserir tags de personalização no corpo de uma mensagem de email, siga as etapas abaixo:

1. No modelo de mensagem, clique na guia que corresponde ao formato do email (HTML ou texto).

1. Insira o corpo da mensagem.

1. No corpo do texto, insira a tag usando o menu **[!UICONTROL Real time events > Event XML]**.

   ![](assets/messagecenter_create_custo_002.png)

1. Preencha a tag usando a seguinte sintaxe: **nome do elemento**.@**nome do atributo**, conforme mostrado abaixo.

   ![](assets/messagecenter_create_custo_003.png)

1. Salve o conteúdo.

Sua mensagem agora está pronta para ser [testada](../../message-center/using/testing-message-templates.md).
