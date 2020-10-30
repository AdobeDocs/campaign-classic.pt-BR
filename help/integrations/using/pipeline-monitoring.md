---
title: Configuração da integração
seo-title: Configuração da integração
description: Configuração da integração
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '438'
ht-degree: 100%

---


# Monitoramento de pipeline {#pipeline-monitoring}

O serviço web de status [!DNL pipelined] fornece informações sobre o status do processo [!DNL pipelined].

Ele pode ser acessado manualmente usando um navegador ou automaticamente com um aplicativo de monitoramento

e está no formato REST, como descrito abaixo.

![](assets/triggers_8.png)

## Indicadores {#indicators}

Esta seção lista os indicadores no serviço web de status.

Os indicadores recomendados para monitorados são realçados.

* Consumidor: nome do cliente que está enviando os acionadores. Configurado na opção pipeline.
* http-request
   * last-live-ms-ago: tempo em ms desde a realização de uma verificação de conexão.
   * last-failed-cnx-ms-ago: tempo em ms desde a última falha de verificação de conexão.
   * pipeline-host: nome do host onde os dados do pipeline são obtidos.
* ponteiro
   * current-offsets: valor do ponteiro no pipeline, por thread filha.
   * last-flush-ms-ago: tempo em ms desde a recuperação de um lote de acionadores.
   * next-offsets-flush: tempo de espera até o próximo lote, quando concluído.
   * processed-since-last-flush: número de acionadores processados no último lote.
* roteamento
   * acionadores: lista de acionadores recuperados. Configurado na opção [!DNL pipelined].
* stats
   * average-pointer-flush-time-ms: tempo médio de processamento para um lote de acionadores.
   * average-trigger-processing-time-ms: tempo médio gasto analisando os dados de acionadores.
   * bytes-read: número de bytes da fila lidos desde o início do processo.
   * current-messages: número atual de mensagens pendentes que foram extraídas da fila e estão aguardando processamento. **Este indicador deve estar próximo de zero**.
   * current-retries: número atual de mensagens que falharam no processamento e estão aguardando nova tentativa.
   * peak-messages: número máximo de mensagens pendentes tratadas pelo processo desde seu início.
   * pointer-flushes: número de lotes de mensagens processadas desde o início.
   * routing-JS-custom: número de mensagens processadas pelo JS personalizado.
   * trigger-discarded: número de mensagens que foram descartadas após muitas tentativas devido a erros de processamento.
   * trigger-processed: número de mensagens que foram processadas sem erro.
   * trigger-received: número de mensagens recebidas da fila.

Essas estatísticas são exibidas por thread de processamento.

* average-trigger-processing-time-ms: tempo médio gasto analisando os dados de acionadores.
* is-JS-processor: valor &quot;1&quot; se esse thread usar o JS personalizado.
* trigger-discarded: número de mensagens que foram descartadas após muitas tentativas devido a erros de processamento. **Este indicador deve ser zero**.
* trigger-failures: número de erros de processamento no JS. **Este indicador deve ser zero**.
* trigger-received: número de mensagens recebidas da fila.

* Configurações: são definidas nos arquivos de configuração.
   * flush-pointer-msg-count: número de mensagens em um lote.
   * flush-pointer-period-ms: tempo entre dois lotes, em milissegundos.
   * processing-threads-JS: número de threads de processamento que executam o JS personalizado.
   * retry-period-ms: tempo entre duas tentativas quando ocorre um erro de processamento.
   * retry-validity-duration-ms: a duração do processamento é repetida até que a mensagem seja descartada.
   * Relatório de mensagens de pipeline

## Relatório de mensagens de pipeline {#pipeline-report}

Este relatório exibe o número de mensagens por hora nos últimos cinco dias.

![](assets/triggers_9.png)
