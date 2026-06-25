---
product: campaign
title: Transferência para mid-sourcing
description: Saiba mais sobre fluxos de trabalho de transferência para mid-sourcing
hide: true
feature: Workflows
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: ht
source-wordcount: '115'
ht-degree: 100%

---


# Transferência para mid-sourcing{#transfer-to-mid-sourcing}



Os fluxos de trabalho detalhados abaixo são instalados com módulo de **Transferência para o Mid-sourcing** por padrão. Para obter mais informações sobre o módulo, consulte o [Manual de instalação do Campaign Classic v7](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-sourcing (contadores de delivery)</span><br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>Este fluxo de trabalho coleta informações de contagem para entregas no servidor mid-sourcing. Informações de contagem incluem indicadores de entregas gerais, como número de entregas enviadas, etc.</p> <p>As informações de rastreamento, como aberturas, não são incluídas.</p> <p>É acionado a cada dez minutos por padrão.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-sourcing (logs do delivery)</span><br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> Esse fluxo de trabalho coleta logs de entrega no servidor mid-sourcing. É acionado a cada hora por padrão.<br /> </td> 
  </tr> 
 </tbody> 
</table>

