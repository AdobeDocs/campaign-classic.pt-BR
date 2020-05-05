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
translation-type: ht
source-git-commit: b2222b2997105801164f930428c7b05ae7d11336

---


# Propriedades do relatório{#properties-of-the-report}

## Visão geral {#overview}

É possível personalizar e configurar completamente seu relatório para atender qualquer necessidade. Para fazer isso, edite suas propriedades. As propriedades do relatório são acessadas por meio do botão Propriedade localizado acima do gráfico de sequência de atividades.

![](assets/s_ncs_advuser_report_properties_01.png)

## Propriedades gerais {#overall-properties}

A guia **[!UICONTROL General]** permite visualizar ou alterar o rótulo e o schema abordados pelo relatório. Esses elementos são inseridos durante a criação do relatório.

Não é recomendável alterar o **[!UICONTROL Internal name]**: ele é usado no URL de acesso do relatório.

O template do relatório é selecionado durante a criação do relatório e não pode ser alterado posteriormente.

Para alterar a tabela que o relatório aborda, clique no **[!UICONTROL Select link]** ícone à direita do campo **[!UICONTROL Document type]**. Para exibir os campos disponíveis na tabela selecionada, clique no ícone **[!UICONTROL Magnifier]**.

![](assets/s_ncs_advuser_report_properties_02.png)

## Acessibilidade do relatório {#report-accessibility}

Um relatório pode ser acessado além do console do Adobe Campaign, por exemplo, por meio de um navegador da Web. Nesse caso, pode ser necessário configurar o controle de acesso do relatório conforme mostrado abaixo.

![](assets/s_ncs_advuser_report_properties_02b.png)

O princípio geral é o seguinte:

* A opção **[!UICONTROL Anonymous access]** permite acesso irrestrito ao relatório. No entanto, nenhuma manipulação é possível.

   Os direitos do operador de relatório padrão (&#39;webapp&#39;) são usados para exibir elementos de relatório.

* A opção **[!UICONTROL Access control]** permite que os operadores do Adobe Campaign acessem o relatório quando estiverem conectados.
* A opção **[!UICONTROL Specific account]** permite executar o relatório com os direitos do operador selecionados no campo **[!UICONTROL Operator]**.

As propriedades do formulário da Web são detalhadas [nesta página](../../web/using/about-web-forms.md).

## Gerenciamento da localização do relatório {#managing-report-localization}

É possível configurar os idiomas para os quais deseja que o relatório seja traduzido. Para fazer isso, clique na guia **[!UICONTROL Localization]**.

![](assets/s_ncs_advuser_report_properties_06.png)

O idioma de edição é o idioma escrito. Quando adicionar um idioma, a subguia aparece na página de edição do relatório.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Para obter mais informações, consulte a seção apropriada [nesta seção](../../web/using/translating-a-web-form.md).

## Personalização da renderização HTML {#personalizing-html-rendering}

Na guia **[!UICONTROL Rendering]**, é possível personalizar o modo de exibição de dados da página. É possível selecionar:

* Mecanismo de renderização de gráfico: o Adobe Campaign oferece dois modos diferentes para realizar a renderização do gráfico. Por padrão, o mecanismo de renderização é HTML 5. Se necessário, é possível selecionar renderização Flash.
* O tipo de navegação no relatório: por botões ou links.
* A posição padrão dos rótulos para elementos do relatório. Essa posição pode ser sobrescrita em cada elemento.
* O template ou tema usado para gerar páginas de relatório.

As propriedades do formulário da Web são detalhadas [nesta página](../../web/using/about-web-forms.md).

![](assets/s_ncs_advuser_report_properties_08.png)

## Definição das configurações adicionais {#defining-additional-settings}

A guia **[!UICONTROL Parameters]** permite criar configurações adicionais para o relatório: essas configurações serão repassadas para o URL durante a chamada.

As propriedades do formulário da Web são detalhadas [nesta página](../../web/using/about-web-forms.md).

>[!CAUTION]
>
>Por motivos de segurança, esses parâmetros devem ser usados com muito cuidado.

Para criar uma nova configuração:

1. Clique no botão **[!UICONTROL Add]** e digite o nome da configuração.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Se necessário, especifique se a configuração será obrigatória ou não.
1. Selecione o tipo de configuração que deseja criar: **[!UICONTROL Filter]** ou **[!UICONTROL Variable]**.

   A opção **[!UICONTROL Filter entities]** permite usar um campo do banco de dados como parâmetro.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   Os dados são recuperados diretamente no nível da entidade: **ctx/receipt/@account**.

   A opção **[!UICONTROL Variable]** permite criar ou selecionar uma variável que será passada como parâmetro do URL e pode ser usada nos filtros.

O **[!UICONTROL Response HTTP headers]** permite que você evite o recurso de clickjacking ao incluir a página do seu relatório em uma página HTML usando o iframe. Para evitar o clickjacking, você pode escolher o comportamento **[!UICONTROL X-Frame-options header]**:

* **[!UICONTROL None]**: O relatório não terá **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Definido por padrão para novos relatórios e relatórios republicados. O nome do host será igual ao URL do relatório.
* **[!UICONTROL Deny]**: O relatório não pode ser incluído em uma página HTML usando iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Adição de variáveis {#adding-variables}

A guia **[!UICONTROL Variables]** contém a lista de variáveis configuradas no relatório. Essas variáveis são expostas no contexto do relatório e podem ser utilizadas em cálculos.

Clique no botão **[!UICONTROL Add]** para criar uma nova variável.

Para exibir a definição de uma variável, selecione-a e clique no botão **[!UICONTROL Detail...]**.

![](assets/s_ncs_advuser_report_properties_10.png)

## Referência de scripts {#referencing-scripts}

A guia **[!UICONTROL Scripts]** permite referenciar códigos JavaScript que serão executados no cliente e/ou no lado do servidor quando a página do relatório for chamada.

Para execução normal no lado do cliente, os scripts referenciados devem ser escritos em JavaScript e precisam ser compatíveis com a maioria dos navegadores. Para obter mais informações, consulte [esta seção](../../web/using/web-forms-answers.md).

## Personalização da página de erro {#personalizing-the-error-page}

A guia **[!UICONTROL Error page]** permite configurar a mensagem que aparecerá no caso de erro na exibição do relatório.

É possível definir textos e vinculá-los a identificadores específicos para gerenciar a localização do relatório. Para obter mais informações, consulte [Adicionar um cabeçalho e um rodapé](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)

