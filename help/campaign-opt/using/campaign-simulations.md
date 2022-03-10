---
product: campaign
title: Simulações de campanha
description: Introdução às simulações de campanha
feature: Campaigns
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: ht
source-wordcount: '1245'
ht-degree: 100%

---

# Simulações de campanha{#campaign-simulations}

![](../../assets/common.svg)

## Sobre simulações {#about-simulations}

A otimização de campanha permite testar a eficiência de um plano de campanha usando simulações. Isso permite medir o sucesso potencial de uma campanha: receita gerada, volume de destino com base nas regras de tipologia aplicadas, etc.

A simulação permite monitorar e comparar o impacto dos deliveries.

>[!NOTE]
>
>Os deliveries preparados no modo Teste não têm impacto entre si ao avaliar uma campanha no marketing distribuído ou contanto que as remessas não estejam programadas no calendário provisional.\
>Isso significa que as regras de pressão e capacidade serão aplicadas apenas aos deliveries no modo **[!UICONTROL Target estimation and message personalization]**. Os deliveries no modo **[!UICONTROL Estimation and approval of the provisional target]** e no **[!UICONTROL Target evaluation]** não são considerados.\
>O modo é escolhido na subguia **[!UICONTROL Typology]** das propriedades do delivery.

![](assets/simu_campaign_select_delivery_mode.png)

## Configurar uma simulação {#setting-up-a-simulation}

### Criar uma simulação {#creating-a-simulation}

Para criar uma simulação, aplique as seguintes etapas:

1. Abra a guia **[!UICONTROL Campaigns]**, clique no link **[!UICONTROL More]** na seção **[!UICONTROL Create]** e selecione a opção **[!UICONTROL Simulation]**.

   ![](assets/simu_campaign_opti_01.png)

1. Insira o template e o nome da simulação. Clique em **[!UICONTROL Save]** para criar a simulação.

   ![](assets/simu_campaign_opti_02.png)

1. Clique na guia **[!UICONTROL Edit]** para configurá-la.

   ![](assets/simu_campaign_opti_edit.png)

1. Na guia **[!UICONTROL Scope]**, especifique os envios que devem ser considerados nessa simulação. Para fazer isso, clique no botão **[!UICONTROL Add]** e especifique o modo de seleção de delivery a ser levado em consideração.

   ![](assets/simu_campaign_opti_edit_scope.png)

   Você pode selecionar cada delivery um por um ou classificá-los por campanha, programa ou plano.

   >[!NOTE]
   >
   >Caso selecione deliveries por meio de um plano, programa ou campanha, o Adobe Campaign poderá atualizar automaticamente a lista de deliveries a serem considerados sempre que uma simulação for iniciada. Para fazer isso, marque a opção **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]**.
   >  
   >Se você não fizer isso, quaisquer deliveries que não estejam disponíveis no plano, programa ou campanha quando a simulação for criada não serão levados em consideração: os deliveries adicionados posteriormente serão ignorados.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Selecione os elementos a serem incluídos no escopo de simulação. Se necessário, selecione vários elementos usando as teclas SHIFT e CTRL.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Clique em **[!UICONTROL Finish]** para aprovar a seleção.

   Você pode combinar manualmente os deliveries selecionados e deliveries pertencentes a planos, programas ou campanhas.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Se necessário, você poderá usar uma condição dinâmica através do link **[!UICONTROL Edit the dynamic condition...]**.

   Clique em **[!UICONTROL Save]** para aprovar essa configuração.

   >[!NOTE]
   >
   >Somente os deliveries cujo objetivo tenha sido calculado são levados em conta no cálculo das simulações (status: **Target ready** ou **Ready to deliver**).

1. Na guia **[!UICONTROL Calculations]**, selecione uma dimensão de análise como, por exemplo, o schema de recipients.

   ![](assets/simu_campaign_opti_dimension.png)

