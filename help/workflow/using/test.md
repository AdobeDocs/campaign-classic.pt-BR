---
title: Teste
seo-title: Teste
description: Teste
seo-description: null
page-status-flag: never-activated
uuid: 3522f4ac-3a72-4ff1-b3aa-1b4c283ef2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 78c70ef4-807d-45d4-ac87-2b741c0ef5cb
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: b78db689958c9b240da9a0315060fe63bcb48e0a

---


# Teste{#test}

Uma atividade de tipo **Test** ativa a primeira transição que satisfaz a condição associada a ela. Se nenhuma condição for satisfeita e se a opção **[!UICONTROL Use the default fork]** for ativada, a transição padrão será ativada.

Uma condição é uma expressão JavaScript que deve ser avaliada como &quot;verdadeira&quot; ou &quot;falsa&quot;. Para inserir a expressão, clique no ícone à direita do nome da condição e selecione **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Para obter mais informações sobre todas as funções adicionais do JavaScript e métodos SOAP do servidor do aplicativo acessível via JavaScript de workflow, consulte a [documentação JSAPI](https://docs.adobe.com/content/help/br/campaign-classic/technicalresources/api/index.html).

Também é possível inserir variáveis diretamente no editor.

As condições podem ser adicionadas, excluídas ou ordenadas a partir da janela de edição da propriedade de atividade, mas também podem ser modificadas a partir da transição.

Se o resultado de um cálculo for reutilizado por condições diferentes, é possível calculá-lo no script de inicialização da atividade. O resultado deve ser armazenado em uma variável da tarefa a ser acessada pelos scripts de condição (task.vars.xxx).
