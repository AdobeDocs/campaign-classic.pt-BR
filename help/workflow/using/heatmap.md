---
solution: Campaign Classic
product: campaign
title: Workflow HeatMap
description: Monitore seus workflows do Campaign com o Workflow HeatMap
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1333'
ht-degree: 100%

---


# Workflow HeatMap {#workflow-heatmap}

O Workflow HeatMap do Adobe Campaign consiste em uma representação gráfica colorida de todos os workflows que estão sendo executados no momento. Está disponível somente para os administradores da instância.

Outras maneiras de monitorar os diferentes processos do Campaign são apresentadas [nesta página](../../production/using/monitoring-guidelines.md).

## Sobre o Workflow HeatMap {#about-the-workflow-heatmap}

Ao fornecer uma visão geral rápida do número de workflows simultâneos, o Workflow HeatMap permite que os administradores da plataforma Adobe Campaign monitorem a carga da instância e planejem os workflows de acordo.

Mais precisamente, ajuda os administradores de plataforma a:

* Ver e entender workflows simultâneos
* Filtrar workflows por duração para ver quais workflows podem encontrar problemas
* Filtrar atividades por duração para ver quais atividades podem encontrar problemas
* Encontre facilmente workflows individuais e todas as atividades relacionadas (com sua duração)
* Pesquisar por tipo de workflow ([technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows) ou [campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows))
* Procure um workflow específico para analisar

>[!NOTE]
>
>Além do **Workflow Heatmap**, é possível criar um workflow que permitirá monitorar o status de um conjunto de workflows e enviar mensagens recorrentes aos supervisores. Para obter mais informações, consulte a [seção dedicada](../../workflow/using/supervising-workflows.md).

O uso do Workflow HeatMap requer uma boa compreensão dos seguintes conceitos: [workflows](../../workflow/using/about-workflows.md), [atividades](../../workflow/using/about-activities.md) e [práticas recomendadas de workflow](../../workflow/using/workflow-best-practices.md).

