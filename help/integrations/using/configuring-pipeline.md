---
product: campaign
title: Configurar o pipeline
description: Saiba como configurar o pipeline para a integração entre o Campaign e os acionadores
feature: Triggers
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 98%

---

# Configurar o pipeline {#configuring-pipeline}

Parâmetros de autenticação, como a ID do cliente, chave privada e ponto de acesso de autenticação são configurados nos arquivos de configuração da instância.

A lista de acionadores que serão processados é configurada em uma opção em formato JSON.

Os acionadores são usados para direcionamento por um fluxo de trabalho de campanha que envia emails. A campanha é configurada para que um cliente que tenha ambos os eventos de acionador receba um email.

## Pré-requisitos {#prerequisites}

Antes de iniciar esta configuração, verifique se você tem:

* Um projeto do Adobe Developer
* Um ID de organização válido - Para encontrar seu ID de organização, consulte [esta página](https://experienceleague.adobe.com/pt-br/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* Um acesso de desenvolvedor para sua organização
* Uma configuração de acionadores válida no Adobe Analytics

A autenticação é necessária, pois o pipeline está hospedado na Adobe Experience Cloud. Ele usa uma autenticação compatível por meio de um projeto do Adobe Developer.

## Etapa 1: criar/atualizar o projeto do Adobe Developer {#creating-adobe-io-project}

Você deve habilitar sua organização com tokens de conta do Adobe Developer para a integração de acionadores.

Saiba como criar sua conta técnica da Adobe [nesta página](../../integrations/using/oauth-technical-account.md). Observe que é necessário selecionar **[!UICONTROL Adobe Analytics]** ao adicionar a API à credencial do Adobe Developer.

## Etapa 2: configurar a opção de pipeline {#configuring-nmspipeline}

Depois que a autenticação for definida, o pipeline recuperará os eventos. Ele processará somente acionadores configurados no Adobe Campaign. O acionador deve ser gerado pelo Adobe Analytics e enviado para o pipeline que processará somente acionadores configurados no Adobe Campaign.

A opção também pode ser configurada com um curinga para capturar todos os acionadores independentemente do nome.

1. No Adobe Campaign, acesse o menu de opções em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** no **[!UICONTROL Explorer]**.

1. Selecione a opção **[!UICONTROL NmsPipeline_Config]**.

1. No campo **[!UICONTROL Value (long text)]**, você pode colar o seguinte código JSON, que especifica dois acionadores. Remova os comentários.

   ```json
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

1. Também é possível optar por colar o seguinte código JSON, que captura todos os acionadores.

   ```json
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

### Definir o parâmetro do consumidor {#consumer-parameter}

O pipeline funciona com um modelo de fornecedor e consumidor. As mensagens são consumidas somente para um consumidor individual: cada consumidor recebe sua própria cópia das mensagens.

O parâmetro **consumidor** identifica a instância como um desses consumidores. A identidade da instância chamará o pipeline. Você pode preenchê-lo com o nome da instância que pode ser encontrado na página Monitoramento do console do cliente.

O serviço de pipeline rastreia as mensagens recuperadas por cada consumidor. Usar consumidores diferentes para instâncias diferentes permite que você se certifique de que cada mensagem seja enviada para cada instância.

### Recomendações da opção de pipeline {#pipeline-option-recommendation}

Para configurar a opção Pipeline, siga estas recomendações:

* Adicionar ou editar acionadores em **[!UICONTROL Triggers]**.
* Verifique se o JSON é válido. 
* O parâmetro **Nome** corresponde à ID do acionador. Um curinga “*” capturará todos os acionadores.
* O parâmetro **Consumidor** corresponde ao nome da instância de chamada ou do aplicativo.
* O processo `pipelined` também aceita o tópico “aliases”.
* Você deve sempre reiniciar o processo `pipelined` após realizar alterações.

## (opcional) Etapa 3: configuração adicional {#step-optional}

Você pode alterar alguns parâmetros internos de acordo com seus requisitos de carga, mas certifique-se de testá-los antes de aplicá-los ao ambiente de produção.

A lista de parâmetros opcionais é:

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
| processingThreads | Número de mensagens de processamento de threads dedicados com código integrado. <br>O padrão é 4 |
| retryPeriodSec | Atraso entre tentativas em caso de erros de processamento. <br>O padrão é 30 (segundos) |
| retryValiditySec | Descarte a mensagem se ela não for processada com êxito após esse período (muitas tentativas). <br>O padrão é 300 (segundos) |

### Início automático do processo de pipeline {#pipelined-process-autostart}

O processo `pipelined` precisa ser iniciado automaticamente.

Para fazer isso, defina o elemento de `<`pipeline`>` no arquivo de configuração como autostart=&quot;true&quot;:

```sql
 <pipelined autoStart="true" ... "/>
```

### Reinicialização do processo de pipeline {#pipelined-process-restart}

É necessário reiniciar para que as alterações entrem em vigor:

```sql
nlserver restart pipelined@instance
```

## Etapa 4: validação {#step-validation}

Para validar a configuração do pipeline para provisionamento, siga as etapas abaixo:

* Certifique-se de que o processo `pipelined` esteja em execução.
* Verifique `pipelined.log` para logs de conexão de pipeline.
* Verifique a conexão e se os pings foram recebidos. Os clientes hospedados podem usar o monitoramento no console do cliente.
