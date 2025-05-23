---
product: campaign
title: Configuração de eventos
description: Saiba como configurar eventos para implementação personalizada
feature: Triggers
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: ht
source-wordcount: '1206'
ht-degree: 100%

---

# Configuração de eventos para implementação personalizada {#events}



Partes dessa configuração são um desenvolvimento personalizado e requerem o seguinte:

* Conhecimento prático de análise JSON, XML e Javascript no Adobe Campaign.
* Conhecimento prático das APIs QueryDef e Writer.
* Noções de trabalho de criptografia e autenticação usando chaves privadas.

Como a edição do código JavaScript requer habilidades técnicas, não tente fazê-la sem a compreensão adequada.

## Processamento de eventos no JavaScript {#events-javascript}

### Arquivo JavaScript {#file-js}

O pipeline usa uma função JavaScript para processar cada mensagem. Essa função é definida pelo usuário.

Está configurado na opção **[!UICONTROL NmsPipeline_Config]** sob o atributo &quot;JSConnector&quot;. Esse JavaScript é chamado toda vez que um evento é recebido. É executado pelo processo [!DNL pipelined].

O arquivo JavaScript de amostra é cus:triggers.js.

### Função JavaScript {#function-js}

O Javascript [!DNL pipelined] deve ser iniciado com uma função específica.

Essa função é chamada uma vez para cada evento:

```
function processPipelineMessage(xmlTrigger) {}
```

Deveria voltar como

```
<undefined/>
```

Você deve reiniciar o [!DNL pipelined] após editar o JavaScript.

### Acionar formato de dados {#trigger-format}

Os dados [!DNL trigger] são passados para a função JS no formato XML.

* O atributo **[!UICONTROL @triggerId]** contém o nome do [!DNL trigger].
* O elemento de **enriquecimentos** no formato JSON contém os dados gerados pelo Adobe Analytics e está anexado ao acionador.
* **[!UICONTROL @offset]** é o &quot;ponteiro&quot; para a mensagem. Indica a ordem da mensagem na fila.
* **[!UICONTROL @partition]** é um container de mensagens na fila. O deslocamento é relativo a uma partição. <br>Há cerca de 15 partições na fila.

