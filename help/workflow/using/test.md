---
product: campaign
title: Teste
description: Saiba mais sobre a atividade do workflow de teste
feature: Workflows
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%

---

# Teste{#test}

![](../../assets/common.svg)

Uma atividade de tipo **Teste** ativa a primeira transição que satisfaz a condição associada a ela. Se nenhuma condição for satisfeita e se a opção **[!UICONTROL Use the default fork]** for ativada, a transição padrão será ativada.

Uma condição é uma expressão JavaScript que deve ser avaliada como &quot;verdadeira&quot; ou &quot;falsa&quot;. Para inserir a expressão, clique no ícone à direita do nome da condição e selecione **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Para obter mais informações sobre todas as funções adicionais do JavaScript e métodos SOAP do servidor do aplicativo acessível via JavaScript de workflow, consulte a [documentação JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=pt-BR).

Também é possível inserir variáveis diretamente no editor. Para obter mais informações sobre como trabalhar com variáveis, consulte [esta seção](javascript-scripts-and-templates.md#variables).

As condições podem ser adicionadas, excluídas ou ordenadas a partir da janela de edição da propriedade de atividade, mas também podem ser modificadas a partir da transição.

Se o resultado de um cálculo for reutilizado por condições diferentes, é possível calculá-lo no script de inicialização da atividade. O resultado deve ser armazenado em uma variável da tarefa a ser acessada pelos scripts de condição (task.vars.xxx).
