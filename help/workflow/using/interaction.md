---
product: campaign
title: Interação
description: Interação
feature: Workflows, Interaction
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 100%

---


# Interação{#interaction}

![](../../assets/common.svg)

Os workflows detalhados abaixo são instalados com o complemento **Mecanismo de oferta (Interação)** por padrão.

Para mais informações, dependendo da versão do Campaign, consulte estas seções:

![](assets/do-not-localize/v7.jpeg)[ Documentação do Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[  Documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html?lang=pt-BR)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Full aggregate calculation (propositionrcp cube)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> Esse workflow atualiza o agregado <strong>completo</strong> do cubo da <strong>Apresentação da oferta. </strong> É acionado todos os dias às 6:00 AM por padrão. Esse agregado captura as seguintes dimensões: canal, delivery, oferta de marketing e data.<br /> O cubo da <strong>Apresentação de oferta</strong> é usado para gerar relatórios com base em ofertas. Você pode saber mais sobre cubos <a href="../../reporting/using/about-cubes.md">nesta seção</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter full aggregate calculation</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Esse workflow atualiza o agregado <strong>completo</strong> para o cubo do <strong>centro de mensagem</strong>. É acionado todos os dias às 3:00 AM por padrão. Esse agregado captura as seguintes dimensões: canal, data, status e tipo de evento.<br /> O cubo do <strong>centro de mensagem</strong> é usado para gerar relatórios com base em eventos. Você pode saber mais sobre cubos <a href="../../reporting/using/about-cubes.md">nesta seção</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

