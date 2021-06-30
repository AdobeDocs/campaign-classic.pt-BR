---
product: campaign
title: Centro de Mensagens (Controle)
description: Centro de Mensagens (Controle)
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '157'
ht-degree: 100%

---


# Centro de Mensagens (Controle){#message-center-control}

O workflow detalhado abaixo é agendado para ser executado a cada hora. Ele é instalado com o módulo do **Centro de Mensagens – Controle** por padrão. Para obter mais informações sobre esse módulo, consulte esta[seção](../../message-center/using/about-transactional-messaging.md).

Para saber mais sobre como configurar workflows técnicos relacionados ao módulo do Centro de Mensagens, consulte [esta página](../../message-center/using/technical-workflows.md).

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

