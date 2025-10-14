---
product: campaign
title: Solução de problemas de envio de entrega
description: Saiba mais sobre o desempenho da entrega e como solucionar problemas relacionados ao monitoramento da entrega
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 87%

---

# Solução de problemas de envio de entrega {#delivery-troubleshooting}

Esta seção lista problemas comuns que você pode encontrar ao enviar entregas e como solucioná-los.

Além disso, siga as práticas recomendadas e a lista de verificação detalhada [nesta página](delivery-performances.md) para garantir que suas entregas tenham bom desempenho.

**Tópicos relacionados:**

* [Status da entrega](delivery-statuses.md)
* [Painel de entrega](delivery-dashboard.md)
* [Noções básicas sobre falhas de entrega](understanding-delivery-failures.md)

## Entregas lentas {#slow-deliveries}

Depois de clicar no botão **[!UICONTROL Send]**, sua entrega parece demorar mais do que o normal. Isso pode ser causado por elementos diferentes:

* Alguns provedores de email podem ter adicionado seus endereços IP a uma lista de bloqueios. Neste caso, verifique seus broadlogs e consulte [esta seção](about-deliverability.md).

* Sua entrega pode ser muito grande para ser processada rapidamente, isso pode ocorrer com alta personalização do JavaScript ou se a sua entrega pesa mais do que 60 kbytes. Consulte as [Práticas recomendadas de entrega](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html?lang=pt-BR){target="_blank"} do Adobe Campaign v8.  para saber mais sobre as diretrizes de conteúdo.

* Pode ter ocorrido limitação dentro do MTA do Adobe Campaign. Isso é causado por:

   * Mensagens pendentes (**[!UICONTROL quotas met]** message): as cotas declaradas pelas regras MX declarativas definidas no Campaign foram atendidas. Para obter mais informações sobre esse tipo de mensagem, consulte [esta página](deliverability-faq.md). Para saber mais sobre as regras MX, consulte [esta seção](../../installation/using/email-deliverability.md#about-mx-rules).

   * Mensagens pendentes (mensagem **[!UICONTROL dynamic flow control]**): o MTA do Campaign encontrou erros ao tentar entregar mensagens para um determinado ISP, o que faz com que um atraso evite uma densidade de erros muito grande e, portanto, enfrente uma possível inclusão na lista de bloqueios.

* Um problema do sistema pode impedir que os servidores interajam: isso pode desacelerar todo o processo de envio. Verifique os servidores para garantir que não haja problemas de memória ou recursos que possam afetar o Campaign no processo de obter os dados de personalização, por exemplo.

## Entregas agendadas {#scheduled-deliveries-}

Se as entregas não forem executadas em uma data agendada específica, pode ser por diferença entre o fuso horário dos servidores. A instância mid-sourcing e a instância de produção podem estar em fusos horários diferentes.

Como exemplo, se a instância mid-sourcing estiver no fuso horário Brisbane e a instância de produção estiver no fuso horário de Darwin, os fusos horários têm meia hora de diferença um do outro e, no log de auditoria, é possível ver claramente que se a entrega está agendada para produção em 11:56, o mesmo delivery agendado para mid deve ser em 12:26, com uma diferença de meia hora.

## Status de falha {#failed-status}

Se o status de uma entrega de email for **[!UICONTROL Failed]**, ela poderá ser vinculada a um problema com blocos de personalização. Os blocos de personalização em uma entrega podem gerar erros quando os esquemas não correspondem ao mapeamento da entrega, por exemplo.

Os logs da entrega são fundamentais para saber por que uma entrega falhou. Aqui estão possíveis erros que você pode detectar nos logs de entrega:

* Se as mensagens do destinatário falharem com uma declaração de erro &quot;Inacessível&quot;:

  ```
  Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
  ```

  A causa desse problema é quase sempre uma personalização na tentativa do HTML que chama uma tabela ou campo que não foi definido ou mapeado no direcionamento de upstream ou no target mapping da entrega.

  Para corrigir isso, o fluxo de trabalho e o conteúdo da entrega precisam ser revisados para determinar especificamente qual personalização está tentando chamar a tabela em questão e se a tabela pode ou não ser mapeada. A partir daí, ao remover a chamada para esta tabela no HTML ou ao corrigir o mapping para a entrega pode ser o caminho para a resolução.

* No modelo de implantação mid-sourcing, a seguinte mensagem pode aparecer nos logs de entrega:

  ```
  Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
  ```

  A causa está vinculada aos problemas de desempenho. Significa que a instância de marketing gasta muito tempo criando dados antes de enviá-los ao servidor mid-sourcing.

  Para resolver isso, recomendamos executar um vácuo e reindexação no banco de dados. Para obter mais informações sobre manutenção de banco de dados, consulte [esta seção](../../production/using/recommendations.md).

  Você também deve reiniciar todos os fluxos de trabalho com uma atividade agendada e todos os fluxos de trabalho com o status de falha. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/scheduler.html){target="_blank"}.

* Quando uma entrega falha, o seguinte erro pode aparecer nos logs de entrega:

  ```
  DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
  ```

  Normalmente, esse erro significa que há um campo ou bloco de personalização no email com mais de um valor para o destinatário. Um bloco de personalização está sendo usado e está buscando mais de um registro para um determinado destinatário.

  Para resolver isso, verifique os dados de personalização usados e verifique o target para os destinatários que têm mais de uma entrada para qualquer um desses campos. Você também pode usar uma atividade **[!UICONTROL Deduplication]** no fluxo de trabalho de segmentação antes da atividade de entrega para verificar se há apenas um campo de personalização por vez. Para obter mais informações sobre desduplicação, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/deduplication.html){target="_blank"}.

* Algumas entregas podem falhar com um erro &quot;Inacessível&quot; informando:

  ```
  Inbound email bounce (rule 'Auto_replies' has matched this bounce).
  ```

  Isso significa que a entrega teve êxito, mas o Adobe Campaign recebeu uma resposta automática do destinatário (por exemplo, uma &quot;ausência temporária&quot;) que corresponde às regras de email de entrada &quot;Respostas_automáticas&quot;.

  O email de resposta automática é ignorado pelo Adobe Campaign e o endereço do destinatário não será enviado para a quarentena.
