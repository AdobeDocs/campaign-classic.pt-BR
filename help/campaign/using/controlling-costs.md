---
title: Controlar custos
seo-title: Controlar custos
description: Controlar custos
seo-description: null
page-status-flag: never-activated
uuid: 4209ebad-966f-44a6-a33c-bbb398c6f5c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 892b93ed-cb0e-4af5-a1ae-eff0c8b703c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Controlar custos{#controlling-costs}

## Sobre o controle de custo {#about-cost-control}

O Adobe Campaign permite controlar os custos de marketing programados, confirmados e faturados e separá-los por categorias usando o módulo Gerenciamento de Recursos de Marketing.

Os custos comprometidos com os vários processos de uma campanha são cobrados de um orçamento definido antecipadamente pelo departamento de marketing. Os valores podem ser divididos em várias categorias para tornar as informações mais legíveis e fornecer relatórios mais detalhados dos investimentos em marketing.

O gerenciamento e o acompanhamento dos orçamentos são centralizados em um nó dedicado da árvore do Adobe Campaign. Isso permite monitorar os valores alocados, reservados, comprometidos e gastos na mesma visão e para todos os orçamentos.

![](assets/s_ncs_user_budget_node_02.png)

As etapas a seguir devem ser aplicadas para implementar o gerenciamento de orçamento usando MRM:

1. Definir o orçamento

   For more on this, refer to [Creating a budget](#creating-a-budget).

1. Definir o método de cálculo de custo

   As estruturas de custo são definidas para os provedores de serviços. See [Creating a service provider and its cost categories](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

1. Definir os custos da campanha (remessas/tarefas)

   Os custos incorridos pelas entregas e tarefas são alimentados individualmente ou globalmente para o template de campanha. See [Calculation of costs and stocks](../../campaign/using/marketing-campaign-deliveries.md#calculation-of-costs-and-stocks).

1. Consolidação

   De acordo com o status do progresso das tarefas, remessas e campanhas, os custos serão calculados e passados para o orçamento correspondente.

   When the creation of the campaign is sufficiently advanced, the progress status of the campaign budget can be changed to **[!UICONTROL Specified]**. O custo calculado do programa é então inserido automaticamente com os custos calculados na campanha. See [Cost commitment, calculation and charging](#cost-commitment--calculation-and-charging).

## Criar um orçamento {#creating-a-budget}

Budgets are created in the map, via the **[!UICONTROL Campaign management > Budgets]** node. The **[!UICONTROL New]** button in the toolbar lets you create a budget.

* Adicionar um novo orçamento

   Click the **[!UICONTROL New]** icon, name and save the budget.

* Inserir a quantidade inicial

   Indique o valor alocado no campo relevante. Os outros montantes são inseridos automaticamente. Consulte [Calculando valores](#calculating-amounts).

* Definir o período de validade

   Especifique as datas de início e término. Estas informações são apenas indicativas.

* Despesas

   Crie as categorias de despesas às quais os custos atribuídos a esse orçamento para campanhas, tarefas etc. podem ser vinculados. Consulte Categorias [de despesas](#expense-categories).

   ![](assets/s_ncs_user_budget_create_and_save.png)

>[!NOTE]
>
>Você pode selecionar um orçamento relacionado.
>
>Para obter mais informações, consulte [Vincular um orçamento a outro](#linking-a-budget-to-another).

### Calcular valores {#calculating-amounts}

Cada orçamento é definido por um valor inicial que será diminuído com os custos das várias campanhas, remessas ou tarefas relacionadas a eles após terem sido agendadas ou realizadas. O status dos valores (planejado, reservado, comprometido, gasto ou faturado) depende do tipo de custo e do nível de comprometimento definido na campanha, no delivery ou na tarefa.

>[!NOTE]
>
>The amounts entered for the categories must match the budget envelope defined in the **[!UICONTROL Allocated]** field.

Para campanhas, de acordo com o nível de compromisso, um custo pode ser planejado, comprometido ou reservado para uma ação futura.

![](assets/s_user_cost_op_engaged.png)

>[!CAUTION]
>
>When a campaign is created, the progress status in **[!UICONTROL Budget]** must be set to **[!UICONTROL Defined]** for the costs to be taken into account on execution. If the status is **[!UICONTROL Being edited]**, the costs will not be consolidated.
>   
>The option **[!UICONTROL Commitment level]** represents a projection of costs into the future before they are charged to the budget. De acordo com o progresso de uma campanha, tarefa ou delivery, pode-se decidir atribuir um nível de compromisso mais alto ou mais baixo (1. Planejado, 2. Reservado, 3. Comprometido) usando a caixa de combinação.

Por exemplo, o custo planejado estimado de uma campanha da Web é 45,000 Euros.

![](assets/s_user_edit_budget_node_impact_0.png)

For the campaign, when the budget creation status is set to **[!UICONTROL Defined]**, the real cost of the campaign (or, if none, the computed cost) will be carried over into the budget totals.

![](assets/s_user_budget_in_op_a.png)

According to the level of commitment of the campaign budget, the amount will be entered in the **[!UICONTROL Planned]**, **[!UICONTROL Reserved]** or **[!UICONTROL Committed]** field.

O nível de comprometimento pode ser modificado:

* in the **campaign** level, in the **[!UICONTROL Budget]** window, found in the **[!UICONTROL Edit]** tab. É onde os orçamentos, custos e despesas são configurados.
* in the **tasks** level, in the **[!UICONTROL Expenses and revenues]** window.

![](assets/s_user_op_engagement_level_costs.png)

When the budget is **[!UICONTROL Reserved]**, the update is performed automatically for the charged budget.

![](assets/s_user_edit_budget_node_impact_2.png)

O procedimento é o mesmo em nível de tarefa.

![](assets/s_user_edit_budget_node_impact_task.png)

When an expenditure gives rise to an invoice and the invoice is paid, its amount is then entered in the **[!UICONTROL Invoiced]** field.

### Categorias de despesas {#expense-categories}

Os valores podem ser distribuídos em várias categorias de despesas para melhorar a legibilidade dos dados e para ter relatórios mais detalhados dos investimentos em marketing. The expense categories are defined during budget creation, via the **[!UICONTROL Budgets]** node of the tree.

To add a category, click the **[!UICONTROL Add]** button in the lower section of the window.

![](assets/s_user_budget_category.png)

É possível selecionar uma categoria dentre as existentes ou definir uma nova categoria, digitando-a diretamente no campo. Quando confirmar a entrada, uma mensagem de confirmação permite adicionar essa categoria à lista de categorias existentes e associá-la a uma Natureza, se necessário. Essas informações serão usadas nos relatórios de orçamento.

### Vincular um orçamento a outro {#linking-a-budget-to-another}

É possível vincular um orçamento a um orçamento principal. To do this, select the main budget in the **[!UICONTROL related budget]** field of the secondary budgets.

![](assets/budget_link.png)

Uma guia adicional será adicionada ao orçamento principal para exibir a lista de orçamentos relacionados.

![](assets/budget_link_new_tab.png)

Essas informações são inseridas nos relatórios de orçamento.

## Adicionar linhas de despesas {#adding-expense-lines}

As linhas de despesa são adicionadas automaticamente ao orçamento. Elas são criadas durante a análise de delivery e quando uma tarefa é concluída.

![](assets/s_ncs_user_budget_line_edit.png)

Para cada campanha, delivery ou tarefa, os custos gerados são agrupados nas linhas de despesa do orçamento ao qual são descontadas. Essas linhas de despesas são criadas de acordo com as linhas de custo do provedor de serviços relacionadas e calculadas por meio das estruturas de custo associadas.

Cada linha de despesa contém as seguintes informações:

* A campanha e o delivery ou a tarefa à qual está relacionada
* A quantia calculada com base nas estruturas de custo ou no custo provisional estimado.
* Custo real do delivery ou da tarefa
* A linha correspondente da fatura (somente MRM).
* Lista de custos calculados pela categoria de custo (se existir uma estrutura de custos).

No exemplo acima, a linha de despesa editada contém os custos calculados para o delivery de **Novos cartões** para a campanha do **Loyalty Spring Pack.** When the delivery is edited, the **[!UICONTROL Direct Mail]** tab lets you see how the expense line is calculated.

O cálculo de custo para esse delivery baseia-se nas categorias de custo selecionadas para o provedor de serviços relacionado:

![](assets/s_user_edit_del_supplier_costs.png)

De acordo com as categorias de custo selecionadas, as estruturas de custo correspondentes são aplicadas a fim de calcular as linhas de custo. Neste exemplo, para o provedor de serviços relacionado, as estruturas de custo são as seguintes:

![](assets/s_user_edit_node_supplier_costs.png)

>[!NOTE]
>
>As categorias e estruturas de custo são apresentadas em [Criação de um provedor de serviços e suas categorias](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)de custo.

## Compromisso de custo, cálculo e carregamento {#cost-commitment--calculation-and-charging}

Os custos podem ser confirmados para remessas e tarefas. De acordo com o progresso do processo ao qual está relacionada, o status de um custo é atualizado.

### Processo de cálculo de custo {#cost-calculation-process}

Os custos dividem-se em três categorias:

1. Custo estimado provisional.

   O custo provisional estimado é uma estimativa dos custos dos processos da campanha. Contanto que seja editado, os valores de entrada não são consolidados. It must have **[!UICONTROL Specified]** status for the amounts input to be taken into account in the calculations.

   Essa quantia é entrada manualmente e pode ser dividida em várias categorias de despesas. To bread down a cost, click the **[!UICONTROL Breakdown...]** link, and then the **[!UICONTROL Add]** button to define a new amount.

   ![](assets/s_user_edit_budget_tab_ventil.png)

   É possível associar cada custo com uma categoria para que a divisão de custos por categoria de despesa possa ser visualizada posteriormente no orçamento relacionado e nos relatórios de orçamento.

1. Custo calculado

   O custo calculado depende do elemento relacionado (campanha, delivery, tarefa etc.) e seu status (sendo editado, em andamento, concluído). Em qualquer caso, se o custo real for especificado, o custo calculado usará essa quantia.

   Se o custo real não for fornecido, as seguintes regras se aplicam:

   * Para uma campanha que está sendo editada, o custo calculado é o custo provisional estimado da campanha ou, se esse custo não for definido, o custo calculado será a soma de todos os custos provisional das remessas e tarefas da campanha. Se a campanha estiver concluída, o custo calculado da campanha será a soma de todos os custos calculados.
   * Para um delivery que ainda não foi analisado, o custo calculado é o custo estimado provisional. Se a análise já tiver sido executada, o custo calculado será a soma de todos os custos calculados da estrutura de custos do provedor de serviços e o número de recipients.
   * Para uma tarefa em andamento, o custo calculado usa o custo provisional estimado. Se a tarefa for concluída, o custo calculado será a soma de todos os custos calculados nas estruturas de custo do provedor de serviços e o número de dias concluídos.
   * Para o plano de marketing, como para o programa, o custo calculado é a soma dos custos calculados para as campanhas. Se esses custos não forem especificados, o custo calculado usará os custos provisional estimados.
   >[!NOTE]
   >
   >The **[!UICONTROL Breakdown]** link lets you view the details of the calculation and the last cost calculation date.

1. Custo real

   O custo real é alimentado manualmente e, se necessário, é dividido em diferentes categorias de despesas.

### Cálculo e carregamento {#calculation-and-charging}

Os custos são calculados por meio de estruturas de custo e cobrados nos orçamentos selecionados nas campanhas, remessas ou tarefas.

Uma verificação pode ser realizada nos valores comprometidos com as campanhas por meio da aprovação do orçamento. Tarefas estilo marcos adicionais podem ser criadas em uma campanha para configurar outras aprovações. Consulte [Tipos de tarefa](../../campaign/using/creating-and-managing-tasks.md#types-of-task).

### Exemplo {#example}

Vamos criar uma campanha com:

* Um delivery de mala direta usando as estruturas de custo de um provedor de serviços.
* Uma tarefa com um custo fixo.
* Uma tarefa com um custo diário.

#### Etapa 1 - Criar o orçamento {#step-1---creating-the-budget}

Crie um novo orçamento por meio do **[!UICONTROL Campaign management > Budgets]** nó.

Define a budget of 10,000 Euros in the **[!UICONTROL Allocated]** field of the **[!UICONTROL Amounts]** section. Adicione duas categorias de despesas na seção inferior da janela:

![](assets/s_user_cost_mgmt_sample_1.png)

#### Etapa 2 - Configurar o provedor de serviços e definir as estruturas de custo {#step-2---configuring-the-service-provider-and-defining-the-cost-structures}

Create a service provider and a service template with its cost structure from the **[!UICONTROL Administration > Campaigns]** node.

Para obter mais informações, consulte [Criação de um provedor de serviços e suas categorias](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)de custo.

* For direct mail deliveries, create cost categories **[!UICONTROL Envelopes]** (types 114x229 and 162x229), **[!UICONTROL Postage]** and **[!UICONTROL Print]** (types A3 and A4). E, em seguida, crie as seguintes estruturas de custo:

   ![](assets/s_user_cost_mgmt_sample_2.png)

   Adicione um custo fixo (nas categorias de custo) cujo cálculo é fixo e cuja quantidade está em branco (na estrutura de custo correspondente) e que será especificada individualmente para cada delivery.

   ![](assets/s_user_cost_mgmt_sample_5.png)

* Para tarefas, crie as duas categorias de custo a seguir:

   1. **[!UICONTROL Room reservation]** (Sala pequena e Sala grande), com uma estrutura de custos **fixa** no montante de 300 e 500 Euros:

      ![](assets/s_user_cost_mgmt_sample_6.png)

   1. **[!UICONTROL Creation]** (Tipo de modelo **de** conteúdo), com uma estrutura de custos **diários** de 300 Euros:

      ![](assets/s_user_cost_mgmt_sample_7.png)

#### Etapa 3 - Carregar o orçamento na campanha {#step-3---charging-the-budget-in-the-campaign}

Crie uma campanha e selecione o orçamento criado na Etapa 1.

>[!NOTE]
>
>Por padrão, o orçamento selecionado para o programa é aplicado em todas as campanhas do programa.

![](assets/s_user_cost_mgmt_sample_4.png)

Especifique o custo provisional estimado, com detalhamento:

![](assets/s_user_cost_mgmt_sample_9.png)

Clique em **[!UICONTROL Ok]** e **[!UICONTROL Save]** para confirmar essas informações. O custo calculado da campanha é, então, atualizado com o custo provisional estimado.

#### Etapa 4 - Criar o delivery de mala direta {#step-4---creating-the-direct-mail-delivery}

Crie um workflow para a campanha e posicione as atividades de query para selecionar o alvo (aviso, os endereços postais dos recipients devem ser especificados).

Crie um delivery de mala direta e selecione o provedor de serviços criado na Etapa 2: as categorias de custo são exibidas automaticamente.

Substitua o custo dos envelopes e adicione um custo fixo. Além disso, selecione as categorias, relacionadas a esses custos.

![](assets/s_user_cost_mgmt_sample_3.png)

>[!NOTE]
>
>Se uma das categorias de custo não for usada, ela não gerará nenhuma despesa.

Inicie o workflow que acabou de criar para iniciar a análise e calcular os custos.

![](assets/s_user_cost_mgmt_sample_10.png)

Se a aprovação do orçamento for habilitada para esta campanha, aprove o orçamento através do painel. É possível verificar a aprovação de categorias de custo.

![](assets/s_user_cost_mgmt_sample_10b.png)

The expense line concerning the delivery is added in the **[!UICONTROL Edit > Budget]** tab of the campaign. Edite-a para exibir os detalhes do cálculo.

![](assets/s_user_cost_mgmt_sample_11.png)

O custo calculado para o delivery é atualizado com estas informações:

![](assets/s_user_cost_mgmt_sample_12.png)

Ao editar o custo calculado, é possível verificar a divisão de custo e o status e a data do cálculo de custo.

#### Etapa 5 - Criar tarefas {#step-5---creating-tasks}

Para essa campanha, adicionaremos as duas tarefas para as quais as estruturas de custo foram criadas anteriormente (consulte [Etapa 2 - Configurar o provedor de serviço e definir as estruturas](#step-2---configuring-the-service-provider-and-defining-the-cost-structures)de custo). To do this, in the campaign dashboard, click the **[!UICONTROL Add a task]** button. Name the task and click **[!UICONTROL Save]**.

A tarefa é, então, adicionada à lista de tarefas. É necessário editá-la para configurá-la.

In the **[!UICONTROL Properties]** tab, select the service and the corresponding cost category:

![](assets/s_user_cost_mgmt_sample_14.png)

Next, click the **[!UICONTROL Expenses and revenue]** icon of the task and specify the estimated provisional cost.

![](assets/s_user_cost_mgmt_sample_15.png)

Quando a tarefa for salva, o custo calculado é especificado com o valor inserido para o custo provisional estimado.

When the task is completed (status **[!UICONTROL Finished]** ), the calculated cost is automatically updated with the cost of the Large Room as entered in its cost structure. Esse custo também aparece nesta categoria da divisão de custos.

Em seguida, crie uma segunda tarefa de acordo com o mesmo procedimento; agendada por cinco dias e relacionada à estrutura de custos criada anteriormente.

![](assets/s_user_cost_mgmt_sample_16.png)

Quando a tarefa é concluída, o custo calculado é especificado com o valor da estrutura de custo relacionada, ou seja 1500 euros em nosso exemplo (5 dias x 300 euros):

![](assets/s_user_cost_mgmt_sample_17.png)

#### Etapa 6 - Atualizar o status do orçamento da campanha {#step-6---update-the-campaign-budget-status}

When the campaign is configured, its status can be updated by setting it to **[!UICONTROL Specified]**. O custo calculado da campanha indicará a soma dos custos calculados do delivery e das tarefas da campanha:

![](assets/s_user_cost_mgmt_sample_18.png)

#### Aprovação de orçamento {#budget-approval}

Quando a aprovação é ativada, um link especial permite aprovar o orçamento do painel de campanha. Esse link é exibido quando o workflow de segmentação foi iniciado e um delivery de mala direta precisa ser aprovado.

![](assets/s_user_cost_mgmt_sample_19.png)

É possível clicar no link para conceder ou rejeitar a aprovação ou usar o link no e-mail de notificação se a notificação tiver sido ativada para esta campanha.

Quando o orçamento tiver sido aprovado e o delivery for concluído, os custos serão automaticamente carregados por meio de um workflow técnico especial.

## Pedidos e faturas {#orders-and-invoices}

No contexto de MRM, é possível salvar pedidos com um provedor de serviços e emitir faturas. O ciclo de vida completo desses pedidos e faturas pode ser gerenciado pela interface do Adobe Campaign.

### Criação de pedidos {#order-creation}

To save a new order with a service provider, click the **[!UICONTROL MRM > Orders]** node of the tree, and then click the **[!UICONTROL New]** button.

Especifique o número do pedido, o provedor de serviços e o valor total do pedido.

![](assets/s_user_cost_create_order.png)

### Emitir e acompanhar faturas {#issuing-and-tracking-invoices}

Para cada provedor de serviços, é possível salvar faturas e definir seus status e o orçamento cobrado.

Invoices are created and stored in the **[!UICONTROL MRM > Invoices]** node of the Adobe Campaign tree.

![](assets/s_user_cost_create_invoice.png)

Uma fatura consiste em linhas de fatura cujo total permite que o valor seja calculado automaticamente. These lines are created manually from the **[!UICONTROL Invoice lines]** tab. Elas podem ser associados a um pedido para carregar as informações nos pedidos.

![](assets/s_user_cost_invoice_add_line.png)

The invoices of each service provider are displayed in the **[!UICONTROL Invoices]** tab of the profile:

![](assets/s_ncs_user_invoice_from_supplier.png)

The **[!UICONTROL Details]** tab lets you display the content of the invoice.

Click **[!UICONTROL Add]** to create a new invoice.
