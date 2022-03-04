---
product: campaign
title: Transferência para mid-sourcing
description: Saiba mais sobre workflows de transferência para mid-sourcing
feature: Workflows
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 100%

---


# Transferência para mid-sourcing{#transfer-to-mid-sourcing}

![](../../assets/common.svg)

Os workflows detalhados abaixo são instalados com módulo de **Transferência para o mid-sourcing** por padrão. Para obter mais informações sobre o módulo, consulte o [Manual de instalação do Campaign Classic v7](../../installation/using/mid-sourcing-deployment.md).

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

