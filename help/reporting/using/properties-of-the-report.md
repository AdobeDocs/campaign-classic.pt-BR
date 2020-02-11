---
title: Propriedades do relatório
seo-title: Propriedades do relatório
description: Propriedades do relatório
seo-description: null
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Propriedades do relatório{#properties-of-the-report}

## Visão geral {#overview}

É possível personalizar e configurar completamente seu relatório para atender qualquer necessidade. Para fazer isso, edite suas propriedades. As propriedades do relatório são acessadas por meio do botão Propriedade localizado acima do gráfico de sequência de atividades.

![](assets/s_ncs_advuser_report_properties_01.png)

## Propriedades gerais {#overall-properties}

The **[!UICONTROL General]** tab lets you view or alter the label and the schema which the report concerns. Esses elementos são inseridos durante a criação do relatório.

We do not recommend changing the **[!UICONTROL Internal name]** : this is used in the report access URL.

O template do relatório é selecionado durante a criação do relatório e não pode ser alterado posteriormente.

To change the table which the report concerns, click the **[!UICONTROL Select link]** icon to the right of the **[!UICONTROL Document type]** field. To view the available fields in the selected table, click the **[!UICONTROL Magnifier]** icon.

![](assets/s_ncs_advuser_report_properties_02.png)

## Acessibilidade do relatório {#report-accessibility}

Um relatório pode ser acessado além do console do Adobe Campaign, por exemplo, por meio de um navegador da Web. Nesse caso, pode ser necessário configurar o controle de acesso do relatório conforme mostrado abaixo.

![](assets/s_ncs_advuser_report_properties_02b.png)

O princípio geral é o seguinte:

* The **[!UICONTROL Anonymous access]** option enables unrestricted access to the report. No entanto, nenhuma manipulação é possível.

   Os direitos do operador de relatório padrão (&#39;webapp&#39;) são usados para exibir elementos de relatório.

* The **[!UICONTROL Access control]** option enables Adobe Campaign operators to access it once they are logged on.
* The **[!UICONTROL Specific account]** option lets you execute the report with the rights of the operator selected in the **[!UICONTROL Operator]** field.

As propriedades do formulário da Web são detalhadas [nesta página](../../web/using/about-web-forms.md).

## Gerenciamento da localização do relatório {#managing-report-localization}

É possível configurar os idiomas para os quais deseja que o relatório seja traduzido. To do this, click the **[!UICONTROL Localization]** tab.

![](assets/s_ncs_advuser_report_properties_06.png)

O idioma de edição é o idioma escrito. Quando adicionar um idioma, a subguia aparece na página de edição do relatório.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Para obter mais informações, consulte a seção apropriada [nesta seção](../../web/using/translating-a-web-form.md).

## Personalização da renderização HTML {#personalizing-html-rendering}

In the **[!UICONTROL Rendering]** tab, you can personalize the data display mode for the page. É possível selecionar:

* O mecanismo de renderização do gráfico: O Adobe Campaign oferece dois modos diferentes para gerar a renderização do gráfico. Por padrão, o mecanismo de renderização é HTML 5. Se necessário, é possível selecionar renderização Flash.
* O tipo de navegação no relatório: por botões ou links.
* A posição padrão dos rótulos para elementos do relatório. Essa posição pode ser sobrescrita em cada elemento.
* O template ou tema usado para gerar páginas de relatório.

As propriedades do formulário da Web são detalhadas [nesta página](../../web/using/about-web-forms.md).

![](assets/s_ncs_advuser_report_properties_08.png)

## Definição das configurações adicionais {#defining-additional-settings}

The **[!UICONTROL Settings]** tab lets you create additional settings for the report: these settings will be passed into the URL during the call up.

As propriedades do formulário da Web são detalhadas [nesta página](../../web/using/about-web-forms.md).

>[!CAUTION]
>
>Por motivos de segurança, esses parâmetros devem ser usados com muito cuidado.

Para criar uma nova configuração:

1. Click the **[!UICONTROL Add]** button and enter the name of the setting.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Se necessário, especifique se a configuração será obrigatória ou não.
1. Select the type of setting you want to create: **[!UICONTROL Filter]** or **[!UICONTROL Variable]**.

   The **[!UICONTROL Filter entities]** option lets you use a field of the database as a parameter.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   Os dados são recuperados diretamente no nível da entidade: **ctx/receipt/@account**.

   The **[!UICONTROL Variable]** option lets you create or select a variable which will be passed as a parameter of the URL and can be used in the filters.

## Adição de variáveis {#adding-variables}

The **[!UICONTROL Variables]** tab contains the list of variables configured in the report. Essas variáveis são expostas no contexto do relatório e podem ser utilizadas em cálculos.

Click the **[!UICONTROL Add]** button to create a new variable.

To view the definition of a variable, select it and click the **[!UICONTROL Detail...]** button.

![](assets/s_ncs_advuser_report_properties_10.png)

## Referência de scripts {#referencing-scripts}

The **[!UICONTROL Scripts]** tab lets you reference JavaScript codes that will be executed on the client and/or server side when the report page is called up.

Para execução normal no lado do cliente, os scripts referenciados devem ser escritos em JavaScript e precisam ser compatíveis com a maioria dos navegadores. Para obter mais informações, consulte [esta seção](../../web/using/web-forms-answers.md).

## Personalização da página de erro {#personalizing-the-error-page}

The **[!UICONTROL Error page]** tab lets you configure the message that will come up in case of an error in the report display.

É possível definir textos e vinculá-los a identificadores específicos para gerenciar a localização do relatório. Para obter mais informações, consulte [Adicionar um cabeçalho e um rodapé](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)

