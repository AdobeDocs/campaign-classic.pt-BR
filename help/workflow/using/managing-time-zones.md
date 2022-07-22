---
product: campaign
title: Gerenciar fusos horários
description: Gerenciar fusos horários
feature: Workflows
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Gerenciamento de fusos horários{#managing-time-zones}

![](../../assets/v7-only.svg)

O Adobe Campaign permite a gestão do intervalo entre vários países relacionados à mesma instância. A configuração aplicada é aplicada durante a criação da instância.

Para mais informações sobre a configuração de fusos horários no Adobe Campaign, consulte o [Guia de instalação do Campaign Classic v7](../../installation/using/time-zone-management.md).

Em um workflow, é possível adaptar os agendamentos de execução de atividades e vincular um fuso horário específico a uma atividade ou ao workflow inteiro. Essa configuração é útil ao importar o arquivo ou dentro da estrutura de agendamento de delivery.

## Agendamento de execução {#execution-scheduling}

É possível agendar a execução das tarefas usando o scheduler (consulte [Scheduler](scheduler.md)). Também é possível usar as opções de agendamento disponíveis nas atividades que oferecem essa funcionalidade. Essas atividades oferecem uma guia **[!UICONTROL Schedule]**: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**, etc.

Para todas as tarefas agendadas, ou seja, todas as atividades com opções de agendamento, é possível selecionar o fuso horário a ser aplicado. O fuso horário é selecionado por meio da guia **[!UICONTROL Advanced]** da atividade relacionada:

![](assets/wf-timezone-in-a-box.png)

Os valores possíveis são:

* Fuso horário do servidor

   Usa o fuso horário do servidor de aplicativos Adobe Campaign.

* Fuso horário do usuário

   Usa o fuso horário do operador do Adobe Campaign que executa o workflow.

* Fuso horário do banco de dados

   Usa o fuso horário do servidor de banco de dados usado.

* Fusos horários específicos

   Usa o fuso horário selecionado.

Se o valor **[!UICONTROL By default]** for selecionado, o fuso horário do workflow será aplicado, caso contrário, será usado o do servidor de aplicativos.

## Vincular um fuso horário a uma atividade {#linking-a-time-zone-to-an-activity}

A guia **[!UICONTROL Advanced]** das atividades do workflow permite selecionar o fuso horário. Embora a maior parte do tempo, o fuso horário dos workflows seja suficiente, pode ser necessário sobrescrever ele agora e novamente em uma atividade específica, como importação de dados, para vincular datas aos seus fusos horários corretos.
