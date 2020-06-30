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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 2%

---


# Monitoramento de tubulação {#pipeline-monitoring}

O serviço Web de status de pipeline fornece informações sobre o status do processo de pipeline.

Ele pode ser acessado manualmente usando um navegador ou automaticamente com um aplicativo de monitoramento.

Está no formato REST, descrito abaixo.

![](assets/triggers_8.png)

## Indicadores {#indicators}

Esta seção lista os indicadores no serviço Web de status.

Os indicadores recomendados a serem monitorados são realçados.

* Consumidor: nome do cliente que está puxando os acionadores. Configurada na opção pipeline.
* http-request
   * last-live-ms-ago: tempo em ms desde que uma verificação de conexão foi feita.
   * last-failed-cnx-ms-ago: tempo em ms desde a última vez que a verificação de conexão falhou.
   * pipeline-host: nome do host do qual os dados do pipeline são obtidos.
* ponteiro
   * deslocamentos atuais: valor do ponteiro no pipeline, por thread filho.
   * last-flush-ms-ago: tempo em ms desde que um lote de acionadores foi recuperado.
   * próximo deslocamento: tempo de espera até o próximo lote, quando concluído.
   * processado desde o último fluxo: número de acionadores processados no último lote.
* roteamento
   * acionadores: lista de acionadores recuperados. Configurado na opção pipeline.
* stats
   * average-pointer-flush-time-ms: tempo médio de processamento para um lote de acionadores.
   * average-trigger-processing-time-ms: tempo médio gasto analisando os dados de acionadores.
   * bytes lidos: número de bytes lidos da fila desde que o processo foi iniciado.
   * mensagens atuais: número atual de mensagens pendentes que foram extraídas da fila e estão aguardando processamento. **Este indicador deve estar próximo de zero**.
   * tentativas atuais: número atual de mensagens que falharam no processamento e estão aguardando nova tentativa.
   * mensagens de pico: número máximo de mensagens pendentes que o processo tem tratado desde que foi iniciado.
   * ponteiro-libera: número de lotes de mensagens processadas desde o start.
   * roteamento-JS-personalizado: número de mensagens que foram processadas pelo JS personalizado.
   * descartado pelo gatilho: número de mensagens que foram descartadas após muitas tentativas devido a erros de processamento.
   * processado pelo acionador: número de mensagens que foram processadas sem um erro.
   * disparador recebido: número de mensagens recebidas da fila.

Essas estatísticas são exibidas por segmento de processamento.

* average-trigger-processing-time-ms: tempo médio gasto analisando os dados de acionadores.
* is-JS-processor: valor &quot;1&quot; se esse thread usar o JS personalizado.
* descartado pelo gatilho: número de mensagens que foram descartadas após muitas tentativas devido a erros de processamento. **Este indicador deve ser zero**.
* falhas de acionador: número de erros de processamento no JS. **Este indicador deve ser zero**.
* disparador recebido: número de mensagens recebidas da fila.

* Configurações: eles são definidos nos arquivos de configuração.
   * flush-pointer-msg-count: número de mensagens em um lote.
   * flush-pointer-period-ms: tempo entre dois lotes, em milissegundos.
   * processing-threads-JS: número de threads de processamento que executam o JS personalizado.
   * período de repetição-ms: tempo entre duas tentativas quando ocorre um erro de processamento.
   * repetir-validade-duração-ms: a duração do processamento é repetida até que a mensagem seja descartada.
   * Relatório de mensagens de pipeline

## Relatório de mensagens de pipeline {#pipeline-report}

Este relatório exibe o número de mensagens por hora nos últimos cinco dias.

![](assets/triggers_9.png)
