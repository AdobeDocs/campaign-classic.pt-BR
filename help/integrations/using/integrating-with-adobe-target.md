---
product: campaign
title: Trabalhar com o Adobe Campaign e o Adobe Target
description: Saiba como integrar o Adobe Campaign ao Adobe Target
feature: Target Integration
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '201'
ht-degree: 100%

---

# Trabalhar com o Campaign e o Target{#integrating-with-adobe-target}



Use o Adobe Campaign com o Adobe Target para otimizar o conteúdo de email.

Para otimizar seu conteúdo de email, é possível criar uma oferta de redirecionamento no Adobe Target e, em seguida, usar o Adobe Campaign para gerenciar as ofertas de email. Por exemplo, é possível exibir diferentes ofertas para destinatários do sexo masculino e feminino.

A integração ocorre quando o email é aberto. Quando o cliente abre o email, é feita uma chamada para o Target e uma versão dinâmica do conteúdo é exibida. O conteúdo consiste em uma imagem estática compatível com todos os navegadores. O Target rastreia a reação à oferta no nível do público ou da sessão e esses dados ficam disponíveis nos relatórios do Target. [Saiba mais na documentação do Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=pt-BR).


>[!NOTE]
>
>A integração só oferece suporte a imagens estáticas. O restante do conteúdo não pode ser personalizado.

Vários tipos de dados podem ser utilizados pelo Adobe Target:

* Dados do datamart do Adobe Campaign
* Segmentos vinculados à ID do visitante no Adobe Target, se os dados usados não estiverem sujeitos a limitações legais
* Dados do Adobe Target: agente do usuário, endereço IP, dados de geolocalização
