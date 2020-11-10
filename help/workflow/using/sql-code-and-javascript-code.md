---
title: Código SQL e código JavaScript
description: Saiba mais sobre atividades de fluxo de trabalho de códigos SQL e JavaScript
page-status-flag: never-activated
uuid: 20a39bbf-c6b0-4697-97b4-c07609cfb048
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 1afa75c2-7377-4d03-9105-11bcc9e3206c
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 95%

---


# Código SQL e código JavaScript{#sql-code-and-javascript-code}

## Código SQL {#sql-code}

Uma atividade **[!UICONTROL SQL code]** executa um script SQL. O script é um template JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   A área central do editor contém o script a ser executado. Este script é um template JST e, portanto, pode ser configurado de acordo com o contexto do workflow.

* **[!UICONTROL Processing errors]**

   Consulte [Processamento de erros](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Código JavaScript e código JavaScript avançado {#javascript-code}

As atividades **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** executam um script JavaScript no contexto de um workflow. Para obter mais informações sobre scripts, consulte a seção [Modelos e scripts do JavaScript](../../workflow/using/javascript-scripts-and-templates.md)

>[!NOTE]
>
>Por padrão, a fase de execução de **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** não pode exceder 1 hora. Após esse atraso, o processo será interrompido com uma mensagem de erro e a execução da atividade falhará.
>
>É possível alterar esse atraso no campo **[!UICONTROL Stop execution after]** disponível nas propriedades da atividade.

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**: A área central do editor contém o script a ser executado.
   * **[!UICONTROL Processing errors]**: Consulte [Processamento de erros](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**: A primeira zona do editor contém o script a ser executado durante a primeira chamada.
   * **[!UICONTROL Next calls]**: A segunda zona do editor contém o script a ser executado durante as próximas chamadas.
   * **[!UICONTROL Transitions]**: Você pode definir várias transições de atividade de output.
   * **[!UICONTROL Schedule]**: A guia **[!UICONTROL Schedule]** permite agendar quando acionar a atividade.
