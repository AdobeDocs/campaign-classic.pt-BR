---
title: Iniciar um fluxo de trabalho
description: Saiba como iniciar e descobrir as ações de fluxos de trabalho na barra de ferramentas e clique com o botão direito do mouse no menu.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68a95962dfecc4b10f48ba16d4f8ab29cae02ee8
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 95%

---


# Iniciando um workflow {#starting-a-workflow}

Um workflow é sempre iniciado manualmente. Ao ser iniciado, ele pode permanecer inativo dependendo das informações especificadas por meio de um scheduler (consulte [Scheduler](../../workflow/using/scheduler.md)) ou de um agendamento de atividade. 

As ações relacionadas à execução do workflow para construção do target (iniciar, parar, pausar etc.) são processos **assíncronos**: a ordem é registrada e entrará em vigor assim que o servidor estiver disponível para aplicá-lo.

A barra de ferramentas permite iniciar e controlar a execução do workflow.

A lista de opções disponíveis no menu **[!UICONTROL Actions]** e no menu de contexto estão detalhadas abaixo.

>[!IMPORTANT]
>
>Keep in mind that, when an operator performs an action on a workflow (start, stop, pause, etc.), the action is not executed straightaway, but instead placed in a queue in order to be processed by the [workflow module](../../workflow/using/architecture.md).

## Barra de ferramentas Ações {#actions-toolbar}

Os botões da barra de ferramentas são detalhados nesta [seção](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). O botão **[!UICONTROL Actions]** dá acesso às opções de execução adicionais para atuar em fluxos de trabalho selecionados. Você também pode usar o menu **[!UICONTROL File > Actions]** ou clicar com o botão direito do mouse em um fluxo de trabalho e selecionar **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   Essa ação permite iniciar a execução de um workflow: um workflow **Concluído**, **Em edição** ou **Pausado** altera o status para **Iniciado**. Em seguida, o motor de workflow manipula a execução desse workflow. Se o workflow tiver sido pausado, ele será retomado, caso contrário, o workflow será iniciado desde o início e as atividades iniciais serão ativadas.

   Iniciar é um processo assíncrono: a solicitação é salva e processada o mais rápido possível por um servidor de workflow.

* **[!UICONTROL Pause]**

   Esta ação define o status do workflow como **Pausado**. Nenhuma atividade é ativada até que o workflow seja retomado. No entanto, as operações em andamento não são interrompidas.

* **[!UICONTROL Stop]**

   Esta ação interrompe um workflow sendo executado no momento. O status da instância é definido como **Concluído**. Se possível, as operações em andamento são interrompidas. Importações e queries SQL são canceladas imediatamente.

   A interrupção é um processo assíncrono. A solicitação é registrada, então o servidor de workflow ou servidores cancelam as operações em andamento. A interrupção de uma instância de workflow pode demorar, especialmente se o workflow estiver em execução em vários servidores, cada um deles deve assumir o controle para cancelar as tarefas em andamento.

* **[!UICONTROL Restart]**

   Essa ação interrompe e depois retoma o workflow. Na maioria dos casos, é possível reiniciar mais rápido. Também é útil automatizar a reinicialização quando a interrupção leva um determinado tempo: isso ocorre porque o comando &#39;Parar&#39; não está disponível quando o workflow está sendo interrompido.

   As ações **[!UICONTROL Start / Pause / Stop / Restart]** também estão disponíveis por meio dos ícones de execução na barra de ferramentas. Para obter mais informações, consulte esta [seção](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   Essa ação permite limpar o histórico do workflow. Para obter mais informações, consulte [Limpeza de logs](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   Essa opção permite iniciar o fluxo de trabalho no modo de simulação em vez do modo real. Isso significa que ao habilitar esse modo, somente as atividades que não afetam o banco de dados ou o sistema de arquivos serão executadas (por exemplo, **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, etc.). Atividades que têm impacto (por exemplo, **[!UICONTROL Export]**, **[!UICONTROL Import]**, etc.) assim como as posteriores (na mesma ramificação) não são executadas.

* **[!UICONTROL Execute pending tasks now]**

   Essa ação permite iniciar todas as tarefas pendentes assim que possível. Para iniciar uma tarefa específica, clique com o botão direito do mouse na atividade e selecione **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   Essa opção altera o status do fluxo de trabalho para **[!UICONTROL Finished]**. Essa ação só deve ser usada como último recurso se o processo de interrupção normal falhar após alguns minutos. Use apenas a interrupção incondicional se tiver certeza de que não há tarefas de workflow em andamento.

   >[!CAUTION]
   >
   >Essa opção destina-se somente aos usuários avançados.

* **[!UICONTROL Save as template]**

   Essa ação cria um novo modelo de fluxo de trabalho com base no fluxo de trabalho selecionado. Você precisa especificar a pasta onde ele será salvo (no campo **[!UICONTROL Folder]**).

   As opções **[!UICONTROL Mass update of selected lines]** e **[!UICONTROL Merge selected lines]** são opções genéricas de plataforma disponíveis em todos os menus **[!UICONTROL Actions]**. Para obter mais informações, consulte esta [seção](../../platform/using/updating-data.md).

## Menu de contexto {#right-click-menu}

Quando uma ou mais atividades de workflow forem selecionadas, você pode clicar com o botão direito do mouse para agir em sua seleção.

![](assets/contextual_menu.png)

As seguintes opções estão disponíveis no menu de contexto:

**[!UICONTROL Open]**: esta opção permite acessar as propriedades da atividade.

**[!UICONTROL Display logs:]** essa opção permite exibir o log de execução da tarefa para a atividade selecionada. Consulte [Exibir logs](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** essa ação permite iniciar tarefas pendentes assim que possível.

**[!UICONTROL Workflow restart from a task:]** essa opção permite reiniciar o fluxo de trabalho usando os resultados armazenados anteriormente para essa atividade.

**[!UICONTROL Cut/Copy/Paste/Delete:]** essas opções permitem recortar, copiar, colar e excluir atividades.

**[!UICONTROL Copy as bitmap:]** essa opção permite capturar a tela de todas as atividades.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** essas opções também estão disponíveis na guia **[!UICONTROL Advanced]** das propriedades da atividade. Maiores detalhes em [Execution](../../workflow/using/advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** permite salvar ou cancelar as alterações feitas em um fluxo de trabalho.

>[!NOTE]
>
>Você pode selecionar um grupo de atividades e aplicar um desses comandos a eles.

O menu de contexto também é detalhado nesta [seção](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
