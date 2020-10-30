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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '1227'
ht-degree: 100%

---


# Configuração de campanhas de marketing{#setting-up-marketing-campaigns}

As campanhas incluem ações (deliveries) e processos (importação ou extração de arquivos), além de recursos (documentos de marketing e delivery outlines). Eles são usados em campanhas de marketing. As campanhas são parte de um programa, e os programas estão incluídos em um plano de campanha.

Para criar uma campanha de marketing:

1. Crie uma campanha: descubra campanhas e suas características: etiqueta, tipo, datas de início e término, orçamento, recursos associados, gerentes e participantes.

   Consulte [Criação de uma campanha](#creating-a-campaign).

1. Defina a população do target: crie um workflow com queries de direcionamento.

   Consulte [Seleção da população do target](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)

1. Crie deliveries: selecione os canais e defina o conteúdo a ser enviado.

   Consulte [Criação de deliveries](../../campaign/using/marketing-campaign-deliveries.md#creating-deliveries).

1. Aprove deliveries.

   Consulte [Processo de aprovação](../../campaign/using/marketing-campaign-approval.md#approval-process).

1. Monitore deliveries

   Consulte [Monitoramento](../../campaign/using/marketing-campaign-monitoring.md).

1. Planeje campanhas e custos associados.

   Consulte [Criação de provedores de serviços e suas estruturas de custo](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

Quando essas etapas forem concluídas, será possível iniciar os deliveries (consulte [Iniciando um delivery](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)), verificar os dados, processos e informações relacionados aos deliveries e, se necessário, gerenciar os documentos associados (consulte [Gerenciamento de documentos associados](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)). Também é possível rastrear a execução das fases de processamento das campanhas e deliveries (consulte [Rastreamento](../../campaign/using/marketing-campaign-monitoring.md)).

## Criação de plano e programa de hierarquia {#creating-plan-and-program-hierarchy}

Para configurar a hierarquia de pastas para planos de marketing e programas:

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

Você pode criar uma campanha através da lista de campanhas. Para exibir essa visualização, selecione o menu **[!UICONTROL Campaigns]** no painel **[!UICONTROL Campaigns]**.

![](assets/s_ncs_user_add_an_op_from_list.png)

O campo **[!UICONTROL Program]** permite selecionar o programa ao qual a campanha será anexada. Essas informações são obrigatórias.

![](assets/s_ncs_user_new_op_wz_a.png)

As campanhas também podem ser criadas por meio de um programa. Para fazer isso, clique no botão **[!UICONTROL Add]** na guia **[!UICONTROL Schedule]** do programa relacionado.

![](assets/s_ncs_user_add_an_op.png)

Ao criar uma campanha por meio da guia **[!UICONTROL Schedule]** de um programa, a campanha é vinculada automaticamente ao programa relacionado. O campo **[!UICONTROL Program]** está oculto nesse caso.

Na janela de criação da campanha, selecione o modelo da campanha e adicione um nome e uma descrição da campanha. Você também pode especificar as datas de início e término da campanha.

Clique em **[!UICONTROL OK]** para criar a campanha. Ela será adicionada ao cronograma do programa.

![](assets/s_ncs_user_program_planning_with_op.png)

>[!NOTE]
>
>Para filtrar as campanhas a serem exibidas, clique no link **[!UICONTROL Filter]** e selecione o status das campanhas a serem exibidas.

![](assets/s_ncs_user_program_planning_filter.png)

### Editar e configurar uma campanha {#editing-and-configuring-a-campaign}

Você pode editar a campanha que acabou de criar e definir seus parâmetros.

Para abrir e configurar uma campanha, selecione-a no cronograma e clique em **[!UICONTROL Open]**.

![](assets/s_ncs_user_new_op_edit.png)

Você será direcionado ao painel de campanha.

## Campanhas recorrentes e periódicas {#recurring-and-periodic-campaigns}

Uma campanha recorrente é uma campanha baseada em um template específico, cujos workflows são configurados para serem executados de acordo com um agendamento associado. Portanto, os workflows serão recorrentes dentro de uma campanha. O direcionamento é duplicado em cada execução e os vários processos e populações do target são rastreados. Também é possível executar os direcionamentos antecipadamente, por meio do período de cobertura durante a criação automática de workflow, para iniciar simulações com estimativas de destino.

Uma campanha periódica é uma campanha criada automaticamente de acordo com o agendamento de execução de seu template.

### Criar uma campanha recorrente {#creating-a-recurring-campaign}

As campanhas recorrentes são criadas a partir de um template específico que define o template de workflow a ser executado e o agendamento de execução.

#### Criação de um template para campanhas recorrentes {#creating-the-campaign-template}

1. Crie um template de campanha **[!UICONTROL Recurring]**.

   >[!NOTE]
   >
   >Recomenda-se duplicar o template padrão em vez de criar um template vazio.

   ![](assets/s_ncs_user_op_template_recur_tab.png)

1. Insira o nome do template e a duração da campanha.

   ![](assets/s_ncs_user_op_template_recur_duplicate.png)

1. Para esse tipo de campanha, uma guia **[!UICONTROL Schedule]** é adicionada para criar o agendamento de execução do template.

Nesta guia, especifique as datas de execução planejadas das campanhas com base neste template.

![](assets/s_ncs_user_op_template_recur_planning.png)

O modo de configuração do agendamento de execução coincide com o objeto **[!UICONTROL Scheduler]** do workflow. Para obter mais informações, consulte [esta seção](../../workflow/using/architecture.md).

>[!IMPORTANT]
>
>A configuração do agendamento de execução deve ser realizada cuidadosamente para evitar sobrecarga do banco de dados. As campanhas recorrentes duplicam o(s) fluxo(s) de trabalho de seu template dependendo do cronograma especificado. A implementação da criação de workflow excessivamente frequente pode dificultar a operação do banco de dados.

1. Especifique um valor no campo **[!UICONTROL Create in advance for]** para criar os workflows correspondentes ao período indicado.
1. Crie o template de workflow a ser usado em campanhas com base nesse template, com os parâmetros de definição de metas e uma ou mais remessas genéricas.

   >[!NOTE]
   >
   >Esse workflow deve ser salvo como um template de workflow recorrente. Para fazer isso, edite as propriedades do workflow e selecione na guia **[!UICONTROL Recurring workflow template]** a opção **[!UICONTROL Execution]**.

   ![](assets/s_ncs_user_op_template_recur_wf_option.png)

#### Criar a campanha recorrente {#create-the-recurring-campaign}

Para criar a campanha recorrente e executar os workflows de acordo com o agendamento definido no template, aplique o seguinte procedimento:

1. Crie uma nova campanha com base em um template de campanha recorrente.
1. Preencha o agendamento de execução do workflow.

   ![](assets/s_ncs_user_op_recur_planning.png)

1. O agendamento da campanha permite que você insira uma data de início ou execução automática de workflow para cada linha.

   Para cada linha, você pode adicionar as seguintes opções adicionais:

   * **[!UICONTROL To be approved]** : permite forçar as solicitações de aprovação de delivery no workflow.
   * **[!UICONTROL To be started]**: permite iniciar o workflow quando a data de início é atingida.

   O campo **[!UICONTROL Create in advance for]** permite criar todos os workflows que abrangem o período inserido.

   Após a execução do workflow **[!UICONTROL Jobs on campaigns]**, os workflows dedicados são criados com base nas ocorrências definidas no agendamento da campanha. Um workflow é criado para cada data de execução.

1. Os workflows recorrentes são criados automaticamente a partir do template de workflow presente na campanha. Eles ficam visíveis na guia **[!UICONTROL Targeting and workflows]** da campanha.

   ![](assets/s_ncs_user_op_recur_planning_wfs.png)

   O rótulo de uma instância de workflow recorrente consiste no rótulo do seu template e no número do workflow, sendo que entre eles há o caractere &quot;#&quot;.

   Os workflows criados a partir do agendamento são associados automaticamente a ele na coluna **[!UICONTROL Workflow]** da guia **[!UICONTROL Schedule]**.

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

1. Crie um template de campanha **[!UICONTROL Periodic]**, preferencialmente duplicando um template de campanha existente.

   ![](assets/s_ncs_user_op_template_period_create.png)

1. Digite as propriedades do template.

   >[!NOTE]
   >
   >O operador que o template está atribuído precisa ter os direitos apropriados para criar campanhas no programa selecionado.

1. Crie o workflow associado a este template. Ele será duplicado em cada campanha periódica criada pelo template.

   ![](assets/s_ncs_user_op_template_period_wf.png)

   >[!NOTE]
   >
   >Este workflow é um template de workflow. Ele não pode ser executado do template de campanha.

1. Conclua o agendamento de execução como para um template de campanha recorrente: clique no botão **[!UICONTROL Add]** e defina as datas de início e término ou preencha o agendamento de execução por meio do link.

   ![](assets/s_ncs_user_op_template_period_planning_add.png)

   >[!IMPORTANT]
   >
   >Os templates de campanha periódicos criam novas campanhas de acordo com o agendamento definido acima. Portanto, deve ser concluída com cuidado, para evitar sobrecarga do banco de dados do Adobe Campaign.

1. Quando a data de início da execução for atingida, a campanha correspondente será criada automaticamente. Leva em conta todas as características do template.

   Cada campanha pode ser editada por meio do agendamento do template.

   ![](assets/s_ncs_user_op_template_period_planning.png)

Cada campanha periódica contém os mesmos elementos. Uma vez criado, ele é gerenciado como uma campanha padrão.
