---
product: campaign
title: Serviços de assinatura
description: Saiba mais sobre a atividade de fluxo de trabalho Serviços de assinatura
feature: Workflows, Targeting Activity, Subscription Services Activity
hide: true
exl-id: 1b526d1c-4a33-45a1-98f4-dcb803c8d228
TQID: 'https://experienceleague.adobe.com/-qfMiHLzlE5uJIV5-ba1MNymo0SHuMYxC6EnurLexI8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
  - id: 2454f09c-f028-5647-8fef-1e986ec2d4e5
    internal-label: Subscription Services Activity
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 100%
---
# Serviços de assinatura{#subscription-services}



Uma atividade tipo **Subscription services** permite criar ou excluir uma subscrição para um serviço de informações para a população especificada na transição.

Para configurá-la, edite a atividade e insira seu rótulo, então selecione a ação a ser executada (Subscrição ou Unsubscription) e o serviço relacionado, como no exemplo a seguir:

![](assets/edit_service_inscription.png)

1. Insira o rótulo da atividade.
1. Selecione **[!UICONTROL Generate an outbound transition]** para criar uma transição no final da execução.

   Geralmente, a assinatura de um segmento em um serviço de informações marca o final do fluxo de trabalho de segmentação, por isso a opção não está ativada por padrão.

1. Clique em **[!UICONTROL Subscription]** ou em **[!UICONTROL Unsubscription]** para assinar ou cancelar a subscrição da população especificada para ou a partir do serviço de informações selecionado.
1. Selecione **[!UICONTROL Send a confirmation message]** para notificar os destinatários que a subscrição de um serviço foi realizada ou cancelada.

   O conteúdo dessa mensagem é definido no modelo de entrega associado ao serviço de assinatura. Para obter mais informações, consulte esta [seção](../../delivery/using/managing-subscriptions.md).

## Exemplo: inscrever uma lista de destinatários em um boletim informativo {#example--subscribe-a-list-of-recipients-to-a-newsletter}

Em uma única operação, o fluxo de trabalho a seguir visa fazer uma lista de destinatários qualificados para um boletim informativo, destinado a pessoas que trabalham em Paris, para que assinem.

Para fazer isso, também é necessário excluir os destinatários que já estão subscritos.

>[!CAUTION]
>
>Antes de subscrever destinatários manualmente a um serviço, verifique se esses destinatário aceitam receber comunicações.

![](assets/subscription_services_example.png)

1. Adicione as três queries a seguir:

   * Uma direcionada a destinatários com idade entre 18 e 60 anos.
   * Uma segunda direcionada a destinatários que residem em Paris.
   * Uma terceira direcionada a destinatários que não se inscreveram no boletim informativo.

1. Adicione uma atividade de interseção para cruzar os resultados diferentes.
1. Se desejar, insira um list update para manter a lista de subscritos atualizada.
1. Insira uma atividade de serviços de subscrição e clique duas vezes nesta opção para configurá-la.
1. Insira o rótulo da atividade e selecione **[!UICONTROL Subscription]**.

   Se desejar, é possível informar os destinatários sobre a subscrição do boletim informativo marcando a caixa **[!UICONTROL Send a confirmation message]**.

1. Selecione a pasta em que o boletim informativo está e em seguida, selecione o boletim informativo na lista exibida.
1. Deixe a opção **[!UICONTROL Generate outbound transition]** desmarcada para que esta atividade marque o final do fluxo de trabalho e clique em **[!UICONTROL Ok]**.

Durante a execução do fluxo de trabalho, os destinatários que correspondem a todas as três queries são adicionados à lista e subscritos ao boletim informativo.

É possível verificar se a subscrição foi bem-sucedida acessando a guia **[!UICONTROL Subscription]** dos destinatários.

## Parâmetros de entrada {#input-parameters}

* tableName
* esquema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

