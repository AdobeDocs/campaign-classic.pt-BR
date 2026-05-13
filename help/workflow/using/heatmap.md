---
product: campaign
title: Workflow HeatMap do Campaign
description: Monitore seus fluxos de trabalho do com o Workflow HeatMap
feature: Workflows, Heatmap
hide: true
exl-id: f1016ddf-0c87-4611-a878-d01f3684935f
TQID: https://experienceleague.adobe.com/i8BnIsz83IdW4kofr2OBtzXokKiyeJuQl3jIBpsOQx0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a658c786-869b-4194-a780-2594d663adda
subfeature_v2: id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
topic_v2: id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 1147
ht-degree: 98%

---

# Workflow HeatMap {#workflow-heatmap}



O Workflow HeatMap do Campaign consiste em uma representação gráfica colorida de todos os fluxos de trabalho que estão sendo executados no momento. Ele só está disponível para **Administradores do Campaign**.

Descubra outras maneiras de monitorar os processos do Campaign [nesta página](../../production/using/monitoring-guidelines.md).

## Introdução ao Workflow HeatMap {#about-the-workflow-heatmap}

Ao fornecer uma visão geral rápida do número de fluxos de trabalho simultâneos, o Workflow HeatMap permite que os administradores da plataforma Adobe Campaign monitorem a carga da instância e planejem os fluxos de trabalho de acordo.

Mais precisamente, ajuda os administradores de plataforma a:

