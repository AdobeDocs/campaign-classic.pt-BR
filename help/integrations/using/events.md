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
source-git-commit: 9f70468e3dd7003a18812d07669f10c561e8bef7
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 2%

---


# Triggers eventos {#events}

## Processando eventos no JavaScript {#events-javascript}

### Arquivo JavaScript {#file-js}

O pipeline usa uma função JavaScript para processar cada mensagem. Essa função é definida pelo usuário.

Está configurado na **[!UICONTROL NmsPipeline_Config]** opção sob o atributo &quot;JSConnector&quot;. Esse javascript é chamado toda vez que um evento é recebido. É executado pelo [!DNL pipelined] processo.

O arquivo JS de amostra é cus:triggers.js.

### função JavaScript {#function-js}

O [!DNL pipelined] Javascript deve ser start com uma função específica.

Essa função é chamada uma vez para cada evento:

```
function processPipelineMessage(xmlTrigger) {}
```

Deve voltar como

```
<undefined/>
```

Reinicie [!DNL pipelined] após editar o JS.

### Acionar formato de dados {#trigger-format}

Os [!DNL trigger] dados são passados para a função JS. Está no formato XML.

* O **[!UICONTROL @triggerId]** atributo contém o nome do [!DNL trigger].
* O elemento **enriquecimentos** no formato JSON contém os dados gerados pela Analytics e está anexado ao acionador.
* **[!UICONTROL @offset]** é o &quot;ponteiro&quot; da mensagem. Indica a ordem da mensagem na fila.
* **[!UICONTROL @partitio]**n é um container de mensagens na fila. O deslocamento é relativo a uma partição. <br>Há cerca de 15 partições na fila.

Exemplo:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Formato dos dados do Enriquecimento {#enrichment-format}

>[!NOTE]
>
>É um exemplo específico de várias implementações possíveis.

O conteúdo é definido no Analytics para cada acionador. Está no formato JSON.
Por exemplo, em um acionador LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** pode conter a ID do comprador usada para reconciliar com recipient de Campanha. Está no formato String. <br>Deve ser reconciliado para localizar a ID do comprador, que é a chave primária.

* **[!UICONTROL timeGMT]** pode conter a hora do acionador no lado do Analytics. Está no formato UTC Epoch (segundos desde 01/01/1970 UTC).

Exemplo:

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### Ordem de processamento dos eventos {#order-events}

Os eventos são processados um de cada vez, por ordem de deslocamento. Cada thread do [!DNL pipelined] processa uma partição diferente.

O &quot;deslocamento&quot; do último evento recuperado é armazenado no banco de dados. Portanto, se o processo for interrompido, ele será reiniciado a partir da última mensagem. Esses dados são armazenados no schema incorporado xtk:pipelineOffset.

Esse ponteiro é específico para cada instância e para cada consumidor. Por conseguinte, quando muitas instâncias acedem ao mesmo gasoduto com consumidores diferentes, cada um recebe todas as mensagens e pela mesma ordem.

O parâmetro &quot;consumer&quot; da opção de pipeline identifica a instância chamadora.

Atualmente, não há como ter filas diferentes para ambientes separados, como &quot;armazenamento temporário&quot; ou &quot;desenvolvimento&quot;.

### Registro e tratamento de erros {#logging-error-handling}

Logs como logInfo() são direcionados ao [!DNL pipelined] log. Erros como logError() são gravados no [!DNL pipelined] log e fazem com que o evento seja colocado em uma fila de tentativas. Verifique o log implantado.
Mensagens com erro são repetidas várias vezes na duração definida nas [!DNL pipelined] opções.

Para fins de depuração e monitoramento, os dados completos do acionador são gravados na tabela do acionador. Está no campo &quot;dados&quot; no formato XML. Como alternativa, um logInfo() contendo os dados do acionador serve a mesma finalidade.

### Análise dos dados {#data-parsing}

Este exemplo de código JS analisa o eVar01 nos enriquecimentos.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

Tenha cuidado ao analisar para evitar erros.
Como esse código é usado para todos os acionadores, a maioria dos dados não é necessária. Portanto, pode ser deixado em branco quando não estiver presente.

### Como guardar o acionador {#storing-triggers-js}

>[!NOTE]
>
>É um exemplo específico de várias implementações possíveis.

Este exemplo de código JS salva o acionador no banco de dados.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>; 
 }
