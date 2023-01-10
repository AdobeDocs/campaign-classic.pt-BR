---
product: campaign
title: Diretrizes de monitoramento
description: Descubra as diretrizes e práticas recomendadas para monitorar processos e instâncias do Campaign.
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 26%

---

# Diretrizes de monitoramento {#monitoring-guidelines}

![](../../assets/v7-only.svg)

## Painel de monitoramento de instância {#instance-monitoring-dashboard}

O **[!UICONTROL Monitoring]** A guia , que é acessível na página inicial do Campaign Classic, é o ponto de entrada principal que ajuda a monitorar sua instância.

Ele fornece um painel do que está ocorrendo em sua instância: seu status (versão de compilação, pacotes instalados etc.), indicadores do sistema, logs, workflows que estão sendo executados no momento, estado dos últimos deliveries enviados, etc.

Informações detalhadas estão disponíveis [aqui](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitorar processos do Campaign Classic {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Monitore sua instância</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">Monitorar workflows</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Monitorar deliveries</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Monitorar o banco de dados</a></p></td></tr>
</table>

Outras maneiras de monitorar os diferentes processos do Campaign estão disponíveis. Eles fornecem várias maneiras de monitorar suas instâncias para garantir que seu sistema esteja íntegro e, eventualmente, solucionar problemas que podem ocorrer ao configurar workflows, enviar deliveries etc.

### Monitorar a instância {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Ferramentas de monitoramento automático**

Vários métodos automáticos estão disponíveis. para ajudá-lo a monitorar a instância. Você pode, por exemplo, configurar relatórios de email com anomalias detectadas, recuperar uma lista de indicadores no formato XML etc. [Clique aqui](../../production/using/monitoring-processes.md#automatic-monitoring) para obter mais informações.

**Trilha de auditoria**

A Trilha de auditoria permite visualizar o histórico completo de alterações relacionadas a opções, fluxos de trabalho e schemas em sua instância. [Clique aqui](../../production/using/audit-trail.md) para obter mais informações.

**Painel de controle do Campaign**

O Painel de controle do Campaign permite gerenciar várias configurações da sua instância: gerencie permissões de URL, verifique os detalhes da instância, como as versões de build dos servidores etc. Ela também permite monitorar o espaço disponível nos servidores SFTP conectados à sua instância. [Clique aqui](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR) para obter mais informações.

>[!NOTE]
>
>O Painel de controle do Campaign é acessível a todos os usuários administradores. As etapas para conceder acesso de Administrador a um usuário estão detalhadas [nesta página](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=pt-BR#discover-control-panel).
>
>Observe que sua instância deve estar hospedada no AWS e atualizada com a [build mais recente disponível](../../rn/using/rn-overview.md). Saiba como verificar a versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Para verificar se sua instância está hospedada no AWS, siga as etapas detalhadas [nesta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=pt-BR).

### Monitoramento de workflows {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow HeatMap**

O Workflow HeatMap forneceu uma representação visual de todos os workflows que estão sendo executados em sua instância. Ela permite monitorar facilmente a carga na instância e planejar os workflows de acordo. [Clique aqui](../../workflow/using/heatmap.md) para obter mais informações.

**Trilha de auditoria**

A Trilha de auditoria permite visualizar todas as modificações que foram feitas em workflows, bem como seus estados atuais. [Clique aqui](../../production/using/audit-trail.md).

**Solução de problemas de workflows**

Ações específicas podem ser executadas ao encontrar problemas com uma execução de workflow. [Clique aqui](../../production/using/workflow-execution.md) para obter mais informações

**Monitoramento do status do workflow**

Além do heatmap, é possível criar um workflow que permitirá monitorar o status de um conjunto de workflows e enviar mensagens recorrentes aos supervisores. [Clique aqui](../../workflow/using/supervising-workflows.md) para obter mais informações.

**Orientações gerais**

Seguir as diretrizes e práticas recomendadas ao usar workflows pode ajudar a melhorar o desempenho. Para obter mais informações, consulte esta seção.
* [Práticas recomendadas para usar workflows](../../workflow/using/workflow-best-practices.md)
* [Monitoramento da execução do fluxo de trabalho](../../workflow/using/monitoring-workflow-execution.md)

### Monitoramento de entregas {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**Relatórios SMTP**

Os relatórios SMTP exibem estatísticas de delivery e erros SMTP por domínio. [Saiba mais](../../production/using/monitoring-processes.md)

**Práticas recomendadas**

[Práticas recomendadas para envio e criação de delivery](../../delivery/using/delivery-best-practices.md) O pode ajudá-lo a melhorar o desempenho.

**Solução de problemas de delivery**
Ações específicas podem ser executadas ao encontrar problemas com deliveries:
* [Problemas na capacidade de delivery](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemas de exibição de imagem](../../production/using/image-display-issues.md)
* [Problemas de desempenho do delivery](../../delivery/using/delivery-performances.md)
* [Problemas de arquivos temporários](../../production/using/temporary-files.md) - *somente em modelos de hospedagem local*

### Monitoramento do banco de dados {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Fluxo de trabalho de limpeza do banco de dados**

O fluxo de trabalho Database cleanup permite excluir dados obsoletos do banco de dados. É recomendável evitar o crescimento exponencial do banco de dados. [Clique aqui](../../production/using/database-cleanup-workflow.md) para obter mais informações.

**Solução de problemas de desempenho do banco de dados**

Ações específicas podem ser executadas ao encontrar problemas com desempenho do banco de dados. [Clique aqui](../../production/using/database-performances.md) para obter mais informações.

**Manutenção do banco de dados**

*apenas modelos de hospedagem local e híbrida*

Recomendamos que você faça a manutenção do banco de dados regularmente para evitar o consumo excessivo de espaço em disco, afetando assim o acesso ao banco de dados. [Clique aqui](../../production/using/recommendations.md) para obter mais informações.

**Backup e restauração**

*apenas modelos de hospedagem local e híbrida*

O backup é essencial para evitar a perda de dados em caso de problema (físico ou relacionado ao sistema) em uma máquina. [Clique aqui](../../production/using/backup.md) para obter mais informações. O procedimento de restauração é descrito em [esta seção](../../production/using/restoration.md).

## Princípios técnicos do Campaign Classic {#campaign-classic-technical-principles}

Os recursos técnicos estão disponíveis na documentação do Campaign Classic. Recomendamos que você se familiarize com esses tópicos antes de executar qualquer operação técnica em sua instância.

**Modelos e recursos de hospedagem**

* [Modelos de hospedagem Campaign Classic](../../installation/using/hosting-models.md)
* [Recursos do modelo de hospedagem](../../installation/using/capability-matrix.md)

**Configuração do servidor**

*Somente modelos de hospedagem local e híbrida*

* [Configurações do servidor](../../installation/using/configuring-campaign-server.md)
* [Configuração do arquivo Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configuração do servidor para entrega](../../installation/using/email-deliverability.md)
* [Linhas de comando para criar uma instância e declarar um banco de dados](../../installation/using/command-lines.md)

**Princípios gerais**

* [Arquitetura do Campaign Classic](../../production/using/general-architecture.md)
* [Módulos Campaign Classic](../../production/using/operating-principle.md)
* [Opções de Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Como configurar a inicialização automática dos módulos](../../production/using/administration.md)
* [Princípio de configuração da campanha](../../production/using/configuration-principle.md)
* [Procedimentos de solução de problemas](../../production/using/performance-and-throughput-issues.md)
