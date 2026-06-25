---
product: campaign
title: Interação
description: Interação
hide: true
feature: Workflows, Interaction, Offers
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: ht
source-wordcount: '169'
ht-degree: 100%

---


# Interação{#interaction}



Os fluxos de trabalho detalhados abaixo são instalados com o complemento **Mecanismo de oferta (Interação)** por padrão.

Para mais informações, dependendo da versão do Campaign, consulte estas seções:

![](assets/do-not-localize/v7.jpeg)[Documentação do Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[Documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html?lang=pt-BR)


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
   <td> Esse fluxo de trabalho atualiza o agregado <strong>completo</strong> do cubo da <strong>Apresentação da oferta. </strong> É acionado todos os dias às 6:00 AM por padrão. Este agregado abrange as seguintes dimensões: Canal, Entrega, Oferta de marketing e Data.<br /> O cubo <strong>Proposta de oferta</strong> é então utilizado para gerar relatórios com base nas ofertas. Você pode saber mais sobre cubos <a href="../../reporting/using/ac-cubes.md">nesta seção</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter full aggregate calculation</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Esse fluxo de trabalho atualiza o agregado <strong>completo</strong> para o cubo do <strong>centro de mensagem</strong>. É acionado todos os dias às 3:00 AM por padrão. Este agregado abrange as seguintes dimensões: Canal, Data, Status e Tipo de evento.<br /> O cubo <strong>Centro de mensagens</strong> é então utilizado para gerar relatórios com base em eventos. Você pode saber mais sobre cubos <a href="../../reporting/using/ac-cubes.md">nesta seção</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

