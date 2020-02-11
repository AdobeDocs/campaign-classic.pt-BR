---
title: Propriedades do workflow
seo-title: Propriedades do workflow
description: Propriedades do workflow
seo-description: null
page-status-flag: never-activated
uuid: bd576cc0-2db8-4519-bcb5-52bf5c811f42
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 71969b30-cc01-4358-9597-f17939720684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Propriedades do workflow{#workflow-properties}

## Guia Execution {#execution-tab}

The **[!UICONTROL Execution]** tab of the **[!UICONTROL Properties]** window in a workflow is broken down into 3 sections:

![](assets/wf_execution_tab.png)

### Agendador {#scheduler}

Esta seção só é exibida nos workflows da campanha.

* **[!UICONTROL Priority]**

   O mecanismo de workflow processa os workflows a serem executados com base no critério de prioridade definido neste campo. For instance, all workflows with an **[!UICONTROL Average]** priority will be executed before those with a **[!UICONTROL Low]** priority.

* **[!UICONTROL Schedule execution for a time of low activity]**

   Essa opção adia o início do workflow para um período menos ocupado. Alguns workflows podem custar caro em termos de recursos para o motor do banco de dados. Recomendamos o agendamento da execução para uma hora de baixa atividade (à noite, por exemplo). Low activity periods are defined in the **[!UICONTROL Processes on campaigns]** technical workflow.

### Execução {#execution}

* **[!UICONTROL Default affinity]**

   Se a sua instalação incluir vários servidores de workflow, utilize este campo para escolher a máquina em que o workflow será executado. Se o valor definido nesse campo não existir em nenhum servidor, o workflow permanecerá pendente.

   Consulte esta [seção](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **[!UICONTROL History in days]**

   As tabelas de trabalho do banco de dados mantêm um histórico de execuções (tarefas, eventos, log). Aqui você pode definir a quantidade de dias para o arquivamento deste workflow: o processo de limpeza excluirá os arquivos mais antigos uma vez por dia. Se o valor nesse campo for zero, o arquivo nunca será excluído.

* **[!UICONTROL Log SQL queries in the journal]**

   Essa operação é reservada para usuários avançados. Refere-se a workflows que contêm atividades de definição de metas (query, união, intersecção, etc.). Quando essa opção é marcada, as queries SQL enviadas ao banco de dados durante a execução do workflow são exibidas na Adobe Campaign: isso significa que você pode analisá-las para otimizar as queries ou diagnosticar problemas.

   Queries are displayed in an **[!UICONTROL SQL logs]** tab which is added to the workflow (except campaign workflows) and to the **[!UICONTROL Properties]** activity when the option is enabled. The **[!UICONTROL Audit]** tab also includes SQL queries.

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   Essa opção só pode ser usada para depuração e nunca em produção. Quando estiver habilitado, o workflow terá prioridade e todos os outros fluxos serão interrompidos até a conclusão deste.

### Gerenciamento de erros {#error-management}

* **[!UICONTROL Troubleshooting]**

   Este campo permite a definição das ações a serem tomadas se uma tarefa de workflow tiver erros. Há duas opções possíveis:

   * **[!UICONTROL Stop the process]**: o fluxo de trabalho é pausado automaticamente. o status do fluxo de trabalho muda para **[!UICONTROL Failed]**. Once the issue is solved, restart the workflow using the **[!UICONTROL Start]** or **[!UICONTROL Restart]** buttons.
   * **[!UICONTROL Ignore]**: o status da tarefa que disparou as alterações no erro **[!UICONTROL Failed]**, mas o fluxo de trabalho mantém o **[!UICONTROL Started]** status. Essa configuração é relevante para tarefas recorrentes: se a ramificação incluir um programador, ela iniciará normalmente na próxima vez que o workflow for executado.

* **[!UICONTROL Consecutive errors]**

   Esse campo fica disponível quando o **[!UICONTROL Ignore]** valor é selecionado no **[!UICONTROL In case of errors]** campo. Você pode especificar quantos erros podem ser ignorados antes que o processo seja interrompido. Once this number is reached, the workflow status changes to **[!UICONTROL Failed]**. Se o valor desse campo for 0, o workflow nunca será interrompido independentemente do número de erros.

* **[!UICONTROL Template]**

   This field lets you select the notification template to be sent to the workflow supervisors when its status changes to **[!UICONTROL Failed]**.

   Os operadores envolvidos serão notificados por e-mail, se houver um endereço de e-mail em seu perfil. To define workflow supervisors, go to the **[!UICONTROL Supervisor(s)]** field of the properties (**[!UICONTROL General]** tab).

   ![](assets/wf-properties_select-supervisors.png)

   The **[!UICONTROL Notification to a workflow supervisor]** default template includes a link for accessing the Adobe Campaign console via the Web so that the recipient can work on the issue once they are logged on.

   Para criar um modelo personalizado, vá para **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**.

