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
TQID: https://experienceleague.adobe.com/f58vs0ePAH-7bcfJ8u1GKLzcz0-fHnrwFyOVUWOFW-o
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 209
ht-degree: 100%

---

# Trabalhar com o Campaign e o Target{#integrating-with-adobe-target}



Use o Adobe Campaign com o Adobe Target para otimizar o conteúdo de email.

Para otimizar seu conteúdo de email, é possível criar uma oferta de redirecionamento no Adobe Target e, em seguida, usar o Adobe Campaign para gerenciar as ofertas de email. Por exemplo, é possível exibir diferentes ofertas para destinatários do sexo masculino e feminino.

A integração ocorre quando o email é aberto. Quando o cliente abre o email, é feita uma chamada para o Target e uma versão dinâmica do conteúdo é exibida. O conteúdo consiste em uma imagem estática compatível com todos os navegadores. O Target rastreia a reação à oferta no nível do público-alvo ou da sessão e esses dados ficam disponíveis nos relatórios do Target. [Saiba mais na documentação do Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=pt-BR).


>[!NOTE]
>
>A integração só oferece suporte a imagens estáticas. O restante do conteúdo não pode ser personalizado.

Vários tipos de dados podem ser utilizados pelo Adobe Target:

* Dados do datamart do Adobe Campaign
* Segmentos vinculados à ID do visitante no Adobe Target, se os dados usados não estiverem sujeitos a limitações legais
* Dados do Adobe Target: agente do usuário, endereço IP, dados de geolocalização
