---
title: Gestão de respostas
seo-title: Gestão de respostas
description: Gestão de respostas
seo-description: null
page-status-flag: never-activated
uuid: 329e2f4a-c5bc-4654-bdef-71a0818fc2b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: affecd87-00a3-4d50-92d3-31ac6228948b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Gestão de respostas{#managing-answers}

## Armazenamento de respostas coletadas {#storing-collected-answers}

Além dos modos de armazenamento padrão comuns a todos os formulários Web no Adobe Campaign (campo de banco de dados e variável local), as pesquisas permitem a extensão dinâmica do modelo de dados usando campos arquivados.

>[!CAUTION]
>
>Esta opção está disponível somente para aplicações Web do tipo **Pesquisa.** Não é oferecido para outros tipos de formulários Web.

### Armazenamento em um campo arquivado {#storing-in-an-archived-field}

É fácil estender o template de dados adicionando novos espaços de armazenamento para salvar as respostas fornecidas em pesquisas. To do this, select the **[!UICONTROL Store answers to a question]** option when creating the input field. Click the **[!UICONTROL New field...]** link and give its properties:

![](assets/s_ncs_admin_survey_new_space.png)

Insira o rótulo e o nome do campo e selecione o tipo de campo: Texto, Booliano, Número inteiro ou decimal, Data etc.

O tipo de campo selecionado envolve um controle dos dados quando as respostas são inseridas por usuários. Para campos de **texto** , é possível adicionar uma restrição (caso, formato) ou um link a uma enumeração existente para forçar a seleção.

Para adicionar uma restrição, selecione-a na lista suspensa. Há dois tipos de restrições:

1. Caixa de caracteres

   As informações inseridas podem ser armazenadas no campo nos seguintes formatos: todas maiúsculas, todas minúsculas ou com letra inicial maiúscula. Essa restrição não exige que o usuário insira os dados no formato selecionado, mas o conteúdo inserido no campo será convertido quando salvo.

1. Formato dos dados

If this field is used in a list, the values of the enumeration can be retrieved automatically in the table of values using the **[!UICONTROL Initialize the list of values from the database]** link above the list of values.

Por exemplo, você pode criar uma lista suspensa para o usuário selecionar seu idioma nativo. O campo arquivado correspondente pode ser associado à enumeração de **idioma** que contém uma lista de idiomas:

![](assets/s_ncs_admin_survey_database_values_2b.png)

The **[!UICONTROL Edit link]** icon located to the right of the field lets you edit the content of this enumeration:

![](assets/s_ncs_admin_survey_database_values_2c.png)

Na **[!UICONTROL General]** guia do campo, o **[!UICONTROL Initialize the list of values from the database]** link permite que você insira automaticamente a lista de rótulos oferecidos.

![](assets/s_ncs_admin_survey_database_values_2.png)

**Exemplo**: armazenamento dos contratos de um recipient em um campo

To store different types of contracts in one field, create a **[!UICONTROL Text]** input field and select the **[!UICONTROL Store answers to a question]** option.

Click the **[!UICONTROL New field...]** link and enter the field properties. Select the **[!UICONTROL Multiple values]** option to enable several values to be stored.

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

Crie campos de entrada para outros contratos e armazene os dados no mesmo campo arquivado.

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

When users approve the survey, their answers will be stored in the **[!UICONTROL Contracts]** field.

Em nosso exemplo, para as seguintes respostas:

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

O perfil do entrevistado conterá os quatro contratos inseridos.

They can be viewed in the **[!UICONTROL Answers]** tab of the survey by displaying the relevant columns.

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

Você também pode filtrar recipients com base em respostas para exibir apenas os usuários que interessam a você. To do this, create a targeting workflow and use the **[!UICONTROL Survey responses]** box.

![](assets/s_ncs_admin_survey_read_responses_wf.png)

Crie o query com base nos perfis que você deseja recuperar. No exemplo a seguir, o query permite selecionar perfis com pelo menos dois contratos, incluindo um contrato do tipo A.

![](assets/s_ncs_admin_survey_read_responses_edit.png)

Para cada formulário, as respostas fornecidas podem ser usadas em campos ou rótulos. Use a sintaxe a seguir para o conteúdo armazenado em um campo arquivado:

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>Para outros tipos de campos, a sintaxe é detalhada [nesta seção](../../platform/using/about-queries-in-campaign.md).

### Configurações de armazenamento {#storage-settings}

É possível arquivar respostas para pesquisas em formato XML. This lets you save a raw copy of the answers collected, which can be useful in case of excessive standardization of the data in an itemized list (for more on this, refer to [Standardizing data](../../web/using/publish--track-and-use-collected-data.md#standardizing-data)).

>[!CAUTION]
>
>O arquivamento de respostas brutas aumenta significativamente o espaço de armazenamento necessário. Use essa opção com cuidado.

Para fazer isso:

* Edite as propriedades da pesquisa pelo **[!UICONTROL Properties]** botão da **[!UICONTROL Edit]** guia.
* Clique no **[!UICONTROL Advanced parameters]** link e marque a **[!UICONTROL Save a copy of raw answers]** opção.

![](assets/s_ncs_admin_survey_xml_archive_option.png)

Você pode habilitá-lo por padrão para todas as pesquisas (esta opção é aplicada quando a pesquisa é publicada). To do this, create the **[!UICONTROL NmsWebApp_XmlBackup]** option and assign value **[!UICONTROL 1]** to it, as shown below:

![](assets/s_ncs_admin_survey_xml_global_option.png)

## Gestão de pontuação {#score-management}

Você pode atribuir uma pontuação às opções oferecidas nas páginas do formulário. As pontuações só podem ser vinculadas a perguntas fechadas: caixa de seleção, valor de uma lista suspensa, subscrição e etc.

>[!CAUTION]
>
>A gestão de pontuação está disponível somente para **Pesquisas** .

![](assets/s_ncs_admin_survey_score_create.png)

The scores are accumulated and saved on the server side when the page is confirmed, i.e. when the user clicks the **[!UICONTROL Next]** or **[!UICONTROL Finish]** button.

>[!NOTE]
>
>Você pode usar valores positivos ou negativos, inteiros ou não inteiros.

As pontuações podem ser usadas em testes ou scripts.

>[!CAUTION]
>
>As pontuações não podem ser usadas nas condições de visibilidade para campos que estão na mesma página. No entanto, elas podem ser usadas nas páginas subsequentes.

* To use scores in tests, use the **[!UICONTROL Score]** field in the test calculation formula, as shown below:

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* Você pode usar a pontuação em um script.

**Exemplo**: calcule uma pontuação e use-a como uma condição para a exibição da próxima página:

* Em uma pesquisa, a próxima página permite atribuir pontuações diferentes aos usuários, dependendo do valor selecionado na lista suspensa:

   ![](assets/s_ncs_admin_survey_score_exa.png)

* Você pode combinar essa pontuação com um segundo valor, dependendo da opção selecionada:

   ![](assets/s_ncs_admin_survey_score_exb.png)

* When the user clicks the **[!UICONTROL Next]** button, the two values are added up.

   ![](assets/s_ncs_admin_survey_score_exe.png)

* As condições podem ser aplicadas para que a página seja exibida de acordo com a pontuação. Isso é configurado da seguinte maneira:

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

