---
solution: Campaign Classic
product: campaign
title: Transferência para mid-sourcing
description: Saiba mais sobre workflows de transferência para mid-sourcing
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '104'
ht-degree: 100%

---


# Transferência para Mid-sourcing{#transfer-to-mid-sourcing}

Os workflows detalhados abaixo são instalados com módulo de **Transferência para o Mid-sourcing** por padrão. Para obter mais informações sobre esse módulo, consulte esta[seção](../../installation/using/mid-sourcing-deployment.md).

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
   <td> <p>Este workflow coleta informações de contagem para deliveries no servidor mid-sourcing. Informações de contagem incluem indicadores de deliveries gerais, como número de deliveries enviados, etc.</p> <p>As informações de rastreamento, como aberturas, não são incluídas.</p> <p>É acionado a cada dez minutos por padrão.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-sourcing (logs do delivery)</span><br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> Esse workflow coleta logs de delivery no servidor mid-sourcing. É acionado a cada hora por padrão.<br /> </td> 
  </tr> 
 </tbody> 
</table>

