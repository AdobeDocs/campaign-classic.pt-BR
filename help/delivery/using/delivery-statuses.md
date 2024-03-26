---
product: campaign
title: Status de entrega
description: Saiba mais sobre os status disponíveis no painel da entrega
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 100%

---

# Status de entrega {#delivery-statuses}



<!--ajouter intro 

ajouter screenshot -->

Depois que uma entrega é enviada, o painel da entrega exibe um status que permite monitorar se o envio foi bem sucedido. Os possíveis status estão detalhados na seção abaixo.

![](assets/delivery-status.png)

Para obter mais detalhes sobre as diferentes falhas de entrega que podem ser encontradas e como resolvê-las, consulte [esta página](understanding-delivery-failures.md).

**Tópicos relacionados:**

* [Painel de entrega](delivery-dashboard.md)
* [Solução de problemas de entrega](delivery-troubleshooting.md)
* [Introdução à capacidade de entrega](about-deliverability.md)

## Lista de status de entrega {#list-delivery-statuses}

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
   <td> A entrega foi enviada corretamente ao provedor de mensagens (mas o destinatário não a recebeu necessariamente).<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorado<br /> </td> 
   <td> A entrega não foi enviada ao destinatário devido a um erro no endereço. Ele foi incluído na lista de bloqueios, colocado em quarentena, não fornecido ou duplicado. <br /> </td> 
  </tr> 
  <tr> 
   <td> Failed<br /> </td> 
   <td> A entrega não conseguiu alcançar o destinatário devido a um endereço inválido ou a uma caixa de entrada cheia, por exemplo. Também pode ser um problema com blocos de personalização, pois esses blocos podem gerar erros quando os schemas não correspondem ao mapeamento da entrega. Consulte <a href="understanding-delivery-failures.md" target="_blank">Conhecendo as falhas de entrega</a><br /> </td> 
  </tr>
  <tr> 
   <td> Pending<br /> </td> 
   <td> A entrega está pronta para ser enviada e será processada pelo servidor de entrega (MTA). Consulte <a href="#pending-status" target="_blank">Status pendente</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Not applicable<br /> </td> 
   <td> A entrega foi levada em conta pelo servidor (MTA), mas não foi processada.<br /> </td> 
  </tr>  
  <tr> 
   <td> Delivery canceled<br /> </td> 
   <td> A entrega foi cancelada por um operador.<br /> </td> 
  </tr> 
  <tr> 
   <td> Levado em consideração pelo provedor de serviço<br /> </td> 
   <td> O provedor de serviços SMS recebeu a entrega.<br /> Para instalações hospedadas ou híbridas, se você atualizou para o <a href="sending-with-enhanced-mta.md" target="_blank">MTA aprimorado</a>, a mensagem foi repassada com êxito do Campaign para o MTA aprimorado.</td> 
  </tr> 
  <tr> 
   <td> Received on mobile<br /> </td> 
   <td> O destinatário recebeu o SMS em seu dispositivo móvel.<br /> </td> 
  </tr>
  <tr> 
   <td> Sent to the service provider<br /> </td> 
   <td> A entrega foi enviada para o provedor de serviços SMS, mas ainda não foi recebida.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Prepared<br /> </td> 
   <td> Status intermediário usado somente para conectores externos como o canal móvel. Ele segue o status "Pendente" e é o conector externo que determinará o status seguinte.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Para saber como otimizar a capacidade de entrega dos emails do Adobe Campaign, consulte [esta seção](about-deliverability.md). Para obter informações mais detalhadas sobre a capacidade de entrega, consulte o [Manual de práticas recomendadas de capacidade de entrega da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).

## Status pendente {#pending-status}

Após confirmar a entrega, você pode ver que o status da entrega é **[!UICONTROL Pending]**. Esse status significa que o processo de execução está aguardando a disponibilidade de alguns recursos.

O status **[!UICONTROL Pending]** pode significar que a sua entrega foi agendada e está pendente até a data especificada. Para obter mais informações, consulte a seção [Agendamento de entrega](steps-sending-the-delivery.md#scheduling-the-delivery-sending).

Se a entrega não estiver sendo enviada e o status permanecer **[!UICONTROL Pending]**, poderá ser devido a:

* O MTA (Message Transfer Agent), que executa módulos e processos no servidor de entrega e que gerencia o envio de emails, pode não ter sido iniciado ou precisa ser reiniciado.

  Para verificar isso e iniciar o módulo se necessário, siga as seguintes etapas:

  >[!NOTE]
  >
  >Esta operação pode ser executada com um modelo de hospedagem **no local** ou **híbrido** com acesso ao servidor do Campaign (consulte [modelos de hospedagem](../../installation/using/hosting-models.md)).

   1. Verifique se os `mta@<instance>` módulos são iniciados nos servidores MTA.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<instance-name> (9268) - 23.0 Mb
      [...]
      ```

   1. Se o MTA não estiver listado, comece com o seguinte comando:

      ```
      nlserver start mta@<instance-name>
      ```

      >[!NOTE]
      >
      >Substitua `<instance-name>` pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração: `[path of application]nl6/conf/config-<instance-name>.xml`

* Pode ser que a entrega esteja usando uma afinidade não configurada no servidor emissor.

  Nesse caso, verifique a configuração do gerenciamento de tráfego (afinidade IP) e use o campo **[!UICONTROL Managing affinities with IP addresses]** para vincular entregas ao MTA que gerencia a afinidade. Para obter mais informações sobre afinidades, consulte [esta seção](../../installation/using/configure-delivery-settings.md).

* Quando muitas campanhas estão sendo executadas, o status da entrega permanece como “Pendente”.

  O limite de campanhas simultâneas é definido na opção **[!UICONTROL NmsOperation_LimitConcurrency]**. O valor padrão é 10.

  Saiba mais sobre opções [nesta página](../../installation/using/configuring-campaign-options.md).


**Tópicos relacionados:**

* [Histórico e logs da entrega](#delivery-logs-and-history)
* [Noções básicas sobre falhas de entrega](understanding-delivery-failures.md)
* [Tipos e motivos de falha de entrega](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
