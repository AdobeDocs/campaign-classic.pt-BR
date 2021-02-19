---
solution: Campaign Classic
product: campaign
title: Aguardar
description: Saiba mais sobre a atividade de workflow Aguardar
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%

---


# Aguardar{#wait}

Uma atividade **Wait** ativa sua transição após um atraso de tempo de qualquer valor entre alguns segundos até vários meses. Uma tarefa de espera não bloqueia a execução de outras tarefas; o workflow pode executar tarefas em paralelo enquanto esta tarefa está pendente.

É possível inserir o rótulo e o tempo de espera usando o editor, como no exemplo abaixo:

![](assets/edit_wait.png)

No campo **[!UICONTROL Duration]**, o valor pode ser expresso na unidade de sua escolha: (de acordo com as configurações regionais do operador):

* Se as configurações regionais não forem especificadas: **s** para segundos, **m** para minutos, **h** para horas, **d** para dias e **y** para anos. No momento da aprovação, o valor é convertido automaticamente para a unidade mais legível.

   A unidade padrão é dia (**d**).

* Enquanto que, por exemplo, se as configurações regionais forem definidas como &quot;Français&quot;: **s** para segundos, **mn** para minutos, **h** para horas, **j** para dias, **m** para meses e **a** para anos. No momento da aprovação, o valor é convertido automaticamente na unidade mais legível, como no exemplo acima, **90s** foi convertido para **1mn 30s**.

   A unidade padrão é dia (**d**).

