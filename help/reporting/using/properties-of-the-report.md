---
title: Propriedades do relatório
description: Saiba mais sobre as configurações de propriedades do relatório
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
translation-type: tm+mt
source-git-commit: b0b9a0714075474bf52c3eed78d45bcef25b44fc
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 50%

---


# Propriedades do relatório{#properties-of-the-report}

É possível personalizar e configurar completamente seu relatório para atender qualquer necessidade. Para fazer isso, edite suas propriedades. Report properties are accessed via the **[!UICONTROL Properties]** button above the activity sequence chart.

![](assets/s_ncs_advuser_report_properties_01.png)

As propriedades gerais estão descritas abaixo. Os recursos avançados configurados nas guias **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** e **[!UICONTROL Scripts]** estão descritos [nesta seção](../../reporting/using/advanced-functionalities.md).

## Propriedades gerais {#overall-properties}

Na **[!UICONTROL General]** guia das propriedades do relatório, é possível editar as configurações listadas abaixo:

* O rótulo e o nome interno do relatório. O **[!UICONTROL Internal name]** é usado no URL final do relatório. Não deve ser alterado após a criação do relatório.

* A **Pasta** do relatório é selecionada durante a criação do relatório. Uma prática recomendada é criar uma pasta dedicada para relatórios personalizados para que eles não sejam misturados com relatórios [](../../reporting/using/about-campaign-built-in-reports.md)incorporados.

* O **Armazenamento** é selecionado ao criar o relatório. To change the data table of the report, click the **[!UICONTROL Select link]** icon to the right of the **[!UICONTROL Document type]** field.

   ![](assets/s_ncs_advuser_report_properties_02.png)

* Os parâmetros do **Controle de acesso** . Essas configurações estão descritas abaixo.

## Controlling access to the report {#report-accessibility}

Um relatório pode ser acessado no console do Adobe Campaign ou com um navegador da Web. Nesse caso, pode ser necessário configurar o controle de acesso do relatório conforme mostrado abaixo.

![](assets/s_ncs_advuser_report_properties_02b.png)

As opções possíveis são:

* **[!UICONTROL Anonymous access]**: essa opção permite o acesso irrestrito ao relatório. No entanto, nenhuma manipulação é possível.

   Os direitos do operador técnico &quot;webapp&quot; são usados para exibir elementos de relatório. Saiba mais [nesta seção](../../platform/using/access-management.md#default-operators).

* **[!UICONTROL Access control]**: essa opção permite que os operadores Adobe Campaign acessem-no depois que estiverem conectados.
* **[!UICONTROL Specific account]**: essa opção permite que você execute o relatório com os direitos do operador selecionado no **[!UICONTROL Operator]** campo.

## Gerenciamento da localização do relatório {#managing-report-localization}

É possível configurar os idiomas para os quais deseja que o relatório seja traduzido. Para fazer isso, clique na guia **[!UICONTROL Localization]**.

![](assets/s_ncs_advuser_report_properties_06.png)

O idioma de edição é o idioma escrito. Quando adicionar um idioma, a subguia aparece na página de edição do relatório.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Para obter mais informações sobre a localização da página da Web na Campanha, consulte [esta seção](../../web/using/translating-a-web-form.md).

## Personalização da renderização HTML {#personalizing-html-rendering}

Na guia **[!UICONTROL Rendering]**, é possível personalizar o modo de exibição de dados da página. É possível selecionar:

* Mecanismo de renderização de gráfico: o Adobe Campaign oferece dois modos diferentes para realizar a renderização do gráfico. Por padrão, o mecanismo de renderização é HTML 5. Se necessário, é possível selecionar renderização Flash.
* O tipo de navegação no relatório: por botões ou links.
* A posição padrão dos rótulos para elementos do relatório. Essa posição pode ser sobrescrita em cada elemento.
* O template ou tema usado para gerar páginas de relatório.

![](assets/s_ncs_advuser_report_properties_08.png)

## Personalização da página de erro {#personalizing-the-error-page}

A guia **[!UICONTROL Error page]** permite configurar a mensagem que aparecerá no caso de erro na exibição do relatório.

É possível definir textos e vinculá-los a identificadores específicos para gerenciar a localização do relatório. Para obter mais informações, consulte [Adicionar um cabeçalho e um rodapé](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
