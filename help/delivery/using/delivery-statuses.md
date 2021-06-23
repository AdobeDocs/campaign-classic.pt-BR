---
product: campaign
title: Status de delivery
description: Saiba mais sobre os status disponíveis no painel do delivery.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 100%

---

# Status da entrega {#delivery-statuses}

<!--ajouter intro 

ajouter screenshot -->

Depois que um delivery é enviado, o painel do delivery exibe um status que permite monitorar se o envio foi bem sucedido. Os possíveis status estão detalhados na seção abaixo.

![](assets/delivery-status.png)

Para obter mais detalhes sobre as diferentes falhas de delivery que podem ser encontradas e como resolvê-las, consulte [esta página](understanding-delivery-failures.md).

**Tópicos relacionados:**

* [Painel de entrega](delivery-dashboard.md)
* [Solução de problemas de entrega](delivery-troubleshooting.md)
* [Sobre a capacidade de entrega](about-deliverability.md)

## Lista de status de delivery {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Definições e soluções<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Sent<br /> </td> 
   <td> O delivery foi enviado corretamente ao provedor de mensagens (mas o recipient não o recebeu necessariamente).<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignored<br /> </td> 
   <td> O delivery não foi enviado ao recipient devido a um erro no endereço. Ele foi incluído na lista de bloqueios, colocado em quarentena, não fornecido ou duplicado. <br /> </td> 
  </tr> 
  <tr> 
   <td> Failed<br /> </td> 
   <td> O delivery não conseguiu alcançar o recipient devido a um endereço inválido ou a uma caixa de entrada cheia, por exemplo. Ele também pode ser vinculado a um problema com blocos de personalização, pois esses blocos podem gerar erros quando os schemas não correspondem ao mapeamento do delivery. Consulte <a href="understanding-delivery-failures.md" target="_blank">Conhecendo as falhas de delivery</a><br /> </td> 
  </tr>
  <tr> 
   <td> Pending<br /> </td> 
   <td> O delivery está pronto para ser enviado e será processado pelo servidor de delivery (MTA). Consulte <a href="#pending-status" target="_blank">Status pendente</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Not applicable<br /> </td> 
   <td> O delivery foi levado em conta pelo servidor (MTA), mas não foi processado.<br /> </td> 
  </tr>  
  <tr> 
   <td> Delivery canceled<br /> </td> 
   <td> O delivery foi cancelado por um operador.<br /> </td> 
  </tr> 
  <tr> 
   <td> Levado em consideração pelo provedor de serviço<br /> </td> 
   <td> O provedor de serviços SMS recebeu o delivery.<br /> Para instalações hospedadas ou híbridas, se você atualizou para o <a href="sending-with-enhanced-mta.md" target="_blank">MTA aprimorado</a>, a mensagem foi repassada com êxito do Campaign para o MTA aprimorado.</td> 
  </tr> 
  <tr> 
   <td> Received on mobile<br /> </td> 
   <td> O recipient recebeu o SMS em seu dispositivo móvel.<br /> </td> 
  </tr>
  <tr> 
   <td> Sent to the service provider<br /> </td> 
   <td> O delivery foi enviado para o provedor de serviços SMS, mas ainda não foi recebido.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Prepared<br /> </td> 
   <td> Status intermediário usado somente para conectores externos como o canal móvel. Ele segue o status "Pendente" e é o conector externo que determinará o status seguinte.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Para saber como otimizar a capacidade de delivery dos emails do Adobe Campaign, consulte [esta seção](about-deliverability.md). Para obter informações mais detalhadas sobre a capacidade de delivery, consulte o [Manual de práticas recomendadas de capacidade de delivery da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).

## Status pendente {#pending-status}

Após confirmar o delivery, você pode ver que o status do delivery é **[!UICONTROL Pending]**. Esse status significa que o processo de execução está aguardando a disponibilidade de alguns recursos.

O status **[!UICONTROL Pending]** pode significar que o seu delivery foi agendado e está pendente até a data especificada. Para obter mais informações, consulte a seção [Agendamento de delivery](steps-sending-the-delivery.md#scheduling-the-delivery-sending).

Se o delivery não estiver sendo enviado e o status permanecer **[!UICONTROL Pending]**, poderá ser devido a:

* O MTA (Message Transfert Agent), que executa módulos e processos no servidor de delivery e que gerencia o envio de email, pode não ter sido iniciado ou precisa ser reiniciado.

   Para verificar isso e iniciar o módulo se necessário, siga as seguintes etapas:

   >[!NOTE]
   >
   >Esta operação pode ser executada com um modelo de hospedagem **no local** ou **híbrido** com acesso ao servidor do Campaign (consulte [modelos de hospedagem](../../installation/using/hosting-models.md)).

   1. Verifique se os `mta@<instance>` módulos são iniciados nos servidores MTA.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. Se o MTA não estiver listado, comece com o seguinte comando:

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >Substitua `<INSTANCENAME>` pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* Pode ser que o delivery esteja usando uma afinidade não configurada no servidor emissor.

   Nesse caso, verifique a configuração do gerenciamento de tráfego (afinidade IP) e use o campo **[!UICONTROL Managing affinities with IP addresses]** para vincular deliveries ao MTA que gerencia a afinidade. Para obter mais informações sobre afinidades, consulte [esta seção](../../installation/using/configure-delivery-settings.md).

* Quando muitas campanhas são executadas, o status do delivery permanece como &quot;Pendente&quot;.

   O limite de campanhas simultâneas é definido na opção **[!UICONTROL NmsOperation_LimitConcurrency]**. O valor padrão é 10.

   Saiba mais sobre opções [nesta página](../../installation/using/configuring-campaign-options.md).


**Tópicos relacionados:**

* [Histórico e logs do delivery](#delivery-logs-and-history)
* [Noções básicas sobre falhas de entrega](understanding-delivery-failures.md)
* [Tipos e motivos de falha de delivery](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
