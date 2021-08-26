---
product: campaign
title: Centro de Mensagens (Controle)
description: Centro de Mensagens (Controle)
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 87%

---


# Centro de Mensagens (Controle){#message-center-control}

![](../../assets/common.svg)

O workflow detalhado abaixo é agendado para ser executado a cada hora. Ele é instalado com o módulo do **Centro de Mensagens – Controle** por padrão.


Para obter mais informações, dependendo da versão do Campaign, consulte estas seções:

![](assets/do-not-localize/v7.jpeg)[  Documentação do Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[  Documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Message Center &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> Esse workflow:<br /> 
    <ul> 
     <li> <p>recupera a lista de eventos processados pela(s) operação(s).</p> </li> 
     <li> <p>sincroniza com a tabela NmsBroadLogMsg para recuperar as qualificações da mensagem de delivery.</p> </li> 
     <li> <p>recupera logs de delivery de eventos assim que a sincronização com a tabela NmsBroadLogMsg for concluída.</p> </li> 
     <li> <p>sincroniza com a tabela NmsTrackingUrl para recuperar o rastreamento para as URLs de delivery.</p> </li> 
     <li> <p>recupera as URLs de rastreamento de eventos assim que a sincronização com a tabela NmsTrackingUrl for concluída.</p> </li> 
     <li> <p>permite recuperar todos os endereços de email colocados em quarentena a cada três horas após o envio de um delivery.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

