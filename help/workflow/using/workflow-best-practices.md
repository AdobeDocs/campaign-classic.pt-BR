---
product: campaign
title: Práticas recomendadas do fluxo de trabalho
description: Conheça as práticas recomendadas do workflow do Campaign
feature: Workflows
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1687'
ht-degree: 100%

---

# Práticas recomendadas de workflow{#workflow-best-practices}

![](../../assets/v7-only.svg)

## Execução e desempenho {#execution-and-performance}

As diretrizes gerais sobre a otimização do desempenho do Campaign estão listadas abaixo, incluindo as práticas recomendadas para aplicar aos workflows.

As diretrizes para solução de problemas relacionados à execução de workflows também estão disponíveis no [Guia de produção do Campaign Classic v7](../../production/using/workflow-execution.md).

### Logs {#logs}

O método **[!UICONTROL logInfo()]** do JavaScript é uma ótima solução para depurar um fluxo de trabalho. É útil, mas deve ser usado com cuidado, especialmente para atividades executadas com frequência: pode sobrecarregar os logs e aumentar significativamente o tamanho da tabela de log. Mas, também pode ser preciso de mais do que **[!UICONTROL logInfo()]**.

Duas soluções adicionais estão disponíveis para ajudar:

* **Manter o resultado de públicos provisórios entre duas execuções**

   Essa opção mantém tabelas temporárias entre duas execuções de um workflow. Está disponível na guia **[!UICONTROL General]** das propriedades do fluxo de trabalho e pode ser usado para desenvolvimento e testes para monitorar dados e verificar resultados. Você pode usar essa opção em ambientes de desenvolvimento, mas nunca usá-la em ambientes de produção. Manter tabelas temporárias pode resultar no aumento significativo do tamanho de banco de dados e, por fim, atingir o limite de tamanho. Além disso, o backup ficará lento.

   Somente as tabelas de trabalho da última execução do workflow são mantidas. As tabelas de trabalho das execuções anteriores são removidas pelo fluxo de trabalho **[!UICONTROL cleanup]**, executado diariamente.

   >[!CAUTION]
   >
   >Essa opção nunca deve ser verificada em um workflow de produção. Essa opção é usada para analisar os resultados e é projetada apenas para fins de teste e, portanto, deve ser usada apenas em ambientes de desenvolvimento ou de preparo.

* **Logs de queries SQL no journal**

   Disponível na guia **[!UICONTROL Execution]** das propriedades do fluxo de trabalho, essa opção registrará todos as consultas SQL geradas pela ferramenta a partir das diferentes atividades. É uma boa forma de ver o que está realmente sendo executado pela plataforma. No entanto, essa opção só deve ser usada temporariamente durante o desenvolvimento e não ativada durante a produção.

Limpe os registros quando não forem mais necessários. O histórico do workflow não é removido automaticamente: todas as mensagens são mantidas por padrão. O histórico pode ser eliminado por meio do menu **[!UICONTROL File > Actions]** ou clicando no botão Actions localizado na barra de ferramentas acima da lista. Selecione Purge history.
Para saber como limpar seus registros, consulte esta [documentação](starting-a-workflow.md).

### Planejamento de workflow {#workflow-planning}

* Tente manter um nível estável de atividade ao longo do dia e evitar picos para prevenir a sobrecarga da instância. Para fazer isso, distribua os horários de início do workflow uniformemente ao longo do dia.
* Agende a carga de dados durante a noite para reduzir o a contenção de recurso.
* Workflows longos podem ter impacto no servidor e nos recursos do banco de dados. Divida os workflows mais longos para reduzir o tempo de processamento.
* Para reduzir os tempos de execução gerais, substitua atividades demoradas por atividades simplificadas e mais rápidas.
* Evite executar mais de 20 workflows simultaneamente. Quando muitos workflows são executados ao mesmo tempo, o sistema pode ficar sem recursos e se tornar instável. Para obter mais informações sobre por que o workflow pode não estar sendo iniciado, consulte este [artigo](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).

### Execução do workflow {#workflow-execution}

**É recomendável não agendar um fluxo de trabalho para execução por mais de 15 minutos**, pois isso pode atrapalhar o desempenho geral do sistema e criar bloqueios no banco de dados.

**Evite deixar os fluxos de trabalho no estado pausado.** Se criar um fluxo de trabalho temporário, certifique-se de que ele será concluído corretamente e não permanecerá no estado **[!UICONTROL paused]**. Se estiver pausado, isso significa que é preciso manter as tabelas temporárias e, portanto, aumentar o tamanho do banco de dados. Atribua supervisores de workflow nas propriedades do workflow para enviar um alerta quando um workflow falhar ou for pausado pelo sistema.

