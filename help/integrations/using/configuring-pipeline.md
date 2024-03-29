---
product: campaign
title: Configuração do pipeline
description: Saiba como configurar o pipeline
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 99%

---

# Configuração de pipeline {#configuring-pipeline}



Parâmetros de autenticação, como ID do cliente, chave privada e ponto de acesso de autenticação, são configurados nos arquivos de configuração da instância.
A lista de acionadores que serão processados é configurada em uma opção em formato JSON.
Os acionadores são usados para direcionamento por um fluxo de trabalho de campanha que envia emails. A campanha é configurada para que um cliente que tenha ambos os eventos de acionador receba um email.

## Pré-requisitos {#prerequisites}

Antes de iniciar esta configuração, verifique se você está usando:

* No mínimo, uma das seguintes builds do Adobe Campaign:
   * 19.1.8.9039
   * 19.1.4.9032 - Gold Standard 11
   * 20.2.4.9187
   * 20.3.1
* Versão do Adobe Analytics Standard

Você também precisará de:

* Autenticação de projeto do Adobe I/O
* um ID de organização válido - Para encontrar seu ID de organização, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=pt-BR){_blank}
* um Acesso de desenvolvedor para sua organização
* configuração de acionadores efetuada no Adobe Analytics

## Arquivos de autenticação e configuração {#authentication-configuration}

A autenticação é necessária, pois o pipeline está hospedado na Adobe Experience Cloud.
Ele usa um par de chaves públicas e privadas. Esse processo tem a mesma função de um usuário/senha, porém é mais seguro.
A autenticação é compatível com a Marketing Cloud por meio do Projeto do Adobe I/O.

## Etapa 1: Criar/atualizar projeto do Adobe I/O {#creating-adobe-io-project}

Para clientes hospedados, você pode criar um tíquete de atendimento ao cliente para habilitar sua organização com tokens de conta técnica do Adobe I/O para a integração do Triggers.

Para clientes locais, consulte a página [Configuração do Adobe I/O para o Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md). Observe que é necessário selecionar **[!UICONTROL Adobe Analytics]** ao adicionar a API à credencial do Adobe I/O.

## Etapa 2: configurar a opção de pipeline NmsPipeline_Config {#configuring-nmspipeline}

Depois que a autenticação for definida, o pipeline recuperará os eventos. Ele processará somente acionadores configurados no Adobe Campaign. O acionador deve ter sido gerado pelo Adobe Analytics e enviado para o pipeline que processará somente acionadores configurados no Adobe Campaign.
A opção também pode ser configurada com um curinga para capturar todos os acionadores independentemente do nome.

1. No Adobe Campaign, acesse o menu de opções em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** no **[!UICONTROL Explorer]**.

1. Selecione a opção **[!UICONTROL NmsPipeline_Config]**.

1. No campo **[!UICONTROL Value (long text)]**, você pode colar o seguinte código JSON, que especifica dois acionadores. Remova os comentários.

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

### O parâmetro do consumidor {#consumer-parameter}

O pipeline funciona com um modelo de fornecedor e consumidor. As mensagens são consumidas somente para um consumidor individual: cada consumidor recebe sua própria cópia das mensagens.

O parâmetro **consumidor** identifica a instância como um desses consumidores. A identidade da instância chamará o pipeline. Você pode preenchê-lo com o nome da instância que pode ser encontrado na página Monitoramento do console do cliente.

O serviço de pipeline rastreia as mensagens recuperadas por cada consumidor. Usar consumidores diferentes para instâncias diferentes permite que você se certifique de que cada mensagem seja enviada para cada instância.

### Recomendações da opção de pipeline {#pipeline-option-recommendation}

Para configurar a opção Pipeline, siga estas recomendações:

* Adicione ou edite acionadores em **[!UICONTROL Triggers]**. Você não deve editar o restante.
* Verifique se o JSON é válido. Você pode usar um Validador de JSON, consulte este [site](https://jsonlint.com/) para obter um exemplo.
* “name” corresponde à ID do acionador. Um curinga “*” capturará todos os acionadores.
* “Consumidor” corresponde ao nome da instância chamadora ou do aplicativo.
* Pipeline também aceita o tópico “aliases”.
* Você sempre deve reiniciar o pipeline depois de fazer alterações.

## Etapa 3: configuração opcional {#step-optional}

Você pode alterar alguns parâmetros internos de acordo com seus requisitos de carga, mas certifique-se de testá-los antes de colocá-los em produção.

A lista de parâmetros opcionais pode ser encontrada abaixo:

| Opção | Descrição |
|:-:|:-:|
| appName(Legacy) | AppID do aplicativo OAuth registrado no aplicativo Legacy Oath em que a chave pública foi carregada. Para obter mais informações, consulte esta [página](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
| authGatewayEndpoint(Legacy) | URL para obter tokens de gateway. Padrão: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | A chave privada, parte pública carregada no aplicativo Legacy Oath, AES criptografada com a opção XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | A ação de desabilitar a autenticação, conectando sem tokens de gateway é aceita somente por alguns pontos de acesso do pipeline de desenvolvimento. |
| discoverPipelineEndpoint | URL para descobrir o ponto de acesso dos serviços de pipeline que serão usados para este locatário. Padrão: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | O período entre dois despejos do processo de estado interno no estado interno ```var/INSTANCE/pipelined.json.``` <br> também está acessível sob demanda aqui: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Desabilite a detecção do PipelineServicesEndpoint e force-a |
| monitorServerPort | O processo de pipeline ouvirá nesta porta para fornecer o processo de estado interno aqui: ```http://INSTANCE:PORT/pipelined/status```. <br>O padrão é 7781 |
| pointerFlushMessageCount | Quando esse número de mensagens é processado, os corretores serão salvos no banco de dados. <br> O padrão é 1000 |
| pointerFlushPeriodSec | Após esse período, os deslocamentos serão salvos no banco de dados. <br>O padrão é 5 (segundos) |
| processingJSThreads | Número de mensagens de processamento de threads dedicados com conectores JS personalizados. <br> O padrão é 4 |
| processingThreads | Número de mensagens de processamento de threads dedicados com código incorporado. <br>O padrão é 4 |
| retryPeriodSec | Atraso entre tentativas em caso de erros de processamento. <br>O padrão é 30 (segundos) |
| retryValiditySec | Descarte a mensagem se ela não for processada com êxito após esse período (muitas tentativas). <br>O padrão é 300 (segundos) |

### Início automático do processo de pipeline {#pipelined-process-autostart}

O processo por pipeline precisa ser iniciado automaticamente.

Para fazer isso, defina o elemento &lt; pipelined > no arquivo de configuração como autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### Reinicialização do processo de pipeline {#pipelined-process-restart}

É necessário reiniciar para que as alterações entrem em vigor:

```
nlserver restart pipelined@instance
```

## Etapa 4: validação {#step-validation}

Para validar a configuração do pipeline para provisionamento, siga as etapas abaixo:

* Certifique-se de que o processo [!DNL pipelined] esteja em execução.
* Verifique se há logs de conexão de pipeline no pipelined.log.
* Verifique a conexão e se os pings foram recebidos. Os clientes hospedados podem usar o monitoramento no console do cliente.
