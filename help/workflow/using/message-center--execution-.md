---
title: Centro de Mensagens (Execução)
seo-title: Centro de Mensagens (Execução)
description: Centro de Mensagens (Execução)
seo-description: null
page-status-flag: never-activated
uuid: 8dfb09d1-da00-43fb-9df4-243bb915cbde
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: dc3d8998-9493-4d71-b3e2-6f9531cb9bac
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 100%

---


# Centro de Mensagens (Execução){#message-center-execution}

Os workflows detalhados abaixo são instalados com o módulo do **Centro de Mensagens – Execução** por padrão. Para obter mais informações sobre esse módulo, consulte esta[seção](../../message-center/using/about-transactional-messaging.md).

Para saber mais sobre como configurar workflows técnicos relacionados ao módulo do Centro de Mensagens, consulte [esta página](../../message-center/using/technical-workflows.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Atualizar status do evento</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> Esse workflow permite atribuir um status a um evento. Os status do evento são como descritos a seguir:<br /> 
    <ul> 
     <li> <p><strong>Pendente</strong>: o evento está em uma fila. Nenhum template de mensagem foi associado a ele.</p> </li> 
     <li> <p><strong>Delivery pendente</strong>: o evento está em uma fila, um template de mensagem foi associado a ele e está sendo processado no momento pelo delivery.</p> </li> 
     <li> <p><strong>Enviado</strong>: esse status é copiado dos logs de delivery. Significa que o delivery foi enviado.</p> </li> 
     <li> <p><strong>Ignorado pelo delivery</strong>: esse status é copiado dos logs de delivery. Significa que o delivery foi ignorado.</p> </li> 
     <li> <p><strong>Erro de delivery</strong>: esse status é copiado dos logs de delivery. Significa que o delivery falhou.</p> </li> 
     <li> <p><strong>Evento não coberto</strong>: o evento falhou ao ser associado a um template de mensagem. O evento não será reprocessado.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processamento de eventos em lote</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Esse workflow permite colocar eventos batch em uma fila antes de associá-los a um template de mensagem. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processamento de eventos em tempo real</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Esse workflow permite colocar eventos em tempo real em uma fila antes de associá-los a um template de mensagem. <br /> </td> 
  </tr> 
 </tbody> 
</table>

