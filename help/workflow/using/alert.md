---
product: campaign
title: Alerta
description: Alerta
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 21698e85-7b58-4bde-bbd2-0ee06ac90307
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 100%

---

# Alerta{#alert}

![](../../assets/common.svg)

Uma atividade **Alert** envia uma mensagem a um grupo de operadores. Ela opera da mesma forma que uma atividade de aprovação, mas nenhuma resposta é esperada nesse caso.

![](assets/edit_alerte.png)

Um alerta não é persistente e, portanto, não é visível do console. Os operadores do grupo atribuído devem ter um endereço de e-mail completo para receber a notificação. A configuração dessa atividade é semelhante àquela de um **Approval**. O template de delivery padrão usado para alertar os operadores é o &quot;alertAssignee&quot;.
