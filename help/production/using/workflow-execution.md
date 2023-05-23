---
product: campaign
title: Execução do workflow
description: Execução do workflow
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
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

## Iniciar assim que possível em campanhas {#start-as-soon-as-possible-in-campaigns}

Em alguns casos, os workflows executados em uma campanha não são iniciados ao clicar no **[!UICONTROL Start]** botão. Em vez de iniciar, ele vai para o estado &quot;Iniciar assim que possível&quot;.

Pode haver várias causas para esse problema. Siga as etapas abaixo para resolvê-lo:

1. Verifique a [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) status do workflow técnico. Esse workflow gerencia jobs ou workflows dentro de uma campanha. Se falhar, os workflows não serão iniciados/interrompidos. Reinicie-o para retomar a execução dos workflows da campanha.

   Para obter mais informações sobre monitoramento de workflows técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Depois que o workflow for reiniciado, certifique-se de executar as tarefas pendentes (clique com o botão direito do mouse no link **[!UICONTROL Scheduler]** atividade / **[!UICONTROL Execute pending task(s) now]**) para verificar se falha novamente em qualquer uma das atividades.

   Se o fluxo de trabalho ainda falhar, verifique o log de auditoria em busca de um erro específico, solucione os problemas de acordo e reinicie o fluxo de trabalho novamente.

1. Verifique a **[!UICONTROL wfserver]** estado do módulo no **[!UICONTROL Monitoring]** , acessível na página inicial do Campaign Classic (consulte [Monitoramento de processos](../../production/using/monitoring-processes.md)). Esse processo é responsável pela execução de todos os workflows.

   Um usuário administrador também pode verificar se a variável **wfserver@`<instance>`** O módulo é iniciado no servidor de aplicativos principal usando o comando abaixo.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente da Adobe. Se você tiver uma instalação no local, um usuário administrador deverá reiniciar o serviço usando o comando abaixo.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Substitua **`<instance-name>`** pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Para obter mais informações sobre como reiniciar módulos, consulte [nesta seção](../../production/using/usual-commands.md#module-launch-commands).

1. Verifique se **número de processos de campanha em execução** na instância é maior do que o limite. Há um limite definido pelo [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) opção em quantos processos de campanha podem ser executados em paralelo na instância. Quando esse limite é atingido, o workflow permanece no estado &quot;Start as soon as possible&quot; desde que o número de workflows em execução esteja acima do limite.

   Para resolver esse problema, interrompa os fluxos de trabalho indesejados e exclua os deliveries com falha. Se o limite for atingido, permitirá a execução de novos processos.

   Para verificar o número de workflows em execução na sua instância, recomendamos usar as exibições predefinidas, acessíveis por padrão no **[!UICONTROL Administration]** / **[!UICONTROL Audit]** pasta. Para obter mais informações, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Aumentar o **[!UICONTROL NmsOperation_LimitConcurrency]** O limite de opção do pode causar problemas de desempenho na sua instância. Em qualquer caso, não faça isso por conta própria e entre em contato com o contato da Adobe Campaign.

Para obter mais informações sobre como monitorar o workflow, consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md).

## Início em andamento {#start-in-progress}

Se os workflows não estiverem em execução e seu status for **Início em andamento**, isso pode significar que o módulo de workflow não é iniciado.

Para verificar isso e iniciar o módulo se necessário, siga as seguintes etapas:

1. Verifique a **[!UICONTROL wfserver]** estado do módulo no **[!UICONTROL Monitoring]** , acessível na página inicial do Campaign Classic (consulte [Monitoramento de processos](../../production/using/monitoring-processes.md)).

   Um usuário administrador também pode verificar se a variável **wfserver@`<instance>`** O módulo é iniciado no servidor de aplicativos principal usando o comando abaixo.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Para obter mais informações sobre como monitorar módulos, consulte [nesta seção](../../production/using/usual-commands.md#monitoring-commands-).

1. Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente da Adobe. Se você tiver uma instalação no local, um administrador deverá reiniciá-la usando o comando abaixo.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Substitua **`<instance-name>`** pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Para obter mais informações sobre como reiniciar módulos, consulte [nesta seção](../../production/using/usual-commands.md#module-launch-commands).

## Falha no fluxo de trabalho {#failed-workflow}

Se um fluxo de trabalho falhar, siga estas etapas:

1. Verifique o journal do workflow. Para obter mais informações, consulte [Monitoramento da execução do fluxo de trabalho](../../workflow/using/monitoring-workflow-execution.md) e [Exibir logs](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) seções.
1. Monitorar fluxos de trabalho técnicos. Para obter mais informações, consulte [nesta seção](../../workflow/using/monitoring-technical-workflows.md).
1. Procure falhas nas atividades individuais do workflow.
