---
product: campaign
title: Centro de Mensagens (Controle)
description: Centro de Mensagens (Controle)
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '145'
ht-degree: 100%

---


# Centro de Mensagens (Controle){#message-center-control}



O workflow detalhado abaixo é agendado para ser executado a cada hora. Ele é instalado por padrão com o módulo do **Centro de Mensagens – Controle**.


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
   <td> Message Center &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> Esse workflow:<br /> 
    <ul> 
     <li> <p>recupera a lista de eventos processados pela(s) operação(s).</p> </li> 
     <li> <p>sincroniza com a tabela NmsBroadLogMsg para recuperar as qualificações da mensagem de entrega.</p> </li> 
     <li> <p>recupera logs de entrega de eventos assim que a sincronização com a tabela NmsBroadLogMsg for concluída.</p> </li> 
     <li> <p>sincroniza com a tabela NmsTrackingUrl para recuperar o rastreamento para as URLs de entrega.</p> </li> 
     <li> <p>recupera as URLs de rastreamento de eventos assim que a sincronização com a tabela NmsTrackingUrl for concluída.</p> </li> 
     <li> <p>permite recuperar todos os endereços de email colocados em quarentena a cada três horas após o envio de uma entrega.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

