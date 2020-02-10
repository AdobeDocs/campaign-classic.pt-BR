---
title: Configuração de campanhas de marketing
seo-title: Configuração de campanhas de marketing
description: Configuração de campanhas de marketing
seo-description: null
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Configuração de campanhas de marketing{#setting-up-marketing-campaigns}

As campanhas incluem ações (deliveries) e processos (importação ou extração de arquivos), além de recursos (documentos de marketing e delivery outlines). Eles são usados em campanhas de marketing. As campanhas são parte de um programa e os programas são incluídos em um plano de campanha.

Para criar uma campanha de marketing:

1. Crie uma campanha: campanhas de descoberta e suas características: etiqueta, tipo, datas de início e término, orçamento, recursos associados, gerentes e participantes.

   Consulte [Criação de uma campanha](#creating-a-campaign).

1. Definir população alvo: crie um fluxo de trabalho com consultas de definição de metas.

   See [Selecting the target population](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population).

1. Criar entregas: selecione os canais e defina o conteúdo a ser enviado.

   Consulte [Criação de entregas](../../campaign/using/marketing-campaign-deliveries.md#creating-deliveries).

1. Aprovar entregas.

   Consulte o processo [de](../../campaign/using/marketing-campaign-approval.md#approval-process)aprovação.

1. Monitore entregas.

   Consulte [Monitoramento](../../campaign/using/marketing-campaign-monitoring.md).

1. Planeje campanhas e custos associados.

   See [Creating service providers and their cost structures](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

When these steps have been completed, you can start the deliveries (see [Starting a delivery](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)), check the data, processes and information relating to the deliveries and, if necessary, manage the associated documents (see [Managing associated documents](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)). You can also track the execution of the processing phases of campaigns and deliveries (see [Tracking](../../campaign/using/marketing-campaign-monitoring.md).

## Criação de plano e programa de hierarquia {#creating-plan-and-program-hierarchy}

Para configurar sua hierarquia de pastas para planos e programas de marketing:

1. Clique no ícone do **Explorer** na home page.
1. Clique com o botão direito na pasta em que deseja criar o plano.
1. Selecione **Add new folder > Campaign Management > Plan**.

   ![](assets/create_plan_1.png)

1. Renomeie o plano.
1. Clique com o botão direito do mouse no plano recém-criado e selecione **Properties...**.

   ![](assets/create_plan_2.png)

1. Na guia **General** , modifique o **nome interno** para evitar duplicidades durante exportações de pacote.
1. Clique em **Save**.
1. Clique com o botão direito do mouse no plano recém-criado e selecione **Create a new &#39;Program&#39; folder**.
1. Repita as etapas acima para renomear a nova pasta do programa e seu nome interno.

## Criação de uma campanha {#creating-a-campaign}

### Adicionar uma campanha {#adding-a-campaign}

Você pode criar uma campanha através da lista de campanhas. Para exibir essa exibição, selecione o **[!UICONTROL Campaigns]** menu no **[!UICONTROL Campaigns]** painel.

![](assets/s_ncs_user_add_an_op_from_list.png)

The **[!UICONTROL Program]** field lets you select the program to which the campaign will be attached. Essas informações são obrigatórias.

![](assets/s_ncs_user_new_op_wz_a.png)

As campanhas também podem ser criadas por meio de um programa. To do this, click the **[!UICONTROL Add]** button in the **[!UICONTROL Schedule]** tab of the concerned program.

![](assets/s_ncs_user_add_an_op.png)

When you create a campaign via the **[!UICONTROL Schedule]** tab of a program, the campaign is automatically linked to the concerned program. The **[!UICONTROL Program]** field is hidden in this case.

Na janela de criação da campanha, selecione o modelo da campanha e adicione um nome e uma descrição da campanha. Você também pode especificar as datas de início e término da campanha.

Clique em **[!UICONTROL OK]** para criar a campanha. Ela será adicionada ao cronograma do programa.

![](assets/s_ncs_user_program_planning_with_op.png)

>[!NOTE]
>
>To filter the campaigns to display, click the **[!UICONTROL Filter]** link and select the status of campaigns to display.

![](assets/s_ncs_user_program_planning_filter.png)

### Editar e configurar uma campanha {#editing-and-configuring-a-campaign}

Você pode editar a campanha que acabou de criar e definir seus parâmetros.

To open and configure a campaign, select it from the schedule and click **[!UICONTROL Open]**.

![](assets/s_ncs_user_new_op_edit.png)

Você será direcionado ao painel de campanha.

## Campanhas recorrentes e periódicas {#recurring-and-periodic-campaigns}

Uma campanha recorrente é uma campanha baseada em um template específico, cujos workflows são configurados para serem executados de acordo com um agendamento associado. Portanto, os workflows serão recorrentes dentro de uma campanha. O direcionamento é duplicado em cada execução e os vários processos e populações do target são rastreados. Também é possível executar os direcionamentos antecipadamente, por meio do período de cobertura durante a criação automática de workflow, para iniciar simulações com estimativas de destino.

Uma campanha periódica é uma campanha criada automaticamente de acordo com o agendamento de execução de seu template.

### Criar uma campanha recorrente {#creating-a-recurring-campaign}

As campanhas recorrentes são criadas a partir de um template específico que define o template de workflow a ser executado e o agendamento de execução.

#### Criação de um modelo para campanhas recorrentes {#creating-the-campaign-template}

1. Crie um modelo de **[!UICONTROL Recurring]** campanha.

   >[!NOTE]
   >
   >Recomenda-se duplicar o template padrão em vez de criar um template vazio.

   ![](assets/s_ncs_user_op_template_recur_tab.png)

1. Insira o nome do template e a duração da campanha.

   ![](assets/s_ncs_user_op_template_recur_duplicate.png)

1. For this type of campaign, a **[!UICONTROL Schedule]** tab is added in order to create the template execution schedule.

Nesta guia, especifique as datas de execução planejadas das campanhas com base neste template.

![](assets/s_ncs_user_op_template_recur_planning.png)

Você pode usar o assistente de criação de agendamento para preencher todas as datas de execução automaticamente. To do this, click the **[!UICONTROL Complete the execution schedule...]** link located above the table.

![](assets/s_ncs_user_op_template_recur_planning_wz.png)

The configuration mode of the execution schedule coincides with the **[!UICONTROL Scheduler]** object of the Workflow. Para obter mais informações, consulte [esta seção](../../workflow/using/executing-a-workflow.md#architecture).

>[!CAUTION]
>
>A configuração do agendamento de execução deve ser realizada cuidadosamente para evitar sobrecarga do banco de dados. As campanhas recorrentes duplicam o(s) fluxo(s) de trabalho de seu template dependendo do cronograma especificado. A implementação da criação de workflow excessivamente frequente pode dificultar a operação do banco de dados.

1. Specify a value in the **[!UICONTROL Create in advance for]** field in order to create the corresponding workflows for the period indicated.
1. Crie o template de workflow a ser usado em campanhas com base nesse template, com os parâmetros de definição de metas e uma ou mais remessas genéricas.

   >[!CAUTION]
   >
   >Esse workflow deve ser salvo como um template de workflow recorrente. To do this, edit the workflow properties and select the **[!UICONTROL Recurring workflow template]** option in the **[!UICONTROL Execution]** tab.

   ![](assets/s_ncs_user_op_template_recur_wf_option.png)

#### Criar a campanha recorrente {#create-the-recurring-campaign}

Para criar a campanha recorrente e executar os workflows de acordo com o agendamento definido no template, aplique o seguinte procedimento:

1. Crie uma nova campanha com base em um template de campanha recorrente.
1. Preencha o agendamento de execução do workflow.

   ![](assets/s_ncs_user_op_recur_planning.png)

1. O agendamento da campanha permite que você insira uma data de início ou execução automática de workflow para cada linha.

   Para cada linha, você pode adicionar as seguintes opções adicionais:

   * **[!UICONTROL To be approved]** : permite forçar as solicitações de aprovação de entrega no fluxo de trabalho
   * **[!UICONTROL To be started]** : permite que você inicie o fluxo de trabalho quando a data inicial for atingida.
   The **[!UICONTROL Create in advance for]** field lets you create all the workflows covering the period entered.

   Upon execution of the **[!UICONTROL Jobs on campaigns]** workflow, the dedicated workflows are created based on the occurrences defined in the campaign schedule. Um workflow é criado para cada data de execução.

1. Os workflows recorrentes são criados automaticamente a partir do template de workflow presente na campanha. They are visible from the **[!UICONTROL Targeting and workflows]** tab of the campaign.

   ![](assets/s_ncs_user_op_recur_planning_wfs.png)

   O rótulo de uma instância de workflow recorrente consiste no rótulo do seu template e no número do workflow, sendo que entre eles há o caractere &quot;#&quot;.

   Workflows created from the schedule are automatically associated with it in the **[!UICONTROL Workflow]** column of the **[!UICONTROL Schedule]** tab.

   ![](assets/s_ncs_user_op_recur_planning_wfs_1.png)

   Cada workflow pode ser editado desta guia.

   ![](assets/s_ncs_user_op_recur_planning_wf_edit.png)

   >[!NOTE]
   >
   >A data de início da linha de agendamento associada ao workflow está disponível em uma variável do workflow com a seguinte sintaxe:\
   >`$date(instance/vars/@startPlanningDate)`

### Criar uma campanha periódica {#creating-a-periodic-campaign}

Uma campanha periódica é uma campanha baseada em um template específico que permite criar instâncias de campanha com base em um agendamento de execução. As instâncias de campanha são criadas automaticamente com base em um template de campanha periódico, dependendo da frequência definida no cronograma do template.

#### Criar o template de campanha {#creating-the-campaign-template-1}

1. Create a **[!UICONTROL Periodic]** campaign template, preferably by duplicating an existing campaign template.

   ![](assets/s_ncs_user_op_template_period_create.png)

1. Digite as propriedades do template.

   >[!CAUTION]
   >
   >O operador que o template está atribuído precisa ter os direitos apropriados para criar campanhas no programa selecionado.

1. Crie o workflow associado a este template. Ele será duplicado em cada campanha periódica criada pelo template.

   ![](assets/s_ncs_user_op_template_period_wf.png)

   >[!NOTE]
   >
   >Este workflow é um template de workflow. Ele não pode ser executado do template de campanha.

1. Complete its execution schedule as for a recurring campaign template: click the **[!UICONTROL Add]** button and define the start and end dates, or fill in the execution schedule via the link.

   ![](assets/s_ncs_user_op_template_period_planning_add.png)

   >[!CAUTION]
   >
   >Os templates de campanha periódicos criam novas campanhas de acordo com o agendamento definido acima. Portanto, deve ser concluída com cuidado, para evitar sobrecarga do banco de dados do Adobe Campaign.

1. Quando a data de início da execução for atingida, a campanha correspondente será criada automaticamente. Leva em conta todas as características do template.

   Cada campanha pode ser editada por meio do agendamento do template.

   ![](assets/s_ncs_user_op_template_period_planning.png)

Cada campanha periódica contém os mesmos elementos. Uma vez criado, ele é gerenciado como uma campanha padrão.
