---
product: campaign
title: Análise da web
description: Saiba mais sobre o pacote do Web Analytics
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Workflows, Analytics Integration
source-git-commit: 59156851156338c9462781d31ce81a651362f2da
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 92%

---


# Análise da web{#web-analytics}



Os workflows detalhados abaixo são instalados com o módulo dos **conectores Web Analytics** por padrão. Para obter mais informações sobre esse módulo, consulte esta[seção](../../platform/using/gs-aa.md).

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
   <td> Este workflow indexa os visitantes do site que concluíram sua compra após uma campanha de re-marketing. Os dados recuperados por esse workflow podem ser acessados no <span class="uicontrol">Relatório de eficiência de re-marketing</span>. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Limpeza de eventos</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Esse fluxo de trabalho permite excluir todos os eventos do campo de banco de dados de acordo com o período configurado no campo <span class="uicontrol">Lifespan</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recuperação de eventos da Web</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> A cada hora, este workflow baixa segmentos do comportamento do usuário na Internet em um determinado site, os coloca no banco de dados do Adobe Campaign e inicia o workflow de re-marketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

