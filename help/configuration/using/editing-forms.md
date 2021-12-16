---
product: campaign
title: Editar formulários
description: Editar formulários
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: f4b9ac3300094a527b5ec1b932d204f0e8e5ee86
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 4%

---


# Editar formulários{#editing-forms}

![](../../assets/common.svg)

## Visão geral

Os profissionais de marketing e operadores usam formulários de entrada para criar, modificar e visualizar registros. O Forms mostra uma representação visual de informações.

É possível criar e modificar formulários de entrada:

* Você pode modificar os formulários de entrada de fábrica que são entregues por padrão. Os formulários de entrada de fábrica são baseados nos esquemas de dados de fábrica.
* É possível criar formulários de entrada personalizados, com base em esquemas de dados definidos por você.

Forms são entidades de `xtk:form` tipo . É possível exibir a estrutura do formulário de entrada na variável `xtk:form` esquema. Para exibir esse esquema, escolha **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** no menu . Leia mais sobre [estrutura do formulário](form-structure.md).

Para acessar formulários de entrada, escolha **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** no menu:

![](assets/d_ncs_integration_form_arbo.png)

Para criar formulários, edite o conteúdo XML no editor XML:

![](assets/d_ncs_integration_form_edit.png)

[Leia mais](form-structure.md#formatting).

Para visualizar um formulário, clique no botão **[!UICONTROL Preview]** guia :

![](assets/d_ncs_integration_form_preview.png)

## Tipos de formulário

É possível criar diferentes tipos de formulários de entrada. O tipo de formulário determina como os usuários navegam no formulário:

* Tela do console

   Esse é o tipo de formulário padrão. O formulário inclui uma única página.

   ![](assets/console_screen_form.png)

* Gerenciamento de conteúdo

   Use esse tipo de formulário para gerenciamento de conteúdo. Veja isso [caso de uso](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistente

   Esse formulário inclui várias telas flutuantes ordenadas em sequências específicas. Os usuários navegam de uma tela para outra. [Leia mais](form-structure.md#wizards).

* Iconbox

   Esse formulário inclui várias páginas. Para navegar no formulário, os usuários selecionam ícones à esquerda do formulário.

   ![](assets/iconbox_form_preview.png)

* Notebook

   Esse formulário inclui várias páginas. Para navegar no formulário, os usuários selecionam guias na parte superior do formulário.

   ![](assets/notebook_form_preview.png)

* Painel vertical

   Este formulário mostra uma árvore de navegação.

* Painel horizontal

   Este formulário mostra uma lista de itens.

## Containers

Nos formulários, é possível usar contêineres para vários fins:

* Organizar o conteúdo nos formulários
* Definir o acesso aos campos de entrada
* Aninhar formulários em outros formulários

[Leia mais](form-structure.md#containers).

### Organizar o conteúdo

Use contêineres para organizar o conteúdo em formulários:

* É possível agrupar campos em seções.
* É possível adicionar páginas a formulários de várias páginas.

Para inserir um contêiner, use o `<container>` elemento. [Leia mais](form-structure.md#containers).

#### Campos de grupo

Use contêineres para agrupar campos de entrada em seções organizadas.

Para inserir uma seção em um formulário, use este elemento: `<container type="frame">`. Como opção, para adicionar um título de seção, use a variável `label` atributo.

Sintaxe: `<container type="frame" label="`*section_title*`"> […] </container>`

Neste exemplo, um contêiner define a variável **Criação** , que compreende a **[!UICONTROL Created by]** e **[!UICONTROL Name]** campos de entrada:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Adicionar páginas a formulários de várias páginas

Para formulários multipáginas, use um contêiner para criar uma página de formulário.

Este exemplo mostra contêineres para a variável **Geral** e **Detalhes** páginas de um formulário:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Definir acesso aos campos

Use containers para definir o que é visível e definir o acesso aos campos. Você pode ativar ou desativar grupos de campos.

### Aninhar formulários

Use contêineres para aninhar formulários em outros formulários. [Leia mais](#add-pages-to-multipage-forms).

## Referências a imagens

Para localizar imagens, escolha **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** no menu .

Para associar uma imagem a um elemento no formulário, por exemplo, um ícone, é possível adicionar uma referência a uma imagem. Use o `img` , por exemplo, no `<container>` elemento.

Sintaxe: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Este exemplo mostra referências ao `book.png` e `detail.png` imagens da `ncm` namespace:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Essas imagens são usadas para ícones em que os usuários clicam para navegar em um formulário de várias páginas:

![](assets/nested_forms_preview.png)