1. Você poderá então adicionar expressões.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Configurações de execução {#execution-settings}

A guia **[!UICONTROL General]** da simulação permite inserir configurações de execução:

* A opção **[!UICONTROL Schedule execution for down-time]** adia o lançamento da simulação para um período menos ocupado, com base no nível escolhido de prioridade. As simulações usam recursos significativos do banco de dados, por isso as simulações não urgentes devem ser agendadas para serem executadas à noite.
* **[!UICONTROL Priority]** é o nível aplicado à simulação para atrasar o acionamento.
* **[!UICONTROL Save SQL queries in the log]**. Os logs em SQL permitem diagnosticar uma simulação se ela terminar com erros. Eles também podem ajudá-lo a descobrir por que uma simulação está muito lenta. Essas mensagens estarão visíveis após a simulação na subguia **[!UICONTROL SQL logs]** da guia **[!UICONTROL Audit]**.

## Executar uma simulação {#executing-a-simulation}

### Iniciar uma simulação {#starting-a-simulation}

Depois que o escopo da simulação for definido, você poderá executá-la.

Para fazer isso, abra o painel de simulação e clique em **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

Uma vez concluída a execução, abra a simulação e clique na guia **[!UICONTROL Results]** para exibir os destinos calculados para cada delivery.

![](assets/simu_campaign_opti_results.png)

1. A subguia **[!UICONTROL Deliveries]** lista todos os deliveries considerados na simulação. Ela mostra duas contagens:

   * **[!UICONTROL Initial count]** é o target como foi calculado durante a estimativa no delivery.
   * **[!UICONTROL Final count]** é o número de recipients contados após a simulação.

      A diferença entre as contagens inicial e final reflete a aplicação de várias regras ou filtros configurados antes da simulação.

      Para saber mais sobre esse cálculo, edite a subguia **[!UICONTROL Exclusions]**.

1. A subguia **[!UICONTROL Exclusions]** permite visualizar a interrupção da exclusão.

   ![](assets/simu_campaign_opti_14.png)

1. A subguia **[!UICONTROL Alerts]** agrupa todas as mensagens de alerta geradas durante a simulação. As mensagens de alerta podem ser enviadas no caso de sobrecarga de capacidade (se o número de recipients exceder a capacidade definida, por exemplo).
1. A subguia **[!UICONTROL Exploration of the exclusions]** permite criar uma tabela de análise de resultado. O usuário precisa indicar variáveis nos eixos abscissa/ordenadas.

   Para um exemplo de criação de tabela de análise, consulte o fim da opção [Exploring results](#exploring-results).

### Exibir resultados {#viewing-results}

#### Auditoria {#audit}

A guia **[!UICONTROL Audit]** permite monitorar a execução da simulação. A subguia **[!UICONTROL SQL Logs]** é útil para usuários avançados. Ela lista logs de execução no formato SQL. Esses logs serão exibidos somente se a opção **[!UICONTROL Save SQL queries in the log]** tiver sido selecionada na guia **[!UICONTROL General]** antes da execução da simulação.

![](assets/simu_campaign_opti_11.png)

#### Explorar resultados {#exploring-results}

A subguia **[!UICONTROL Exploration of the exclusions]** permite analisar os dados resultantes de uma simulação.

A análise descritiva é apresentada [nesta seção](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Resultados de uma simulação {#results-of-a-simulation}

Os indicadores nas guias **[!UICONTROL Log]** e **[!UICONTROL Results]** fornecem uma primeira visão geral dos resultados da simulação. Para obter uma visão mais detalhada dos resultados, abra a guia **[!UICONTROL Reports]**.

### Relatórios {#reports}

Para analisar o resultado de uma simulação, edite os relatórios: eles mostram exclusões e causas.

Os seguintes relatórios são fornecidos como padrão:

* **[!UICONTROL Detail of simulation exclusions]**: esse relatório fornece um gráfico detalhado das causas de exclusão para todos os deliveries relacionados.
* **[!UICONTROL Simulation summary]**: esse relatório mostra as amostragens excluídas da simulação em todos os deliveries.
* **[!UICONTROL Summary of exclusions linked to the simulation]**: esse relatório mostra um gráfico das exclusões causadas pela simulação junto com a regra de tipologia aplicada e um gráfico que mostra a taxa de exclusão por regra.

>[!NOTE]
>
>É possível criar novos relatórios e adicioná-los aos existentes. Para obter mais informações, consulte [esta seção](../../reporting/using/about-adobe-campaign-reporting-tools.md).

Para acessar os relatórios, clique no link **[!UICONTROL Reports]** da simulação direcionada por meio do painel.

![](assets/campaign_opt_reporting_edit_from_board.png)

Também é possível editar os relatórios ao usar o link **[!UICONTROL Reports]** acessível no painel de simulação.

### Comparar simulações {#comparing-simulations-}

Sempre que uma simulação é executada, resultados anteriores são substituídos: não é possível exibir e comparar resultados de uma execução para outra.

É necessário usar os relatórios para comparar os resultados. Na verdade, o Adobe Campaign permite que um histórico de relatórios seja salvo para exibi-los novamente mais tarde. Este histórico é salvo no ciclo de vida das simulações.

**Exemplo:**

1. Crie uma simulação em um delivery ao qual a tipologia **A** é aplicada.
1. Na guia **[!UICONTROL Reports]**, edite um dos relatórios disponíveis, como o **[!UICONTROL Detail of simulation exclusions]**, por exemplo.
1. Na seção superior direita do relatório, clique no ícone para criar um novo histórico.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Feche a simulação e altere a configuração de tipologia **A**.
1. Execute a simulação novamente e compare o resultado com o exibido no relatório para o qual um histórico foi criado.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   Você pode salvar quantos históricos de relatórios forem necessários.

### Relatórios de eixos {#reporting-axes}

A guia **[!UICONTROL Calculations]** permite definir eixos de relatórios no target. Esses eixos serão usados durante a análise de resultados (consulte [Exploração de resultados](#exploring-results)).

>[!NOTE]
>
>Recomendamos definir eixos de cálculo nos templates de simulação, em vez de individualmente para cada simulação.\
>Os modelos de simulação são salvos no nó **[!UICONTROL Resources > Templates > Simulation templates]** da árvore do Adobe Campaign.

**Exemplo:**

No exemplo abaixo, queremos criar um eixo de relatórios adicional com base no status dos recipients (&quot;Cliente&quot;, &quot;Prospecto&quot; ou nenhum).

1. Para definir um eixo de relatórios, selecione a tabela que contém as informações a serem processadas no campo **[!UICONTROL Analysis dimension]**. Essas informações são obrigatórias.
1. Aqui, queremos selecionar o campo Segmento da tabela de recipients.

   ![](assets/simu_campaign_opti_09.png)

1. As seguintes opções estão disponíveis:

   * **[!UICONTROL Generate target overlap statistics]** permite recuperar todas as estatísticas de sobreposição no relatório de simulação. As sobreposições são recipients a quem são direcionadas, no mínimo, dois deliveires em uma simulação.

      >[!IMPORTANT]
      >
      >A seleção dessa opção aumenta consideravelmente o tempo de execução da simulação.

   * **[!UICONTROL Keep the simulation work table]** permite que você mantenha os rastreamentos de simulação.

      >[!IMPORTANT]
      >
      >O salvamento automático dessas tabelas requer uma capacidade de armazenamento significativa: verifique se o banco de dados é grande o suficiente.

Quando os resultados da simulação forem exibidos, as informações sobre a expressão selecionada serão exibidas na subguia **[!UICONTROL Overlaps]**.

A sobreposição do target de delivery indica os recipients pretendidos em pelo menos dois deliveries de uma simulação.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Esta subguia será exibida somente se a opção **[!UICONTROL Generate target recovery statistics]** tiver sido habilitada.

As informações sobre os eixos de relatórios podem ser processadas em relatórios de análise de exclusão criados na subguia **[!UICONTROL Exploring exclusions]**. Para obter mais informações, consulte [Exploração de resultados](#exploring-results).
