---
title: Aguardar
seo-title: Aguardar
description: Aguardar
seo-description: null
page-status-flag: never-activated
uuid: 55e4f15d-8d69-45b1-b842-5ccdfdedf550
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 41bcfe67-b5d6-4ee6-9f8a-6a7a208e2036
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Aguardar{#wait}

Uma atividade **Wait** ativa sua transição após um atraso de tempo de qualquer valor entre alguns segundos até vários meses. Uma tarefa de espera não bloqueia a execução de outras tarefas; o workflow pode executar tarefas em paralelo enquanto esta tarefa está pendente.

É possível inserir o rótulo e o tempo de espera usando o editor, como no exemplo abaixo:

![](assets/edit_wait.png)

No **[!UICONTROL Duration]** campo, o valor pode ser expresso na unidade de sua escolha: (de acordo com as configurações regionais do operador):

* Se as configurações regionais não forem especificadas: **s** por segundos, **m** por minutos, **h** por horas, **d** por dias, **y** por anos. No momento da aprovação, o valor é convertido automaticamente para a unidade mais legível.

   A unidade padrão é dia (**d**).

* Enquanto que, por exemplo, se as configurações regionais forem definidas como &quot;Français&quot;: **s** por segundos, **mn** por minutos, **h** por horas, **j** por dias, **m** **** por meses, a por anos. No momento da aprovação, o valor é convertido automaticamente na unidade mais legível, como no exemplo acima, **90s** foi convertido para **1mn 30s**.

   A unidade padrão é dia (**d**).

