---
product: campaign
title: Usar o explorador do Adobe Campaign
description: Saiba como usar o Explorador do Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: fdb840a9e6349f074378899e07f794b62fb5b054
workflow-type: ht
source-wordcount: '442'
ht-degree: 100%

---

# Usar o explorador do Adobe Campaign {#using-adobe-campaign-explorer}

![](../../assets/v7-only.svg)

O explorador do Adobe Campaign é acessível por meio do ícone da barra de ferramentas. Ele permite que você acesse todos os recursos do Adobe Campaign, as telas de configuração e uma visão mais detalhada de alguns dos elementos da plataforma.

O espaço de trabalho **[!UICONTROL Explorer]** é dividido em três zonas:

![](assets/s_ncs_user_navigation.png)

**1 - Tree**: é possível personalizar o conteúdo da árvore (adicionar, mover ou excluir nós). Esse procedimento destina-se somente a usuários especializados. Para obter mais informações, consulte [esta seção](#about-navigation-hierarchy).).

**2 - Lista**: é possível filtrar essa lista, executar pesquisas, adicionar informações ou classificar dados. [Saiba mais](adobe-campaign-ui-lists.md).

**3 - Details**: é possível exibir os detalhes do elemento selecionado. O ícone na seção superior direita permite exibir essas informações no formato de tela inteira.

## Pastas e árvore de navegação{#about-navigation-hierarchy}

A árvore de navegação funciona como um navegador de arquivos (por exemplo, Windows Explorer). As pastas podem conter subpastas. Selecionar um nó exibe a visualização correspondente ao nó.

A visualização exibida é uma lista associada a um esquema e um formulário de entrada para editar a linha selecionada.

![](assets/d_ncs_integration_navigation.png)

Para adicionar uma nova pasta à árvore, clique com o botão direito do mouse na pasta na ramificação em que deseja inserir uma pasta e selecione **[!UICONTROL Add new folder]**. No menu de atalho, selecione o tipo de arquivo que será criado.

![](assets/d_ncs_integration_navigation_create.png)

Saiba como configurar a árvore de navegação do Campaign [nesta seção](../../configuration/using/configuration.md).

Saiba como definir permissões em pastas [nesta seção](access-management-folders.md).

## Práticas recomendadas de configuração de pasta

* **Usar pastas integradas**

   Usar as pastas integradas faz com que as pessoas não envolvidas no projeto usem, mantenham e solucionem problemas do aplicativo com mais facilidade. Você não deve criar estruturas de pastas personalizadas para recipients, listas, deliveries etc., mas usar as pastas padrão, como Administração, Perfis e direcionamentos e Gestão de campanha.

* **Criar subpastas**

   Coloque workflows técnicos na pasta padrão: Administração/Produção/Workflows técnicos e crie subdiretórios por tipo de fluxo de trabalho.

* **Definir uma convenção de nomenclatura**

   Por exemplo, é possível nomear os workflows em ordem alfabética, para que apareçam classificados na ordem de execução.

   Por exemplo:

   * A1 - importar recipients, começa às 10h;
   * A2 - importar tíquetes, começa às 11h.

* **Criar modelos para os usuários começarem com**

   Crie templates de delivery, templates de fluxo de trabalho, templates de campanha específicos para usuários. Essa estrutura pode economizar tempo e garantir que o mapeamento de delivery e as tipologias corretas sejam usadas para cada usuário.

## Resolução da tela {#screen-resolution}

Para uma navegação e usabilidade ideal, a Adobe recomenda usar uma resolução mínima de tela de 1600x900 pixels.

>[!CAUTION]
>
>Resoluções abaixo de 1600x900 pixels não são aceitas pelo Adobe Campaign.

No workspace do **[!UICONTROL Explorer]**, se alguma parte da zona **[!UICONTROL Details]** aparecer cortada, amplie-a usando a seta na parte superior da zona ou clique no botão **[!UICONTROL Enlarge]**.

![](assets/s_ncs_user_resolution.png)

## Procurar e personalizar listas {#browsing-lists}

Saiba como procurar, gerenciar e personalizar listas [nesta seção](adobe-campaign-ui-lists.md).
