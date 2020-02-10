---
title: Consulta incremental
seo-title: Consulta incremental
description: Consulta incremental
seo-description: null
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Consulta incremental{#incremental-query}

Um query incremental permite selecionar periodicamente um target com base em um critério, enquanto exclui as pessoas já alvos desse critério.

O público que já foi alvo é armazenado na memória pela instância de workflow e por atividade, ou seja, dois workflows iniciados do mesmo template não compartilham o mesmo log. Por outro lado, duas tarefas baseadas no mesmo query incremental para a mesma instância de workflow usarão o mesmo log.

The query is defined in the same way as for standard queries (refer to [Creating a query](../../workflow/using/query.md#creating-a-query)), but its execution is scheduled.

>[!CAUTION]
>
>Se o resultado de um query incremental for igual a **0** durante uma de suas execuções, o workflow será pausado até a próxima execução programada do query. As transições e as atividades que seguem o query incremental não são, portanto, processadas antes da execução a seguir.

Para fazer isso:

1. Na **[!UICONTROL Scheduling & History]** guia, selecione a **[!UICONTROL Schedule execution]** opção. A tarefa permanece ativa após sua criação e só será acionada nos horários especificados pelo agendamento para execução do query. No entanto, se a opção estiver desabilitada, o query será executado imediatamente, **de uma só vez**.
1. Clique no botão **[!UICONTROL Change]**.

   In the **[!UICONTROL Schedule editing wizard]** window, you can configure the type of frequency, event recurrence and event validity period.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Clique **[!UICONTROL Finish]** para salvar o agendamento.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. The lower section of the **[!UICONTROL Scheduling & History]** tab allows you to select the number of days to be taken into account in the history.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      Os recipients já alvos podem ser registrados em um número máximo de dias a partir do dia de envio do target. Se esse valor for zero, os recipients nunca serão removidos do log.

   * **[!UICONTROL Keep history when starting]**

      Essa opção não permite limpar o log quando a atividade estiver habilitada.

   * **[!UICONTROL SQL table name]**

      Esse parâmetro permite que você sobrecarregue a tabela SQL padrão contendo os dados do histórico.

## Exemplo de um query incremental: atualização trimestral da lista {#example-of-an-incremental-query--quarterly-list-update}

No exemplo a seguir, um query incremental é usado para atualizar automaticamente uma lista de recipients. Esses recipients são alvos como parte das campanhas de marketing sazonais.

Como essas campanhas são iniciadas no início de cada temporada para oferecer atividades esportivas relevantes, essas listas são atualizadas a cada trimestre. No entanto, um recipient só deve ser alvo dessa campanha uma vez a cada 9 meses. Isso permite espaçar a frequência de elegibilidade do recipient e oferecer atividades para diferentes estações ao longo dos anos.

![](assets/incremental_query_example.png)

1. Adicione um query incremental, bem como uma atividade de atualização da lista em um novo workflow.
1. Configure a **[!UICONTROL Incremental query]** guia da atividade conforme especificado em [Criação de uma consulta](../../workflow/using/query.md#creating-a-query).
1. Select the **[!UICONTROL Scheduling & History]** tab and then specify a 270-day history. Um recipient que já foi alvo não será novamente por um período de 270 dias ou aproximadamente 9 meses.

   Then click the **[!UICONTROL Change...]** button.

1. To ensure the list is updated before the start of each season, select **[!UICONTROL Monthly]**.
1. Na próxima tela, selecione março, junho, setembro e dezembro. Escolha o dia 20 do mês e escolha o horário que deseja iniciar o workflow.
1. Em seguida, selecione o período de validade do query. For example, if you want this activity to be permanently active, select **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. After approving the incremental query, configure the list update activity as explained in [List update](../../workflow/using/list-update.md).

O workflow será iniciado automaticamente e imediatamente antes do início de cada estação. A lista será atualizada com os novos recipients qualificados para receber as ofertas.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o público alvo do query. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de metas, **[!UICONTROL schema]** é o esquema da população (normalmente nms:customer) e **[!UICONTROL recCount]** é o número de elementos na tabela.
