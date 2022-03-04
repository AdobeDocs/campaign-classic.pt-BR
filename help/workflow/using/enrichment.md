---
product: campaign
title: Enriquecimento
description: Saiba mais sobre a atividade do workflow de enriquecimento
feature: Workflows, Enrichment Activity, Targeting Activity
exl-id: 4c7bc0f3-5877-47dc-bd72-dc94fb7bd479
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 100%

---

# Enriquecimento{#enrichment}

![](../../assets/common.svg)

A atividade **[!UICONTROL Enrichment]** permite adicionar informações a uma lista de perfis e a vincula a uma tabela existente (criar uma nova associação). Os critérios de reconciliação com perfis no banco de dados também podem ser definidos.

![](assets/enrichment_design.png)

## Definições {#definitions}

Para utilizar a atividade de enriquecimento, é preciso estar familiarizado com as várias opções disponíveis ao adicionar dados.

![](assets/enrichment_edit.png)

A opção **[!UICONTROL Data linked to the filtering dimension]** dá acesso a:

* Dados da dimensão do filtro: acesso aos dados da tabela de trabalho.
* Dados vinculados à dimensão do filtro: acesso aos dados vinculados à tabela de trabalho.

![](assets/wf_enrich_linkoptions.png)

A opção **[!UICONTROL A link]** permite criar uma ligação em qualquer tabela do banco de dados.

![](assets/wf_enrich_linkstype.png)

Existem quatro tipos de vinculações:

* **[!UICONTROL Define a collection]**: permite definir um vínculo com uma cardinalidade 1-N entre as tabelas.
* **[!UICONTROL Define a link whose target is still available]**: possibilita definir um vínculo com uma cardinalidade 1-1 entre as tabelas. As condições de associação devem ser definidas por um único registro na tabela do target.
* **[!UICONTROL Define a link whose target does not necessarily exist in the base]**: possibilita definir um vínculo com uma cardinalidade 0-1 entre as tabelas. A condição de ligação deve ser definida por um registro 0 ou 1 (máx.) na tabela de público alvo.

   Essa opção é configurada na guia **[!UICONTROL Simple Join]** que pode ser acessada por meio do link **[!UICONTROL Edit additional data]** da atividade **[!UICONTROL Enrichment]**.

* **[!UICONTROL Define a link by searching for a reference among several options]**: esse tipo de link define uma reconciliação em direção a um registro exclusivo. O Adobe Campaign cria um link para uma tabela de target adicionando uma chave externa na tabela de target para armazenar uma referência ao registro exclusivo.

   Essa opção é configurada na guia **[!UICONTROL Reconciliation and deduplication]** que pode ser acessada por meio do link **[!UICONTROL Edit additional data]** da atividade **[!UICONTROL Enrichment]**.

Os casos de uso que detalham o funcionamento das atividades de Enriquecimento em seu contexto também estão disponíveis nas seguintes seções:

* [Enriquecimento de email com campos de data personalizados](email-enrichment-with-custom-date-fields.md).
* [Enriquecimento de dados](enriching-data.md)
* [Criação da lista de resumo](creating-a-summary-list.md)

## Adição de informações {#adding-information}

Use a atividade **[!UICONTROL Enrichment]** para adicionar colunas a uma tabela de trabalho: essa atividade pode ser usada como um complemento para uma atividade de query.

