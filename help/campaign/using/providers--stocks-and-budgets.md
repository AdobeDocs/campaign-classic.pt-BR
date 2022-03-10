---
product: campaign
title: Provedores, estoques e orçamentos
description: Provedores, estoques e orçamentos
feature: Budget Management, Campaigns
exl-id: c60c4f86-a957-4c44-a0fe-39b6e3f0e5d6
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: ht
source-wordcount: '1902'
ht-degree: 100%

---

# Provedores, estoques e orçamentos{#providers-stocks-and-budgets}

![](../../assets/common.svg)

O Adobe Campaign permite que você defina provedores de serviços que estarão envolvidos nas tarefas realizadas nas campanhas. As informações relacionadas aos provedores de serviços e as estruturas de custo relacionadas são definidas pelo administrador do Adobe Campaign a partir da visualização principal. O provedor de serviços é referenciado a partir do delivery e suas estruturas de custo permitem o cálculo de custos associados a esse delivery, bem como o gerenciamento do estoque.

## Criação de provedores de serviços e estruturas de custo {#creating-service-providers-and-their-cost-structures}

Cada provedor de serviços é salvo em um arquivo com detalhes de contato, modelos de serviço e tarefas relacionadas.

Os provedores de serviços são configurados no nó **[!UICONTROL Administration > Campaign management]** da árvore.

As tarefas realizadas durante as entregas são realizadas por provedores de serviços, especialmente para mala direta e canais móveis. Esses provedores de serviços podem, por exemplo, estar envolvidos na impressão ou distribuição de mensagens. Essas tarefas envolvem configurações e custos que são específicos para cada provedor de serviços. A configuração dos provedores de serviços envolve quatro estágios:

