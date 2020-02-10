---
title: HeatMap do fluxo de trabalho
seo-title: HeatMap do fluxo de trabalho
description: HeatMap do fluxo de trabalho
seo-description: null
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d6a4d56c595f16f454684b1d6afc7d7323c5914c

---


# HeatMap do fluxo de trabalho {#workflow-heatmap}

O mapa de calor do fluxo de trabalho do Adobe Campaign consiste em uma representação gráfica colorida de todos os fluxos de trabalho que estão sendo executados no momento. Está disponível somente para os administradores da instância.

Outras maneiras de monitorar os diferentes processos do Campaign são apresentadas [nesta página](https://helpx.adobe.com/campaign/kb/acc-maintenance.html).

## Sobre o Workflow HeatMap {#about-the-workflow-heatmap}

Ao fornecer uma visão geral rápida do número de fluxos de trabalho simultâneos, o Workflow HeatMap permite que os administradores da plataforma Adobe Campaign monitorem a carga da instância e planejem os fluxos de trabalho de acordo.

Mais precisamente, ajuda os administradores de plataforma a:

* Ver e entender fluxos de trabalho simultâneos
* Filtrar fluxos de trabalho por duração para ver quais fluxos de trabalho podem encontrar problemas
* Filtrar atividades por duração para ver quais atividades podem encontrar problemas
* Encontre facilmente fluxos de trabalho individuais e todas as atividades relacionadas (com sua duração)
* Pesquisar por tipo de fluxo de trabalho (fluxos de trabalho[](../../workflow/using/building-a-workflow.md#technical-workflows) técnicos ou fluxos de trabalho [de](../../workflow/using/building-a-workflow.md#campaign-workflows)campanha)
* Procure um fluxo de trabalho específico para analisar

>[!NOTE]
>
>Além do mapa de calor do **fluxo de trabalho**, você pode criar um fluxo de trabalho que permitirá monitorar o status de um conjunto de fluxos de trabalho e enviar mensagens recorrentes aos supervisores. Para obter mais informações, consulte a [seção dedicada](../../workflow/using/supervising-workflows.md).

O uso do Workflow HeatMap requer uma boa compreensão dos seguintes conceitos: [Fluxos](../../workflow/using/about-workflows.md)de trabalho, [Atividades](../../workflow/using/about-activities.md) e Práticas [recomendadas](../../workflow/using/workflow-best-practices.md)de fluxo de trabalho.

O Workflow HeatMap está disponível por padrão no Adobe Campaign a partir da versão 18.10. Se você tiver um build entre 8700 e 8977 (18.10), também poderá se beneficiar desse recurso. Para solicitar o pacote correspondente, entre em contato com o Atendimento [ao cliente da](https://support.neolane.net/) Adobe e siga as instruções [desta página](https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html) para entender como instalá-lo.

Quando você acessa pela primeira vez o Worfklow HeatMap, a seguinte janela pop-up será exibida. Este contrato permite a transferência e o armazenamento nos Estados Unidos, permitindo que o Adobe Campaign:

* monitore as instâncias para investigar quaisquer problemas de desempenho.
* coletar dados para detecção de anomalias.

Observe que a transferência de seus dados só está disponível para usuários que se conectam ao Adobe Campaign usando sua Adobe ID.

![](assets/wf_monitoring_agreement.png)

Três opções estão disponíveis:

* **[!UICONTROL Accept]** : Ao aceitar este contrato, você autoriza o Adobe Campaign a coletar seus dados e a transferi-los para os Estados Unidos para ajudá-lo no caso de detecções de anomalias.
* **[!UICONTROL Refuse]** : Ao recusar o contrato, seus dados não serão transferidos, mas você ainda poderá usar o Mapa de calor do fluxo de trabalho.
* **[!UICONTROL Do not show this message again]** : Ao clicar em **[!UICONTROL Do not show this message again]** , a janela pop-up parará de ser exibida ao acessar o mapa de calor do fluxo de trabalho, mas ainda estará disponível no **[!UICONTROL Term of use]** botão.

Essa opção não é final, você sempre pode alterá-la clicando no **[!UICONTROL Term of use]** botão.

## Uso do HeatMap {#using-the-heatmap}

>[!NOTE]
>
>Somente usuários com direitos administrativos podem acessar o Mapa de calor do fluxo de trabalho da campanha.

1. Vá para **[!UICONTROL Monitoring]** e clique no **[!UICONTROL Workflow HeatMap]** link para exibir a **[!UICONTROL Campaign Workflow HeatMap]** página.

   ![](assets/wkf_monitoring_path.png)

1. Clique no calendário para selecionar um dia.

   Por padrão, a página mostra a atividade do fluxo de trabalho do dia atual. Você pode alterá-la e selecionar qualquer dia no passado.

   >[!NOTE]
   >
   >Somente os fluxos de trabalho que não foram excluídos pelo **[!UICONTROL Database cleanup]** fluxo de trabalho ficam visíveis. For more on the Database cleanup workflow, refer to [this section](../../production/using/database-cleanup-workflow.md).\
   >Por padrão, o fuso horário do Workflow HeatMap é aquele definido para o usuário administrador atual. Por exemplo, talvez você queira alterá-la se não estiver na mesma área dos usuários de marketing com os quais você está trabalhando.

1. Clique no botão **[!UICONTROL Filters]**.

   ![](assets/wkf_monitoring_filters.png)

1. Use o controle deslizante para definir a duração mínima de 0 segundo a 1 hora. Isso permite pesquisar somente os fluxos de trabalho em execução por mais de um determinado número de segundos ou minutos.

   ![](assets/wkf_monitoring_filters_duration.png)

1. Você também pode escolher um fluxo de trabalho específico na **[!UICONTROL Workflows]** lista.

   ![](assets/wkf_monitoring_filters_workflows.png)

   >[!NOTE]
   >
   >O **[!UICONTROL Min duration]** filtro é aplicado. Se não conseguir encontrar um fluxo de trabalho específico, redefina a duração mínima para 0 para que todos os fluxos de trabalho sejam exibidos na lista.

1. Você também pode filtrar no **[!UICONTROL Workflow type]** :

   * **[!UICONTROL Technical]** : Somente fluxos de trabalho [técnicos](../../workflow/using/building-a-workflow.md#technical-workflows) prontos e fluxos de trabalho [de gerenciamento de](../../workflow/using/targeting-data.md#data-management) dados são exibidos.
   * **[!UICONTROL Marketing]** : Somente os fluxos de trabalho vinculados a uma campanha de marketing, conhecidos como fluxos de trabalho [de](../../workflow/using/building-a-workflow.md#campaign-workflows)campanha, são exibidos.

1. Para pesquisar um fluxo de trabalho específico por nome, você também pode usar o **[!UICONTROL Workflow name filter]** campo.

   ![](assets/wkf_monitoring_filters_name.png)

1. Se você editou alguns fluxos de trabalho no intervalo, clique no **[!UICONTROL Reload data]** botão para atualizar os dados exibidos na grade.

## Lendo o HeatMap {#reading-the-heatmap}

O mapa de calor do fluxo de trabalho da campanha é uma grade naturalmente legível do canto superior esquerdo ao inferior direito, permitindo encontrar as &quot;zonas ativas&quot; com um intervalo de cores verde a vermelho.

* As células vermelhas mais escuras correspondem a períodos em que um número alto de fluxos de trabalho está sendo executado ao mesmo tempo.
* As células cinza correspondem a períodos em que nenhum fluxo de trabalho está em execução.

Para saber como o código de cor é aplicado e como navegar no HeatMap, clique no **[!UICONTROL Help]** botão.

![](assets/wkf_monitoring_legend.png)

Cada linha representa uma hora do dia e cada célula representa 5 minutos dessa hora.

A grade mostra todos os fluxos de trabalho que estão sendo executados ao mesmo tempo para cada um desses períodos de 5 minutos.

No exemplo abaixo, entre 8am e 8h05 da manhã, três fluxos de trabalho estão em execução (independentemente da duração individual):

![](assets/wkf_monitoring_ex_8am.png)

1. Clique em uma célula colorida para exibir os detalhes de todos os fluxos de trabalho simultâneos em execução durante esse período.

   ![](assets/wkf_monitoring_details.png)

   Para cada fluxo de trabalho, todas as atividades que ele contém são listadas, com sua duração.

1. Clique na ID ou no nome do fluxo de trabalho para abrir diretamente um fluxo de trabalho.
1. Para voltar à **[!UICONTROL Campaign Workflow HeatMap]** exibição, clique no **[!UICONTROL Home]** botão.

## Casos de uso: usar o HeatMap para executar ações {#use-cases--using-the-heatmap-to-take-actions}

Há dois casos principais em que o Mapa de atividade do fluxo de trabalho da campanha pode ser útil.

### Redução do número de fluxos de trabalho simultâneos {#reducing-the-number-of-concurrent-workflows}

Como administrador da Campanha, o Workflow HeatMap pode ajudá-lo a entender a carga na instância e planejar fluxos de trabalho novos ou existentes em momentos apropriados.

1. Na **[!UICONTROL Campaign Workflow HeatMap]** exibição, clique no **[!UICONTROL Filters]** botão.
1. Defina a duração para alguns segundos ou alguns minutos.
1. Exclua os fluxos de trabalho mais curtos que não são significativos ao aumentar o filtro de duração.

   ![](assets/wkf_monitoring_short_duration.png)

1. Explore os resultados para entender a carga na instância e execute as ações apropriadas:

   * Se você encontrar problemas de desempenho e se uma ou mais células vermelhas forem exibidas na grade, considere alterar a hora de início de vários fluxos de trabalho. Solicite aos usuários de marketing que movam fluxos de trabalho manualmente de períodos ocupados (&quot;quentes&quot;) para períodos de tempo mais disponíveis. Isso deve manter um nível estável de atividade ao longo do dia.
   * Para evitar picos e a sobrecarga da instância, verifique o HeatMap antes de planejar novos fluxos de trabalho e escolha o melhor momento. Considere os intervalos de tempo correspondentes às células cinza ou verde na grade para iniciar novos fluxos de trabalho.

### Encontrar fluxos de trabalho de longa duração que afetam o desempenho {#finding-long-running-workflows-that-impact-performance}

Como administrador da Campanha, o Workflow HeatMap ajuda a encontrar os fluxos de trabalho mais longos que podem retardar a atividade.

1. Na **[!UICONTROL Campaign Workflow HeatMap]** exibição, clique no **[!UICONTROL Filters]** botão.
1. Defina a duração como 1 hora.

   ![](assets/wkf_monitoring_long_duration.png)

1. Inclua mais resultados diminuindo o **[!UICONTROL Min duration]** filtro.
1. Explore os resultados para encontrar os fluxos de trabalho mais longos, que podem potencialmente ter mais impacto nos recursos do servidor e do banco de dados (CPU, RAM, rede, IOPS etc.).
1. Execute as ações apropriadas:

   * Aconselhe os usuários de marketing a dividirem os fluxos de trabalho mais longos para reduzir o tempo de processamento.
   * Inicie uma análise mais profunda de fluxos de trabalho específicos e atividades específicas (como JavaScript, importação, exportação etc.) para isolar os problemas e resolvê-los com mais facilidade.

## Exemplo: Usar o HeatMap para melhorar o planejamento do fluxo de trabalho {#example--using-the-heatmap-to-improve-workflow-planning}

O exemplo abaixo mostra como o planejamento pode ser mais eficiente e como o desempenho pode ser melhorado ao usar o Mapa de calor do fluxo de trabalho do Adobe Campaign.

Nesse caso, muitos usuários estão reclamando do desempenho do fluxo de trabalho. Você precisa verificar o que está atrasando a atividade e como resolver o problema.

1. Vá para **[!UICONTROL Monitoring]** e clique no **[!UICONTROL Workflows]** link para exibir a **[!UICONTROL Campaign Workflow HeatMap]** página.
1. Defina o **[!UICONTROL Min duration]** filtro para 5 minutos.
1. Defina o **[!UICONTROL Workflow type]** filtro como **[!UICONTROL Marketing]** .
1. Na grade HeatMap, observe o seguinte:

   ![](assets/wkf_monitoring_without.png)

   * Cinquenta fluxos de trabalho de campanha de longa duração (mais de 5 minutos) estão sendo executados às 10h.
   * A maioria deles tem um estado pendente (por padrão, o limite de simultaneidade é definido como 20).
   * Os fluxos de trabalho pendentes precisam ser reiniciados manualmente todos os dias.
   * O desempenho é baixo.

1. Em vez de ter cinquenta fluxos de trabalho começando às 10h, distribua os horários de início dos fluxos de trabalho uniformemente pelo resto do dia.
1. Volte para a **[!UICONTROL Campaign Workflow HeatMap]** página e clique no **[!UICONTROL Reload data]** botão.
1. Agora observe o seguinte:

   ![](assets/wkf_monitoring_with.png)

   * Apenas dezoito fluxos de trabalho de campanha de longa duração ainda estão em execução às 10h00.
   * Não há mais fluxos de trabalho em estado pendente (o limite de simultaneidade ainda está definido como 20).
   * Os horários de início do fluxo de trabalho são distribuídos uniformemente ao longo do dia.
   * Não há mais usuários que se queixam de problemas de desempenho.