A configuração de colunas adicionais é apresentada em [Adding data](query.md#adding-data).

O campo **[!UICONTROL Primary set]** permite selecionar a transição de entrada: os dados da tabela de trabalho dessa atividade serão enriquecidos.

Clique no link **[!UICONTROL Add data]** e selecione o tipo de dados a serem adicionados. A lista de tipos de dados oferecidos depende dos módulos e das opções instalados na sua plataforma. Em uma configuração mínima, é sempre possível adicionar dados vinculados à dimensão do filtro e um link.

![](assets/enrichment_edit.png)

No exemplo abaixo, a transição de saída será enriquecida com informações sobre a idade dos perfis de destino.

![](assets/enrichment_add_data.png)

Clique com o botão direito na transição de entrada da atividade de enriquecimento para visualizar os dados antes da fase de enriquecimento.

![](assets/enrichment_content_before.png)

A tabela de trabalho contém os seguintes dados e o schema associado:

![](assets/enrichment_content_before_a.png)

Repita esta operação na saída da fase de enriquecimento.

![](assets/enrichment_content_after.png)

Veja que os dados relacionados ao perfil idades foram adicionados:

![](assets/enrichment_content_after_a.png)

O schema correspondente também foi enriquecido.

## Gerenciamento de dados adicionais {#managing-additional-data}

Desmarque a opção **[!UICONTROL Keep all additional data from the main set]** se não quiser manter os dados adicionais definidos anteriormente. Neste caso, somente as colunas adicionais que foram selecionadas na atividade de enriquecimento serão adicionadas na tabela de trabalho de saída. As informações adicionais adicionadas às atividades transmitidas não serão salvas.

![](assets/enrichment_edit_without_additional.png)

Os dados e o schema na saída do estágio de enriquecimento serão como a seguir:

![](assets/enrichment_content_after_without_additional.png)

## Criação de um link {#creating-a-link}

É possível utilizar a atividade de enriquecimento para criar um link entre os dados de trabalho e o banco de dados do Adobe Campaign: isto será um link local para o workflow entre os dados de entrada.

Por exemplo, se carregar dados de um arquivo que contenha o número da conta, o país e o e-mail dos recipients, será necessário criar um link para a tabela do país para atualizar essas informações em seus perfis.

Para fazer isso, siga as etapas abaixo:

1. Colete e carregue o seguinte tipo de arquivo:

   ```
   Account number;Country;Email
   18D65;FRANCE;agnes@gmail.com
   243PP;RUSSIA;paul@gmail.com
   55H87;CROATIA;dave@gmail.com
   56U81;USA;susan@gmail.com
   853PI;ITALY;anna@gmail.com
   890LP;FRANCE;robert@gmail.com
   83TY2;SWITZERLAND;mike@gmail.com
   ```

1. Edite a atividade de enriquecimento e clique no link **Add data...** para criar uma ligação com a tabela País.

   ![](assets/enrichment_edit_after_file_box.png)

1. Selecione a opção **[!UICONTROL Link definition]** e clique no botão **[!UICONTROL Next]**. Especifique o tipo de link a ser criado. Neste exemplo, devemos reconciliar o país do recipient do arquivo com um país na lista de países disponíveis na tabela dedicada do banco de dados. Escolha a opção **[!UICONTROL Define a link by searching for a reference among several options]**. Selecione a tabela do país no campo **[!UICONTROL Target schema]**.

   ![](assets/enrichment_add_a_link_select_option4.png)

1. Finalmente, selecione os campos que permitirão vincular os valores do arquivo de origem àqueles no banco de dados.

   ![](assets/enrichment_add_a_link_select_join.png)

Na saída desta atividade de enriquecimento, o schema temporário conterá o link para a tabela de países:

![](assets/enrichment_external_link_schema.png)

## Reconciliação dos dados {#data-reconciliation}

A atividade de enriquecimento pode ser usada para configurar a reconciliação de dados, incluindo quando os dados tiverem sido carregados no banco de dados. Nesse caso, a guia **[!UICONTROL Reconciliation]** permite definir o link entre os dados no banco de dados do Adobe Campaign e os dados na tabela de trabalho.

Selecione a opção **[!UICONTROL Identify the targeting document based on work data]**, especifique o schema em que deseja criar um link e defina as condições de ligação: para fazer isto, selecione os campos a serem reconciliados nos dados de trabalho (**[!UICONTROL Source expression]**) e na targeting dimension (**[!UICONTROL Destination expression]**).

É possível usar um ou mais critérios de reconciliação.

![](assets/enrichment_reconciliations_tab_01.png)

Se várias condições de associação forem especificadas, TODAS elas deverão ser verificadas para que os dados possam ser vinculados.

## Inserção de uma proposta de oferta {#inserting-an-offer-proposition}

A atividade de enriquecimento permite adicionar ofertas ou links para ofertas de recipients de delivery.

Para obter mais informações sobre a atividade de enriquecimento, consulte esta [seção](enrichment.md).

Por exemplo, é possível enriquecer os dados de uma query de recipient antes de um delivery.

![](assets/int_enrichment_offer1.png)

Após configurar sua query (consulte esta [seção](query.md)):

1. Adicione e abra uma atividade de enriquecimento.
1. Na guia **[!UICONTROL Enrichment]**, selecione **[!UICONTROL Add data]**.
1. Selecione **[!UICONTROL An offer proposition]** nos tipos de dados para adicionar.

   ![](assets/int_enrichment_offer2.png)

1. Especifique um identificador e um rótulo para a proposta que será adicionada.
1. Especifique a seleção da oferta. Há duas opções possíveis para isso:

   * **[!UICONTROL Search for the best offer in a category]**: marque esta opção e especifique os parâmetros de chamada do mecanismo de oferta (espaços de oferta, categoria ou tema(s), data de contato, número de ofertas a serem mantidas). O mecanismo calculará automaticamente as ofertas para adicionar de acordo com esses parâmetros. Recomendamos completar o campo **[!UICONTROL Category]** ou o campo **[!UICONTROL Theme]**, em vez de ambos ao mesmo tempo.

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]**: marque esta opção e especifique um espaço de ofertas, uma oferta específica e uma data de contato para configurar diretamente a oferta que deseja adicionar, sem chamar o mecanismo de oferta.

      ![](assets/int_enrichment_offer4.png)

