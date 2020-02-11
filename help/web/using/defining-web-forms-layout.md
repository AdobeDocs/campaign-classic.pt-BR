---
title: Definição do layout de formulários web
seo-title: Definição do layout de formulários web
description: Definição do layout de formulários web
seo-description: null
page-status-flag: never-activated
uuid: ae8659d0-3608-44dd-93ec-33c418a66ad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 67d1d39b-3a5f-4ed6-8fcf-570891043b10
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Definição do layout de formulários web{#defining-web-forms-layout}

## Criação de containers {#creating-containers}

Os containers permitem combinar os campos de uma página e configurar seu layout; para organizar os elementos na página.

For each page of the form, containers are created via the **[!UICONTROL Containers]** button of the toolbar.

![](assets/s_ncs_admin_survey_containers_add.png)

Use um container para agrupar elementos da página sem adicionar um rótulo à renderização final. Os elementos são agrupados na subárvore container. Contêineres padrão permitem gerenciar o layout.

Por exemplo:

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

A posição dos rótulos é aplicada aos elementos posicionados abaixo do container na hierarquia. Ela pode ser sobrecarregada para cada elemento, se necessário. Adicionar ou remover colunas para alterar o layout. See [Positioning the fields on the page](#positioning-the-fields-on-the-page).

No exemplo acima, a renderização será a seguinte:

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## Posicionamento dos campos na página {#positioning-the-fields-on-the-page}

O layout do formulário web é definido pela página em cada container e pode ser sobrecarregado para cada verificação.

As páginas são divididas em colunas: cada página contém determinado número de colunas. Cada campo da página ocupa **n** células. Os containers também ocupam determinado número de colunas e os campos que contêm ocupam determinado número de células

Por padrão, as páginas são criadas em uma única coluna e cada elemento ocupa uma célula. Isso significa que os campos são exibidos um embaixo do outro e cada um ocupa uma linha inteira, como mostrado abaixo:

![](assets/s_ncs_admin_survey_container_ex.png)

No exemplo a seguir, a configuração padrão foi mantida. A página ocupa uma única coluna que inclui quatro containers.

![](assets/s_ncs_admin_survey_container_ex0.png)

Cada container ocupa uma coluna e cada elemento ocupa uma célula:

![](assets/s_ncs_admin_survey_container_ex0a.png)

A renderização é a seguinte:

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

Você pode adaptar os parâmetros de exibição para obter a seguinte renderização:

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

No exemplo de renderização acima, cada campo de entrada, título e imagem ocupa uma célula nas colunas dos containers.

Você pode modificar a formatação em cada container. No nosso exemplo, você pode distribuir o conteúdo do container 4 em duas colunas e distribuir os elementos.

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

O título e a lista ocupam uma célula cada (e, portanto, uma linha inteira do container) e a caixa de seleção se estende por duas células. The number of cells attributed to the input field is defined in the **[!UICONTROL General]** tab or the **[!UICONTROL Advanced]** tab, according to the type of field:

![](assets/s_ncs_admin_survey_container_ex2.png)

## Definição da posição dos rótulos {#defining-the-position-of-labels}

Você pode definir o alinhamento dos campos e rótulos no formulário.

Por padrão, os parâmetros de exibição para campos e outros conteúdos da página são herdados da configuração geral do formulário, da configuração da página ou da configuração do container primário, se existir.

Os parâmetros de exibição global para todo o formulário são especificados na caixa de propriedades do formulário. The **[!UICONTROL Rendering]** tab lets you select the position of labels.

![](assets/s_ncs_admin_survey_label_position.png)

This position can be overloaded for each page, each container, and each field, via the **[!UICONTROL Advanced]** tab.

Os seguintes alinhamentos são suportados:

* Herdado: o alinhamento é herdado do elemento primário (valor padrão), ou seja, o container primário, se houver, ou a página,
* Esquerda/Direita: o rótulo é posicionado à direita ou à esquerda do campo,
* Acima/Abaixo: o rótulo está posicionado acima ou abaixo do campo,
* Oculto: o rótulo não é exibido.