```

### Restrições {#constraints}

O desempenho deste código deve ser ideal, pois ele é executado em altas frequências. Existem potenciais efeitos negativos para outras atividades de marketing. Especialmente se o processamento de mais de um milhão de eventos acionam por hora no servidor de marketing. Ou se não estiver ajustado corretamente.

O contexto deste Javascript é limitado. Nem todas as funções da API estão disponíveis. Por exemplo, getOption() ou getCurrentdate() não funcionam.

Para permitir um processamento mais rápido, vários threads desse script são executados ao mesmo tempo. O código deve ser seguro para thread.

## Como armazenar os eventos {#store-events}

>[!NOTE]
>
>É um exemplo específico de várias implementações possíveis.

### schema do evento Pipeline {#pipeline-event-schema}

Eventos são armazenados em uma tabela de banco de dados. Ele é usado pelas campanhas de marketing para clientes do público alvo e enriquece emails usando acionadores.
Embora cada acionador possa ter uma estrutura de dados distinta, todos os acionadores podem ser mantidos em uma única tabela.
O campo triggerType identifica a partir do qual os dados são acionados.

Este é um exemplo de código de schema para esta tabela:

| Atributo | Tipo | Rótulo | Descrição |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Longo | Chave primária | A chave primária interna do acionador. |
| data | Memorando | Dados do acionador | O conteúdo completo dos dados de disparo no formato XML. Para depurar e auditar. |
| triggerType | Sequência 50 | TriggerType | O nome do acionador. Identifica o comportamento do cliente no site. |
| shopper_id | Sequência 32 | shopper_id | O identificador interno do comprador. Definido pelo fluxo de trabalho de reconciliação. Se zero, isso significa que o cliente é desconhecido na Campanha. |
| shopper_key | Longo | shopper_key | O Identificador externo do comprador foi capturado pela Analytics. |
| created | Data e hora | Criado | A hora em que o evento foi criado na Campanha. |
| lastModified | Data e hora | Última modificação | A última vez que o evento foi modificado no Adobe. |
| timeGMT | Data e hora | Carimbo de data e hora | A hora em que o evento foi gerado no Analytics. |

### Exibição dos eventos {#display-events}

Os eventos podem ser exibidos com um formulário simples baseado no schema eventos.

>[!NOTE]
>
>O nó do Evento Pipeline não está integrado e precisa ser adicionado, assim como o formulário relacionado precisa ser criado na Campanha. Essas operações são restritas somente a usuários especialistas. Para obter mais informações, consulte estas seções: [Hierarquia](../../configuration/using/about-navigation-hierarchy.md) de navegação e [edição de formulários](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Processamento dos eventos {#processing-the-events}

### Fluxo de trabalho de reconciliação {#reconciliation-workflow}

A reconciliação é o processo de fazer a correspondência do cliente da Analytics ao banco de dados da Campanha. Por exemplo, os critérios de correspondência podem ser o shopper_id.

Por motivos de desempenho, a correspondência deve ser feita no modo de lote por um fluxo de trabalho.
A frequência deve ser definida como 15 minutos para otimizar a carga de trabalho. Como consequência, o atraso entre uma recepção de evento e seu processamento por um fluxo de trabalho de marketing é de até 15 minutos.

### Opções de reconciliação de unidade em JavaScript {#options-unit-reconciliation}

Em teoria, é possível executar o query de reconciliação para cada acionador no JavaScript. Ele tem um impacto maior no desempenho e oferece resultados mais rápidos. Pode ser necessário para casos específicos de utilização quando for necessária reatividade.

Pode ser difícil fazer isso se nenhum índice estiver definido em shopper_id. Se os critérios estiverem em um servidor de banco de dados separado do que o servidor de marketing, ele usará um link de banco de dados, que tem desempenho ruim.

### Expurgar fluxo de trabalho {#purge-workflow}

Os acionadores são processados dentro de uma hora, portanto não há razão para mantê-los por um longo tempo. O volume pode ser de aproximadamente 1 milhão de acionadores por hora. Isso explica por que um fluxo de trabalho de purga deve ser implementado. A limpeza exclui todos os acionadores com mais de três dias e é executada uma vez por dia.

### Fluxo de trabalho de Campanha {#campaign-workflow}

O fluxo de trabalho da campanha de disparo geralmente é semelhante a outras campanhas recorrentes que foram usadas.
Por exemplo, ele pode ser start com um query nos acionadores que procuram eventos específicos durante o último dia. Esse público alvo é usado para enviar o e-mail. Enriquecimentos ou dados podem vir do acionador. Ele pode ser usado com segurança pelo Marketing, pois não requer configuração.
