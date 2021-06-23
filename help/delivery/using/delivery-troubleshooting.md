---
product: campaign
title: Solução de problemas
description: Saiba mais sobre o desempenho do delivery e como solucionar problemas relacionados ao monitoramento do delivery.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 100%

---

# Solução de problemas de envio de delivery {#delivery-troubleshooting}

Esta seção lista problemas comuns que você pode encontrar ao enviar deliveries e como solucioná-los.

Além disso, siga as práticas recomendadas e a lista de verificação detalhada [nesta página](delivery-performances.md) para garantir que seus deliveries tenham bom desempenho.

**Tópicos relacionados:**

* [Status da entrega](delivery-statuses.md)
* [Painel de entrega](delivery-dashboard.md)
* [Noções básicas sobre falhas de entrega](understanding-delivery-failures.md)

## Deliveries lentos {#slow-deliveries}

Depois de clicar no botão **[!UICONTROL Send]**, seu delivery parece demorar mais do que o normal. Isso pode ser causado por elementos diferentes:

* Alguns provedores de email podem ter adicionado seus endereços IP a uma lista de bloqueios. Neste caso, verifique seus broadlogs e consulte [esta seção](about-deliverability.md).

* Seu delivery pode ser muito grande para ser processado rapidamente, isso pode ocorrer com alta personalização do JavaScript ou se o seu delivery pesa mais do que 60 kbytes. Consulte as [Práticas recomendadas de delivery](delivery-best-practices.md) do Adobe Campaign para saber mais sobre as diretrizes de conteúdo.

* Pode ter ocorrido limitação dentro do MTA do Adobe Campaign. Isso é causado por:

   * Mensagens pendentes (**[!UICONTROL quotas met]** message): as cotas declaradas pelas regras MX declarativas definidas no Campaign foram atendidas. Para obter mais informações sobre esse tipo de mensagem, consulte [esta página](deliverability-faq.md). Para saber mais sobre as regras MX, consulte [esta seção](../../installation/using/email-deliverability.md#about-mx-rules).

   * Mensagens pendentes (mensagem **[!UICONTROL dynamic flow control]**): o MTA do Campaign encontrou erros ao tentar entregar mensagens para um determinado ISP, o que faz com que um atraso evite uma densidade de erros muito grande e, portanto, enfrente uma possível inclusão na lista de bloqueios.

* Um problema do sistema pode impedir que os servidores interajam: isso pode desacelerar todo o processo de envio. Verifique os servidores para garantir que não haja problemas de memória ou recursos que possam afetar o Campaign no processo de obter os dados de personalização, por exemplo.

## Deliveries agendados {#scheduled-deliveries-}

Se os deliveries não forem executados em uma data agendada específica, ela poderá estar relacionada a uma diferença entre o fuso horário dos servidores. A instância mid-sourcing e a instância de produção podem estar em fusos horários diferentes.

Como exemplo, se a ocorrência de mid-sourcing estiver no fuso horário de Brisbane e a instância de produção estiver no fuso horário de Darwin, os fusos horários têm meia hora de diferença um do outro e, no log de auditoria, é possível ver claramente que se o delivery estiver agendado para a produção às 11h56, o mesmo delivery agendado para mid deveria ser às 12h26, com uma diferença de meia hora.

## Falha no status {#failed-status}

Se o status de um delivery de email for **[!UICONTROL Failed]**, ele poderá ser vinculado a um problema com blocos de personalização. Os blocos de personalização em um delivery podem gerar erros quando os schemas não correspondem ao mapeamento do delivery, por exemplo.

Os logs do delivery são fundamentais para saber por que um delivery falhou. Aqui estão possíveis erros que você pode detectar nos logs de delivery:

* Se as mensagens do recipient falharem com uma declaração de erro &quot;Inacessível&quot;:

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   A causa desse problema é quase sempre uma personalização na tentativa do HTML que chama uma tabela ou campo que não foi definido ou mapeado no direcionamento de upstream ou no target mapping do delivery.

   Para corrigir isso, o workflow e o conteúdo do delivery precisam ser revisados para determinar especificamente qual personalização está tentando chamar a tabela em questão e se a tabela pode ou não ser mapeada. A partir daí, ao remover a chamada para esta tabela no HTML ou ao corrigir o mapping para o delivery pode ser o caminho para a resolução.

* No modelo de implantação mid-sourcing, a seguinte mensagem pode aparecer nos logs de delivery:

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   A causa está vinculada aos problemas de desempenho. Significa que a instância de marketing gasta muito tempo criando dados antes de enviá-los ao servidor mid-sourcing.

   Para resolver isso, recomendamos executar um vácuo e reindexação no banco de dados. Para obter mais informações sobre manutenção de banco de dados, consulte [esta seção](../../production/using/recommendations.md).

   Você também deve reiniciar todos os workflows com uma atividade agendada e todos os workflows com o status de falha. Consulte [esta seção](../../workflow/using/scheduler.md).

* Quando um delivery falha, o seguinte erro pode aparecer nos logs de delivery:

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   Normalmente, esse erro significa que há um campo ou bloco de personalização no email com mais de um valor para o recipient. Um bloco de personalização está sendo usado e está buscando mais de um registro para um determinado recipient.

   Para resolver isso, verifique os dados de personalização usados e verifique o target para os recipients que têm mais de uma entrada para qualquer um desses campos. Você também pode usar uma atividade **[!UICONTROL Deduplication]** no workflow para construção do target antes da atividade de delivery para verificar se há apenas um campo de personalização por vez. Para obter mais informações sobre desduplicação, consulte [esta página](../../workflow/using/deduplication.md).

* Alguns deliveries podem falhar com um erro &quot;Inacessível&quot; informando:

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   Isso significa que o delivery teve êxito, mas o Adobe Campaign recebeu uma resposta automática do recipient (por exemplo, uma &quot;ausência temporária&quot;) que corresponde às regras de email de entrada &quot;Respostas_automáticas&quot;.

   O email de resposta automática é ignorado pelo Adobe Campaign e o endereço do recipient não será enviado para a quarentena.
