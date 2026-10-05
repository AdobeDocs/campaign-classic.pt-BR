---
product: campaign
title: Transferência para mid-sourcing
description: Saiba mais sobre fluxos de trabalho de transferência para mid-sourcing
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
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