Para evitar workflows no estado pausado:

* Verifique seus workflows regularmente para garantir que não haja erros inesperados.
* Mantenha seus workflows o mais simples possível, por exemplo, dividindo grandes workflows em vários workflows diferentes. É possível usar as atividades **[!UICONTROL External signal]** para acionar a execução com base na execução de outros fluxos de trabalho.
* Evite desabilitar atividades com fluxos nos fluxos de trabalho, deixando threads abertos e levando a muitas tabelas temporárias que podem consumir muito espaço. Não mantenha as atividades nos estados **[!UICONTROL Do not enable]** ou **[!UICONTROL Enable but do not execute]** em seus fluxos de trabalho.

**Interromper fluxos de trabalho não utilizados**. Os fluxos de trabalho que continuam em execução mantêm conexões com o banco de dados.

**Use a interrupção incondicional apenas nos casos mais raros**. Não utilize esta ação regularmente. Não executar um encerramento limpo nas conexões geradas pelos workflows com o banco de dados afeta o desempenho.

**Não execute várias solicitações de interrupção no mesmo fluxo de trabalho**. A interrupção de um fluxo de trabalho é um processo assíncrono: a solicitação é registrada e, em seguida, o servidor ou servidores de fluxo de trabalho cancelam as operações em andamento. A interrupção de uma instância de fluxo de trabalho pode demorar, especialmente se o fluxo de trabalho estiver em execução em vários servidores, em que cada um deles deve assumir o controle para cancelar as tarefas em andamento. Para evitar problemas, aguarde a conclusão da operação de interrupção e evite interromper um fluxo de trabalho várias vezes.

### Opção de Executar no mecanismo {#execute-in-the-engine-option}

Na janela **[!UICONTROL Workflow properties]**, nunca marque a opção **[!UICONTROL Execute in the engine]**. Quando essa opção está habilitada, o workflow tem prioridade e todos os outros workflows são interrompidos pelo mecanismo do workflow até que este seja concluído.

![](assets/wf-execute-in-engine.png)

## Propriedades do workflow {#workflow-properties}

### Pastas de workflow {#workflow-folders}

A Adobe recomenda criar seus workflows em uma pasta dedicada.

Se o fluxo de trabalho afetar toda a plataforma (processos de limpeza, por exemplo), é possível considerar adicionar uma subpasta à pasta interna **[!UICONTROL Technical Workflows]**.

### Nomeação do workflow {#workflow-naming}

Como facilita a localização e a solução de problemas se não estiverem executando da forma esperada, a Adobe recomenda que os workflows tenham nomes e rótulos adequados: preencha o campo de descrição do workflow para resumir o processo para que o operador possa entender facilmente.

Se o workflow fizer parte de um processo envolvendo vários workflows, você pode ser explícito ao inserir um rótulo. Usar números é uma ótima maneira de organizar os workflows (por Rótulo).

Por exemplo:

* 001 – Importar – Importação de recipientes
* 002 – Importar – Importação de vendas
* 003 – Importar – Importação de detalhes de vendas
* 010 – Exportar – Exportação de logs de entregas
* 011 – Exportar – Exportação de logs de rastreamento

### Severidade do workflow {#workflow-severity}

É possível configurar a severidade nas propriedades do fluxo de trabalho, na guia **[!UICONTROL Execution]**:

* Normal
* Produção
* Crítico

Fornecer essas informações ao criar um workflow ajudará a entender a severidade do processo configurado.

Essa opção tem impacto funcional somente nos workflows da campanha.

Workflows da campanha (workflows criados como parte de uma campanha/operação) com uma severidade mais alta são executados com prioridade caso a campanha tenha muitos processos executados simultaneamente. Por padrão, apenas dez processos podem ser executados simultaneamente em uma campanha, de acordo com a opção NmsOperation_LimitConcurrency. Por exemplo, se uma campanha contêm 25 workflows, os workflows com uma severidade mais alta serão executados no primeiro pool de dez processos.

### Monitoramento do workflow {#workflow-monitoring}

Todos os workflows agendados que estão sendo executados em ambientes de produção devem ser monitorados para que um alerta seja enviado em caso de erro.

Nas propriedades do fluxo de trabalho, selecione um grupo supervisor, seja o grupo **[!UICONTROL Workflow supervisors]** padrão ou um grupo personalizado. Certifique-se de que pelo menos um operador participe desse grupo, com um email definido.

