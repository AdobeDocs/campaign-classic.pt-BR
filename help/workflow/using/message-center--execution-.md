---
product: campaign
title: Centro de Mensagens (Execução)
description: Centro de Mensagens (Execução)
feature: Workflows
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '229'
ht-degree: 100%

---


# Centro de Mensagens (Execução){#message-center-execution}

![](../../assets/v7-only.svg)

Os workflows detalhados abaixo são instalados com o complemento **Centro de Mensagens – Execução** por padrão.

Para mais informações, dependendo da versão do Campaign, consulte estas seções:

![](assets/do-not-localize/v7.jpeg)[ Documentação do Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[  Documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html?lang=pt-BR)

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

