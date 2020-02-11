---
title: Sobre formulários web
seo-title: Sobre formulários web
description: Sobre formulários web
seo-description: null
page-status-flag: never-activated
uuid: 1d129af4-008b-4f6a-9094-b2edd6c1eee1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 3b8e4691-fcbc-48ef-b529-11c9a9a9d788
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Sobre formulários web{#about-web-forms}

O Adobe Campaign integra um módulo gráfico para definir e publicar formulários web a fim de criar páginas contendo campos de entrada e seleção e que possam incluir dados no banco de dados. Isso permite a criação e publicação de páginas da Web onde os usuários podem visualizar ou inserir informações.

Este capítulo detalha a criação e o gerenciamento de formulários web, campos e páginas, assim como os modos de armazenamento e salvamento.

>[!CAUTION]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

## Etapas para criar um formulário web {#steps-for-creating-a-web-form}

Este capítulo detalha as etapas necessárias para criar um formulário do tipo **webForm** no Adobe Campaign, assim como as opções e configurações disponíveis. O Adobe Campaign permite disponibilizar esse formulário web aos usuários, assim como coletar e arquivar respostas no banco de dados.

>[!CAUTION]
>
>Ao configurar aplicativos da Web e formulários da Web, você precisa de uma resolução vertical mínima de 900 pixels (ex: 1600 x 900).

Web forms are accessed via the Web Applications menu of the **Campaigns** tab. In the Adobe Campaign tree, they are grouped under the **[!UICONTROL Resources > Online > Web Applications]** node.

To create a Web form, click the **[!UICONTROL Create]** button above the list of Web applications.

![](assets/webapp_create_new.png)

Select the Web form template ( **[!UICONTROL newWebForm]** by default).

![](assets/s_ncs_admin_survey_select_template.png)

Isso o levará ao painel do formulário.

![](assets/webapp_empty_dashboard.png)

The **[!UICONTROL Edit]** tab lets you create your content.

![](assets/webapp_edit_tab.png)

Para definir a configuração e o conteúdo do formulário Web, siga as etapas abaixo:

* Comece com a criação das páginas e verificações necessárias: os campos de entrada, as listas suspensas, o conteúdo HTML, etc.

   Essa etapa é detalhada abaixo.

* Defina o sequenciamento de páginas e condicione a exibição.

   Essa etapa é detalhada em [Definição de sequenciamento](../../web/using/defining-web-forms-page-sequencing.md)de páginas de formulários da Web.

* Traduza o conteúdo, se necessário.

   Esta etapa é detalhada em [Traduzir um formulário](../../web/using/translating-a-web-form.md)da Web.

## Sobre o design do formulários web {#about-web-forms-designing}

As páginas do formulário são criadas por meio de um editor específico que permite definir e configurar as zonas de entrada (texto), campos de seleção (listas, caixas de seleção, etc.) e elementos estáticos (imagens, conteúdo HTLM, etc.). They can be grouped into containers and their layout altered to suit your needs (for more on this, refer to [Creating containers](../../web/using/defining-web-forms-layout.md#creating-containers)).

As seções a seguir detalham como definir o conteúdo e o layout nas telas do formulário:

* [Inclusão de campos em um formulário web](../../web/using/adding-fields-to-a-web-form.md),
* [Inserção de conteúdo HTML](../../web/using/static-elements-in-a-web-form.md#inserting-html-content),
* [Elementos estáticos em um formulário web](../../web/using/static-elements-in-a-web-form.md),
* [Definição do layout de formulários web](../../web/using/defining-web-forms-layout.md).

>[!NOTE]
>
>* During page design, you can view the final rendering in the **[!UICONTROL Preview]** tab. Para visualizar as alterações, salve o formulário primeiro. Any errors are displayed in the **[!UICONTROL Log]** tab.
>* Para garantir que a exibição da página e o armazenamento de informações ocorram na sequência apropriada, habilite o modo de depuração no formulário Web. To do this, go to the **[!UICONTROL Preview]** sub-tab and check the **[!UICONTROL Enable debug mode]** box: all collected information and possible execution errors will be displayed at the bottom of each page.
>



### Utilização dos ícones na barra de ferramentas {#using-the-icons-in-the-toolbar}

É possível usar os ícones na barra de ferramentas ou um clique com o botão direito do mouse para inserir uma zona de entrada.

![](assets/s_ncs_admin_webform_add_selection.png)

Nesse caso, primeiro selecione o tipo de campo que deve ser adicionado e o modo de armazenamento de resposta.

![](assets/s_ncs_admin_webform_select_storage.png)

Clique em **[!UICONTROL Ok]** para aprovar a seleção.

![](assets/s_ncs_admin_webform_confirm_storage.png)

