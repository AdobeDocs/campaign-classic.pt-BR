---
product: campaign
title: Configuração da integração
description: Configuração da integração
audience: integrations
content-type: reference
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '373'
ht-degree: 100%

---


# Opção de pipeline NmsPipeline_Config {#nmspipeline_config}

Quando a autenticação funcionar, [!DNL pipelined] poderá recuperar os eventos e processá-los. Somente os acionadores configurados no Adobe Campaign são processados, os demais são ignorados. O acionador deve ter sido gerado pelo Analytics e enviado previamente para o pipeline.
A opção também pode ser configurada com um curinga para capturar todos os acionadores independentemente do nome.

A configuração dos acionadores é feita em uma opção, em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. O nome da opção é **[!UICONTROL NmsPipeline_Config]**. O tipo de dados é &quot;long text&quot; em formato JSON.

Este exemplo especifica dois acionadores.

Cole o código JSON desse modelo no valor da opção. Remova os comentários.

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
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

Este segundo exemplo captura todos os acionadores.

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

>[!NOTE]
>
>O valor da UID [!DNL Trigger] para um nome de acionador específico na interface do Analytics pode ser encontrado como parte dos parâmetros de sequência de consulta de URL na interface dos acionadores. A UID triggerType é transmitida no fluxo de dados do pipeline e o código pode ser gravado no pipeline.JS para mapear a UID do acionador para um rótulo amigável ao usuário que pode ser armazenado em uma coluna Nome do acionador no schema pipelineEvents.

## O parâmetro consumidor {#consumer-parameter}

O pipeline funciona com um modelo de &quot;fornecedor e consumidor&quot;. Pode haver muitos consumidores na mesma fila. As mensagens são &quot;consumidas&quot; somente para um consumidor individual. Cada consumidor recebe sua própria &quot;cópia&quot; das mensagens.

O parâmetro &quot;consumidor&quot; identifica a instância como um desses consumidores. É a identidade da instância que chama o pipeline. Você pode preenchê-lo com o nome da instância. O serviço de pipeline rastreia as mensagens recuperadas por cada consumidor. Usar consumidores diferentes para instâncias diferentes garante que cada mensagem seja enviada para cada instância.

## Como configurar a opção Pipeline {#configure-pipeline-option}

Adicione ou edite acionadores da Experience Cloud sob a matriz &quot;acionadores&quot;; não edite o resto.
Verifique se o JSON é válido com a ajuda deste [site](http://jsonlint.com/).

* “name” é a ID do acionador. Um curinga &quot;*&quot; captura todos os acionadores.
* &quot;Consumidor&quot; é qualquer string única que identifique exclusivamente a instância nlserver. Normalmente, pode ser o próprio nome da instância. Para vários ambientes (dev/stage/prod), verifique se ela é exclusiva para cada um deles para que cada instância receba uma cópia da mensagem.
* [!DNL Pipelined] também aceita o tópico &quot;aliases&quot;.

Reinicie o [!DNL pipelined] depois de fazer as alterações.
