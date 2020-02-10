---
title: Usando um template de conteúdo
seo-title: Usando um template de conteúdo
description: Usando um template de conteúdo
seo-description: null
page-status-flag: never-activated
uuid: 893b9711-593f-4865-b61a-ef0fede9a2b0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 48f491b7-bf7b-457f-9cf2-db2bbf4eceea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Usando um template de conteúdo{#using-a-content-template}

## Sobre templates de conteúdo {#about-content-templates}

Os templates de conteúdo podem ser referenciados e usados nas remessas diretamente. Consulte [Criação de uma entrega por meio do gerenciamento de conteúdo](#creating-a-delivery-via-content-management)

Eles também podem ser usados para criar instâncias de conteúdo. Depois de criadas, essas instâncias estão prontas para serem entregues (consulte [Fornecer uma instância](#delivering-a-content-instance)de conteúdo) ou exportadas (consulte [Criar uma instância](#creating-a-content-instance)de conteúdo).

## Criação de um delivery via gestão de conteúdo {#creating-a-delivery-via-content-management}

É possível referenciar um template de conteúdo em um delivery tendo em conta o uso de campos de entrada para inserir conteúdo. Uma guia adicional é incluída no assistente do delivery para definir o conteúdo do delivery.

![](assets/s_ncs_content_deliver_a_content.png)

O layout será aplicado automaticamente com base nas configurações selecionadas. To view it, click the **[!UICONTROL HTML preview]** (or **[!UICONTROL Text preview]** ) and select a recipient to test personalization elements.

![](assets/s_ncs_content_deliver_a_content_html.png)

Para obter mais informações, consulte o exemplo de implementação completa: [Criar conteúdo no assistente](../../delivery/using/use-case--creating-content-management.md#creating-content-in-the-delivery-wizard)de entrega.

## Criação de uma instância de conteúdo {#creating-a-content-instance}

É possível criar conteúdo diretamente na árvore do Adobe Campaign para ser usado em workflows, exportado ou inserido diretamente em novos deliveries.

Siga as etapas abaixo:

1. Selecione o **[!UICONTROL Resources > Contents]** nó da árvore, clique com o botão direito do mouse e escolha **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Selecione os templates de publicação que estarão ativos para esta pasta.

   ![](assets/s_ncs_content_folder_templates.png)

1. You can now create new content using the **[!UICONTROL New]** button above the content list.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Insira os campos no formulário.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Then click the **[!UICONTROL HTML preview]** tab to view the rendering. Os campos de personalização obtidos do banco de dados não são inseridos aqui.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Uma vez criado, o conteúdo será adicionado à lista de conteúdos disponíveis. Click the **[!UICONTROL Properties]** link to change its label, status, or view its history.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Se necessário, quando o conteúdo for aprovado, ele poderá ser gerado usando o botão apropriado na barra de ferramentas.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >Você pode autorizar a geração de conteúdos não aprovados. Para fazer isso, altere a opção relevante no template de publicação. Para obter mais informações, consulte [Criação e configuração do modelo](../../delivery/using/publication-templates.md#creating-and-configuring-the-template).

   O conteúdo HTML e texto é gerado por padrão na pasta da **publicação** da instância do Adobe Campaign. Você pode alterar a pasta da publicação graças à opção **NcmPublishingDir**.

## Delivery de uma instância de conteúdo {#delivering-a-content-instance}

Para criar e entregar uma instância de conteúdo, um template do delivery precisa ser vinculado ao template de publicação usado para gerar esse conteúdo. For more on this, refer to [Delivery](../../delivery/using/publication-templates.md#delivery).

Além disso, a pasta de armazenamento de conteúdo deve ser dedicada ao conteúdo obtido deste template de publicação (quando uma pasta de conteúdo permite gerar vários tipos de conteúdo, os deliveries não podem ser criados automaticamente).

To create the delivery automatically based on the selected content, click the **[!UICONTROL Delivery]** icon and choose the template.

![](assets/s_ncs_content_folder_create_the_delivery.png)

O conteúdo de texto e HTML é inserido automaticamente.
