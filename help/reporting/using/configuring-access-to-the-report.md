---
title: Configuração do acesso ao relatório
seo-title: Configuração do acesso ao relatório
description: Configuração do acesso ao relatório
seo-description: null
page-status-flag: never-activated
uuid: d32d9805-f84f-457f-b37b-a8278642336a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: dd50ca25-8fa2-48fa-84cc-a63e476701a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Configuração do acesso ao relatório{#configuring-access-to-the-report}

## Contexto de exibição do relatório {#report-display-context}

Define the display context of the report in the Adobe Campaign platform using the **[!UICONTROL Display]** tab. O acesso a um relatório depende do tipo de seleção, das condições de exibição e das autorizações de acesso.

### Tipo de seleção {#selection-type}

O acesso ao relatório pode ser limitado a um contexto específico ou a um espaço de ofertas, por exemplo, uma entrega, um destinatário, uma seleção de destinatários etc. Esse acesso é configurado na **[!UICONTROL Selection type]** seção da **[!UICONTROL Display]** guia.

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** : o relatório só é acessível quando uma entidade específica é selecionada.
* **[!UICONTROL Multiple selection]** : o relatório é acessado quando várias entidades são selecionadas.
* **[!UICONTROL Global]** : o relatório é acessado por meio da lista de relatórios disponíveis no universo de Relatórios.

### Sequência de exibição {#display-sequence}

The **[!UICONTROL Sequence]** field lets you enter a numeric value that specifies the display sequence of the report in the list.

Por padrão, os relatórios são exibidos por relevância: o valor inserido neste campo permite classificar relatórios do mais alto (valor mais alto) para o menor (valor menor) relevante.

Você pode selecionar a escala a ser usada com base nas suas necessidades: 1 a 10, 0 a 100, -10 a 10, etc.

### Condições de exibição {#display-conditions}

Também é possível determinar as condições de exibição do relatório por meio de uma query.

![](assets/s_ncs_advuser_report_visibility_5.png)

No exemplo a seguir, o relatório é exibido se o canal principal da campanha for email.

![](assets/s_ncs_advuser_report_visibility_6.png)

Isso significa que, se o canal principal da campanha for mala direta, o relatório não estará disponível nos relatórios da campanha.

### Autorização de acesso {#access-authorization}

O relatório pode ser compartilhado com outros operadores.

Para tornar o relatório acessível, selecione a **[!UICONTROL Report shared with other operators]** opção. Se essa opção não estiver selecionada, somente o operador que criou o relatório poderá acessá-lo.

O relatório também pode ser compartilhado com operadores ou grupos de operadores específicos adicionados pela janela de autorizações.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Definição das opções de filtro {#defining-the-filtering-options}

The **[!UICONTROL Reports]** universe displays all available reports in the platform and for which the connected operator has an access right.

Por padrão, eles são classificados por relevância, mas é possível aplicar outros tipos de filtros: alfabético, por idade, etc.

Também é possível filtrar a exibição com base na categoria do relatório:

![](assets/report_ovv_select_type.png)

To define the category of a report, select it via the **[!UICONTROL Display]** tab, as shown below:

![](assets/report_select_category.png)

É possível inserir uma nova categoria aqui e adicioná-la à lista de categorias disponíveis. A numeração correspondente é atualizada automaticamente.

## Criação de um link para um relatório {#creating-a-link-to-a-report-}

É possível tornar um relatório acessível por meio de um nó específico da árvore, como uma lista, um recipient, um delivery, etc. Para fazer isso, basta criar um link para o relatório em questão e especificar a entidade onde deseja torná-lo disponível.

Como exemplo, vamos criar um link para um relatório para torná-lo acessível por meio de uma lista de recipients.

1. Clique **[!UICONTROL New]** e selecione **[!UICONTROL Create a link to an existing report]** no assistente de criação de relatórios.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Selecione o relatório que deseja criar um link usando a lista suspensa. Neste exemplo, vamos selecionar o relatório **Análise por país**.

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Insira um rótulo e selecione o schema. Neste exemplo, vamos selecionar a tabela de lista de recipients.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Isso significa que o relatório estará acessível por meio de qualquer lista de recipients e que as estatísticas abordarão os recipients na lista selecionada.

1. Salvamento e exibição seu relatório
1. Insira a chave do link. Nesse caso, a chave externa do link &quot;Folders&quot;.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Publique seu relatório.
1. Go to one of your recipient lists and click the **[!UICONTROL Reports]** link: the report you have just created is accessible.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Pré-visualização do relatório {#preview-of-the-report}

Before publishing your report, make sure it is displayed correctly in the **[!UICONTROL Preview]** tab.

![](assets/s_ncs_advuser_report_preview_01.png)

To display the preview of the report, select the **[!UICONTROL Global]** or the **[!UICONTROL Selection]** option.

Essas duas opções são selecionadas com base nas configurações de exibição do relatório. If the display setting is **[!UICONTROL Global]**, you need to select the **[!UICONTROL Global]** preview option. Se as configurações de exibição forem **[!UICONTROL Single selection]** ou **[!UICONTROL Multiple selection]**, a opção de **[!UICONTROL Selection]** visualização deverá estar selecionada.

Para obter mais informações, consulte o contexto [de exibição do](#report-display-context)Relatório.

As configurações específicas permitem controlar erros. A configuração **_uuid** é encontrada na URL do relatório. É possível adicionar as configurações **configurações &amp;_preview** ou **&amp;_debug**.

Para saber mais sobre essas configurações, consulte a seção **Definição das propriedades dos formulários web** do capítulo de [Formulários web](../../web/using/about-web-forms.md).

## Publicação do relatório {#publishing-the-report}

Publishing the report is mandatory in order to share them with other operators and display them in the list of available reports (also refer to [Report display context](#report-display-context)). Essa operação deve ser executada novamente cada vez que o relatório for alterado.

1. Open the publishing wizard by clicking **[!UICONTROL Publish]** in the toolbar.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Clique **[!UICONTROL Start]** para publicar.

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Click the **[!UICONTROL Enlarge]** icon to open the report in a web browser.

