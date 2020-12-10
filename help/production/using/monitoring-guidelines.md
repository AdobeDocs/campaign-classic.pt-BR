---
solution: Campaign Classic
product: campaign
title: Orientações de monitoramento
description: Descubra as diretrizes e práticas recomendadas para monitorar processos e instâncias do Campaign.
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 9aa0ecd423bfbf1082e9ce5bdb36aaf1611dea54
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 10%

---


# Orientações de monitoramento {#monitoring-guidelines}

## Painel de monitoramento de instância {#instance-monitoring-dashboard}

A guia **[!UICONTROL Monitoring]**, que pode ser acessada a partir da página inicial do Campaign Classic, é o principal ponto de entrada para ajudar a monitorar sua instância.

Ele fornece uma painel do que está ocorrendo em sua instância: seu status (versão de compilação, pacotes instalados etc.), indicadores do sistema, registros, workflows que estão em execução no momento, estado dos últimos delivery enviados etc.

Informações detalhadas estão disponíveis [aqui](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitoramento de processos de Campaign Classic {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Monitore sua instância</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">Workflows de monitor</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Delivery de monitor</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Monitorar o banco de dados</a></p></td></tr>
</table>

Existem outras formas de monitorar os diferentes processos de Campanha. Eles fornecem várias maneiras de monitorar suas instâncias para garantir que seu sistema esteja saudável e, eventualmente, solucionar problemas que podem ocorrer ao configurar workflows, enviar delivery etc.

### Monitorando sua instância {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Ferramentas de monitoramento automático**

Vários métodos automáticos estão disponíveis. para ajudá-lo a monitorar sua instância. Você pode, por exemplo, configurar relatórios de email com anomalias detectadas, recuperar uma lista de indicadores no formato XML etc. [Clique ](../../production/using/monitoring-processes.md#automatic-monitoring) aqui para obter mais informações.

**Trilha de auditoria**

A trilha de auditoria permite visualizar o histórico completo de alterações relacionadas a opções, workflows e schemas dentro da sua instância. [Clique ](../../production/using/audit-trail.md) aqui para obter mais informações.

**Painel de controle do Campaign**

O Painel de controle do Campaign permite gerenciar várias configurações da sua instância: gerencie permissões de URL, verifique os detalhes da instância, como as versões de compilação dos servidores etc. Também permite monitorar o espaço disponível nos servidores SFTP conectados à sua instância. [Clique ](https://docs.adobe.com/content/help/pt-BR/control-panel/using/control-panel-home.translate.html) aqui para obter mais informações.

>[!NOTE]
>
>Observe que o Painel de controle do Campaign é acessível somente para usuários administradores e está disponível para todos os clientes que usam os Serviços gerenciados da Adobe.

### Monitoramento de workflows {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow HeatMap**

O Workflow HeatMap forneceu uma representação visual de todos os workflows que estão sendo executados em sua instância. Permite monitorar facilmente a carga na instância e planejar workflows de acordo. [Clique ](../../workflow/using/heatmap.md) aqui para obter mais informações.

**Trilha de auditoria**

A trilha de auditoria permite visualizar todas as modificações que foram feitas em workflows, bem como seus estados atuais. [Clique aqui](../../production/using/audit-trail.md).

**Solução de problemas de workflows**

Ações específicas podem ser executadas ao encontrar problemas com uma execução de fluxo de trabalho. [Clique ](../../production/using/workflow-execution.md) aqui para obter mais informações

**Monitoramento do status do fluxo de trabalho**

Além do mapa de calor, você pode criar um fluxo de trabalho que permitirá monitorar o status de um conjunto de workflows e enviar mensagens recorrentes aos supervisores. [Clique ](../../workflow/using/supervising-workflows.md) aqui para obter mais informações.

**Orientações gerais**

Seguir as diretrizes e as práticas recomendadas ao usar workflows pode ajudar a melhorar o desempenho. Para obter mais informações, consulte esta seção.
* [Práticas recomendadas ao usar workflows](../../workflow/using/workflow-best-practices.md)
* [Monitoramento da execução do workflow](../../workflow/using/monitoring-workflow-execution.md)

### Monitoramento de deliveries {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**Relatórios SMTP**

Os relatórios SMTP exibem estatísticas de delivery e erros SMTP por domínio. [Saiba mais](../../production/using/monitoring-processes.md)

**Práticas recomendadas**

[As práticas recomendadas para envio e ](../../delivery/using/delivery-best-practices.md) criação de delivery podem ajudá-lo a melhorar seu desempenho.

**Solução de**
problemas do deliveryAções específicas podem ser executadas ao encontrar problemas com delivery:
* [Problemas com delivery](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemas de exibição de imagem](../../production/using/image-display-issues.md)
* [Problemas de desempenho do delivery](../../delivery/using/delivery-performances.md)
* [Problemas](../../production/using/temporary-files.md)  de arquivos temporários - somente  *em modelos de hospedagem locais*

### Monitorando o banco de dados {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Workflow de limpeza do banco de dados**

O fluxo de trabalho de limpeza do banco de dados permite que você exclua dados obsoletos do banco de dados. É recomendável evitar o crescimento exponencial do banco de dados. [Clique ](../../production/using/database-cleanup-workflow.md) aqui para obter mais informações.

**Solução de problemas de desempenho do banco de dados**

Ações específicas podem ser executadas ao encontrar problemas com o desempenho do banco de dados. [Clique ](../../production/using/database-performances.md) aqui para obter mais informações.

**Manutenção do banco de dados**

*apenas modelos de hospedagem local e híbrido*

Recomendamos que você execute a manutenção do banco de dados regularmente para evitar o consumo excessivo de espaço em disco, afetando assim o acesso ao banco de dados. [Clique ](../../production/using/recommendations.md) aqui para obter mais informações.

**Backup e restauração**

*apenas modelos de hospedagem local e híbrido*

O backup é essencial para evitar a perda de dados no evento de um problema (físico ou relacionado ao sistema) em uma máquina. [Clique ](../../production/using/backup.md) aqui para obter mais informações. O procedimento de restauração está descrito em [esta seção](../../production/using/restoration.md).

## Princípios técnicos do Campaign Classic {#campaign-classic-technical-principles}

Os recursos técnicos estão disponíveis na documentação do Campaign Classic. Recomendamos que você se familiarize com esses tópicos antes de executar qualquer operação técnica em sua instância.

**Hospedagem de modelos e recursos**

* [modelos de hospedagem de Campaign Classic](../../installation/using/hosting-models.md)
* [Recursos do modelo de hospedagem](../../installation/using/capability-matrix.md)

**Configuração do servidor**

*Somente modelos de hospedagem local e híbrido*

* [Configurações obrigatórias do servidor](../../installation/using/campaign-server-configuration.md)
* [Configuração do arquivo Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configuração do servidor para entrega](../../installation/using/email-deliverability.md)
* [Linhas de comando para criar uma instância e declarar um banco de dados](../../installation/using/command-lines.md)

**Princípios gerais**

* [arquitetura Campaign Classic](../../production/using/general-architecture.md)
* [módulos Campaign Classic](../../production/using/operating-principle.md)
* [Opções de Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Como configurar a inicialização automática dos módulos](../../production/using/administration.md)
* [Princípio de configuração de campanha](../../production/using/configuration-principle.md)
* [Procedimentos de solução de problemas](../../production/using/performance-and-throughput-issues.md)
