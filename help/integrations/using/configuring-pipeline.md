---
title: Configuração do pipeline
description: Saiba como configurar o pipeline
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 4f949d8db3aa3082acf1765bf66080b270cc6db4
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 20%

---


# Configuração de pipeline {#configuring-pipeline}

Parâmetros de autenticação, como ID do cliente, chave privada e ponto de entrada de autenticação, são configurados nos arquivos de configuração da instância.
A lista de acionadores a serem processados é configurada em uma opção no formato JSON.
Os acionadores são usados para segmentação por um workflow de campanha que envia emails. A campanha é configurada para que um cliente que tenha ambos os eventos de acionador receba um email.

>[!CAUTION]
>
>No caso de implantação híbrida, verifique se o pipeline está configurado em uma instância intermediária.

## Pré-requisitos {#prerequisites}

Antes de iniciar esta configuração, verifique se você tem:

* uma versão recente do Adobe Campaign (20.2.1 e superior),
* Versão Adobe Analytics Standard

Você também precisará:

* Autenticação de projeto de E/S de Adobe
* um IMSOrgID válido, o identificador do cliente Experience Cloud com a Adobe Analytics foi adicionado
* um acesso do desenvolvedor à Organização IMS
* aciona a configuração feita no Adobe Analytics

## Arquivos de autenticação e configuração {#authentication-configuration}

A autenticação é necessária, pois o pipeline está hospedado no Adobe Experience Cloud.
Ele usa um par de chaves públicas e privadas. Esse processo tem a mesma função de usuário/senha, mas é mais seguro.
A autenticação é compatível com o Marketing Cloud por meio do Projeto de E/S do Adobe.

## Etapa 1: Criando/atualizando projetos de E/S de Adobe {#creating-adobe-io-project}

Para clientes hospedados, você pode criar um ticket de atendimento ao cliente para habilitar sua organização com tokens de conta técnica de E/S do Adobe para a integração de Acionadores.

Para clientes locais, consulte a página [Configuração de E/S de Adobe para acionadores](../../integrations/using/configuring-adobe-io.md) Adobe Experience Cloud. Observe que é necessário selecionar **[!UICONTROL Adobe Analytics]** ao adicionar a API à credencial de E/S do Adobe.

## Etapa 2: Configuração da opção de pipeline NmsPipeline_Config {#configuring-nmspipeline}

Depois que a autenticação for definida, o pipeline recuperará os eventos. Ele processará somente acionadores configurados no Adobe Campaign. O acionador deve ter sido gerado da Adobe Analytics e enviado para o pipeline que processará somente acionadores configurados no Adobe Campaign.
A opção também pode ser configurada com um curinga para capturar todos os acionadores independentemente do nome.

1. No Adobe Campaign, acesse o menu de opções em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** no **[!UICONTROL Explorer]**.

1. Selecione a opção **[!UICONTROL NmsPipeline_Config]**.

1. No **[!UICONTROL Value (long text)]** campo, você pode colar o seguinte código JSON, que especifica dois acionadores. Você precisa remover os comentários.

   ```
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
           "triggers": [ // Array of triggers.
               {
                   "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                   "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
               }, {
                   "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                   "jsConnector": "cus:triggers.js" // Can use the same JS for all.
               },
           ]
       }
   ]
   }
   ```

1. Você também pode optar por colar o seguinte código JSON, que captura todos os acionadores.

   ```
   {
   "topics": [
     {
       "name": "triggers",
       "consumer":  "customer_dev",
       "triggers": [
         {
           "name": "*",
           "jsConnector": "cus:pipeline.js"
         }
       ]
     }
   ]
   }
   ```

### The Consumer parameter {#consumer-parameter}

O gasoduto funciona como um modelo de fornecedor e de consumidor. As mensagens são consumidas somente para um consumidor individual: cada consumidor recebe sua própria cópia das mensagens.

The **Consumer** parameter identifies the instance as one of these consumers. A identidade da instância chamará o pipeline. Você pode preenchê-lo com o nome da instância que pode ser encontrado na página Monitoramento do Console do cliente.

