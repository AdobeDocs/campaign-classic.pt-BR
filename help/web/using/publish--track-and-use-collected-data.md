---
title: Publicar, acompanhar e usar dados coletados
seo-title: Publicar, acompanhar e usar dados coletados
description: Publicar, acompanhar e usar dados coletados
seo-description: null
page-status-flag: never-activated
uuid: eac16f2c-0423-4727-a2da-3af1d6c616ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 434a4bda-0907-42a7-8a75-2db658bba046
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Publicar, acompanhar e usar dados coletados{#publish-track-and-use-collected-data}

Depois que o formulário for criado, configurado e publicado, você poderá compartilhar o link com seu público-alvo e rastrear as respostas.

>[!NOTE]
>
>O ciclo de vida de uma pesquisa no Adobe Campaign, bem como seus modos de publicação e delivery são semelhantes aos dos formulários Web: esses são detalhados [nesta seção](../../web/using/about-web-forms.md).

## Painel de pesquisa {#survey-dashboard}

Cada pesquisa tem seu próprio painel de controle que permite visualizar seu status, descrição, URL pública e cronograma de disponibilidade. Também permite exibir os relatórios disponíveis. For more on this, refer to [Reports on surveys](#reports-on-surveys).

A URL pública da pesquisa é mostrada no painel:

![](assets/survey_public_url.png)

## Acompanhamento de resposta {#response-tracking}

Você pode acompanhar as respostas da pesquisa em logs e relatórios.

### Logs de pesquisa {#survey-logs}

For each survey delivered, you can track the responses in the **[!UICONTROL Logs]** tab. Essa guia exibe a lista de usuários que concluíram a pesquisa e sua origem:

![](assets/s_ncs_admin_survey_logs.png)

Clique duas vezes em uma linha para exibir o formulário de pesquisa como preenchido pelo entrevistado. Você pode navegar pela pesquisa e acessar as respostas integralmente. Elas podem ser exportadas em um arquivo externo. For more on this, refer to [Exporting answers](#exporting-answers).

A origem é indicada na URL da pesquisa adicionando os seguintes caracteres:

```
?origin=xxx
```

while the survey is being edited, its URL contains the parameter **[!UICONTROL __uuid]**, which indicates that it is in a test phase and not yet online. Ao acessar a pesquisa por meio dessa URL, os registros criados não são considerados no acompanhamento (relatórios). The origin is forced to the value **[!UICONTROL Adobe Campaign]**.

Para obter mais informações sobre os parâmetros da URL, consulte [esta página](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Relatórios sobre pesquisas {#reports-on-surveys}

A guia do painel permite acessar relatórios de pesquisa. Clique em um nome de relatório para visualizá-lo.

![](assets/s_ncs_admin_survey_report_doc.png)

The structure of the survey is visible in the **[!UICONTROL Documentation]** report.

Two other reports on Web surveys are available in the **[!UICONTROL Reports]** tab of the surveys: **[!UICONTROL General]** and **[!UICONTROL Breakdown of responses]**.

* Geral

   Este relatório contém informações gerais sobre a pesquisa: como o número de respostas é alterado com o tempo e a distribuição por origem e idioma.

   Exemplo de um relatório geral:

   ![](assets/s_ncs_admin_survey_report_0.png)

* Detalhamento das respostas

   Este relatório mostra o detalhamento das respostas para cada pergunta. This breakdown is only available for answers given to fields stored in **[!UICONTROL Question]** type containers. É válido apenas para controles de seleção (sem detalhamento em campos de texto, por exemplo).

   ![](assets/s_ncs_admin_survey_report_2.png)

## Exportação de respostas {#exporting-answers}

As respostas de uma pesquisa podem ser exportadas em um arquivo externo para serem processadas posteriormente. Há duas maneiras de fazer isso:

1. Exportação de dados de relatórios

   To export report data, click the **[!UICONTROL Export]** button and choose the export format.

   Para obter mais informações sobre exportação de dados de relatórios, consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md).

1. Exportação de respostas

   To export answers, click the **[!UICONTROL Responses]** tab of the survey and right-click. Select **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Em seguida, insira as informações que deseja exportar e o arquivo de armazenamento.

   Você pode configurar o conteúdo e o formato do arquivo de saída no assistente de exportação.

   Isso permite:

   * adicionar colunas ao arquivo de saída e recuperar as informações do recipient (que é armazenado no banco de dados),
   * formatar os dados exportados,
   * selecionar o formato de codificação para as informações no arquivo.
   If the survey you want to export contains several **[!UICONTROL Multi-line text]** or **[!UICONTROL HTML text]** fields, it has to be exported in **[!UICONTROL XML]** format. To do this, select this format in the drop-down list of the **[!UICONTROL Output format]** field, as shown below:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Clique em **[!UICONTROL Start]** para executar a exportação.

   >[!NOTE]
   >
   >As exportações de dados e as etapas de sua configuração são detalhadas [nesta seção](../../platform/using/generic-imports-and-exports.md).

## Uso dos dados coletados {#using-the-collected-data}

As informações coletadas por pesquisas online podem ser recuperadas dentro da estrutura de um workflow para construção do target. Para fazer isso, use a **[!UICONTROL Survey responses]** caixa.

No exemplo a seguir, queremos fazer uma oferta da Web especialmente para os cinco recipients com pelo menos duas crianças e com as pontuações mais altas em uma pesquisa online. As respostas para essa pesquisa são:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

In the targeting workflow, the **[!UICONTROL Survey responses]** will be configured as follows:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Comece selecionando a pesquisa relacionada e os dados a serem extraídos na seção central da janela. Nesse caso, precisamos extrair pelo menos a coluna de pontuação, pois ela será usada na caixa de divisão para recuperar as cinco pontuações mais altas.

Indicate the filtering conditions for answers by clicking the **[!UICONTROL Edit query...]** link.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Inicie o workflow para construção do target. O query recupera 8 recipients.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Clique com o botão direito do mouse na transição de saída da caixa de coleção para exibi-los.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Em seguida, coloque uma caixa de divisão no workflow para recuperar os 5 recipients com a pontuação mais alta.

Edite a caixa de divisão para configurá-la:

* Start by selecting the adequate schema in the **[!UICONTROL General]** tab, then configure the sub-set:

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Vá para a guia **[!UICONTROL Sub-sets]** , selecione a **[!UICONTROL Limit the selected records]** opção e clique no **[!UICONTROL Edit...]** link.

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Selecione a **[!UICONTROL Keep only the first records after sorting]** opção e selecione a coluna de classificação. Marque a **[!UICONTROL Descending sort]** opção.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Click the **[!UICONTROL Next]** button and limit the number of records to 5.

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Click **[!UICONTROL Finish]** then restart the workflow to approve targeting.

## Padronização de dados {#standardizing-data}

É possível configurar processos de padronização no Adobe Campaign para dados coletados usando aliases. Isso permite padronizar os dados armazenados no banco de dados: para fazer isso, defina aliases nas listas discriminadas que contêm as informações relevantes.

Para obter mais informações, consulte [esta página](../../platform/using/managing-enumerations.md#about-enumerations).