Exemplo:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Enriquecimento do formato de dados {#enrichment-format}

>[!NOTE]
>
>É um exemplo específico de várias implementações possíveis.

O conteúdo é definido no formato JSON no Adobe Analytics para cada acionador.
Por exemplo, em um acionador LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** pode conter a ID do consumidor em formato String, utilizada para reconciliar com destinatários do Adobe Campaign. <br>Deve ser reconciliado para localizar a ID do consumidor, que é a chave primária.

* **[!UICONTROL timeGMT]** pode conter a hora do acionador no lado do Adobe Analytics no formato UTC Epoch (segundos desde 01/01/1970 UTC).

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

### Ordem de processamento de eventos{#order-events}

Os eventos são processados um de cada vez, por ordem de deslocamento. Cada thread do [!DNL pipelined] processa uma partição diferente.

O “deslocamento” do último evento recuperado é armazenado no banco de dados. Portanto, se o processo for interrompido, será reiniciado a partir da última mensagem. Esses dados são armazenados no schema integrado xtk:pipelineOffset.

Esse ponteiro é específico para cada instância e para cada consumidor. Portanto, quando muitas instâncias acessam o mesmo pipeline com consumidores diferentes, cada um recebe todas as mensagens na mesma ordem.

O parâmetro **consumidor** da opção de pipeline identifica a instância de chamada.

Atualmente, não há como ter filas diferentes para ambientes separados, como &quot;staging&quot; ou &quot;dev&quot;.

### Registro e tratamento de erros {#logging-error-handling}

Registros como logInfo() são direcionados ao log de [!DNL pipelined]. Erros como logError() são gravados no log de [!DNL pipelined] e fazem com que o evento seja colocado em uma fila de tentativas. Nesse caso, você deve verificar o log de pipeline.
Mensagens com erro são repetidas várias vezes na duração definida nas opções de [!DNL pipelined].

Para fins de depuração e monitoramento, os dados completos do acionador são gravados na tabela de acionadores no campo &quot;dados&quot; no formato XML. Como alternativa, um logInfo() contendo os dados do acionador tem a mesma finalidade.

### Análise dos dados {#data-parsing}

Este código JavaScript de amostra analisa a eVar01 nos enriquecimentos.

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
Como esse código é usado para todos os acionadores, a maioria dos dados não é exigida. Portanto, pode ser deixado em branco quando não estiver presente.

### Armazenar o acionador {#storing-triggers-js}

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

O desempenho deste código deve ser ideal, pois é executado em altas frequências e pode causar possíveis efeitos negativos para outras atividades de marketing. Especialmente se ocorrer o processamento de mais de um milhão de eventos acionadores por hora no servidor de marketing ou se ele não estiver ajustado corretamente.

O contexto deste Javascript é limitado. Nem todas as funções da API estão disponíveis. Por exemplo, getOption() ou getCurrentdate() não funcionam.

Para permitir um processamento mais rápido, vários threads desse script são executados ao mesmo tempo. O código deve ser seguro para thread.

## Armazenar os eventos {#store-events}

>[!NOTE]
>
>É um exemplo específico de várias implementações possíveis.

### Schema do evento pipeline {#pipeline-event-schema}

Eventos são armazenados em uma tabela do banco de dados. Ele é usado pelas campanhas de marketing para clientes do público-alvo e enriquece emails usando acionadores.
Embora cada acionador possa ter uma estrutura de dados distinta, todos os acionadores podem ser mantidos em uma única tabela.
O campo triggerType identifica o acionador a partir do qual os dados são originados.

Este é um exemplo de código de schema para esta tabela:

| Atributo | Tipo | Rótulo | Descrição |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Longo | Chave primária | A chave primária interna do acionador. |
| dados | Memorando | Dados do acionador | O conteúdo completo dos dados do acionador em formato XML. Para fins de depuração e auditoria. |
| triggerType | String 50 | TriggerType | O nome do acionador. Identifica o comportamento do cliente no site. |
| shopper_id | String 32 | shopper_id | O identificador interno do comprador. Definido pelo workflow de reconciliação. Se for zero, significa que o cliente é desconhecido no Campaign. |
| shopper_key | Longo | shopper_key | O identificador externo do comprador foi capturado pelo Analytics. |
| criado | Data e hora | Criado | A hora em que o evento foi criado no Campaign. |
| lastModified | Data e hora | Última modificação | A última vez que o evento foi modificado na Adobe. |
| timeGMT | Data e hora | Carimbo de data e hora | A hora em que o evento foi gerado no Analytics. |

### Exibição de eventos {#display-events}

Os eventos podem ser exibidos com um formulário simples baseado no schema de eventos.

>[!NOTE]
>
>O nó do evento pipeline não está integrado e precisa ser adicionado, assim como o formulário relacionado precisa ser criado no Campaign. Essas operações são restritas unicamente a usuários especialistas. Para obter mais informações, consulte estas seções: [Hierarquia de navegação](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy) e [Edição de formulários](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Processamento de eventos {#processing-the-events}

### Workflow de reconciliação {#reconciliation-workflow}

A reconciliação é o processo que faz a correspondência do cliente do Adobe Analytics ao banco de dados do Campaign. Por exemplo, os critérios de correspondência podem ser o shopper_id.

Por motivos de desempenho, a correspondência deve ser feita no modo de lote por um workflow.
A frequência deve ser definida como 15 minutos para otimizar a carga de trabalho. Como consequência, o atraso entre uma recepção de evento e seu processamento por um workflow de marketing é de até 15 minutos.

### Opções de reconciliação de unidade em JavaScript {#options-unit-reconciliation}

É possível executar o query de reconciliação para cada acionador no JavaScript. Ele tem um impacto maior no desempenho e oferece resultados mais rápidos. Pode ser necessário para casos específicos de utilização quando for necessária reatividade.

A implementação pode ser difícil se nenhum índice estiver definido em shopper_id. Se os critérios estiverem em um servidor de banco de dados separado do servidor de marketing, será usado um link de banco de dados com desempenho inadequado.

### Limpar workflow {#purge-workflow}

Os acionadores são processados em uma hora. O volume pode ser de aproximadamente 1 milhão de acionadores por hora. Isso explica por que um workflow de limpeza deve ser implementado. A limpeza é executada uma vez por dia e exclui todos os acionadores com mais de três dias.

### Workflow de campanha {#campaign-workflow}

O workflow de campanha do acionador geralmente é semelhante a outras campanhas recorrentes já usadas.
Por exemplo, pode iniciar com um query nos acionadores que procuram eventos específicos durante o último dia. Esse público-alvo é usado para enviar o email. Enriquecimentos ou dados podem vir do acionador. Pode ser usado com segurança pelo Marketing, pois não requer configuração.