Antes de começar a construir um workflow, lembre-se de definir supervisores de workflow. Eles serão notificados por email em caso de erro. Para obter mais informações, consulte [Gerenciando erros](monitoring-workflow-execution.md#managing-errors).

Verifique regularmente a guia **[!UICONTROL Monitoring]** para visualizar o status geral dos workflows ativos. Para obter mais informações, consulte [Supervisão de instância](monitoring-workflow-execution.md#instance-supervision).

O Workflow HeatMap permite aos administradores da plataforma Adobe Campaign monitorarem a carga na instância e planejarem os workflows correspondentes. Para obter mais informações, consulte [Monitoramento de workflow](heatmap.md).

## Uso das atividades {#using-activities}

>[!CAUTION]
>
>É possível copiar e colar atividades dentro de um mesmo workflow. No entanto, não recomendamos atividades de copiar e colar em workflows diferentes. Algumas configurações anexadas a atividades como Delivery e Scheduler podem gerar conflitos e erros ao executar o workflow de destino. Em vez disso, recomendamos usar **Duplicate** nos workflows. Para obter mais informações, consulte [Duplicação de workflows](building-a-workflow.md#duplicating-workflows).

### Nome da atividade {#name-of-the-activity}

Ao desenvolver seu workflow, todas as atividades terão um nome, como todos os objetos do Adobe Campaign. Embora o nome seja gerado pela ferramenta, recomendamos que você renomeie com um nome explícito ao configurá-lo. O risco de fazer isso depois é que pode interromper o workflow com atividades usando o nome de outra atividade anterior. Portanto, seria um trabalho difícil atualizar os nomes depois.

O nome da atividade pode ser encontrado na guia **[!UICONTROL Advanced]**. Não use nomes como **[!UICONTROL query]**, **[!UICONTROL query1]**, **[!UICONTROL query11]**, mas sim nomes explícitos como **[!UICONTROL querySubscribedRecipients]**. Esse nome aparecerá no diário e, se aplicável, nos logs SQL, e isso ajudará a depurar o fluxo de trabalho ao configurá-lo.

### Primeira e última atividades {#first-and-last-activities}

* Sempre inicie o fluxo de trabalho com uma atividade **[!UICONTROL Start]** ou atividade **[!UICONTROL Scheduler]** . Quando pertinente, também é possível usar uma atividade **[!UICONTROL External signal]**.
* Ao criar o fluxo de trabalho, use apenas uma atividade **[!UICONTROL Scheduler]** por ramificação. Se a mesma ramificação de um fluxo de trabalho tiver vários schedulers (vinculados uns aos outros), o número de tarefas a serem executadas será multiplicado exponencialmente, o que irá sobrecarregar consideravelmente o banco de dados. Essa regra também se aplica a todas as atividades com uma guia **[!UICONTROL Scheduling & History]**. Saiba mais em [Agendamento](scheduler.md).

   ![](assets/wf-scheduler.png)

* Use atividades **[!UICONTROL End]** para cada fluxo de trabalho. Isso permite que o Adobe Campaign libere espaço temporário usado para cálculos dentro de workflows. Para obter mais informações, consulte [início e fim](start-and-end.md).

### Javascript em uma atividade {#javascript-within-an-activity}

Você pode adicionar JavaScript ao inicializar uma atividade do fluxo de trabalho. Isso pode ser feito na guia **[!UICONTROL Advanced]** da atividade.

Para facilitar a identificação do fluxo de trabalho, recomendamos usar traços duplos no início e no fim do rótulo da atividade da seguinte maneira: -- Meu rótulo --.

### Sinal {#signal}

Na maior parte do tempo, você não saberá de onde o sinal é chamado. Para evitar esse problema, use o campo **[!UICONTROL Comment]** dentro da guia **[!UICONTROL Advanced]** da atividade do sinal para documentar a origem esperada de um sinal para essa atividade.

![](assets/workflow-signal-bp.png)

## Atualização de fluxo de trabalho {#workflow-update}

Um workflow de produção não deve ser atualizado diretamente. A menos que o processo consista na criação de uma campanha com templates de workflows, os processos devem ser testados primeiro em um ambiente de desenvolvimento. Após essa validação, o workflow pode ser implantado e iniciado na produção.

Realize todos os testes em ambientes de desenvolvimento ou de preparo, não em ambientes de produção. O desempenho não pode ser assegurado em tais casos.

Os workflows arquivados podem ser mantidos em plataformas de desenvolvimento ou teste, em uma pasta Arquivada, mas o ambiente de produção deve permanecer o mais limpo possível. Os workflows antigos devem ser removidos do ambiente de produção se estiverem inativos.
