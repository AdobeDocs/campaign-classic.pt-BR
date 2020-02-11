---
title: Web Analytics
seo-title: Web Analytics
description: Web Analytics
seo-description: null
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Web Analytics{#web-analytics}

Os workflows detalhados abaixo são instalados com o módulo dos **conectores
			Web Analytics** por padrão. Para obter mais informações sobre esse módulo, consulte esta[seção](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome 
								interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Envio de indicadores e atributos</span> de campanha <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span><br /> </td> 
   <td> Esse workflow permite enviar indicadores de campanha de email do Adobe Campaign 
								para o Adobe Experience Cloud Suite por meio do conector do Adobe® Genesis. The indicators concerned are as follows: <strong>Sent</strong> (iSent), <strong>Total count of opens</strong> (iTotalRecipientOpen), <strong>Total number of recipients who clicked</strong> (iTotalRecipientClick), <strong>Errors</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificação de contatos</span> convertidos <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> Este workflow indexa os visitantes do site que concluíram sua compra após uma campanha de re-marketing. The data recovered by this workflow can be accessed in the <span class="uicontrol">Re-marketing efficiency report</span> (Refer to this <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> page</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Expurgação</span> de evento <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span><br /> </td> 
   <td> This workflow lets you delete every event from the database field according to the period configured in the <span class="uicontrol">Lifespan</span> field. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recuperação de eventos</span> da Web <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span><br /> </td> 
   <td> A cada hora, este workflow baixa segmentos do comportamento do usuário na Internet em um determinado site, os coloca no banco de dados do Adobe Campaign e inicia o workflow de re-marketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

