---
product: campaign
title: Serviços de assinatura
description: Saiba mais sobre a atividade do workflow de serviços de assinatura
feature: Workflows, Targeting Activity, Subscription Services Activity
exl-id: 1b526d1c-4a33-45a1-98f4-dcb803c8d228
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: ht
source-wordcount: '407'
ht-degree: 100%

---

# Serviços de assinatura{#subscription-services}

![](../../assets/common.svg)

Uma atividade tipo **Subscription services** permite criar ou excluir uma subscrição para um serviço de informações para a população especificada na transição.

Para configurá-la, edite a atividade e insira seu rótulo, então selecione a ação a ser executada (Subscrição ou Unsubscription) e o serviço relacionado, como no exemplo a seguir:

![](assets/edit_service_inscription.png)

1. Insira o rótulo da atividade.
1. Selecione **[!UICONTROL Generate an outbound transition]** para criar uma transição no final da execução.

   Geralmente, a subscrição de um target em um serviço de informações marca o final do workflow para construção do target, por isso a opção não está ativada por padrão.

1. Clique em **[!UICONTROL Subscription]** ou em **[!UICONTROL Unsubscription]** para assinar ou cancelar a subscrição da população especificada para ou a partir do serviço de informações selecionado.
1. Selecione **[!UICONTROL Send a confirmation message]** para notificar os destinatários que a subscrição de um serviço foi realizada ou cancelada.

   O conteúdo dessa mensagem é definido no template de delivery associado ao serviço de assinatura. Para obter mais informações, consulte esta [seção](../../delivery/using/managing-subscriptions.md).

## Exemplo: inscrever uma lista de recipients em um boletim informativo {#example--subscribe-a-list-of-recipients-to-a-newsletter}

Em uma única operação, o workflow a seguir visa fazer uma lista de recipients qualificados para um boletim informativo, destinado a pessoas que trabalham em Paris, a fim de subscrevê-las.

Para fazer isso, também é necessário excluir os recipients que já estão subscritos.

>[!CAUTION]
>
>Antes de subscrever recipients manualmente a um serviço, verifique se esses recipient aceitam receber comunicações.

![](assets/subscription_services_example.png)

1. Adicione as três queries a seguir:

   * Uma voltada a recipients com idade entre 18 e 60 anos.
   * Uma segunda direcionada a recipients que residem em Paris.
   * Uma terceira direcionada a recipients que não se inscreveram no boletim informativo.

1. Adicione uma atividade de interseção para cruzar os resultados diferentes.
1. Se desejar, insira um list update para manter a lista de subscritos atualizada.
1. Insira uma atividade de serviços de subscrição e clique duas vezes nesta opção para configurá-la.
1. Insira o rótulo da atividade e selecione **[!UICONTROL Subscription]**.

   Se desejar, é possível informar os destinatários sobre a subscrição do boletim informativo marcando a caixa **[!UICONTROL Send a confirmation message]**.

1. Selecione a pasta em que o boletim informativo está e em seguida, selecione o boletim informativo na lista exibida.
1. Deixe a opção **[!UICONTROL Generate outbound transition]** desmarcada para que esta atividade marque o final do workflow e clique em **[!UICONTROL Ok]**.

Durante a execução do workflow, os recipients que correspondem a todas as três queries são adicionados à lista e subscritos ao boletim informativo.

É possível verificar se a subscrição foi bem-sucedida acessando a guia **[!UICONTROL Subscription]** dos destinatários.

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.
