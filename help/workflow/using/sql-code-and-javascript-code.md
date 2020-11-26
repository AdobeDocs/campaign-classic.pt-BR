---
solution: Campaign Classic
product: campaign
title: Código SQL e código JavaScript
description: Saiba mais sobre atividades de workflow de códigos SQL e JavaScript
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%

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
