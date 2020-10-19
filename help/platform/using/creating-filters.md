---
title: Criação de filtros
seo-title: Criação de filtros
description: Criação de filtros
seo-description: null
page-status-flag: never-activated
uuid: 9fa4a80d-8f03-4f24-92a1-44f6ae2a2337
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: 066e730b-2527-4257-b11f-2e73f746a8a5
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '1976'
ht-degree: 88%

---


# Criação de filtros{#creating-filters}

## Introdução {#introduction}

Ao navegar na árvore do Adobe Campaign (no menu **[!UICONTROL Explorer]** da home page), os dados no banco de dados são exibidos em listas. Essas listas podem ser configuradas para exibir apenas os dados exigidos pelo operador. As ações podem então ser iniciadas nos dados filtrados. A configuração de filtro permite selecionar dados de uma lista **[!UICONTROL dynamically]**. Se os dados forem modificados, os dados filtrados serão atualizados.

>[!NOTE]
>
>As configurações de lista são definidas no local no nível da estação de trabalho. Esses dados são armazenados em arquivos ocultos e pode ser necessário limpá-los, principalmente se surgirem problemas ao atualizar dados. To do this, use **[!UICONTROL File > Clear the local cache]** menu.

## Tipologia de filtros disponíveis {#typology-of-available-filters}

O Adobe Campaign permite aplicar filtros a listas de dados.

Esses filtros podem ser usados uma vez ou você pode salvá-los para usar depois. É possível aplicar vários filtros ao mesmo tempo.

Os seguintes tipos de filtro estão disponíveis no Adobe Campaign:

