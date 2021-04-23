---
solution: Campaign Classic
product: campaign
title: Dados de personalização
description: Dados de personalização
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 587d48aa-43ae-41c5-a0e3-6805a0e9b6a4
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '151'
ht-degree: 100%

---

# Dados de personalização{#personalization-data}

É possível usar dados no template de mensagem para testar a personalização da mensagem transacional. Essa funcionalidade é usada para gerar uma pré-visualização ou enviar uma prova. Se instalar o módulo **Deliverability** , esses dados permitirão exibir uma renderização das mensagens para vários provedores de acesso à Internet (**renderização da caixa de entrada**: para obter mais informações, consulte [esta seção](../../delivery/using/inbox-rendering.md)).

O objetivo desses dados é testar suas mensagens antes do delivery final. Essas mensagens não coincidem com os dados reais para serem processados pelo Centro de Mensagens. Entretanto, a estrutura XML deve ser idêntica à do evento armazenado na instância de execução, conforme mostrado abaixo.

![](assets/messagecenter_create_custo_006.png)

Essas informações permitem personalizar o conteúdo da mensagem usando tags de personalização (para obter mais informações, consulte [Criação do conteúdo da mensagem](../../message-center/using/creating-message-content.md)).

1. No modelo de mensagem, clique na guia **[!UICONTROL Seed addresses]**.
1. No conteúdo do evento, insira as informações de teste no formato XML.

   ![](assets/messagecenter_create_custo_001.png)
