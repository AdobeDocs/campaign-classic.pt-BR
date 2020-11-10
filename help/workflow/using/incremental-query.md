---
title: Query incremental
description: Saiba mais sobre a atividade do fluxo de trabalho do Query incremental
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 97%

---


# Query incremental{#incremental-query}

Um query incremental permite selecionar periodicamente um target com base em um critério, enquanto exclui as pessoas já alvos desse critério.

O público que já foi alvo é armazenado na memória pela instância de workflow e por atividade, ou seja, dois workflows iniciados do mesmo template não compartilham o mesmo log. Por outro lado, duas tarefas baseadas no mesmo query incremental para a mesma instância de workflow usarão o mesmo log.

O query é definido da mesma forma que queries padrão, mas sua execução é agendada.

**Tópicos relacionados:**

* [Caso de uso: atualização da lista trimestral usando um query incremental](../../workflow/using/quarterly-list-update.md)
* [Criação de query](../../workflow/using/query.md#creating-a-query)

>[!CAUTION]
>
>Se o resultado de um query incremental for igual a **0** durante uma de suas execuções, o workflow será pausado até a próxima execução programada do query. As transições e as atividades que seguem o query incremental não são, portanto, processadas antes da execução a seguir.

Para fazer isso:

1. Na guia **[!UICONTROL Scheduling & History]**, selecione a opção **[!UICONTROL Schedule execution]**. A atividade permanece ativa após a criação e será acionada somente nos horários especificados pelo agendamento para execução do query. No entanto, se a opção estiver desabilitada, o query será executado imediatamente, **de uma só vez**.
1. Clique no botão **[!UICONTROL Change]**.

   Na janela **[!UICONTROL Schedule editing wizard]**, você pode configurar o tipo de frequência, a recorrência do evento e o período de validade do evento.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Clique em **[!UICONTROL Finish]** para salvar o cronograma.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. A seção inferior da guia **[!UICONTROL Scheduling & History]** permite selecionar o número de dias que serão considerados no histórico.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      Os recipients já alvos podem ser registrados em um número máximo de dias a partir do dia de envio do target. Se esse valor for zero, os recipients nunca serão removidos do log.

   * **[!UICONTROL Keep history when starting]**

      Essa opção não permite limpar o log quando a atividade estiver habilitada.

   * **[!UICONTROL SQL table name]**

      Esse parâmetro permite sobrecarregar a tabela SQL padrão que contém os dados do histórico.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o público alvo do query. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de target, **[!UICONTROL schema]** é o schema do público (normalmente nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.
