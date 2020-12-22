---
solution: Campaign Classic
product: campaign
title: Execução do workflow
description: Execução do workflow
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 13%

---


# Execução do workflow{#workflow-execution}

A seção abaixo apresenta informações sobre problemas comuns relacionados à execução de workflows e como solucioná-los.

Para obter mais informações sobre workflows, consulte estas seções:

* [Sobre workflows](../../workflow/using/about-workflows.md)
* [Iniciar um workflow](../../workflow/using/starting-a-workflow.md)
* [Ciclo de vida do workflow](../../workflow/using/workflow-life-cycle.md)
* [Práticas recomendadas ao usar workflows](../../workflow/using/workflow-best-practices.md)

## Start assim que possível no campanha {#start-as-soon-as-possible-in-campaigns}

Em alguns casos, workflows executados a partir de uma campanha não são start ao clicar no botão **[!UICONTROL Start]**. Em vez de começar, ele vai para um estado &quot;Start o mais rápido possível&quot;.

Pode haver várias causas para esse problema, siga as etapas abaixo para resolvê-lo:

1. Verifique o status do fluxo de trabalho técnico [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md). Esse fluxo de trabalho gerencia trabalhos ou workflows dentro de uma campanha. Se falhar, isso resultará em workflows para não start / parar. Reinicie-o para retomar a execução de workflows da campanha.

   Para obter mais informações sobre o monitoramento de workflows técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Depois que o fluxo de trabalho for reiniciado, certifique-se de executar as tarefas pendentes (clique com o botão direito do mouse na atividade **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**) para verificar se há falha novamente em qualquer uma das atividades.

   Se o fluxo de trabalho ainda falhar, verifique se há um erro específico no registro de auditoria, solucione os problemas de acordo e reinicie o fluxo de trabalho novamente.

1. Verifique o estado do módulo **[!UICONTROL wfserver]** na guia **[!UICONTROL Monitoring]**, acessível a partir da página inicial do Campaign Classic (consulte [Processos de monitoramento](../../production/using/monitoring-processes.md)). Esse processo é responsável pela execução de todos os workflows.

   Um usuário administrador também pode verificar se o módulo **wfserver@`<instance>`** é iniciado no servidor de aplicativos principal usando o comando abaixo.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente do Adobe. Se você tiver uma instalação local, um usuário administrador deverá reiniciar o serviço usando o comando abaixo.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Substitua **`<instancename>`** pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Para obter mais informações sobre como reiniciar módulos, consulte [esta seção](../../production/using/usual-commands.md#module-launch-commands).

1. Verifique se o **número de processos de campanha em execução** na instância é maior que o limite. Há um limite definido pela opção [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) sobre quantos processos de campanha podem ser executados na instância em paralelo. Quando esse limite é atingido, o fluxo de trabalho permanece no estado &quot;Start assim que possível&quot;, desde que o número de workflows em execução esteja acima do limite.

   Para resolver esse problema, pare workflows indesejados e exclua delivery com falha. Se o limite for atingido, isso permitirá a execução de novos processos.

   Para verificar o número de workflows em execução de sua instância, recomendamos usar as visualizações predefinidas, acessíveis por padrão na pasta **[!UICONTROL Administration]** / **[!UICONTROL Audit]**. Para saber mais, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >O aumento do limite de opção **[!UICONTROL NmsOperation_LimitConcurrency]** pode levar a problemas de desempenho em sua instância. Em qualquer caso, não execute isso sozinho e entre em contato com seu Adobe Campaign.

Para obter mais informações sobre como monitorar o workflow, consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md).

## Start em andamento {#start-in-progress}

Se os workflows não estiverem sendo executados e seu status for **Start em andamento**, isso pode significar que o módulo de fluxo de trabalho não será iniciado.

Para verificar isso e iniciar o módulo se necessário, siga as seguintes etapas:

1. Verifique o estado do módulo **[!UICONTROL wfserver]** na guia **[!UICONTROL Monitoring]**, acessível a partir da página inicial do Campaign Classic (consulte [Processos de monitoramento](../../production/using/monitoring-processes.md)).

   Um usuário administrador também pode verificar se o módulo **wfserver@`<instance>`** é iniciado no servidor de aplicativos principal usando o comando abaixo.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Para obter mais informações sobre como monitorar módulos, consulte [esta seção](../../production/using/usual-commands.md#monitoring-commands-).

1. Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente do Adobe. Se você tiver uma instalação local, um administrador deverá reiniciá-la usando o comando abaixo.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Substitua **`<instancename>`** pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Para obter mais informações sobre como reiniciar módulos, consulte [esta seção](../../production/using/usual-commands.md#module-launch-commands).

## Falha no fluxo de trabalho {#failed-workflow}

Se um fluxo de trabalho falhar, execute as seguintes etapas:

1. Verifique o journal do fluxo de trabalho. Para obter mais informações, consulte as seções [Monitoramento da execução do fluxo de trabalho](../../workflow/using/monitoring-workflow-execution.md) e [Exibir logs](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).
1. Monitore workflows técnicos. Para obter mais informações, consulte [esta seção](../../workflow/using/monitoring-technical-workflows.md).
1. Procure falhas nas atividades de fluxo de trabalho individuais.
