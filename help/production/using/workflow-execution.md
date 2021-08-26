---
product: campaign
title: Execução do fluxo de trabalho
description: Execução do fluxo de trabalho
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 13%

---

# Execução do fluxo de trabalho{#workflow-execution}

![](../../assets/v7-only.svg)

A seção abaixo apresenta informações sobre problemas comuns relacionados à execução de workflows e como solucioná-los.

Para obter mais informações sobre fluxos de trabalho, consulte estas seções:

* [Sobre workflows](../../workflow/using/about-workflows.md)
* [Iniciar um workflow](../../workflow/using/starting-a-workflow.md)
* [Ciclo de vida do fluxo de trabalho](../../workflow/using/workflow-life-cycle.md)
* [Práticas recomendadas para usar workflows](../../workflow/using/workflow-best-practices.md)

## Comece o mais rápido possível em campanhas {#start-as-soon-as-possible-in-campaigns}

Em alguns casos, os workflows executados de uma campanha não são iniciados ao clicar no botão **[!UICONTROL Start]**. Em vez de começar, ele vai para um estado &quot;Iniciar o mais rápido possível&quot;.

Pode haver várias causas para esse problema, siga as etapas abaixo para resolvê-lo:

1. Verifique o status do workflow técnico [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md). Esse workflow gerencia trabalhos ou fluxos de trabalho dentro de uma campanha. Se falhar, os fluxos de trabalho não serão iniciados/interrompidos. Reinicie-o para retomar a execução dos workflows da campanha.

   Para obter mais informações sobre o monitoramento de workflows técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Depois que o workflow for reiniciado, certifique-se de executar as tarefas pendentes (clique com o botão direito do mouse na atividade **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**) para verificar se ela falha novamente em qualquer uma das atividades.

   Se o workflow ainda falhar, verifique o log de auditoria quanto a um erro específico, solucione os problemas adequadamente e reinicie o workflow novamente.

1. Verifique o estado do módulo **[!UICONTROL wfserver]** na guia **[!UICONTROL Monitoring]**, acessível na página inicial do Campaign Classic (consulte [Monitoring processes](../../production/using/monitoring-processes.md)). Esse processo é responsável por executar todos os workflows.

   Um usuário administrador também pode verificar se o módulo **wfserver@`<instance>`** é iniciado no servidor de aplicativos principal usando o comando abaixo.

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

1. Verifique se o **number of campaign processes running** na instância é maior do que o limite. Há um limite definido pela opção [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) em quantos processos de campanha podem ser executados simultaneamente na instância. Quando esse limite é atingido, o workflow permanece no estado &quot;Start as soon as possible&quot;, desde que o número de workflows em execução esteja acima do limite.

   Para resolver esse problema, pare workflows indesejados e exclua deliveries com falha. Se o limite foi atingido, isso permitirá a execução de novos processos.

   Para verificar o número de workflows em execução da sua instância, recomendamos usar as exibições predefinidas, acessíveis por padrão na pasta **[!UICONTROL Administration]** / **[!UICONTROL Audit]**. Para obter mais informações, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Aumentar o limite da opção **[!UICONTROL NmsOperation_LimitConcurrency]** pode levar a problemas de desempenho em sua instância. Em qualquer caso, não faça isso sozinho e entre em contato com o Adobe Campaign.

Para obter mais informações sobre como monitorar o workflow, consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md).

## Início em progresso {#start-in-progress}

Se os workflows não estiverem em execução e seu status for **Start in progress**, isso pode significar que o módulo de workflow não é iniciado.

Para verificar isso e iniciar o módulo se necessário, siga as seguintes etapas:

1. Verifique o estado do módulo **[!UICONTROL wfserver]** na guia **[!UICONTROL Monitoring]**, acessível na página inicial do Campaign Classic (consulte [Monitoring processes](../../production/using/monitoring-processes.md)).

   Um usuário administrador também pode verificar se o módulo **wfserver@`<instance>`** é iniciado no servidor de aplicativos principal usando o comando abaixo.

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

1. Verifique o diário do workflow. Para obter mais informações, consulte as seções [Monitoring workflow execution](../../workflow/using/monitoring-workflow-execution.md) e [Display logs](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) .
1. Monitorar workflows técnicos. Para obter mais informações, consulte [esta seção](../../workflow/using/monitoring-technical-workflows.md).
1. Procure falhas em atividades de workflow individuais.