* Ver e entender fluxos de trabalho simultâneos
* Filtrar fluxos de trabalho por duração para ver quais fluxos de trabalho podem encontrar problemas
* Filtrar atividades por duração para ver quais atividades podem encontrar problemas
* Encontre facilmente fluxos de trabalho individuais e todas as atividades relacionadas (com sua duração)
* Filtrar por tipo de fluxo de trabalho: [workflows técnicos](building-a-workflow.md#technical-workflows) ou [workflows da campanha](building-a-workflow.md#campaign-workflows)
* Procure um fluxo de trabalho específico para analisar

>[!NOTE]
>
>Além do **Workflow Heatmap**, é possível criar um fluxo de trabalho que permitirá monitorar o status de um conjunto de fluxos de trabalho e enviar mensagens recorrentes aos supervisores. Para obter mais informações, consulte a [seção dedicada](supervising-workflows.md).

O uso do Workflow HeatMap requer uma boa compreensão dos seguintes conceitos: [fluxos de trabalho](about-workflows.md), [atividades](about-activities.md) e [práticas recomendadas de fluxo de trabalho](workflow-best-practices.md).

## Personalizar o Workflow HeatMap {#using-the-heatmap}

>[!NOTE]
>
>Se nenhum dado for exibido no Workflow HeatMap, clique no botão **[!UICONTROL Load data]**.

1. Vá para **[!UICONTROL Monitoring]** e clique no link **[!UICONTROL Workflow HeatMap]** para exibir a página **[!UICONTROL Campaign Workflow HeatMap]**.

   ![](assets/wkf_monitoring_path.png)

1. Clique no calendário para selecionar um dia.

   Por padrão, a página mostra a atividade do fluxo de trabalho do dia atual. Você pode alterá-la e selecionar qualquer dia no passado.

   >[!NOTE]
   >
   >Somente os fluxos de trabalho que não foram excluídos pelo fluxo de trabalho do **[!UICONTROL Database cleanup]** ficam visíveis. Para obter mais informações sobre o fluxo de trabalho de limpeza de banco de dados, consulte [esta seção](../../production/using/database-cleanup-workflow.md).\
   >Por padrão, o fuso horário do Workflow HeatMap é aquele definido para o usuário administrador atual. Por exemplo, talvez você queira alterá-la se não estiver na mesma área dos usuários de marketing com os quais você está trabalhando.

1. Clique no botão **[!UICONTROL Filters]**.

   ![](assets/wkf_monitoring_filters.png)

1. Use o controle deslizante para definir a duração mínima de 0 segundo a 1 hora. Isso permite pesquisar somente os fluxos de trabalho em execução por mais de um determinado número de segundos ou minutos.

   ![](assets/wkf_monitoring_filters_duration.png)

1. Você também pode escolher um fluxo de trabalho específico na lista suspensa **[!UICONTROL Workflows]**:

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >O filtro **[!UICONTROL Min duration]** é aplicado. Se não conseguir encontrar um fluxo de trabalho específico, redefina a duração mínima para 0 para que todos os fluxos de trabalho sejam exibidos na lista.

1. Também é possível filtrar no campo **[!UICONTROL Workflow type]**:

   * **[!UICONTROL Technical]**: somente [fluxos de trabalho técnicos prontos](building-a-workflow.md#technical-workflows) e [fluxos de trabalho de gerenciamento de dados](targeting-data.md#data-management) são exibidos.
   * **[!UICONTROL Marketing]**: somente os fluxos de trabalho vinculados a uma campanha de marketing, conhecidos como [fluxos de trabalho da campanha](building-a-workflow.md#campaign-workflows), são exibidos.

1. Para pesquisar um fluxo de trabalho específico por nome, também é possível usar o campo **[!UICONTROL Workflow name filter]**.

1. Se você editou alguns fluxos de trabalho no intervalo de tempo, clique no botão **[!UICONTROL Reload data]** para atualizar os dados exibidos na grade.

## Interpretar o Workflow HeatMap {#reading-the-heatmap}

O Campaign Workflow HeatMap é uma grade naturalmente legível do canto superior esquerdo ao inferior direito, permitindo encontrar as &quot;zonas ativas&quot; com um intervalo de cores verde a vermelho.

* As células vermelhas mais escuras correspondem a períodos em que um número alto de fluxos de trabalho está sendo executado ao mesmo tempo.
* As células cinza correspondem a períodos em que nenhum fluxo de trabalho está em execução.

Para saber como o código de cor é aplicado e como navegar no HeatMap, clique no botão **[!UICONTROL Help]**.

![](assets/wkf_monitoring_legend.png)

Cada linha representa uma hora do dia e cada célula representa 5 minutos dessa hora.

A grade mostra todos os fluxos de trabalho que estão sendo executados ao mesmo tempo para cada um desses períodos de 5 minutos.

No exemplo abaixo, entre 8h e 8:05am, três workflows estão em execução (independentemente da duração individual):

![](assets/wkf_monitoring_ex_8am.png)

1. Clique em uma célula colorida para exibir os detalhes de todos os fluxos de trabalho simultâneos em execução durante esse período.

   ![](assets/wkf_monitoring_details.png)

   Para cada fluxo de trabalho, todas as atividades que ele contém são listadas, com sua duração.

1. Clique na ID ou no nome do fluxo de trabalho para abri-lo diretamente.
1. Para voltar para a exibição do **[!UICONTROL Campaign Workflow HeatMap]**, clique no botão **[!UICONTROL Home]**.

## Casos de uso: usar o HeatMap para realizar ações {#use-cases--using-the-heatmap-to-take-actions}

Há dois casos principais em que o Workflow HeatMap do Campaign pode ser útil.

### Reduzir o número de fluxos de trabalho simultâneos {#reducing-the-number-of-concurrent-workflows}

Como administrador do Campaign, o Workflow HeatMap pode ajudá-lo a entender a carga na instância e planejar fluxos de trabalho novos ou existentes em momentos apropriados.

1. Na exibição do **[!UICONTROL Campaign Workflow HeatMap]**, clique no botão **[!UICONTROL Filters]**.
1. Defina a duração para alguns segundos ou alguns minutos.
1. Aumente o filtro de duração para excluir os fluxos de trabalho mais curtos que não são significativos.

   ![](assets/wkf_monitoring_short_duration.png)

1. Explore os resultados para entender a carga na instância e execute as ações apropriadas:

   * Se você encontrar problemas de desempenho e se uma ou mais células vermelhas forem exibidas na grade, considere alterar a hora de início de vários fluxos de trabalho. Solicite aos usuários de marketing que movam fluxos de trabalho manualmente de períodos ocupados (&quot;ativos&quot;) para períodos mais disponíveis. Isso deve manter um nível estável de atividade ao longo do dia.
   * Para evitar picos e a sobrecarga da instância, verifique o HeatMap antes de planejar novos fluxos de trabalho e escolha o melhor momento. Considere os intervalos de tempo correspondentes às células cinza ou verde na grade para iniciar novos fluxos de trabalho.

### Encontrar fluxos de trabalho de longa duração que afetam desempenhos {#finding-long-running-workflows-that-impact-performance}

Como administrador do Campaign, o Workflow HeatMap ajuda você a encontrar os fluxos de trabalho mais longos que podem retardar a atividade.

1. Na exibição do **[!UICONTROL Campaign Workflow HeatMap]**, clique no botão **[!UICONTROL Filters]**.
1. Defina a duração como 1 hora.

   ![](assets/wkf_monitoring_long_duration.png)

1. Inclua mais resultados diminuindo o filtro **[!UICONTROL Min duration]**.
1. Explore os resultados para encontrar os fluxos de trabalho mais longos, que podem potencialmente ter mais impacto nos recursos do servidor e do banco de dados (CPU, RAM, rede, IOPS etc.).
1. Execute as ações apropriadas:

   * Aconselhe os usuários de marketing a dividirem os fluxos de trabalho mais longos para reduzir o tempo de processamento.
   * Inicie uma análise mais profunda de fluxos de trabalho específicos e atividades específicas (como JavaScript, importação, exportação etc.) para isolar os problemas e resolvê-los com mais facilidade.

## Usar o HeatMap para aprimorar o planejamento do fluxo de trabalho {#example--using-the-heatmap-to-improve-workflow-planning}

O exemplo abaixo mostra como o planejamento pode ser mais eficiente e como o desempenho pode ser melhorado ao usar o Adobe Campaign Workflow HeatMap.

Nesse caso, muitos usuários estão reclamando do desempenho do fluxo de trabalho. Você precisa verificar o que está atrasando a atividade e como resolver o problema.

1. Vá para **[!UICONTROL Monitoring]** e clique no link **[!UICONTROL Workflows]** para exibir a página **[!UICONTROL Campaign Workflow HeatMap]**.
1. Defina o filtro **[!UICONTROL Min duration]** como 5 minutos.
1. Defina o filtro **[!UICONTROL Workflow type]** como **[!UICONTROL Marketing]**.
1. Na grade do HeatMap, observe o seguinte:

   ![](assets/wkf_monitoring_without.png)

   * Cinquenta fluxos de trabalho da campanha de longa duração (mais de 5 minutos) estão sendo executados às 10h.
   * A maioria deles tem um estado pendente (por padrão, o limite de simultaneidade é definido como 20).
   * Os fluxos de trabalho pendentes precisam ser reiniciados manualmente todos os dias.
   * O desempenho está baixo.

1. Em vez de ter cinquenta fluxos de trabalho começando às 10h, distribua os horários de início dos fluxos de trabalho uniformemente pelo resto do dia.
1. Volte para a página **[!UICONTROL Campaign Workflow HeatMap]** e clique no botão **[!UICONTROL Reload data]**.
1. Agora observe o seguinte:

   ![](assets/wkf_monitoring_with.png)

   * Apenas dezoito fluxos de trabalho da campanha de longa duração ainda estão em execução às 10h.
   * Não há mais fluxos de trabalho em estado pendente (o limite de simultaneidade ainda está definido como 20).
   * Os horários de início do fluxo de trabalho são distribuídos uniformemente ao longo do dia.
   * Não há mais usuários que se queixam de problemas de desempenho.
