---
product: campaign
title: Testar modelos de mensagem transacional
description: Saiba como gerenciar seed addresses em mensagens transacionais para visualizá-los e testá-los no Adobe Campaign Classic
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
TQID: 'https://experienceleague.adobe.com/jcmXX4aMPaTBatt4m3s-IAaAeoXnjmPaEE4oqIDoIOI'
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
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: ht
source-wordcount: '298'
ht-degree: 100%
---
# Testar modelos de mensagem transacional {#testing-message-templates}

Quando seu [modelo de mensagem](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentação do Campaign v8) estiver pronto, siga as etapas abaixo para visualizá-lo e testá-lo.

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8. Para saber como adicionar seed addresses, visualizar uma mensagem transacional e enviar uma prova, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}

## Dados de personalização {#personalization-data}

É possível usar dados no modelo de mensagem para testar a personalização da mensagem transacional. Essa funcionalidade é usada para gerar uma pré-visualização ou enviar uma prova. Você também pode exibir a renderização da mensagem para vários provedores de acesso à Internet. Para obter mais informações, consulte [Renderização da caixa de entrada](../../delivery/using/inbox-rendering.md).

O objetivo desses dados é testar suas mensagens antes da entrega final. Essas mensagens não coincidem com os dados reais que serão processados. Entretanto, a estrutura XML deve ser idêntica à do evento armazenado na instância de execução, conforme mostrado abaixo:

![](assets/messagecenter_create_custo_006.png)

Essas informações permitem personalizar o conteúdo da mensagem usando tags de personalização (para obter mais informações, consulte [Criar o conteúdo da mensagem](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/transactional-template#create-message-content){target="_blank"} na documentação do Campaign v8).

1. Publicar o modelo de mensagem transacional.

1. No modelo, clique na guia **[!UICONTROL Seed addresses]**.

1. No conteúdo do evento, insira as informações de teste no formato XML.

   ![](assets/messagecenter_create_custo_001.png)

1. Clique em **[!UICONTROL Save]**.
