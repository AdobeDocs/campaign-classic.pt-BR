---
product: campaign
title: Publicar, rastrear e usar dados coletados
description: Saiba como publicar, rastrear e usar dados coletados em uma pesquisa
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '831'
ht-degree: 100%

---

# Publicar, rastrear e usar dados coletados{#publish-track-and-use-collected-data}



Depois que o formulário tiver sido criado, configurado e publicado, é possível compartilhar o link com o público e acompanhar as respostas.

>[!NOTE]
>
>O ciclo de vida de uma pesquisa no Adobe Campaign, bem como seus modos de publicação e delivery são semelhantes aos dos formulários Web: esses são detalhados [nesta seção](../../web/using/about-web-forms.md).

## Painel de pesquisa {#survey-dashboard}

Cada pesquisa tem seu próprio painel de controle que permite visualizar seu status, descrição, URL pública e cronograma de disponibilidade. Também permite exibir os relatórios disponíveis. [Saiba mais](#reports-on-surveys).

O URL público da pesquisa é mostrado no painel:

![](assets/survey_public_url.png)

## Rastreamento de resposta {#response-tracking}

Você pode rastrear as respostas da pesquisa em logs e relatórios.

### Logs de pesquisa {#survey-logs}

Para cada pesquisa entregue, você pode acompanhar as respostas na guia **[!UICONTROL Logs]**. Essa guia exibe a lista de usuários que concluíram a pesquisa e sua origem:

![](assets/s_ncs_admin_survey_logs.png)

Clique duas vezes em uma linha para exibir o formulário de pesquisa como preenchido pelo entrevistado. Você pode navegar pela pesquisa e acessar as respostas integralmente. Elas podem ser exportadas em um arquivo externo. Para obter mais informações, consulte [Exportação de respostas](#exporting-answers).

A origem é indicada na URL da pesquisa adicionando os seguintes caracteres:

```
?origin=xxx
```

enquanto a pesquisa está sendo editada, o URL contém o parâmetro **[!UICONTROL __uuid]**, indicando que está em uma fase de teste e ainda não online. Ao acessar a pesquisa por meio dessa URL, os registros criados não são considerados no acompanhamento (relatórios). A origem é forçada ao valor **[!UICONTROL Adobe Campaign]**.

Para obter mais informações sobre parâmetros de URL, consulte [esta página](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Relatórios sobre pesquisas {#reports-on-surveys}

A guia do painel permite acessar relatórios de pesquisa. Clique em um nome de relatório para visualizá-lo.

![](assets/s_ncs_admin_survey_report_doc.png)

A estrutura da pesquisa é visível no relatório **[!UICONTROL Documentation]**.

Dois outros relatórios sobre pesquisas na web estão disponíveis na guia **[!UICONTROL Reports]** das pesquisas: **[!UICONTROL General]** e **[!UICONTROL Breakdown of responses]**.

* Geral

   Este relatório contém informações gerais sobre a pesquisa: como o número de respostas é alterado com o tempo e a distribuição por origem e idioma.

   Exemplo de um relatório geral:

   ![](assets/s_ncs_admin_survey_report_0.png)

* Detalhamento das respostas

   Este relatório mostra o detalhamento das respostas para cada pergunta. Esse detalhamento só está disponível para respostas dos campos armazenados em containers do tipo **[!UICONTROL Question]**. É válido apenas para controles de seleção (sem detalhamento em campos de texto, por exemplo).

   ![](assets/s_ncs_admin_survey_report_2.png)

## Exportação de respostas {#exporting-answers}

As respostas de uma pesquisa podem ser exportadas em um arquivo externo para serem processadas posteriormente. Há duas maneiras de fazer isso:

1. Exportação de dados de relatórios

   Para exportar dados do relatório, clique no botão **[!UICONTROL Export]** e escolha o formato de exportação.

   Para obter mais informações sobre exportação de dados de relatórios, consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md).

1. Exportação de respostas

   Para exportar respostas, clique na guia **[!UICONTROL Responses]** da pesquisa e clique com o botão direito do mouse. Selecione **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Em seguida, insira as informações que deseja exportar e o arquivo de armazenamento.

   Você pode configurar o conteúdo e o formato do arquivo de saída no assistente de exportação.

   Isso permite:

   * adicionar colunas ao arquivo de saída e recuperar as informações do recipient (que é armazenado no banco de dados),
   * formatar os dados exportados,
   * selecionar o formato de codificação para as informações no arquivo.

   Se a pesquisa que você deseja exportar contiver vários campos **[!UICONTROL Multi-line text]** ou **[!UICONTROL HTML text]**, ela deve ser exportada no formato **[!UICONTROL XML]**. Para fazer isso, selecione este formato na lista suspensa do campo **[!UICONTROL Output format]**, conforme mostrado abaixo:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Clique em **[!UICONTROL Start]** para executar a exportação.

   >[!NOTE]
   >
   >As exportações de dados e as etapas de configuração são detalhadas [nesta seção](../../platform/using/about-generic-imports-exports.md).

## Utilização de dados coletados {#using-the-collected-data}

As informações coletadas por pesquisas online podem ser recuperadas na estrutura de um fluxo de trabalho de direcionamento. Para fazer isso, use a caixa **[!UICONTROL Survey responses]**.

No exemplo a seguir, queremos fazer uma oferta da Web especialmente para os cinco recipients com pelo menos duas crianças e com as pontuações mais altas em uma pesquisa online. As respostas para essa pesquisa são:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

No workflow para construção do target, as **[!UICONTROL Survey responses]** serão configuradas da seguinte maneira:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Comece selecionando a pesquisa relacionada e os dados a serem extraídos na seção central da janela. Nesse caso, precisamos extrair pelo menos a coluna de pontuação, pois ela será usada na caixa de divisão para recuperar as cinco pontuações mais altas.

Indique as condições de filtragem para respostas clicando no link **[!UICONTROL Edit query...]**.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Inicie o workflow para construção do target. O query recupera 8 recipients.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Clique com o botão direito do mouse na transição de saída da caixa de coleção para exibi-los.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Em seguida, coloque uma caixa de divisão no workflow para recuperar os 5 recipients com a pontuação mais alta.

Edite a caixa de divisão para configurá-la:

* Comece selecionando o schema adequado na guia **[!UICONTROL General]** e configure o subconjunto:

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Acesse a guia **[!UICONTROL Sub-sets]** e selecione a opção **[!UICONTROL Limit the selected records]**; depois, clique no link **[!UICONTROL Edit...]**.

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Selecione a opção **[!UICONTROL Keep only the first records after sorting]** e selecione a coluna de classificação. Marque a opção **[!UICONTROL Descending sort]**.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Clique no botão **[!UICONTROL Next]** e limite o número de registros a 5.

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Clique em **[!UICONTROL Finish]** e reinicie o workflow para aprovar o target.

## Padronização de dados {#standardizing-data}

É possível configurar processos de padronização no Adobe Campaign para dados coletados usando aliases. Permite padronizar os dados armazenados no banco de dados: para fazer isso, defina aliases nas listas discriminadas que contêm as informações relevantes. [Saiba mais](../../platform/using/managing-enumerations.md#about-enumerations)
