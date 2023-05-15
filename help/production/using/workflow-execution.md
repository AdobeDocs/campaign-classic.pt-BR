---
product: campaign
title: Execução do workflow
description: Execução do workflow
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 13%

---

# Execução do workflow{#workflow-execution}



A seção abaixo apresenta informações sobre problemas comuns relacionados à execução de workflows e como solucioná-los.

Para obter mais informações sobre fluxos de trabalho, consulte estas seções:

* [Sobre workflows](../../workflow/using/about-workflows.md)
* [Iniciar um fluxo de trabalho](../../workflow/using/starting-a-workflow.md)
* [Ciclo de vida do workflow](../../workflow/using/workflow-life-cycle.md)
* [Práticas recomendadas para usar workflows](../../workflow/using/workflow-best-practices.md)

## Comece o mais rápido possível em campanhas {#start-as-soon-as-possible-in-campaigns}

Em alguns casos, os workflows executados a partir de uma campanha não são iniciados ao clicar no botão **[!UICONTROL Start]** botão. Em vez de começar, ele vai para um estado &quot;Iniciar o mais rápido possível&quot;.

Pode haver várias causas para esse problema, siga as etapas abaixo para resolvê-lo:

1. Verifique a [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) status técnico do workflow. Esse workflow gerencia trabalhos ou fluxos de trabalho dentro de uma campanha. Se falhar, os fluxos de trabalho não serão iniciados/interrompidos. Reinicie-o para retomar a execução dos workflows da campanha.

   Para obter mais informações sobre o monitoramento de workflows técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Depois que o workflow for reiniciado, certifique-se de executar as tarefas pendentes (clique com o botão direito do mouse no **[!UICONTROL Scheduler]** atividade / **[!UICONTROL Execute pending task(s) now]**) para verificar se ele falha novamente em qualquer uma das atividades.

   Se o workflow ainda falhar, verifique o log de auditoria quanto a um erro específico, solucione os problemas adequadamente e reinicie o workflow novamente.

1. Verifique a **[!UICONTROL wfserver]** estado do módulo no **[!UICONTROL Monitoring]** guia , acessível na página inicial do Campaign Classic (consulte [Processos de monitoramento](../../production/using/monitoring-processes.md)). Esse processo é responsável por executar todos os workflows.

   Um usuário administrador também pode verificar se a variável **wfserver@`<instance>`** O módulo é iniciado no servidor de aplicativos principal usando o comando abaixo.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente do Adobe. Se você tiver uma instalação no local, um usuário administrador deverá reiniciar o serviço usando o comando abaixo.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Substitua **`<instancename>`** pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Para obter mais informações sobre como reiniciar módulos, consulte [esta seção](../../production/using/usual-commands.md#module-launch-commands).

1. Verifique se a variável **número de processos de campanha em execução** na instância é maior que o limite. Existe um limite definido pela variável [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) em quantos processos de campanha podem ser executados simultaneamente na instância. Quando esse limite é atingido, o workflow permanece no estado &quot;Start as soon as possible&quot;, desde que o número de workflows em execução esteja acima do limite.

   Para resolver esse problema, pare workflows indesejados e exclua deliveries com falha. Se o limite foi atingido, isso permitirá a execução de novos processos.

   Para verificar o número de workflows em execução da sua instância, recomendamos usar as exibições predefinidas, acessíveis por padrão no **[!UICONTROL Administration]** / **[!UICONTROL Audit]** pasta. Para obter mais informações, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Aumentar o **[!UICONTROL NmsOperation_LimitConcurrency]** limite de opções pode levar a problemas de desempenho em sua instância. Em qualquer caso, não faça isso sozinho e entre em contato com o Adobe Campaign.

Para obter mais informações sobre como monitorar o workflow, consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md).

## Início em progresso {#start-in-progress}

Se os workflows não estiverem em execução e seu status for **Início em progresso**, isso pode significar que o módulo de workflow não é iniciado.

Para verificar isso e iniciar o módulo se necessário, siga as seguintes etapas:

1. Verifique a **[!UICONTROL wfserver]** estado do módulo no **[!UICONTROL Monitoring]** guia , acessível na página inicial do Campaign Classic (consulte [Processos de monitoramento](../../production/using/monitoring-processes.md)).

   Um usuário administrador também pode verificar se a variável **wfserver@`<instance>`** O módulo é iniciado no servidor de aplicativos principal usando o comando abaixo.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Para obter mais informações sobre como monitorar módulos, consulte [esta seção](../../production/using/usual-commands.md#monitoring-commands-).

1. Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente do Adobe. Se você tiver uma instalação no local, um administrador deverá reiniciá-la usando o comando abaixo.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Substitua **`<instancename>`** pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Para obter mais informações sobre como reiniciar módulos, consulte [esta seção](../../production/using/usual-commands.md#module-launch-commands).

## Fluxo de trabalho com falha {#failed-workflow}

Se um fluxo de trabalho falhar, siga as etapas abaixo:

1. Verifique o diário do workflow. Para obter mais informações, consulte [Monitoramento da execução do workflow](../../workflow/using/monitoring-workflow-execution.md) e [Logs de exibição](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) seções.
1. Monitorar fluxos de trabalho técnicos. Para obter mais informações, consulte [esta seção](../../workflow/using/monitoring-technical-workflows.md).
1. Procure falhas em atividades de workflow individuais.
