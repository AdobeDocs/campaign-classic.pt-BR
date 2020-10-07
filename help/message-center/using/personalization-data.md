---
title: Dados de personalização
seo-title: Dados de personalização
description: Dados de personalização
seo-description: null
page-status-flag: never-activated
uuid: d3d66216-502a-410b-b062-fb413eb9363f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 2cd8a320-37e8-410a-b71b-0c13c8e15482
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 100%

---


# Dados de personalização{#personalization-data}

É possível usar dados no template de mensagem para testar a personalização da mensagem transacional. Essa funcionalidade é usada para gerar uma pré-visualização ou enviar uma prova. Se instalar o módulo **Deliverability** , esses dados permitirão exibir uma renderização das mensagens para vários provedores de acesso à Internet (**renderização da caixa de entrada**: para obter mais informações, consulte [esta seção](../../delivery/using/about-deliverability.md)).

O objetivo desses dados é testar suas mensagens antes do delivery final. Essas mensagens não coincidem com os dados reais para serem processados pelo Centro de Mensagens. Entretanto, a estrutura XML deve ser idêntica à do evento armazenado na instância de execução, conforme mostrado abaixo.

![](assets/messagecenter_create_custo_006.png)

Essas informações permitem personalizar o conteúdo da mensagem usando tags de personalização (para obter mais informações, consulte [Criação do conteúdo da mensagem](../../message-center/using/creating-message-content.md)).

1. No modelo de mensagem, clique na guia **[!UICONTROL Seed addresses]**.
1. No conteúdo do evento, insira as informações de teste no formato XML.

   ![](assets/messagecenter_create_custo_001.png)

