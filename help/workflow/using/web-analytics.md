---
product: campaign
title: Análise da web
description: Saiba mais sobre o pacote do Web Analytics
hide: true
feature: Workflows, Analytics Integration
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 100%

---


# Análise da web{#web-analytics}



Os fluxos de trabalho detalhados abaixo são instalados com o módulo dos **conectores Web Analytics** por padrão. Para obter mais informações sobre esse módulo, consulte esta[seção](../../integrations/using/gs-aa.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Envio de indicadores e atributos de campanha</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> Esse fluxo de trabalho permite enviar indicadores de campanha de email do Adobe Campaign para o Adobe Experience Cloud Suite por meio do conector do Adobe® Analytics. Os indicadores relacionados são: <strong>Sent</strong> (iSent), <strong>Total count of opens</strong> (iTotalRecipientOpen), <strong>Total number of recipients who clicked</strong> (iTotalRecipientClick), <strong>Errors</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificação de contatos convertidos</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Este fluxo de trabalho indexa os visitantes do site que concluíram sua compra após uma campanha de re-marketing. Os dados recuperados por esse fluxo de trabalho podem ser acessados no <span class="uicontrol">Relatório de eficiência de remarketing</span>. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Limpeza de eventos</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Esse fluxo de trabalho permite excluir todos os eventos do campo de banco de dados de acordo com o período configurado no campo <span class="uicontrol">Lifespan</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recuperação de eventos da Web</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> A cada hora, este fluxo de trabalho baixa segmentos do comportamento do usuário na Internet em um determinado site, os coloca no banco de dados do Adobe Campaign e inicia o fluxo de trabalho de re-marketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

