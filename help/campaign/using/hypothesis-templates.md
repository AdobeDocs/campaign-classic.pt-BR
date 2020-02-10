---
title: Templates de Hipóteses
seo-title: Templates de Hipóteses
description: Templates de Hipóteses
seo-description: null
page-status-flag: never-activated
uuid: 080417c2-1c45-4404-961e-2e660d8f0436
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: addfc395-7a85-4be1-a757-a719ed34bb33
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Templates de Hipóteses{#hypothesis-templates}

## Cria um template de hipótese {#creating-a-hypothesis-model}

A configuração do template de hipótese permite definir o contexto para mensurar as reações, seja para um delivery ou para uma oferta. É onde as várias tabelas de mensuração são referenciadas, assim como aquelas que definem as relações entre individuais, hipóteses e a tabela de transações.

Aplique as seguintes etapas para criar um template de hipótese:

1. In the Adobe Campaign explorer, click **[!UICONTROL Resources>Templates>Hypothesis templates]**.

   ![](assets/response_hypothesis_model_creation_001.png)

1. Click **[!UICONTROL New]** or right-click in the list of templates and choose **[!UICONTROL New]** in the drop-down list.
1. Insira o rótulo da hipótese.
1. Specify whether the template is destined for hypotheses on offers or deliveries via the **[!UICONTROL Hypothesis type]**.
1. For **[!UICONTROL Delivery]** type templates, specify whether measurements should be carried out with or without a control group (for more on this, refer to [Properties of a hypothesis template](#properties-of-a-hypothesis-template)).
1. For **[!UICONTROL Delivery]** type templates, you can choose a specific channel or decide to apply the template to all available channels in Adobe Campaign using the **[!UICONTROL Channel]** drop-down list (for more on this, refer to [Properties of a hypothesis template](#properties-of-a-hypothesis-template)).
1. Select the **[!UICONTROL Execution folder]** in which you wish to create and automatically execute the hypotheses that will be created from this template.
1. Escolha as configurações de execução (para obter mais informações, consulte as configurações [de execução do modelo de](#hypothesis-template-execution-settings)Hipótese).
1. Especifique o período de cálculo da hipótese (para saber mais sobre isso, consulte as configurações [de execução do modelo de](#hypothesis-template-execution-settings)Hipótese).

   >[!CAUTION]
   >
   >Esse período é determinado a partir da data de contato.

1. In the **[!UICONTROL Transactions]** tab, specify the tables and fields required for the hypothesis calculation (for more on this, refer to [Transactions](#transactions)).
1. If your template is configured for **[!UICONTROL Offer]** type hypotheses, you can enable the **[!UICONTROL Update offer proposition status]** option: in this case, select the status of the offer proposition you want to change.
1. Specify the scope of the hypothesis application (for more on this, refer to [Hypothesis perimeter](#hypothesis-perimeter)).
1. If necessary, use a script to complete filtering (for more on this, refer to [Hypothesis perimeter](#hypothesis-perimeter)).

### Propriedades de um template de hipótese {#properties-of-a-hypothesis-template}

The template&#39;s **[!UICONTROL General]** tab lets you specify the general template options. Os campos disponíveis são:

* **[!UICONTROL Hypothesis type]**: permite que você determine se o modelo deve ser destinado a hipóteses em entregas ou ofertas.

   É possível optar por criar uma hipótese que será aplicada tanto em envios quanto em ofertas.

   >[!NOTE]
   >
   >Se o modelo se aplicar às ofertas, a **[!UICONTROL Update offer proposition status]** opção estará disponível na **[!UICONTROL Transactions]** guia.

* **[!UICONTROL Measurement with control group]**: permite que você indique se um grupo de controle foi definido para a entrega ou a campanha e o inclua em indicadores de medição. O grupo de controle, que não recebe deliveries, permite medir o impacto da campanha após o delivery, comparando-o com a amostragem alvo que recebeu o delivery.

   >[!NOTE]
   >
   >Se o template está configurado para assumir um grupo de controle em conta, mas nenhum grupo está definido no delivery relacionado a hipótese, os resultados são baseados somente em recipients direcionados.

   Para obter mais informações sobre como definir e configurar um grupo de controle, consulte [Definição de um grupo](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)de controle.

* **[!UICONTROL Channel]**: você pode escolher um canal específico ou disponibilizar o modelo de hipótese para todos os canais no console do Adobe Campaign selecionando-o **[!UICONTROL All channels]** na lista suspensa. If you configure the template for a specific channel, this lets you automatically filter deliveries per channel when creating the hypothesis (refer to [Creating hypotheses](../../campaign/using/creating-hypotheses.md)).

   ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**: permite que você especifique a pasta de execução para a hipótese.
* **[!UICONTROL Taken into account in campaign ROI calculation]**: considera o resultado da hipótese no cálculo do ROI para a campanha relacionada.

### Configurações de execução do template de Hipótese {#hypothesis-template-execution-settings}

The template&#39;s **[!UICONTROL General]** tab also lets you specify the hypothesis execution parameters. As opções disponíveis são:

* **[!UICONTROL Schedule execution for a time of low activity]**: permite agendar a inicialização da hipótese para otimizar o desempenho do Adobe Campaign. Quando essa opção é marcada, o workflow do processamento em campanhas executa o cálculo de hipóteses durante o tempo de inatividade.

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**: nível aplicado à hipótese para excluir as ordens de cálculo da hipótese se houver execuções simultâneas.

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**: se necessário, permite programar o recálculo da hipótese (por exemplo, se você deseja atualizar indicadores regularmente até o final da entrega).

   ![](assets/response_exec_settings_001.png)

   Aplique o seguinte processo para especificar um cronograma:

   1. Clique no **[!UICONTROL Frequency of execution...]** link e, em seguida, no **[!UICONTROL Change...]** botão.

      ![](assets/response_frequency_execution_001.png)

   1. Configure a frequência, os eventos relacionados e o período de validade.

      ![](assets/response_frequency_execution_002.png)

   1. Clique **[!UICONTROL Finish]** para salvar o agendamento.

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**: esta função é reservada para usuários especialistas. Ele permite adicionar uma guia à auditoria da hipótese de mensuração para mostrar queries SQL. Isso permite a detecção de possíveis defeitos se uma simulação terminar com erros.
* **[!UICONTROL Keep execution workflow]**: permite manter o fluxo de trabalho que foi gerado automaticamente no início do cálculo da hipótese. Na hipótese criada a partir de um template que tem essa opção marcada, o workflow gerado está disponível para seguir o processo.

   >[!CAUTION]
   >
   >Essa opção deve ser ativada somente para fins de depuração, caso ocorra um erro durante a execução da hipótese.\
   >Além disso, os workflows gerados automaticamente não devem ser modificados. Qualquer modificação eventual em outro lugar é desconsiderada para cálculos posteriores.\
   >Se essa opção está marcada, exclua o workflow após a execução.

### Transações {#transactions}

Esta guia contém vários campos e tabelas que permitem salvar o histórico das reações do recipient em termos de transações. Consulte o guia [Configuração](../../configuration/using/about-schema-reference.md) para obter mais informações sobre as tabelas dedicadas ao gestor de resposta.

* **[!UICONTROL Schema (reaction log storage)]**: selecione a tabela de reação do destinatário. A tabela pronta para uso no Adobe Campaign é a **NmsRemaMatchRcp**.
* **[!UICONTROL Transaction schema]**: escolha a tabela que as hipóteses se referirão, ou seja, a transação ou a tabela de compra.
* **[!UICONTROL Querying schema]**: escolha os critérios para filtrar a hipótese.
* **[!UICONTROL Link to individuals]**: escolha o link entre indivíduos e a tabela usada como esquema de transação.
* **[!UICONTROL Link to the household]**: selecione o link para o agregado no esquema de transações se desejar incluir todos os membros de um agregado em uma hipótese. Este campo é opcional.
* **[!UICONTROL Transaction date]**: esse campo é opcional, mas recomendado, pois permite definir um escopo para o cálculo de hipóteses.
* **[!UICONTROL Measurement period]**: permite configurar datas de início e término durante as quais as hipóteses são executadas e as linhas de compra são recuperadas.

   Quando a hipótese está vinculada a um delivery, a mensuração é acionada automaticamente por alguns dias após a data de contato da mala direta ou após a data do email ou SMS.

   ![](assets/response_measurement_001.png)

   Se a hipótese é iniciada em tempo real, pode ser forçada para acionar imediatamente. Caso contrário, ele será acionado automaticamente com base na data de término do cálculo configurada, que se baseia na data de criação da hipótese (consulte [Criar uma hipótese dinamicamente em uma entrega](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)).

* **[!UICONTROL Transaction/Margin amount]**: esses campos são opcionais e permitem calcular indicadores de rotatividade automaticamente (consulte [Indicadores](../../campaign/using/hypothesis-tracking.md#indicators)).
* **[!UICONTROL Unit amount]**: permite definir uma quantia para calcular a receita (consulte [Indicadores](../../campaign/using/hypothesis-tracking.md#indicators)).

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**: permite que você especifique medidas de relatório ou eixos adicionais de campos nas diferentes tabelas.
* **[!UICONTROL Update offer proposition status]**: permite alterar o status da proposta da oferta se um destinatário da oferta for identificado pela hipótese.

   ![](assets/response_offer_status_001.png)

### Perímetro da Hipótese {#hypothesis-perimeter}

Depois de definir a tabela de transações e os campos que são relacionados, é possível refinar o escopo da sua hipótese especificando as transações de destino e envios através do uso de filtros. Também é possível usar um script JavaScript para apontar explicitamente para um produto referenciado na tabela de transações.

* **Filtragem de transações**: na **[!UICONTROL Scope]** guia, é possível configurar um filtro na hipótese. Para fazer isso:

   1. Clique no **[!UICONTROL Edit query]** link.

      ![](assets/response_scope_filtering_001.png)

   1. Especifique as condições de filtragem.

      ![](assets/response_scope_filtering_002.png)

   1. Selecione a transação que a hipótese deve relacionar.

      ![](assets/response_scope_filtering_003.png)

* **Filtrar nos destinatários**: na **[!UICONTROL Scope]** guia, você pode limitar sua hipótese a qualquer informação vinculada a uma mensagem (entrega, destinatário, endereço de email, serviço etc.):

   1. Clique no **[!UICONTROL Add a filter]** link e depois **[!UICONTROL Edit query]**.

      ![](assets/response_scope_filtering_004.png)

   1. Especifique as condições de filtragem.

      ![](assets/response_scope_filtering_005.png)

   1. Clique **[!UICONTROL Finish]** para salvar sua consulta.

      ![](assets/response_scope_filtering_006.png)

* **Script**: é possível usar um script JavaScript para sobrecarregar dinamicamente as configurações de hipótese durante a execução.

   To do this, click the **[!UICONTROL Advanced settings]** link then enter the desired script.

   >[!NOTE]
   >
   >Esse procedimento destina-se somente aos usuários especializados.

   ![](assets/response_hypothesis_model_creation_011.png)

## Exemplo: criar um template de hipótese em um delivery {#example--creating-a-hypothesis-template-on-a-delivery}

Neste exemplo é criado um template de hipótese em um delivery do tipo mala direta. A tabela de transações (**Compras** no exemplo) que a hipótese está baseada contém linhas de compra vinculadas aos artigos ou produtos. O template é configurado para criar hipóteses em artigos ou produtos da tabela de compras.

1. In the Adobe Campaign explorer, go to the **[!UICONTROL Resources > Templates > Hypothesis templates]** node.
1. Clique em **[!UICONTROL New]** para criar um modelo.

   ![](assets/response_hypothesis_model_example_001.png)

1. Alterar o rótulo do template.

   ![](assets/response_hypothesis_model_example_002.png)

1. Selecione **[!UICONTROL Deliveries]** como um tipo de hipótese.
1. Marque a opção correspondente para especificar que o delivery pode conter um grupo de controle.
1. Escolha o **[!UICONTROL Direct mail]** canal.

   >[!NOTE]
   >
   >Como o template é específico para o delivery de mala direta, a hipótese criada através desse template pode não estar vinculada a nenhum outro tipo de delivery.

1. In the **[!UICONTROL Transactions]** tab, select the recipient reactions table.

   ![](assets/response_hypothesis_model_example_006.png)

1. In the **[!UICONTROL Transactions schema]** field, choose your purchase table.

   ![](assets/response_hypothesis_model_example_007.png)

1. Selecione linhas de compra no **[!UICONTROL Querying schema]** campo.

   ![](assets/response_hypothesis_model_example_008.png)

1. Escolha os recipients vinculados à tabela de compras.

   ![](assets/response_hypothesis_model_example_009.png)

1. Selecione o campo vinculado à data de compra.

   Isso permite a definição de um período de tempo para hipóteses. Este estágio não é obrigatório, mas é recomendado.

   ![](assets/response_hypothesis_model_example_010.png)

1. Configure o período de cálculo de 5 a 25 dias.

   ![](assets/response_hypothesis_model_example_005.png)

1. Na **[!UICONTROL Scope]** guia, clique **[!UICONTROL Edit query]** para criar um filtro em hipóteses.

   ![](assets/response_hypothesis_model_example_011.png)

   O template criado permite a execução da hipótese nos produtos ou artigos da tabela de compras.

1. Clique **[!UICONTROL Save]** para gravar seu modelo.

