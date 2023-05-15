---
product: campaign
title: Direcionamento de dados
description: Saiba mais sobre como direcionar dados em um workflow
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Query Editor, Data Management
exl-id: 74b82019-bdab-4442-84cf-5ad18d0db788
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1924'
ht-degree: 100%

---

# Dados do público alvo{#targeting-data}



## Criar consultas {#creating-queries}

### Selecionar dados {#selecting-data}

Uma atividade **[!UICONTROL Query]** permite que você selecione dados básicos para criar o público-alvo. Para obter mais informações, consulte [Criação de uma consulta](query.md#creating-a-query).

Também é possível usar as seguintes atividades para consultar e refinar dados do banco de dados: [Incremental query](incremental-query.md) e [Read list](read-list.md).

É possível coletar dados adicionais para serem encaminhados e processados durante o ciclo de vida do workflow. Para obter mais informações, consulte [Adicionar dados](query.md#adding-data) e [Editar dados adicionais](#editing-additional-data).

### Editar dados adicionais {#editing-additional-data}

Após adicionar os dados adicionais, você pode editá-los ou utilizá-los para refinar o target definido na atividade de query.

O link **[!UICONTROL Edit additional data...]** permite visualizar os dados adicionados e modificá-los ou adicioná-los.

![](assets/wf_add_data_edit_link.png)

Para adicionar dados às colunas de output definidas anteriormente, selecione-os na lista de campos disponíveis. Para criar uma nova coluna de output, clique no ícone **[!UICONTROL Add]** e, em seguida, selecione o campo e clique em **[!UICONTROL Edit expression]**.

![](assets/query_add_an_output_column.png)

Defina um modo de cálculo para que o campo seja adicionado, como, por exemplo, uma agregação.

![](assets/query_add_an_output_column_formula.png)

A opção **[!UICONTROL Add a sub-item]** permite anexar dados calculados à coleção. Isso permite selecionar os dados adicionais da coleção ou definir cálculos agregados em elementos de coleção.

![](assets/query_add_columns_subscription_sub-element.png)

O subelementos será representado na subárvore da coleção em que são mapeados.

As coleções são mostradas na subguia **[!UICONTROL Collections]**. Você pode filtrar os elementos coletados clicando no ícone **[!UICONTROL Detail]** da coleção selecionada. O assistente de filtro permite selecionar os dados coletados e especificar as condições de filtragem a serem aplicadas aos dados na coleção.

![](assets/query_add_columns_collection.png)

### Refinar o público alvo usando dados adicionais {#refining-the-target-using-additional-data}

Os dados adicionais coletados podem capacitá-lo a refinar a filtragem de dados no banco de dados. Para fazer isso, clique no link **[!UICONTROL Refine the target using additional data...]**: isso permite filtrar os dados adicionados.

![](assets/wf_add_data_use_additional_data.png)

### Uniformizar dados {#homogenizing-data}

Em **[!UICONTROL Union]** ou **[!UICONTROL Intersection]** digite atividades, é possível escolher manter apenas os dados adicionais compartilhados para manter a consistência dos dados. Nesse caso, a mesa de trabalho de saída temporária dessa atividade conterá apenas os dados adicionais encontrados em todos os conjuntos de entradas.

![](assets/option-common_additionnal_col_only.png)

### Reconciliação com dados adicionais {#reconciliation-with-additional-data}

Durante as fases de reconciliação de dados (**[!UICONTROL Union]**, **[!UICONTROL Intersection]**, etc. você pode selecionar as colunas a serem usadas para reconciliação de dados das colunas adicionais. Para fazer isso, configure uma reconciliação em uma seleção de colunas e especifique o conjunto principal. Em seguida, selecione as colunas na coluna inferior da janela, como mostrado no exemplo a seguir:

![](assets/select-column-and-join.png)

### Criar subconjuntos {#creating-subsets}

A atividade **[!UICONTROL Split]** permite criar subconjuntos em critérios definidos por consultas de extração. Para cada subconjunto, ao editar uma condição de filtro no público, você acessará a atividade de query padrão que permite definir as condições de segmentação de target.

Você pode dividir um target em vários subconjuntos usando apenas dados adicionais como condições de filtragem ou como complemento aos dados de target. Você também pode usar dados externos se tiver comprado a opção **Federated Data Access**.

Para obter mais informações, consulte [Criação de subconjuntos usando a atividade Split](#creating-subsets-using-the-split-activity).

## Segmentar dados {#segmenting-data}

### Combinar vários públicos alvos (União) {#combining-several-targets--union-}

A atividade de união permite combinar o resultado de várias atividades em uma transição. Os conjuntos não precisam ser necessariamente homogêneos.

![](assets/join_reconciliation_options.png)

As seguintes opções de reconciliação de dados estão disponíveis:

* **[!UICONTROL Keys only]**

   Essa opção pode ser usada se os públicos de entrada forem homogêneos.

* **[!UICONTROL All columns in common]**

   Esta opção permite reconciliar dados baseado em todas as colunas comuns para os vários públicos do target.

   O Adobe Campaign identifica colunas com base em seu nome. Um limite de tolerância é aceito: uma coluna &#39;Email&#39; pode ser reconhecida como idêntica a uma coluna &#39;@email&#39;, por exemplo.

* **[!UICONTROL A selection of columns]**

   Selecione essa opção para definir a lista de colunas na qual a reconciliação de dados será aplicada.

   Comece selecionando o conjunto principal (aquele que contém os dados de origem) e as colunas a serem usadas na associação.

   ![](assets/join_reconciliation_options_01.png)

   >[!CAUTION]
   >
   >Durante a reconciliação de dados, não haverá a eliminação da duplicação dos públicos.

   Você pode restringir o tamanho do público a um determinado número de registros. Para fazer isso, clique na opção adequada e especifique o número de registros a serem mantidos.

   Além disso, especifique a prioridade dos públicos de entrada: a seção inferior da janela lista as transições de entrada da atividade de união e permite organizá-las com as setas azuis à direita da janela.

   Os registros serão retirados primeiro do público da primeira transição de entrada na lista, e, se o máximo não tiver sido atingido, eles serão retirados do público da segunda transição de entrada e etc.

   ![](assets/join_limit_nb_priority.png)

### Extrair dados conjuntos (Intersecção) {#extracting-joint-data--intersection-}

![](assets/traitements.png)

A intersecção permite recuperar apenas as linhas compartilhadas pelos públicos de transições de entrada. Essa atividade será configurada como a atividade de união.

Além disso, é possível manter apenas uma seleção de colunas ou apenas as colunas compartilhadas pelo público de entrada.

A atividade de intersecção é detalhada na seção [Intersection](intersection.md).

### Excluir uma população (Exclusão) {#excluding-a-population--exclusion-}

A atividade de exclusão permite excluir os elementos de um target de um público alvo diferente. O targeting dimension de output dessa atividade será do conjunto principal.

Quando necessário, é possível manipular as tabelas de entrada. De fato, para excluir um target de outra dimensão, esse target deve ser devolvido ao mesmo targeting dimension como o target principal. Para fazer isso, clique no botão **[!UICONTROL Add]** e especifique as condições de alteração da dimensão.

A reconciliação de dados é realizada por meio de um identificador, alterando o eixo ou uma junção. Um exemplo está disponível em [Uso de dados de uma lista: lista de leitura](../../platform/using/import-export-workflows.md#using-data-from-a-list--read-list).

![](assets/exclusion_edit_add_rule_01.png)

### Criar subconjuntos usando a atividade de Split {#creating-subsets-using-the-split-activity}

A atividade **[!UICONTROL Split]** é uma atividade padrão que permite criar os conjuntos necessários por meio de uma ou várias dimensões de filtro, bem como gerar uma transição de output por subconjunto ou uma transição exclusiva.

Os dados adicionais transmitidos pela transição de entrada podem ser usados nos critérios de filtragem.

Para configurá-lo, primeiro é necessário selecionar os critérios:

1. No workflow, arraste e solte uma atividade **[!UICONTROL Split]**.
1. Na guia **[!UICONTROL General]**, selecione a opção desejada: **[!UICONTROL Use data from the target and additional data]**, **[!UICONTROL Use the additional data only]** ou **[!UICONTROL Use external data]**.
1. Se a opção **[!UICONTROL Use data from the target and additional data]** for selecionada, o targeting dimension permitirá o uso de todos os dados transmitidos pela transição de entrada.

   ![](assets/split-general-tab-options.png)

   Quando subconjuntos são criados, os parâmetros de filtragem mencionados anteriormente são usados.

   Para definir condições de filtragem, escolha a opção **[!UICONTROL Add a filtering condition on the inbound population]** e clique no link **[!UICONTROL Edit...]**. Em seguida, especifique as condições de filtragem para criar esse subconjunto.

   ![](assets/split-subset-config-all-data.png)

   Um exemplo de uso das condições de filtragem na atividade **[!UICONTROL Split]** para segmentar o target em diferentes públicos é descrito [nesta seção](cross-channel-delivery-workflow.md).

   O campo **[!UICONTROL Label]** permite que você dê um nome ao subconjunto recém-criado, que corresponderá à transição de saída.

   Você também pode atribuir um código de segmento ao subconjunto para identificá-lo e usá-lo para o target do seu público.

   Se necessário, você pode alterar o targeting dimension e a dimensão de filtro individualmente para cada subconjunto que deseja criar. Para fazer isso, edite a condição de filtragem do subconjunto e verifique a opção **[!UICONTROL Use a specific filtering dimension]**.

   ![](assets/split-subset-config-specific-filtering.png)

1. Se a opção **[!UICONTROL Use the additional data only]** for selecionada, somente os dados adicionais serão oferecidos para a filtragem do subconjunto.

   ![](assets/split-subset-config-additional-data-only.png)

1. Se a opção **Federated Data Access** estiver habilitada, o campo **[!UICONTROL Use external data]** permitirá processar dados em um banco de dados externo já configurado ou criar uma nova conexão com um banco de dados.

   ![](assets/split-subset-config-add_external_data.png)

   Para mais informações, dependendo da versão do Campaign, consulte estas seções:

   ![](assets/do-not-localize/v7.jpeg)[ Documentação do Campaign v7](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png)[ Documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html?lang=pt-BR)

Em seguida, precisamos adicionar novos subconjuntos:

1. Clique no botão **[!UICONTROL Add]** para definir as condições de filtragem.

   ![](assets/wf_split_add_a_tab.png)

1. Defina a dimensão do filtro na guia **[!UICONTROL General]** da atividade (veja acima). Ela se aplica a todos os subconjuntos por padrão.

   ![](assets/wf_split_edit_filtering.png)

1. Se necessário, você pode alterar a dimensão de filtro para cada subconjunto individualmente. Isso permite criar um conjunto para todos os titulares de cartões Gold, um para todos os recipients que clicaram no boletim informativo mais recente e um terceiro para pessoas entre 18 e 25 anos que fizeram uma compra na loja nos últimos 30 dias, tudo usando a mesma atividade de Split. Para fazer isso, selecione a opção **[!UICONTROL Use a specific filtering dimension]** e selecione o contexto da filtragem de dados.

   ![](assets/wf_split_change_dimension.png)

   >[!NOTE]
   >
   >Se você adquiriu a opção **Federated Data Access**, é possível criar subconjuntos com base nas informações em uma base externa. Para fazer isso, selecione o schema da tabela externa no campo **[!UICONTROL Targeting dimension]**. Para obter mais informações, consulte [Acesso a um banco de dados externo (FDA)](accessing-an-external-database--fda-.md).

Após a criação dos subconjuntos, por padrão, a atividade de split mostrará tantas transições de output quanto houver subconjuntos:

![](assets/wf_split_multi_outputs.png)

Você pode agrupar todos esses subconjuntos em uma única transição de output. Nesse caso, o link para os respectivos subconjuntos será visível no código do segmento, por exemplo. Para fazer isso, selecione a opção **[!UICONTROL Generate all subsets in the same table]**.

![](assets/wf_split_select_option_single_output.png)

Por exemplo, você pode colocar uma única atividade de delivery e personalizar o conteúdo do delivery com base no código do segmento de cada conjunto de recipients:

![](assets/wf_split_single_output.png)

Subconjuntos também podem ser criados usando a atividade **[!UICONTROL Cells]**. Para obter mais informações, consulte a seção [Cells](cells.md).

### Usar dados direcionados {#using-targeted-data}

Depois que os dados forem identificados e preparados, eles poderão ser usados nos seguintes contextos:

* Você pode atualizar os dados no banco de dados após a manipulação de dados nos vários estágios do workflow.

   Para obter mais informações, consulte [Atualizar dados](update-data.md).

* Você também pode atualizar o conteúdo de listas existentes.

   Para obter mais informações, consulte [Atualizar lista](list-update.md).

* Você pode preparar ou iniciar deliveries no workflow diretamente.

   Para obter mais informações, consulte [Delivery](delivery.md), [Controle de delivery](delivery-control.md) e [Delivery contínuo](continuous-delivery.md).

## Gerenciamento de dados {#data-management}

No Adobe Campaign, a Gestão de Dados combina um conjunto de atividades para resolver problemas complexos de target oferecendo ferramentas mais eficientes e flexíveis. Isso permite implementar uma gestão consistente de todas as comunicações com um contato usando informações relacionadas a seus contratos, assinaturas, reatividade aos deliveries, etc. A Gestão de Dados permite acompanhar o ciclo de vida dos dados durante as operações de segmentação, especificamente:

* Simplificação e otimização de processos de target, ao incluir dados que não são modelados no datamart (criando novas tabelas: extensão local para todo workflow para construção do target, dependendo da configuração).
* Manutenção e transmissão de cálculos de buffer, especialmente durante as fases de construção do target ou para administração de banco de dados.
* Acesso a bases externas (opcional): bancos de dados heterogêneos considerados durante o processo de segmentação.

Para implementar essas operações, o Adobe Campaign oferece:

* Atividades de coleção de dados: [File transfer](file-transfer.md), [Data loading (file)](data-loading--file-.md), [Data loading (RDBMS)](data-loading--rdbms-.md) e [Update data](update-data.md). Essa primeira etapa de coleta de dados prepara os dados para que ele seja processado em outras atividades. Vários parâmetros precisam ser monitorados para garantir que o workflow seja executado corretamente e forneça os resultados esperados. Por exemplo, ao importar os dados, a chave primária (Pkey) para esses dados deve ser única para cada registro.
* As atividades de direcionamento foram aprimoradas com as opções de gerenciamento de dados: [Query](query.md), [Union](union.md), [Intersection](intersection.md) e [Split](split.md). Isso permite configurar uma união ou uma intersecção entre dados de diferentes targeting dimensions, desde que a reconciliação dos dados seja possível.
* Atividades de transformação de dados: [Enrichment](enrichment.md) e [Change dimension](change-dimension.md).

>[!CAUTION]
>
>Quando dois workflows são vinculados, a exclusão de um elemento de tabela de origem não significa que todos os dados vinculados a ele serão excluídos.
>  
>Por exemplo, excluir um recipient por meio de um workflow não resultará na exclusão de todo o histórico de delivery. No entanto, excluir um recipient diretamente na pasta &#39;Recipients&#39; resultará na exclusão de todos os dados vinculados a este recipient.

### Enriquecer e modificar dados {#enriching-and-modifying-data}

Além do targeting dimension, a dimensão de filtro permite especificar a natureza dos dados coletados. Consulte [Direcionamento e dimensões de filtragem](building-a-workflow.md#targeting-and-filtering-dimensions).

Os dados identificados e coletados podem ser enriquecidos, agregados e manipulados para otimizar a construção de target. Para fazer isso, além das atividades de manipulação de dados detalhadas na seção [Segmenting data](#segmenting-data), use o seguinte:

* A atividade **[!UICONTROL Enrichment]** permite adicionar colunas momentaneamente a um schema, bem como adicionar informações a determinados elementos. Ela é detalhada na seção [Enrichment](enrichment.md) do repositório de atividades.
* A atividade **[!UICONTROL Edit schema]** permite modificar a estrutura de um schema. Ela é detalhada na seção [Edit schema](edit-schema.md) do repositório de atividades.
* A atividade **[!UICONTROL Change dimension]** permite alterar o targeting dimension durante o ciclo de construção do target. Ela é detalhada na seção [Change dimension](change-dimension.md).
