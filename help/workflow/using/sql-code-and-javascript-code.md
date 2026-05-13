---
product: campaign
title: Código SQL e código JavaScript
description: Saiba mais sobre atividades de fluxo de trabalho de códigos SQL e JavaScript
feature: Workflows
hide: true
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
TQID: https://experienceleague.adobe.com/B-OWeBTtXSxSD1k-qgRq06ymp00LvVH2U7k9yRAN3YE
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 100%

---

# Código SQL e código JavaScript{#sql-code-and-javascript-code}



## Código SQL {#sql-code}

Uma atividade **[!UICONTROL SQL code]** executa um script SQL. O script é um modelo JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

  A área central do editor contém o script a ser executado. Este script é um modelo JST e, portanto, pode ser configurado de acordo com o contexto do fluxo de trabalho.

* **[!UICONTROL Processing errors]**

  Consulte [Processamento de erros](monitoring-workflow-execution.md#processing-errors).

## Código JavaScript e código JavaScript avançado {#javascript-code}

As atividades **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** executam um script JavaScript no contexto de um fluxo de trabalho. Para obter mais informações sobre scripts, consulte essas seções:

* [Modelos e scripts JavaScript](javascript-scripts-and-templates.md)
* [Exemplos de código JavaScript em fluxos de trabalho](javascript-in-workflows.md)

### Atraso de execução {#exec-delay}

A partir da versão 20.2, um atraso de execução foi adicionado às atividades **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]**. Por padrão, a fase de execução não pode exceder 1 hora. Após esse atraso, o processo será interrompido com uma mensagem de erro e a execução da atividade falhará.

É possível alterar esse atraso no campo **[!UICONTROL Stop execution after]**, disponível nestas atividade.

Para ignorar esse limite, é necessário definir o valor como **0**.

### Código JavaScript {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: A área central do editor contém o script a ser executado.

* **[!UICONTROL Process errors]**: Consulte [Processamento de erros](monitoring-workflow-execution.md#processing-errors).

### Código JavaScript avançado {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**: A primeira zona do editor contém o script a ser executado durante a primeira chamada.
* **[!UICONTROL Next calls]**: A segunda zona do editor contém o script a ser executado durante as próximas chamadas.
* **[!UICONTROL Transitions]**: Você pode definir várias transições de atividade de output.
* **[!UICONTROL Schedule]**: A guia **[!UICONTROL Schedule]** permite agendar quando acionar a atividade.

O JavaScript avançado é uma tarefa persistente e será retomado periodicamente se não for marcado como concluído. Para encerrar a tarefa e evitar futuras recuperações, você deve usar o método **task.setCompleted()** na seção **[!UICONTROL Next calls]**:

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
