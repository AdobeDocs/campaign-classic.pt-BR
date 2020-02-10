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
source-git-commit: 69b562979f3b32a4d30dfed0695cf3cf6c0fd26a

---


# Execução do workflow{#workflow-execution}

A seção abaixo apresenta informações sobre problemas comuns relacionados à execução de fluxos de trabalho e como solucioná-los.

Para obter mais informações sobre fluxos de trabalho, consulte estas seções:

* [Sobre workflows](../../workflow/using/about-workflows.md)
* [Execução de um fluxo de trabalho](../../workflow/using/executing-a-workflow.md)
* [Práticas recomendadas ao usar fluxos de trabalho](../../workflow/using/workflow-best-practices.md)

## Iniciar assim que possível em campanhas {#start-as-soon-as-possible-in-campaigns}

Em alguns casos, os fluxos de trabalho executados de uma campanha não são iniciados ao clicar no **[!UICONTROL Start]** botão. Em vez de começar, ele vai para um estado &quot;Iniciar o mais rápido possível&quot;.

Pode haver várias causas para esse problema, siga as etapas abaixo para resolvê-lo:

1. Verifique o status do fluxo de trabalho [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) técnico. Esse fluxo de trabalho gerencia trabalhos ou fluxos de trabalho dentro de uma campanha. Se falhar, isso resultará em fluxos de trabalho que não serão iniciados/parados. Reinicie-o para retomar a execução dos fluxos de trabalho da campanha.

   Para obter mais informações sobre o monitoramento de fluxos de trabalho técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[OBSERVAÇÃO]
   >
   >Depois que o fluxo de trabalho for reiniciado, certifique-se de executar as tarefas pendentes (clique com o botão direito do mouse na **[!UICONTROL Scheduler]** atividade / **[!UICONTROL Execute pending task(s) now]**) para verificar se há falha novamente em qualquer uma das atividades.

   Se o fluxo de trabalho ainda falhar, verifique se há um erro específico no registro de auditoria, solucione os problemas de acordo e reinicie o fluxo de trabalho novamente.

1. Verifique o estado do **[!UICONTROL wfserver]** módulo na **[!UICONTROL Monitoring]** guia, acessível na página inicial do Campaign Classic (consulte [Monitoramento de processos](../../production/using/monitoring-processes.md)). Esse processo é responsável por executar todos os fluxos de trabalho.

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
   >Replace **`<instancename>`** with the name of your instance (production, development, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Para obter mais informações sobre como reiniciar módulos, consulte [esta seção](../../production/using/usual-commands.md#module-launch-commands).

1. Verifique se o **número de processos de campanha em execução** na instância é maior que o limite. Há um limite definido pela [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) opção sobre quantos processos de campanha podem ser executados na instância em paralelo. Quando esse limite é atingido, o fluxo de trabalho permanece no estado &quot;Iniciar assim que possível&quot;, desde que o número de fluxos de trabalho em execução esteja acima do limite.

   Para resolver esse problema, pare os fluxos de trabalho indesejados e exclua entregas com falha. Se o limite for atingido, isso permitirá a execução de novos processos.

   Para verificar o número de fluxos de trabalho em execução de sua instância, recomendamos usar as exibições predefinidas, acessíveis por padrão na **[!UICONTROL Administration]** / **[!UICONTROL Audit]** pasta. Para obter mais informações, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[CUIDADO]
   >
   >Aumentar o limite de **[!UICONTROL NmsOperation_LimitConcurrency]** opções pode causar problemas de desempenho em sua instância. Em qualquer caso, não execute isso sozinho e entre em contato com seu contato do Adobe Campaign.

Para obter mais informações sobre como monitorar seus fluxos de trabalho, consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md).

## Início em andamento {#start-in-progress}

Se os fluxos de trabalho não estiverem sendo executados e seu status for **Iniciar em andamento**, isso pode significar que o módulo de fluxo de trabalho não será iniciado.

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

   Para obter mais informações sobre como monitorar módulos, consulte [esta seção](../../production/using/usual-commands.md#monitoring-commands-).

1. Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente da Adobe. Se você tiver uma instalação local, um administrador deverá reiniciá-la usando o comando abaixo.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Replace **`<instancename>`** with the name of your instance (production, development, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Para obter mais informações sobre como reiniciar módulos, consulte [esta seção](../../production/using/usual-commands.md#module-launch-commands).

## Fluxo de trabalho com falha {#failed-workflow}

Se um fluxo de trabalho falhar, execute as seguintes etapas:

1. Verifique o diário de fluxo de trabalho. Para obter mais informações, consulte as seções Execução [do fluxo de trabalho de](../../workflow/using/monitoring-workflow-execution.md) Monitoramento e Logs [de](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) exibição.
1. Monitore fluxos de trabalho técnicos. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. Procure falhas em atividades de fluxo de trabalho individuais.