1. Em seguida, configure uma atividade de delivery que corresponda ao canal escolhido. Consulte [Deliveries entre canais](cross-channel-deliveries.md).

   O número de propostas disponíveis para pré-visualizar depende da configuração executada na atividade de enriquecimento, ao invés de qualquer configuração possível executada diretamente no delivery.

Para especificar propostas de oferta, também é possível optar por referenciar um link para uma oferta. Para obter mais informações, consulte a seguinte seção [Referência a um link para uma oferta](#referencing-a-link-to-an-offer).

## Referenciar um link para uma oferta {#referencing-a-link-to-an-offer}

Também é possível referenciar um link para uma oferta em uma atividade de enriquecimento.

Para fazer isso:

1. Selecione **[!UICONTROL Add data]** na guia **[!UICONTROL Enrichment]** da atividade.
1. Na janela onde você escolhe o tipo de dados a serem adicionados, selecione **[!UICONTROL A link]**.
1. Selecione o tipo de link que deseja estabelecer, assim como seu target. Nesse caso, o target é o schema de oferta.

   ![](assets/int_enrichment_link1.png)

1. Especifique a ligação entre os dados da tabela de entrada na atividade de enriquecimento (aqui a tabela de recipients) e a tabela de ofertas. Por exemplo, é possível vincular um código de oferta a um recipient.

   ![](assets/int_enrichment_link2.png)

1. Em seguida, configure uma atividade de delivery que corresponda ao canal escolhido. Consulte [Deliveries entre canais](cross-channel-deliveries.md).

   >[!NOTE]
   >
   >O número de propostas disponíveis para a pré-visualização depende da configuração realizada no delivery.

## Armazenamento de classificações e pesos de ofertas {#storing-offer-rankings-and-weights}

Por padrão, quando uma atividade de **enriquecimento** é usada para delivery de ofertas, suas classificações e seus pesos não são armazenados na tabela de propostas.

A atividade **[!UICONTROL Offer engine]** armazena essas informações por padrão.

No entanto, é possível armazenar essas informações da seguinte maneira:

1. Crie uma chamada para o mecanismo de oferta em uma atividade de enriquecimento feita após uma query e antes de uma atividade de delivery.
1. Na janela principal da atividade, selecione **[!UICONTROL Edit additional data...]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Adicione as colunas **[!UICONTROL @rank]** para a classificação e **[!UICONTROL @weight]** para o peso da oferta.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Confirme sua adição e salve seu workflow.

O delivery armazena automaticamente a classificação e o peso das ofertas. Essas informações estão visíveis na guia **[!UICONTROL Offers]** do delivery.
