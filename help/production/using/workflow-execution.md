---
title: Execução do workflow
seo-title: Execução do workflow
description: Execução do workflow
seo-description: null
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 13%

---


# Execução do workflow{#workflow-execution}

A seção abaixo apresenta informações sobre problemas comuns relacionados à execução de workflows e como solucioná-los.

Para obter mais informações sobre workflows, consulte estas seções:

* [Sobre workflows](../../workflow/using/about-workflows.md)
* [Iniciando um workflow](../../workflow/using/starting-a-workflow.md)
* [Ciclo de vida do workflow](../../workflow/using/workflow-life-cycle.md)
* [Práticas recomendadas ao usar workflows](../../workflow/using/workflow-best-practices.md)

## Start o mais rápido possível no campanha {#start-as-soon-as-possible-in-campaigns}

Em alguns casos, workflows executados a partir de uma campanha não são start ao clicar no **[!UICONTROL Start]** botão. Em vez de começar, ele vai para um estado &quot;Start o mais rápido possível&quot;.

Pode haver várias causas para esse problema, siga as etapas abaixo para resolvê-lo:

1. Verifique o status do fluxo de trabalho [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) técnico. Esse fluxo de trabalho gerencia trabalhos ou workflows dentro de uma campanha. Se falhar, isso resultará em workflows para não start / parar. Reinicie-o para retomar a execução de workflows da campanha.

   Para obter mais informações sobre o monitoramento de workflows técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[OBSERVAÇÃO]
   >
   >Depois que o fluxo de trabalho for reiniciado, certifique-se de executar as tarefas pendentes (clique com o botão direito do mouse na **[!UICONTROL Scheduler]** atividade / **[!UICONTROL Execute pending task(s) now]**) para verificar se há falha novamente em qualquer uma das atividades.

   Se o fluxo de trabalho ainda falhar, verifique se há um erro específico no registro de auditoria, solucione os problemas de acordo e reinicie o fluxo de trabalho novamente.

1. Verifique o estado do **[!UICONTROL wfserver]** módulo na **[!UICONTROL Monitoring]** guia, acessível na página inicial do Campaign Classic (consulte [Monitoramento de processos](../../production/using/monitoring-processes.md)). Esse processo é responsável pela execução de todos os workflows.

   Um usuário administrador também pode verificar se o módulo **wfserver@`<instance>`**foi iniciado no servidor de aplicativos principal usando o comando abaixo.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente da Adobe. Se você tiver uma instalação local, um usuário administrador deverá reiniciar o serviço usando o comando abaixo.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Substitua **`<instancename>`** pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   For more on how to restart modules, refer to [this section](../../production/using/usual-commands.md#module-launch-commands).

1. Verifique se o **número de processos de campanha em execução** na instância é maior que o limite. Há um limite definido pela [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) opção sobre quantos processos de campanha podem ser executados na instância em paralelo. Quando esse limite é atingido, o fluxo de trabalho permanece no estado &quot;Start assim que possível&quot;, desde que o número de workflows em execução esteja acima do limite.

   Para resolver esse problema, pare workflows indesejados e exclua delivery com falha. Se o limite for atingido, isso permitirá a execução de novos processos.

   Para verificar o número de workflows em execução de sua instância, recomendamos usar as visualizações predefinidas, acessíveis por padrão na **[!UICONTROL Administration]** / **[!UICONTROL Audit]** pasta. Para obter mais informações, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[CUIDADO]
   >
   >Aumentar o limite de **[!UICONTROL NmsOperation_LimitConcurrency]** opções pode causar problemas de desempenho em sua instância. Em qualquer caso, não execute isso sozinho e entre em contato com seu Adobe Campaign.

Para obter mais informações sobre como monitorar o workflow, consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md).

## Start em andamento {#start-in-progress}

Se os workflows não estiverem em execução e seu status estiver em **Start em andamento**, isso pode significar que o módulo de fluxo de trabalho não será iniciado.

Para verificar isso e iniciar o módulo se necessário, siga as seguintes etapas:

1. Verifique o estado do **[!UICONTROL wfserver]** módulo na **[!UICONTROL Monitoring]** guia, acessível na página inicial do Campaign Classic (consulte [Monitoramento de processos](../../production/using/monitoring-processes.md)).

   Um usuário administrador também pode verificar se o módulo **wfserver@`<instance>`**foi iniciado no servidor de aplicativos principal usando o comando abaixo.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   For more on how to monitor modules, refer to [this section](../../production/using/usual-commands.md#monitoring-commands-).

1. Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente da Adobe. Se você tiver uma instalação local, um administrador deverá reiniciá-la usando o comando abaixo.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Substitua **`<instancename>`** pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   For more on how to restart modules, refer to [this section](../../production/using/usual-commands.md#module-launch-commands).

## Fluxo de trabalho com falha {#failed-workflow}

Se um fluxo de trabalho falhar, execute as seguintes etapas:

1. Verifique o journal do fluxo de trabalho. Para obter mais informações, consulte as seções Execução [do fluxo de trabalho de](../../workflow/using/monitoring-workflow-execution.md) Monitoramento e Logs [de](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) exibição.
1. Monitore workflows técnicos. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. Procure falhas nas atividades de fluxo de trabalho individuais.