O serviço de pipeline rastreia as mensagens recuperadas por cada consumidor. Usar consumidores diferentes para instâncias diferentes permite que você se certifique de que cada mensagem seja enviada para cada instância.

### Recomendações da opção Pipeline {#pipeline-option-recommendation}

Para configurar a opção Pipeline, siga estas recomendações:

* Adicione ou edite acionadores em **[!UICONTROL Triggers]**, você não deve editar o restante.
* Verifique se o JSON é válido. Você pode usar um JSON Validator, consulte este [site](http://jsonlint.com/) , por exemplo.
* &quot;name&quot; corresponde à ID do acionador. Um caractere curinga &quot;*&quot; capturará todos os acionadores.
* &quot;Consumidor&quot; corresponde ao nome da instância chamadora ou do aplicativo.
* O pipeline também suporta o tópico &quot;aliases&quot;.
* Você deve sempre reiniciar o pipeline depois de fazer alterações.

## Etapa 3: Configuração opcional {#step-optional}

Você pode alterar alguns parâmetros internos de acordo com seus requisitos de carga, mas certifique-se de testá-los antes de colocá-los em produção.

A lista de parâmetros opcionais pode ser encontrada abaixo:

| Opção | Descrição |
|:-:|:-:|
| appName(Herdado) | AppID do aplicativo OAuth registrado no aplicativo Legacy Oath no qual a chave pública foi carregada. Para obter mais informações, consulte esta [página](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint(Legacy) | URL para obter tokens de gateway. Padrão: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | A chave privada, parte pública carregada no aplicativo Legacy Oath, AES criptografada com a opção XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Desabilitar autenticação, a conexão sem tokens de gateway será aceita somente por alguns pontos de extremidade do Pipeline de desenvolvimento. |
| discoverPipelineEndpoint | URL para localizar o ponto de extremidade do Pipeline Services a ser usado para este locatário. Padrão: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | O período entre dois despejos do processo de estado interno no estado ```var/INSTANCE/pipelined.json.``` <br> interno também está acessível sob demanda aqui: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Desative a detecção do PipelineServicesEndpoint para forçá-lo |
| monitorServerPort | O processo implantado ouvirá nesta porta para fornecer o processo de estado interno aqui: ```http://INSTANCE:PORT/pipelined/status```. <br>O padrão é 7781 |
| pointerFlushMessageCount | Quando esse número de mensagens é processado, os deslocamentos serão salvos no banco de dados. <br> O padrão é 1000 |
| pointerFlushPeriodSec | Após esse período, os deslocamentos serão salvos no banco de dados. <br>O padrão é 5 (segundos) |
| processingJSThreads | Número de mensagens de processamento de threads dedicados com conectores JS personalizados. <br> O padrão é 4 |
| processingThreads | Número de mensagens de processamento de threads dedicados com código incorporado. <br>O padrão é 4 |
| retryPeriodSec | Atraso entre tentativas em caso de erros de processamento. <br>O padrão é 30 (segundos) |
| retryValiditySec | Descarte a mensagem se ela não for processada com êxito após esse período (muitas tentativas). <br>O padrão é 300 (segundos) |

### Início automático do processo de pipeline {#pipelined-process-autostart}

O processo por pipeline precisa ser iniciado automaticamente.

Para isso, defina o elemento &lt; pipelined > no arquivo de configuração como autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### Reinicialização do processo de pipeline {#pipelined-process-restart}

É necessário reiniciar para que as alterações entrem em vigor:

```
nlserver restart pipelined@instance
```

## Etapa 4: Validação {#step-validation}

Para validar a configuração do pipeline para provisionamento, siga as etapas abaixo:

* Make sure the [!DNL pipelined] process is running.
* Verifique se há registros de conexão de pipeline no pipelined.log.
* Verifique a conexão e se os pings foram recebidos. Os clientes hospedados podem usar o Monitoramento no Console do cliente.
