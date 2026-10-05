---
product: campaign
title: Centro de Mensagens (Execução)
description: Centro de Mensagens (Execução)
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
source-wordcount: '232'
ht-degree: 100%
---

# Centro de Mensagens (Execução){#message-center-execution}



Os fluxos de trabalho detalhados abaixo são instalados com o complemento **Centro de Mensagens – Execução** por padrão.

Para mais informações, dependendo da versão do Campaign, consulte estas seções:

![](assets/do-not-localize/v7.jpeg)[Documentação do Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[Documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html?lang=pt-BR)

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
   <td> Esse fluxo de trabalho permite atribuir um status a um evento. Os status do evento são como descritos a seguir:<br /> 
    <ul> 
     <li> <p><strong>Pendente</strong>: o evento está em uma fila. Nenhum modelo de mensagem foi associado a ele.</p> </li> 
     <li> <p><strong>Entrega pendente</strong>: o evento está em uma fila, um modelo de mensagem foi associado a ele e está sendo processado no momento pela entrega.</p> </li> 
     <li> <p><strong>Enviado</strong>: esse status é copiado dos logs de entrega. Significa que a entrega foi enviada.</p> </li> 
     <li> <p><strong>Ignorado pela entrega</strong>: esse status é copiado dos logs de entrega. Significa que a entrega foi ignorada.</p> </li> 
     <li> <p><strong>Erro de entrega</strong>: esse status é copiado dos logs de entrega. Significa que a entrega falhou.</p> </li> 
     <li> <p><strong>Evento não coberto</strong>: o evento falhou ao ser associado a um modelo de mensagem. O evento não será reprocessado.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processamento de eventos em lote</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Esse fluxo de trabalho permite colocar eventos batch em uma fila antes de associá-los a um modelo de mensagem. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processamento de eventos em tempo real</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Esse fluxo de trabalho permite colocar eventos em tempo real em uma fila antes de associá-los a um modelo de mensagem. <br /> </td> 
  </tr> 
 </tbody> 
</table>

