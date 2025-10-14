---
product: campaign
title: Execução do fluxo de trabalho
description: Execução do fluxo de trabalho
feature: Monitoring, Workflows
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 12%

---

# Execução do fluxo de trabalho{#workflow-execution}



A seção abaixo apresenta informações sobre problemas comuns relacionados à execução de workflows e como solucioná-los.

Para obter mais informações sobre fluxos de trabalho, consulte estas seções:

* [Sobre fluxos de trabalho](../../workflow/using/about-workflows.md)
* [Iniciando um fluxo de trabalho](https://experienceleague.adobe.com/docs/campaign/automation/workflows/executing-a-workflow/start-a-workflow.html?lang=pt-BR){target="_blank"}.
* [Ciclo de vida do fluxo de trabalho](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=pt-BR){target="_blank"}.
* [Práticas recomendadas para usar fluxos de trabalho](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html?lang=pt-BR){target="_blank"}.

## Iniciar assim que possível em campanhas {#start-as-soon-as-possible-in-campaigns}

Em alguns casos, os fluxos de trabalho executados de uma campanha não são iniciados ao clicar no botão **[!UICONTROL Start]**. Em vez de iniciar, ele vai para o estado &quot;Iniciar assim que possível&quot;.

Pode haver várias causas para esse problema. Siga as etapas abaixo para resolvê-lo:

1. Verifique o status do fluxo de trabalho técnico [**[!UICONTROL operationMgt]**](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html?lang=pt-BR){target="_blank"}. Esse workflow gerencia jobs ou workflows dentro de uma campanha. Se falhar, os workflows não serão iniciados/interrompidos. Reinicie-o para retomar a execução dos workflows da campanha.

   Para obter mais informações sobre o monitoramento de workflows técnicos, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=pt-BR){target="_blank"}.

   >[!NOTE]
   >
   >Depois que o fluxo de trabalho for reiniciado, execute as tarefas pendentes (clique com o botão direito do mouse na atividade **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**) para verificar se ela falha novamente em qualquer uma das atividades.

   Se o fluxo de trabalho ainda falhar, verifique o log de auditoria em busca de um erro específico, solucione os problemas de acordo e reinicie o fluxo de trabalho novamente.

1. Verifique o estado do módulo **[!UICONTROL wfserver]** na guia **[!UICONTROL Monitoring]**, acessível na página inicial do Campaign Classic (consulte [Processos de monitoramento](../../production/using/monitoring-processes.md)). Esse processo é responsável pela execução de todos os workflows.

   Um usuário administrador também pode verificar se o módulo **wfserver@`<instance>`** é iniciado no servidor de aplicativos principal usando o comando abaixo.

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

   Para obter mais informações sobre como reiniciar módulos, consulte [esta seção](../../production/using/usual-commands.md#module-launch-commands).

1. Verifique se o **número de processos de campanha em execução** na instância é maior que o limite. Há um limite definido pela opção [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) em quantos processos de campanha podem ser executados em paralelo na instância. Quando esse limite é atingido, o workflow permanece no estado &quot;Start as soon as possible&quot; desde que o número de workflows em execução esteja acima do limite.

   Para resolver esse problema, interrompa os fluxos de trabalho indesejados e exclua os deliveries com falha. Se o limite for atingido, permitirá a execução de novos processos.

   Para verificar o número de fluxos de trabalho em execução da sua instância, recomendamos usar os modos de exibição predefinidos, acessíveis por padrão na pasta **[!UICONTROL Administration]** / **[!UICONTROL Audit]**. Para obter mais informações, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=pt-BR){target="_blank"}.

   >[!IMPORTANT]
   >
   >O aumento do limite da opção **[!UICONTROL NmsOperation_LimitConcurrency]** pode causar problemas de desempenho na sua instância. Em qualquer caso, não faça isso por conta própria e entre em contato com o contato da Adobe Campaign.

Para obter mais informações sobre como monitorar os fluxos de trabalho, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=pt-BR){target="_blank"}.

## Início em andamento {#start-in-progress}

Se os fluxos de trabalho não estiverem em execução e seu status for **Início em andamento**, talvez o módulo de fluxo de trabalho não seja iniciado.

Para verificar isso e iniciar o módulo se necessário, siga as seguintes etapas:

1. Verifique o estado do módulo **[!UICONTROL wfserver]** na guia **[!UICONTROL Monitoring]**, acessível na página inicial do Campaign Classic (consulte [Processos de monitoramento](../../production/using/monitoring-processes.md)).

   Um usuário administrador também pode verificar se o módulo **wfserver@`<instance>`** é iniciado no servidor de aplicativos principal usando o comando abaixo.

   ```sql
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Para obter mais informações sobre como monitorar módulos, consulte [esta seção](../../production/using/usual-commands.md#monitoring-commands-).

1. Se o módulo não estiver em execução, entre em contato com o Atendimento ao cliente da Adobe. Se você tiver uma instalação no local, um administrador deverá reiniciá-la usando o comando abaixo.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Substitua **`<instance-name>`** pelo nome da sua instância (produção, desenvolvimento, etc.). O nome da instância é identificado por meio dos arquivos de configuração:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Para obter mais informações sobre como reiniciar módulos, consulte [esta seção](../../production/using/usual-commands.md#module-launch-commands).

## Falha no fluxo de trabalho {#failed-workflow}

Se um fluxo de trabalho falhar, siga estas etapas:

1. Verifique o journal do workflow. Para obter mais informações, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=pt-BR){target="_blank"}.
1. Monitore workflows técnicos. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=pt-BR){target="_blank"}.
1. Procure falhas nas atividades individuais do workflow.