1. Criação de um provedor de serviços no Adobe Campaign

   Consulte [Adicionar um provedor de serviço](#adding-a-service-provider).

1. Definindo categorias de custo e estruturas de templates de serviço associados

   Consulte [Definição de categorias de custo](#defining-cost-categories) e [Definição da estrutura de custo](#defining-the-cost-structure).

1. Configuração de processos

   Consulte [Configuração de processos associados a um serviço](#configuring-processes-associated-with-a-service).

1. Fazendo referência ao provedor de serviços no nível da campanha

   Consulte [Associar um serviço a uma campanha](#associating-a-service-with-a-campaign).

### Criação de um provedor de serviços e categorias de custo {#creating-a-service-provider-and-its-cost-categories}

#### Adição de um provedor de serviços {#adding-a-service-provider}

Você pode criar quantos provedores de serviços forem necessários para suas remessas. O procedimento para adicionar um provedor de serviços é o seguinte:

1. Clique com o botão direito do mouse na lista de provedores de serviços e selecione **[!UICONTROL New]** ou clique no botão **[!UICONTROL New]** acima da lista de provedores de serviços.
1. Na seção inferior da janela, especifique o nome e os detalhes de contato do provedor de serviços.

   ![](assets/s_ncs_user_supplier_node_01.png)

1. Clique no botão **[!UICONTROL Save]** para adicionar o provedor de serviço à lista.

#### Definição de categorias de custo {#defining-cost-categories}

Você deve associar templates de serviço a cada provedor de serviços. Nesses templates, você deve primeiro identificar as categorias de custo e se necessário o estoque em questão. Em seguida, você deve criar as regras de cálculo de custo para cada categoria, por meio das estruturas de custo.

>[!NOTE]
>
>Para obter mais informações, consulte [Definição da estrutura de custo](#defining-the-cost-structure).

Uma categoria de custo é uma entidade que contém um conjunto de custos qualificados para um tipo de delivery (e-mail, mala direta, etc.) ou para uma tarefa. As categorias de custo são agrupadas nos templates de serviços associados aos provedores de serviço. Cada provedor de serviço pode referenciar um ou mais templates de serviço.

Para criar um template de serviço e definir seu conteúdo, aplique as seguintes etapas:

1. Na guia **[!UICONTROL Services]** do provedor de serviço, clique no botão **[!UICONTROL Add]** e nomeie o modelo de serviço.

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. Crie as categorias de custo para cada tipo de processo (tarefa ou delivery por mala direta/email/etc.). Para fazer isso, clique na guia **[!UICONTROL Cost categories]** e, em seguida, no botão **[!UICONTROL Add]** e insira os parâmetros de cada categoria de custo.

   ![](assets/s_ncs_user_supplier_node_03.png)

   * Insira um rótulo para esta categoria de custo e selecione o tipo de processo em questão: delivery por **[!UICONTROL Direct mail]**, **[!UICONTROL Email]**, **[!UICONTROL Mobile]**, **[!UICONTROL Telephone]** ou **[!UICONTROL Task]**.
   * Clique no botão **[!UICONTROL Add]** para definir os tipos de custo associados a esta categoria.
   * Se necessário, associada a uma linha de estoque com cada tipo de custo para que as quantidades usadas sejam relacionadas automaticamente aos estoques existentes.

      >[!NOTE]
      >
      >As linhas de estoque são definidas no nó **[!UICONTROL Stock management]**.\
      >Para obter mais informações, consulte [Estoque e gerenciamento de pedidos](#stock-and-order-management).

1. Você pode pré-selecionar um valor para essa categoria de custo, que será oferecida por padrão nas categorias de custo do provedor de serviços (em vez de em branco). Para fazer isso, selecione a opção na coluna **[!UICONTROL Selected]** referente ao tipo de categoria em questão:

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   No nível de entrega, o valor será selecionado por padrão:

   ![](assets/s_ncs_user_supplier_default_cost.png)

### Definição da estrutura de custos {#defining-the-cost-structure}

Para cada tipo de custo, uma estrutura de custos especifica as regras de cálculo a serem aplicadas.

Clique na guia **[!UICONTROL Cost structure]** para configurar o cálculo de custo para cada categoria de custo e tipo. Clique em **[!UICONTROL Add]** e insira a estrutura de custos.

![](assets/s_ncs_user_supplier_node_04.png)

* Para criar a estrutura de custos, selecione o tipo de mensagem e a categoria de custo relacionada às listas suspensas, bem como o tipo de custo ao qual a regra de cálculo será aplicada. O conteúdo dessas listas suspensas é proveniente das informações inseridas por meio da guia **[!UICONTROL Cost categories]**.

   Você deve atribuir um rótulo à estrutura de custos. Por padrão, ela tem o seguinte delivery outline: **Cost category - Type of cost**.

   No entanto, você pode renomeá-la: digite o valor desejado diretamente no campo **[!UICONTROL Label]**.

* A fórmula de cálculo de custo é definida na seção inferior da janela.

   Essa fórmula pode ser corrigida (para qualquer número de mensagens) ou calculadas de acordo com o número de mensagens.

   Quando depender do número de mensagens, a estrutura de cálculo de custos pode ser **[!UICONTROL Linear]**, **[!UICONTROL Linear by threshold]** ou **[!UICONTROL Constant by threshold]**.

#### Estrutura linear {#linear-structure}

Se a quantidade for sempre a mesma para uma mensagem (ou um lote de mensagens) independentemente do número total de mensagens, selecione **[!UICONTROL Linear]** e insira o custo de cada mensagem.

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

Se essa quantia se aplicar a um lote de mensagens, especifique o número de mensagens relacionadas ao campo **[!UICONTROL for]**.

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### Estrutura linear por limite {#linear-structure-by-threshold}

Se a quantidade se aplicar ao limite de cada mensagem, você deve definir uma estrutura de cálculo **[!UICONTROL Linear by threshold]**. Neste tipo de estrutura de custo, cada mensagem custará 0.13, por exemplo, se o número total de mensagens estiver entre 1 e 100, e custará 0.12 de 100 a 1000 mensagens enviadas ou 0.11 acima de 1000 mensagens.

A configuração será a seguinte:

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

Para adicionar um limite, clique no botão **[!UICONTROL Add]** à direita da lista.

#### Estrutura constante por limite {#constant-structure-by-threshold}

Por fim, você pode configurar um cálculo de custo de acordo com o número total de mensagens. Para fazer isso, selecione uma estrutura de cálculo **[!UICONTROL Constant by threshold]**. Por exemplo, o custo será definido em uma quantidade fixa de 12,00 para 1 a 100 mensagens, de 100,00 para uma entrega de 101 a 1.000 mensagens e de 500,00 para qualquer entrega acima de 1.000 mensagens, independentemente do número total.

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### Configuração de processos associados a um serviço {#configuring-processes-associated-with-a-service}

Você pode associar informações nos processos associados ao serviço através da guia **[!UICONTROL Processes]**.

Para fazer isso, clique na guia **[!UICONTROL Processes]** para configurar o envio de informações para o roteador.

![](assets/s_ncs_user_supplier_node_02.png)

* A seção **[!UICONTROL File extraction]** indica o modelo de exportação usado para o delivery quando esse serviço é selecionado. Você pode indicar o nome do arquivo de saída no campo **[!UICONTROL Extraction file]**. O botão à direita do campo permite inserir variáveis.

   ![](assets/s_ncs_user_supplier_node_02a.png)

* A seção **[!UICONTROL Notification email]** permite especificar o modelo para notificar os provedores de serviço depois que os arquivos forem enviados. Selecione o template usado para criar a mensagem de alerta e o grupo de recipients.

   Por padrão, os modelos de delivery para mensagens de notificação são salvos no nó **[!UICONTROL Administration > Campaign management > Technical delivery templates]**, que é acessível na visualização geral.

* A seção **[!UICONTROL Post-processing]** permite que você selecione o workflow a ser iniciado após a aprovação do delivery. Se um template de workflow for inserido, uma instância de workflow será criada automaticamente e será iniciada assim que a aprovação entrar em vigor. Esse workflow pode enviar o arquivo de extração para um provedor de serviços externos para processamento, por exemplo.

### Associação de um serviço a uma campanha {#associating-a-service-with-a-campaign}

Os serviços estão associados a campanhas via entregas ou tarefas. Os provedores de serviço estão vinculados a templates de delivery para oferecer seus serviços nos deliveries criados por meio desse template.

Quando um serviço é selecionado, as categorias de custo correspondentes ao tipo de delivery (mala direta, email, etc.) são automaticamente indicadas na tabela central juntamente com as opções de processamento definidas.

>[!NOTE]
>
>Se nenhuma categoria de custo for exibida quando um serviço for selecionado, isso significa que nenhuma categoria de custo foi definida para esse tipo de processo. Por exemplo, para um delivery de email, se nenhuma categoria de custo do tipo **[!UICONTROL Email]** tiver sido definida, nenhuma categoria será exibida, e a seleção do serviço não terá efeito.

* Para um delivery de mala direta, você pode selecionar o serviço na janela de configuração.

   ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* Para uma entrega em canais móveis ou telefone, é possível aplicar o mesmo modo de seleção.
* Para um delivery de email, o serviço é selecionado na guia **[!UICONTROL Advanced]** nas propriedades do delivery, como no exemplo a seguir:

   ![](assets/s_ncs_user_supplier_email_delivery_select.png)

A coluna **[!UICONTROL Amount to surcharge]** permite que você adicione um custo para essa categoria no contexto do delivery ou tarefa relacionada.

Você pode impor a seleção obrigatória de um tipo de custo durante a definição de classes de custo para um delivery. Para fazer isso, selecione **[!UICONTROL A cost type must be selected]**.

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## Gerenciamento de estoque e pedido {#stock-and-order-management}

Os tipos de custo podem ser associados a linhas de estoque para manipular alertas, controlar suprimentos e pedidos de lançamento.

O procedimento para configurar o estoque e o gerenciamento de pedidos no Adobe Campaign, e alertas os operadores no caso de fornecimentos insuficientes para um delivery a ser realizado, é o seguinte:

1. Criação de estoque e referência de provedores de serviços associados

   Consulte [Criação de um estoque](#creating-a-stock).

1. Adicionar linhas de estoque

   Consulte [Adicionar linhas de estoque](#adding-stock-lines).

1. Notificar operadores no caso de um alerta

   Consulte [Alertar operadores](#alerting-operators).

1. Pedidos e fornecimento.

   Consulte [Pedidos](#orders).

### Gerenciamento de estoque {#stock-management}

O Adobe Campaign poderá alertar um grupo de operadores se o estoque tiver acabado ou atingido um limite mínimo. Os níveis de estoque podem ser acessados poe meio do link **[!UICONTROL Stocks]** da guia **[!UICONTROL Campaigns]** por meio do link **[!UICONTROL Other choices]** da área de navegação.

![](assets/s_ncs_user_stocks_view.png)

#### Criação de um estoque {#creating-a-stock}

Execute as seguintes etapas para criar um novo estoque:

1. Clique no botão **[!UICONTROL Create]** acima da lista de estoques.
1. Insira o rótulo do estoque e selecione o provedor de serviços com o qual ele está associado na lista suspensa.

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >Para obter mais informações, consulte [Criação de provedores de serviços e suas estruturas de custo](#creating-service-providers-and-their-cost-structures).

#### Adicionar linhas de estoque {#adding-stock-lines}

Um estoque consiste em várias linhas de estoque. Uma linha de estoque contém uma quantidade inicial de recursos que serão consumidos pelas entregas. Cada linha de estoque indica a quantidade consumida, a quantidade em estoque e a quantidade solicitada.

Ao criar um estoque, clique na guia **[!UICONTROL Stock lines]** para adicionar novas linhas.

![](assets/s_ncs_user_stocks_display_line.png)

Depois que o estoque for criado, clique nele para editar e usar seu painel para criar e exibir linhas de estoque.

Clique no botão **[!UICONTROL Create]** para definir os parâmetros de estoque.

![](assets/s_ncs_user_stocks_new_line.png)

* Indique a quantidade inicialmente em estoque no campo **[!UICONTROL Initial stock]**. Os campos **[!UICONTROL Consumed]** e **[!UICONTROL In stock]** são calculados automaticamente e atualizados conforme as campanhas avançam.

   ![](assets/s_ncs_user_stocks_create_line.png)

* Indique o limite do qual os operadores devem ser avisados no estoque de pedidos no campo **[!UICONTROL Alert level]**. Quando o nível de alerta for atingido, uma mensagem de aviso será exibida na janela de aprovação de entregas usando esse estoque.

#### Associação de um estoque com categorias de custo {#associating-a-stock-with-cost-categories}

Para determinado provedor de serviços, em um serviço, uma linha de estoque pode ser referenciada por uma das classes de custo, da seguinte maneira:

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### Rastreamento de estoque {#stock-tracking}

#### Alerta a operadores {#alerting-operators}

Um alerta é exibido quando um estoque referenciado em um delivery é insuficiente. Por exemplo, o alerta a seguir será exibido quando um arquivo de extração for aprovado:

![](assets/s_ncs_user_stocks_valid_alert.png)

#### Pedidos {#orders}

A subguia **[!UICONTROL Orders]** permite visualizar pedidos atuais e salvar novos pedidos.

![](assets/s_ncs_user_stocks_edit_from_board.png)

Para salvar um pedido, edite a linha de estoque direcionada, clique no botão **[!UICONTROL Add]** e especifique a data e a quantidade do delivery.

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>Quando a data do delivery for atingida, a linha de estoque solicitada desaparecerá automaticamente, e a quantidade inserida no campo **[!UICONTROL Volume on order]** será adicionada à guia **[!UICONTROL Tracking]**. Essa quantidade é automaticamente adicionada ao volume de estoque.

![](assets/s_ncs_user_stocks_node_08.png)

A guia **[!UICONTROL Consumptions]** contém o volume consumido por campanha. As informações desta guia são inseridas automaticamente de acordo com as remessas realizadas. Clique no botão **[!UICONTROL Edit]** para abrir a campanha.

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## Cálculo de orçamentos {#calculating-budgets}

### Princípio {#principle}

Os custos são gerenciados para remessas e campanha. De acordo com o progresso, esses custos são alocados para os orçamentos.

Os custos de delivery de uma campanha são consolidados no nível da campanha, e os custos de todas as campanhas de um programa são passados para o programa com o qual estão associados. Relatórios dedicados permitem rastrear os orçamentos para toda a plataforma ou para cada plano e cada programa.

### Implementação {#implementation}

Em uma campanha, ao selecionar o orçamento, você deve inserir o valor inicial. Os custos calculados serão atualizados automaticamente de acordo com o nível de compromisso dos valores inseridos (despesas feitas, esperadas, reservadas e confirmadas). Consulte [Cálculo de valores](../../mrm/using/controlling-costs.md#calculating-amounts).

>[!NOTE]
>
>O procedimento para a criação de orçamentos é apresentado em [Criação de um orçamento](../../mrm/using/controlling-costs.md#creating-a-budget).
