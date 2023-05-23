---
product: campaign
title: Diretrizes de monitoramento
description: Descubra as diretrizes e práticas recomendadas para monitorar processos e instâncias do Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 26%

---

# Diretrizes de monitoramento {#monitoring-guidelines}



## Painel de monitoramento de instância {#instance-monitoring-dashboard}

A variável **[!UICONTROL Monitoring]** , que pode ser acessada na página inicial do Campaign Classic, é o principal ponto de entrada para ajudar você a monitorar sua instância.

Ele fornece um painel do que está ocorrendo na sua instância: seu status (versão de compilação, pacotes instalados etc.), indicadores do sistema, logs, workflows que estão em execução no momento, estado dos últimos deliveries enviados etc.

Informações detalhadas estão disponíveis [aqui](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitoramento de processos Campaign Classic {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Monitorar sua instância</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">Monitorar workflows</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Monitorar deliveries</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Monitorar o banco de dados</a></p></td></tr>
</table>

Outras maneiras de monitorar os diferentes processos do Campaign estão disponíveis. Elas fornecem várias maneiras de monitorar suas instâncias para garantir que seu sistema esteja íntegro e, eventualmente, solucionar problemas que podem ocorrer ao configurar workflows, enviar deliveries etc.

### Monitoramento de sua instância {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Ferramentas de monitoramento automático**

Vários métodos automáticos estão disponíveis. para ajudar você a monitorar sua instância. Você pode, por exemplo, configurar relatórios de email com anomalias detectadas, recuperar uma lista de indicadores no formato XML etc. [Clique aqui](../../production/using/monitoring-processes.md#automatic-monitoring) para obter mais informações.

**Trilha de auditoria**

A Trilha de auditoria permite visualizar o histórico completo de alterações relacionadas a opções, workflows e esquemas na sua instância. [Clique aqui](../../production/using/audit-trail.md) para obter mais informações.

**Painel de controle**

O Painel de controle do Campaign permite gerenciar várias configurações da sua instância: gerenciar permissões de URL, verificar detalhes da instância como as versões de build dos servidores etc. Também permite monitorar o espaço disponível nos servidores SFTP conectados à sua instância. [Clique aqui](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR) para obter mais informações.

>[!NOTE]
>
>O Painel de controle é acessível a todos os usuários administradores. As etapas para conceder acesso de Administrador a um usuário estão detalhadas [nesta página](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=pt-BR#discover-control-panel).
>
>Observe que sua instância deve estar hospedada no AWS e atualizada com a [build mais recente disponível](../../rn/using/rn-overview.md). Saiba como verificar a versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Para verificar se sua instância está hospedada no AWS, siga as etapas detalhadas [nesta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=pt-BR).

### Monitoramento de workflows {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow HeatMap**

O Workflow HeatMap forneceu uma representação visual de todos os workflows que estão sendo executados em sua instância. Ele permite monitorar facilmente a carga na instância e planejar os workflows de acordo. [Clique aqui](../../workflow/using/heatmap.md) para obter mais informações.

**Trilha de auditoria**

A Trilha de auditoria permite visualizar todas as modificações que foram feitas em workflows, bem como seus estados atuais. [Clique aqui](../../production/using/audit-trail.md).

**Solução de problemas de fluxos de trabalho**

Ações específicas podem ser executadas ao encontrar problemas com a execução de um workflow. [Clique aqui](../../production/using/workflow-execution.md) para obter mais informações

**Monitoramento do status do fluxo de trabalho**

Além do mapa de calor, você pode criar um fluxo de trabalho que permitirá monitorar o status de um conjunto de fluxos de trabalho e enviar mensagens recorrentes aos supervisores. [Clique aqui](../../workflow/using/supervising-workflows.md) para obter mais informações.

**Orientações gerais**

Seguir as diretrizes e práticas recomendadas ao usar workflows pode ajudar a melhorar o desempenho. Para obter mais informações, consulte esta seção.
* [Práticas recomendadas para usar workflows](../../workflow/using/workflow-best-practices.md)
* [Monitoramento da execução do fluxo de trabalho](../../workflow/using/monitoring-workflow-execution.md)

### Monitoramento de entregas {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**Relatórios SMTP**

Os relatórios SMTP exibem estatísticas de delivery e erros SMTP por domínio. [Saiba mais](../../production/using/monitoring-processes.md)

**Práticas recomendadas**

[Práticas recomendadas para envio e design de delivery](../../delivery/using/delivery-best-practices.md) O pode ajudá-lo a melhorar o desempenho.

**Solução de problemas de entrega**
Ações específicas podem ser executadas ao encontrar problemas com os deliveries:
* [Problemas na capacidade de delivery](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemas de exibição de imagem](../../production/using/image-display-issues.md)
* [Problemas de desempenho do delivery](../../delivery/using/delivery-performances.md)
* [Problemas com arquivos temporários](../../production/using/temporary-files.md) - *somente modelos de hospedagem no local*

### Monitoramento do banco de dados {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Fluxo de trabalho de limpeza do banco de dados**

O fluxo de trabalho Limpeza do banco de dados permite excluir dados obsoletos do banco de dados. É recomendável evitar o crescimento exponencial do banco de dados. [Clique aqui](../../production/using/database-cleanup-workflow.md) para obter mais informações.

**Solução de problemas de desempenho do banco de dados**

Ações específicas podem ser executadas ao encontrar problemas com desempenhos de bancos de dados. [Clique aqui](../../production/using/database-performances.md) para obter mais informações.

**Manutenção do banco de dados**

*somente modelos de hospedagem no local e híbridos*

Recomendamos que você execute a manutenção do banco de dados regularmente para evitar o consumo excessivo de espaço em disco, afetando assim o acesso ao banco de dados. [Clique aqui](../../production/using/recommendations.md) para obter mais informações.

**Backup e restauração**

*somente modelos de hospedagem no local e híbridos*

O backup é essencial para evitar a perda de dados no caso de um problema (seja físico ou relacionado ao sistema) em uma máquina. [Clique aqui](../../production/using/backup.md) para obter mais informações. O procedimento de restauração é descrito em [nesta seção](../../production/using/restoration.md).

## Princípios técnicos do Campaign Classic {#campaign-classic-technical-principles}

Os recursos técnicos estão disponíveis na documentação do Campaign Classic. Recomendamos que você se familiarize com esses tópicos antes de executar qualquer operação técnica em sua instância.

**Modelos e recursos de hospedagem**

* [modelos de hospedagem de Campaign Classic](../../installation/using/hosting-models.md)
* [Recursos do modelo de hospedagem](../../installation/using/capability-matrix.md)

**Configuração do servidor**

*Somente modelos de hospedagem no local e híbridos*

* [Configurações do servidor](../../installation/using/configuring-campaign-server.md)
* [Configuração do arquivo Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configuração do servidor para capacidade de entrega](../../installation/using/email-deliverability.md)
* [Linhas de comando para criar uma instância e declarar um banco de dados](../../installation/using/command-lines.md)

**Princípios gerais**

* [Arquitetura de Campaign Classic](../../production/using/general-architecture.md)
* [módulos Campaign Classic](../../production/using/operating-principle.md)
* [opções de Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Como configurar a inicialização automática dos módulos](../../production/using/administration.md)
* [Princípio de configuração da campanha](../../production/using/configuration-principle.md)
* [Procedimentos de solução de problemas](../../production/using/performance-and-throughput-issues.md)