O Workflow HeatMap está disponível por padrão no Adobe Campaign a partir da versão 18.10. Se você tiver uma build entre 8700 e 8977 (18.10), também poderá se beneficiar desse recurso. Para solicitar o pacote correspondente, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) e siga as instruções [desta página](https://helpx.adobe.com/br/campaign/kb/install-workflow-heatmap-package.html) para entender como instalá-lo.

Quando você acessa o Worfklow HeatMap pela primeira vez, a seguinte janela pop-up será exibida. Este contrato permite a transferência e o armazenamento nos Estados Unidos, permitindo que o Adobe Campaign:

* monitore as instâncias para investigar quaisquer problemas de desempenho.
* colete dados para detecção de anomalias.

Observe que a transferência de seus dados só está disponível para usuários que se conectam ao Adobe Campaign usando a Adobe ID.

![](assets/wf_monitoring_agreement.png)

Três opções estão disponíveis:

* **[!UICONTROL Accept]** : ao aceitar este contrato, você autoriza o Adobe Campaign a coletar seus dados e a transferi-los para os Estados Unidos para que você possa receber ajuda no caso de detecções de anomalias.
* **[!UICONTROL Refuse]** : ao recusar o contrato, seus dados não serão transferidos, mas você ainda poderá usar o Workflow Heatmap.
* **[!UICONTROL Do not show this message again]** : ao clicar em **[!UICONTROL Do not show this message again]**, a janela pop-up deixará de ser exibida quando você acessar o Workflow Heatmap, mas ainda estará disponível no botão **[!UICONTROL Term of use]**.

Essa opção não é definitiva, você sempre pode alterá-la clicando no botão **[!UICONTROL Term of use]**.

## Uso do HeatMap {#using-the-heatmap}

>[!NOTE]
>
>Somente usuários com direitos administrativos podem acessar o Campaign Workflow HeatMap.

1. Vá para **[!UICONTROL Monitoring]** e clique no link **[!UICONTROL Workflow HeatMap]** para exibir a página **[!UICONTROL Campaign Workflow HeatMap]**.

   ![](assets/wkf_monitoring_path.png)

1. Clique no calendário para selecionar um dia.

   Por padrão, a página mostra a atividade do workflow do dia atual. Você pode alterá-la e selecionar qualquer dia no passado.

   >[!NOTE]
   >
   >Somente os workflows que não foram excluídos pelo workflow do **[!UICONTROL Database cleanup]** ficam visíveis. Para obter mais informações sobre o workflow de limpeza de banco de dados, consulte [esta seção](../../production/using/database-cleanup-workflow.md).\
   >Por padrão, o fuso horário do Workflow HeatMap é aquele definido para o usuário administrador atual. Por exemplo, talvez você queira alterá-la se não estiver na mesma área dos usuários de marketing com os quais você está trabalhando.

1. Clique no botão **[!UICONTROL Filters]**.

   ![](assets/wkf_monitoring_filters.png)

1. Use o controle deslizante para definir a duração mínima de 0 segundo a 1 hora. Isso permite pesquisar somente os workflows em execução por mais de um determinado número de segundos ou minutos.

   ![](assets/wkf_monitoring_filters_duration.png)

1. Você também pode escolher um workflow específico na lista **[!UICONTROL Workflows]**.

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >O filtro **[!UICONTROL Min duration]** é aplicado. Se não conseguir encontrar um workflow específico, redefina a duração mínima para 0 para que todos os workflows sejam exibidos na lista.

1. Também é possível filtrar no campo **[!UICONTROL Workflow type]**:

   * **[!UICONTROL Technical]**: somente [workflows técnicos prontos](../../workflow/using/building-a-workflow.md#technical-workflows) e [workflows de gerenciamento de dados](../../workflow/using/targeting-data.md#data-management) são exibidos.
   * **[!UICONTROL Marketing]**: somente os workflows vinculados a uma campanha de marketing, conhecidos como [workflows da campanha](../../workflow/using/building-a-workflow.md#campaign-workflows), são exibidos.

1. Para pesquisar um workflow específico por nome, também é possível usar o campo **[!UICONTROL Workflow name filter]**.

   ![](assets/wkf_monitoring_filters_name.png)

1. Se você editou alguns workflows no intervalo de tempo, clique no botão **[!UICONTROL Reload data]** para atualizar os dados exibidos na grade.

## Leitura do HeatMap {#reading-the-heatmap}

O Campaign Workflow HeatMap é uma grade naturalmente legível do canto superior esquerdo ao inferior direito, permitindo encontrar as &quot;zonas ativas&quot; com um intervalo de cores verde a vermelho.

* As células vermelhas mais escuras correspondem a períodos em que um número alto de workflows está sendo executado ao mesmo tempo.
* As células cinza correspondem a períodos em que nenhum workflow está em execução.

Para saber como o código de cor é aplicado e como navegar no HeatMap, clique no botão **[!UICONTROL Help]**.

![](assets/wkf_monitoring_legend.png)

Cada linha representa uma hora do dia e cada célula representa 5 minutos dessa hora.

A grade mostra todos os workflows que estão sendo executados ao mesmo tempo para cada um desses períodos de 5 minutos.

No exemplo abaixo, entre as 8h e a 8h05 da manhã, três workflows estão em execução (independentemente da duração individual):

![](assets/wkf_monitoring_ex_8am.png)

1. Clique em uma célula colorida para exibir os detalhes de todos os workflows simultâneos em execução durante esse período.

   ![](assets/wkf_monitoring_details.png)

   Para cada workflow, todas as atividades que ele contém são listadas, com sua duração.

1. Clique na ID ou no nome do workflow para abri-lo diretamente.
1. Para voltar para a exibição do **[!UICONTROL Campaign Workflow HeatMap]**, clique no botão **[!UICONTROL Home]**.

## Casos de uso: usar o HeatMap para executar ações {#use-cases--using-the-heatmap-to-take-actions}

Há dois casos principais em que o Campaign Workflow HeatMap pode ser útil.

### Redução do número de workflows simultâneos {#reducing-the-number-of-concurrent-workflows}

Como administrador do Campaign, o Workflow HeatMap pode ajudá-lo a entender a carga na instância e planejar workflows novos ou existentes em momentos apropriados.

1. Na exibição do **[!UICONTROL Campaign Workflow HeatMap]**, clique no botão **[!UICONTROL Filters]**.
1. Defina a duração para alguns segundos ou alguns minutos.
1. Aumente o filtro de duração para excluir os workflows mais curtos que não são significativos.

   ![](assets/wkf_monitoring_short_duration.png)

1. Explore os resultados para entender a carga na instância e execute as ações apropriadas:

   * Se você encontrar problemas de desempenho e se uma ou mais células vermelhas forem exibidas na grade, considere alterar a hora de início de vários workflows. Solicite aos usuários de marketing que movam workflows manualmente de períodos ocupados (&quot;ativos&quot;) para períodos mais disponíveis. Isso deve manter um nível estável de atividade ao longo do dia.
   * Para evitar picos e a sobrecarga da instância, verifique o HeatMap antes de planejar novos workflows e escolha o melhor momento. Considere os intervalos de tempo correspondentes às células cinza ou verde na grade para iniciar novos workflows.

### Encontrar workflows de longa duração que afetam o desempenho {#finding-long-running-workflows-that-impact-performance}

Como administrador do Campaign, o Workflow HeatMap ajuda a encontrar os workflows mais longos que podem retardar a atividade.

1. Na exibição do **[!UICONTROL Campaign Workflow HeatMap]**, clique no botão **[!UICONTROL Filters]**.
1. Defina a duração como 1 hora.

   ![](assets/wkf_monitoring_long_duration.png)

1. Inclua mais resultados diminuindo o filtro **[!UICONTROL Min duration]**.
1. Explore os resultados para encontrar os workflows mais longos, que podem potencialmente ter mais impacto nos recursos do servidor e do banco de dados (CPU, RAM, rede, IOPS etc.).
1. Execute as ações apropriadas:

   * Aconselhe os usuários de marketing a dividirem os workflows mais longos para reduzir o tempo de processamento.
   * Inicie uma análise mais profunda de workflows específicos e atividades específicas (como JavaScript, importação, exportação etc.) para isolar os problemas e resolvê-los com mais facilidade.

## Exemplo: usar o HeatMap para melhorar o planejamento do workflow {#example--using-the-heatmap-to-improve-workflow-planning}

O exemplo abaixo mostra como o planejamento pode ser mais eficiente e como o desempenho pode ser melhorado ao usar o Adobe Campaign Workflow HeatMap.

Nesse caso, muitos usuários estão reclamando do desempenho do workflow. Você precisa verificar o que está atrasando a atividade e como resolver o problema.

1. Vá para **[!UICONTROL Monitoring]** e clique no link **[!UICONTROL Workflows]** para exibir a página **[!UICONTROL Campaign Workflow HeatMap]**.
1. Defina o filtro **[!UICONTROL Min duration]** como 5 minutos.
1. Defina o filtro **[!UICONTROL Workflow type]** como **[!UICONTROL Marketing]**.
1. Na grade do HeatMap, observe o seguinte:

   ![](assets/wkf_monitoring_without.png)

   * Cinquenta workflows da campanha de longa duração (mais de 5 minutos) estão sendo executados às 10h.
   * A maioria deles tem um estado pendente (por padrão, o limite de simultaneidade é definido como 20).
   * Os workflows pendentes precisam ser reiniciados manualmente todos os dias.
   * O desempenho está baixo.

1. Em vez de ter cinquenta workflows começando às 10h, distribua os horários de início dos workflows uniformemente pelo resto do dia.
1. Volte para a página **[!UICONTROL Campaign Workflow HeatMap]** e clique no botão **[!UICONTROL Reload data]**.
1. Agora observe o seguinte:

   ![](assets/wkf_monitoring_with.png)

   * Apenas dezoito workflows da campanha de longa duração ainda estão em execução às 10h.
   * Não há mais workflows em estado pendente (o limite de simultaneidade ainda está definido como 20).
   * Os horários de início do workflow são distribuídos uniformemente ao longo do dia.
   * Não há mais usuários que se queixam de problemas de desempenho.