* Filtros padrão

   O **filtro padrão** pode ser acessado nos campos acima das listas. Ele permite aplicar filtros em campos predefinidos (para perfis de destinatários, esses são o nome e endereço de email por padrão). Você pode usar os campos para inserir os caracteres para filtrar ou selecionar as condições do filtro de uma lista suspensa.

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an e-mail address in the domain "yahoo.com".
-->
É possível alterar o filtro padrão de uma lista. Para obter mais informações, consulte [Alteração do filtro padrão](#altering-the-default-filter).

* Filtros simples

   **Filtros simples** são os filtros únicos nas colunas. Eles são definidos com um ou mais critérios de pesquisa simples nas colunas exibidas.

   Você pode combinar vários filtros simples na mesma lista de dados para refinar sua pesquisa. Os campos de filtro são exibidos um abaixo do outro. Eles podem ser excluídos de maneira independente.

   ![](assets/filters_recipient_simple_filter.png)

   Filtros simples são detalhados em [Criação de um filtro simples](#creating-a-simple-filter).

* Filtros avançados

   **Filtros avançados** são criados usando uma consulta ou combinação de consultas sobre os dados.

   Para obter mais informações sobre como criar um filtro avançado, consulte [Criação de um filtro avançado](#creating-an-advanced-filter).

   Você pode usar funções para definir o conteúdo do filtro. Para obter mais informações, consulte [Criação de um filtro avançado com funções](#creating-an-advanced-filter-with-functions).

   >[!NOTE]
   >
   >Para obter mais informações sobre criação de queries no Adobe Campaign, consulte [esta seção](../../platform/using/about-queries-in-campaign.md).

* Filtros de usuário

   Um **filtro de aplicação** é um filtro avançado que foi salvo, para usar e compartilhar sua configuração com outros operadores.

   O botão **[!UICONTROL Filters]** acima das listas oferece um conjunto de filtros de aplicação que podem ser combinados para refinar a filtragem. O método para criar esses filtros é apresentado em [Salvar um filtro](#saving-a-filter).

## Alteração do filtro padrão {#altering-the-default-filter}

To change the default filter for a recipient list, click the **[!UICONTROL Profiles and Targets > Pre-defined filters]** node of the tree.

For all other types of data, configure the default filter via the **[!UICONTROL Administration > Configuration > Predefined filters]** node.

Siga as etapas abaixo:

1. Selecione o filtro que deseja usar como padrão.
1. Click the **[!UICONTROL Parameters]** tab and select **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >Se um filtro padrão já estiver aplicado à lista, será necessário desabilitá-lo antes de aplicar um novo filtro. Para fazer isso, clique no xis vermelho à direita dos campos de filtragem.

1. Clique em **[!UICONTROL Save]** para aplicar o filtro.

   >[!NOTE]
   >
   >A janela de definição de filtro está detalhada em [Criação de um filtro avançado](#creating-an-advanced-filter) e [Salvar um filtro](#saving-a-filter).

## Criar um filtro simples {#creating-a-simple-filter}

Para criar um **filtro simples**, siga as seguintes etapas:

1. Right-click the field you want to filter and select **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   Os campos de filtro padrão são exibidos acima da lista.

1. Selecione a opção de filtro na lista suspensa ou digite os critérios de filtro para aplicar (o método para selecionar ou inserir critérios depende do tipo de campo: texto, enumerado etc.).

   ![](assets/s_ncs_user_sort_fields.png)

1. Para ativar o filtro, pressione Enter ou clique na seta verde à direita dos campos de filtro.

Se o campo no qual você deseja filtrar os dados não for exibido no formulário do perfil, você poderá adicioná-lo nas colunas exibidas e, em seguida, filtrar nessa coluna. Para fazer isso,

1. Clique no ícone **[!UICONTROL Configure the list]**.

   ![](assets/s_ncs_user_configure_list.png)

1. Selecione a coluna a ser exibida, por exemplo, a idade dos destinatários.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. Right-click the **Age** column in the recipient list, and select **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   Em seguida, é possível selecionar as opções de filtragem por idade.

   ![](assets/s_ncs_user_delete_filter.png)

## Criar um filtro avançado {#creating-an-advanced-filter}

Para criar um **filtro avançado**, siga as seguintes etapas:

1. Clique no botão **[!UICONTROL Filters]** e selecione **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   Além disso, é possível clicar com o botão direito do mouse na lista de dados para filtrar, e depois selecionar **[!UICONTROL Advanced filter...]**.

   A janela de definição de condição de filtragem é exibida.

1. Clique na coluna **[!UICONTROL Expression]** para definir o valor de entrada.
1. Clique em **[!UICONTROL Edit expression]** para selecionar o campo no qual o filtro será aplicado.

   ![](assets/s_user_filter_choose_field.png)

1. Na lista, selecione o campo no qual os dados serão filtrados. Clique em **[!UICONTROL Finish]** para confirmar.
1. Clique na coluna **[!UICONTROL Operator]** e selecione o operador a ser aplicado na lista suspensa.
1. Selecione um valor esperado na coluna **[!UICONTROL Value]**. Você pode combinar vários filtros para refinar seu query. Para adicionar uma condição de filtro, clique em **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. É possível atribuir uma hierarquia para as expressões ou alterar a ordem das expressões de query utilizando as setas da barra de ferramentas.
1. O operador padrão entre expressões é **e**, mas você pode alterá-lo clicando no campo. É possível selecionar um operador **ou**.

   ![](assets/s_ncs_user_filter_operator.png)

1. Clique em **[!UICONTROL OK]** para confirmar a criação do filtro e aplicá-lo à lista.

O filtro aplicado é exibido acima da lista.

![](assets/s_ncs_user_filter_adv_edit.png)

Para editar ou modificar esse filtro, clique em seu rótulo.

Para cancelar esse filtro, clique no ícone **[!UICONTROL Remove this filter]** à direita do filtro.

![](assets/s_ncs_user_filter_adv_remove.png)

Você pode salvar um filtro avançado para usá-lo depois. Para obter mais informações sobre esse tipo de filtro, consulte [Salvar um filtro](#saving-a-filter).

### Criar um filtro avançado com funções {#creating-an-advanced-filter-with-functions}

Filtros avançados podem usar funções; **filtros com funções** são criados por meio de um editor de expressão que permite criar fórmulas usando os dados do banco de dados e funções avançadas. Para criar um filtro com funções, repita as etapas de criação de filtro avançado 1, 2 e 3 e, em seguida, proceda da seguinte maneira:

1. In the field selection window, click **[!UICONTROL Advanced selection]**.
1. Selecione o tipo de fórmula a ser usado: agregação, filtro de usuário existente ou expressão.

   ![](assets/s_ncs_user_filter_formula_select.png)

   As seguintes opções estão disponíveis:

   * **[!UICONTROL Field only]** para selecionar um campo. Este é o modo padrão.
   * **[!UICONTROL Aggregate]** para selecionar a fórmula agregada a ser usada (contagens, soma, média, máximo, mínimo).
   * **[!UICONTROL User filter]** para selecionar um dos filtros de usuário existentes. Os filtros do usuário são detalhados em [Salvar um filtro](#saving-a-filter).
   * **[!UICONTROL Expression]** para acessar o editor de expressões.

      O editor de expressão permite definir um filtro avançado. Ela tem a seguinte aparência:

      ![](assets/s_ncs_user_create_exp_exple01.png)

      It lets you select fields in the database tables and attach advanced functions to them: Select the function to use in the **[!UICONTROL List of functions]**. As funções disponíveis são detalhadas em [Lista de funções](../../platform/using/defining-filter-conditions.md#list-of-functions). Em seguida, selecione o campo ou os campos relacionados pelas funções e clique em **[!UICONTROL OK]** para aprovar a expressão.

      >[!NOTE]
      >
      >Para ver um exemplo de criação de filtro com base em uma expressão, consulte [Identificar destinatários cujo aniversário é](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is).

## Salvar um filtro {#saving-a-filter}

Os filtros são específicos para cada operador e são reiniciados cada vez que o operador limpa o cache do console do cliente.

É possível criar um **application filter** salvando um filtro avançado: ele pode ser reutilizado clicando com o botão direito do mouse em qualquer lista ou pelo botão **[!UICONTROL Filters]** localizado acima das listas.

Esses filtros também podem ser acessados diretamente pelo assistente de delivery, no estágio de seleção de target (consulte [esta seção](../../delivery/using/creating-an-email-delivery.md) para obter mais informações sobre como criar deliveries). Para criar o filtro de aplicação, você pode:

* Converter um filtro avançado em um filtro de aplicação. Para fazer isso, clique em **[!UICONTROL Save]** antes de fechar o editor de filtro avançado.

   ![](assets/s_ncs_user_filter_save.png)

* Create this application filter via the **[!UICONTROL Administration > Configuration > Predefined filters]** (or **[!UICONTROL Profiles and targets > Predefined filters]** for recipients) node of the tree. Para fazer isso, clique com o botão direito do mouse na lista de filtros e selecione **[!UICONTROL New...]**. O procedimento é o mesmo para criar filtros avançados.

   O campo **[!UICONTROL Label]** permite nomear esse filtro. This name will appear in the combo box of the **[!UICONTROL Filters...]** button.

   ![](assets/user_filter_apply.png)

É possível excluir todos os filtros na lista atual clicando com o botão direito do mouse e selecionando **[!UICONTROL No filter]** ou usando o ícone **[!UICONTROL Filters]** acima da lista.

You can combine filters by clicking the **[!UICONTROL Filters]** button and using the **[!UICONTROL And...]** menu.

![](assets/s_ncs_user_filter_combination.png)

## Filtrar destinatários {#filtering-recipients}

Filtros predefinidos (consulte [Salvar um filtro](#saving-a-filter)) permitem filtrar os perfis dos destinatários no banco de dados. You can edit filters from the **[!UICONTROL Profiles and Targets > Predefined filters]** node of the tree. Os filtros são listados na seção superior do espaço de trabalho, por meio do botão **[!UICONTROL Filters]**.

Selecione um filtro para exibir sua definição e para acessar uma pré-visualização dos dados filtrados.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>Para verificar um exemplo detalhado de criação de filtro predefinido, consulte [Caso de uso](../../platform/using/use-case.md).

Os filtros predefinidos são:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo</strong><br /> </td> 
   <td> <strong>Query</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Aberto<br /> </td> 
   <td> Seleciona destinatários que abriram um delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aberto, mas não clicado<br /> </td> 
   <td> Seleciona destinatários que abriram um delivery, mas não clicaram em um link.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatários inativos<br /> </td> 
   <td> Seleciona destinatários que não abriram um delivery em X meses.<br /> </td> 
  </tr> 
  <tr> 
   <td> Última atividade por tipo de dispositivo<br /> </td> 
   <td> Seleciona destinatários que clicaram em ou abriram delivery Y usando o dispositivo X nos últimos Z dias.<br /> </td> 
  </tr> 
  <tr> 
   <td> Última atividade por tipo de dispositivo (rastreamento)<br /> </td> 
   <td> Seleciona destinatários que clicaram em ou abriram delivery Y usando o dispositivo X nos últimos Z dias.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatários não direcionados<br /> </td> 
   <td> Seleciona destinatários que nunca foram direcionados por canal Y em X meses.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatários muito ativos<br /> </td> 
   <td> Seleciona destinatários que clicaram em um delivery pelo menos X vezes nos últimos Y meses.<br /> </td> 
  </tr> 
  <tr> 
 <td> Endereço de email Incluir na lista de bloqueios<br /> </td> 
    <td> Seleciona recipient cujo endereço de email está na lista de bloqueios.<br/> </td>
  </tr> 
  <tr> 
   <td> Endereço de email na quarentena<br /> </td> 
   <td> Seleciona destinatários cujo endereço de email está em quarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Endereços de email duplicados na pasta<br /> </td> 
   <td> Seleciona destinatários cujo endereço de email está duplicado na pasta.<br /> </td> 
  </tr> 
  <tr> 
   <td> Não aberto nem clicado<br /> </td> 
   <td> Seleciona destinatários que não abriram ou não clicaram em um delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Novos destinatários (dias)<br /> </td> 
   <td> Seleciona destinatários que foram criados nos últimos X dias.<br /> </td> 
  </tr> 
  <tr> 
   <td> Novos destinatários (minutos)<br /> </td> 
   <td> Seleciona destinatários que foram criados nos últimos X minutos.<br /> </td> 
  </tr> 
  <tr> 
   <td> Novos destinatários (meses)<br /> </td> 
   <td> Seleciona destinatários que foram criados nos últimos X meses.<br /> </td> 
  </tr> 
  <tr> 
   <td> Por assinatura<br /> </td> 
   <td> Seleciona destinatários por assinatura.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ao clicar em um link específico<br /> </td> 
   <td> Seleciona destinatários que clicaram em um determinado URL em um delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Por comportamento pós-delivery<br /> </td> 
   <td> Seleciona destinatários de acordo com seu comportamento após receber um delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Por data de criação<br /> </td> 
   <td> Seleciona destinatários por data de criação, por um período variando de X meses (data atual menos n meses) para Y meses (data atual menos n meses).<br /> </td> 
  </tr> 
  <tr> 
   <td> Por lista<br /> </td> 
   <td> Seleciona destinatários por lista.<br /> </td> 
  </tr> 
  <tr> 
   <td> Por número de cliques<br /> </td> 
   <td> Seleciona destinatários que clicaram em um delivery nos últimos X meses.<br /> </td> 
  </tr> 
  <tr> 
   <td> Por número de mensagens recebidas<br /> </td> 
   <td> Seleciona destinatários de acordo com o número de mensagens recebidas.<br /> </td> 
  </tr> 
  <tr> 
   <td> Por número de aberturas<br /> </td> 
   <td> Seleciona destinatários que abriram deliveries entre X e Y ao longo da quantidade Z de tempo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Por nome ou email<br /> </td> 
   <td> Seleciona destinatários de acordo com seu nome ou email.<br /> </td> 
  </tr> 
  <tr> 
   <td> Por faixa etária<br /> </td> 
   <td> Seleciona destinatários de acordo com sua idade.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Todas as comparações referentes à contagem e aos períodos devem ser entendidas no sentido mais amplo (destinatários que correspondem aos limites de query estão incluídos na comparação).

Exemplos de como os dados são calculados:

* Seleciona destinatários com menos de 30 anos de idade:

   ![](assets/predefined_filters_01.png)

* Seleciona destinatários acima de 18 anos de idade:

   ![](assets/predefined_filters_03.png)

* Seleciona destinatários entre 18 e 30 anos:

   ![](assets/predefined_filters_02.png)

## Configurações avançadas para filtros de dados {#advanced-settings-for-data-filters}

Clique na guia **[!UICONTROL Settings]** para acessar as seguintes opções:

* **[!UICONTROL Default filter for the associated document type]**: essa opção permite que você sugira esse filtro por padrão no editor das listas afetadas pela classificação.

   For example, the **[!UICONTROL By name or login]** filter is applied to operators. Essa opção é selecionada e o filtro sempre é oferecido em todas as listas de operadores.

* **[!UICONTROL Filter shared with other operators]**: essa opção permite que você disponibilize o filtro para todos os outros operadores no banco de dados atual.
* **[!UICONTROL Use parameter entry form]**: esta opção permite definir os campos de filtro a serem exibido acima da lista quando esse filtro for selecionado. Esses campos permitem definir as configurações de filtro. Este formulário deve ser inserido no formato XML por meio do botão **[!UICONTROL Form]**. Por exemplo, o filtro pré-configurado **[!UICONTROL Recipients who have opened]**, disponível na lista de destinatários, exibe um campo de filtro que permite selecionar o delivery em que o filtro é direcionado.

   O botão **[!UICONTROL Preview]** exibe o resultado do filtro selecionado.

* The **[!UICONTROL Advanced parameters]** link lets you define additional settings. Especificamente, você pode associar uma tabela SQL ao filtro para torná-la comum a todos os editores que a compartilham.

   Select the **[!UICONTROL Do not restrict the filter]** option if you want to stop the user from overriding this filter.

   Essa opção está habilitada para os filtros &quot;Destinatários de um delivery&quot; e &quot;Destinatários de deliveries pertencentes a uma pasta&quot; oferecidos no assistente de delivery que não pode ser sobrecarregado.

   ![](assets/s_ncs_user_filter_advanced_param.png)

