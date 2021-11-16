---
product: campaign
title: Integração com o Adobe Target
description: Integração com o Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 40%

---

# Integração com o Adobe Target{#integrating-with-adobe-target}

![](../../assets/common.svg)

Use o Adobe Campaign com Adobe Target para otimizar o conteúdo de email.

Para otimizar seu conteúdo de email, você pode criar uma oferta de redirecionamento no Adobe Target e, em seguida, usar o Adobe Campaign para gerenciar as ofertas de email. Por exemplo, você pode exibir diferentes ofertas para recipients do sexo masculino e feminino.

A integração ocorre quando o email é aberto. Quando o cliente abre o email, é feita uma chamada para o Target e é exibida uma versão dinâmica do conteúdo. O conteúdo consiste em uma imagem estática compatível com todos os navegadores. O Target rastreia a reação à oferta no nível do público-alvo ou da sessão e esses dados estão disponíveis nos relatórios do Target. [Saiba mais na documentação do Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=pt-BR).


>[!NOTE]
>
>A integração só oferece suporte a imagens estáticas. O restante do conteúdo não pode ser personalizado.

Vários tipos de dados podem ser utilizados pelo Adobe Target:

* Dados do datamart do Adobe Campaign
* Segmentos vinculados à ID do visitante no Adobe Target, se os dados usados não estiverem sujeitos a limitações legais
* Dados do Adobe Target: agente do usuário, endereço IP, dados de geolocalização
