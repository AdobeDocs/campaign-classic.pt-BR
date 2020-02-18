---
title: Código SQL e código JavaScript
seo-title: Código SQL e código JavaScript
description: Código SQL e código JavaScript
seo-description: null
page-status-flag: never-activated
uuid: 20a39bbf-c6b0-4697-97b4-c07609cfb048
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 1afa75c2-7377-4d03-9105-11bcc9e3206c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 16e35b62cdf42c04139cc17645095a3d1f6e0fa7

---


# Código SQL e código JavaScript{#sql-code-and-javascript-code}

## Código SQL {#sql-code}

Uma atividade **[!UICONTROL SQL code*]* executa um script SQL. O script é um template JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   A área central do editor contém o script a ser executado. Este script é um template JST e, portanto, pode ser configurado de acordo com o contexto do workflow.

* **[!UICONTROL Processing errors]**

   Consulte Erros [de](../../workflow/using/monitoring-workflow-execution.md#processing-errors)processamento.

## Código JavaScript e código JavaScript avançado {#javascript-code}

**[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** as atividades executam um script JavaScript no contexto de um fluxo de trabalho. Para obter mais informações sobre scripts, consulte a seção scripts e modelos [do](../../workflow/using/javascript-scripts-and-templates.md) JavaScript.

>[!NOTE]
>
>Por padrão, a fase de execução das atividades **[!UICONTROL JavaScript code]** **[!UICONTROL Advanced JavaScript code]** e das atividades não pode exceder uma hora. Após esse atraso, o processo será abortado com uma mensagem de erro e a execução da atividade falhará.
>
>É possível alterar esse atraso no **[!UICONTROL Stop execution after]** campo disponível nas propriedades das atividades.

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**: A área central do editor contém o script a ser executado.
   * **[!UICONTROL Processing errors]**:Consulte Erros [de](../../workflow/using/monitoring-workflow-execution.md#processing-errors)processamento.

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**: A primeira zona do editor contém o script a ser executado durante a primeira chamada.
   * **[!UICONTROL Next calls]**: A segunda zona do editor contém o script a ser executado durante as próximas chamadas.
   * **[!UICONTROL Transitions]**: Você pode definir várias transições de atividade de output.
   * **[!UICONTROL Schedule]**:A **[!UICONTROL Schedule]** guia permite agendar quando a atividade será acionada.
