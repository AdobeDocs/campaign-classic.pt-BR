---
product: campaign
title: Usar um modelo de conteúdo
description: Usar um modelo de conteúdo
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: ht
source-wordcount: '427'
ht-degree: 100%

---

# Usar um modelo de conteúdo{#using-a-content-template}

![](../../assets/common.svg)

## Sobre modelos de conteúdo {#about-content-templates}

Os templates de conteúdo podem ser referenciados e usados nas remessas diretamente. Consulte [Criação de um delivery via gestão de conteúdo](#creating-a-delivery-via-content-management)

Eles também podem ser usados para criar instâncias de conteúdo. Depois de criadas, essas instâncias estão prontas para serem entregues (consulte [Delivery de uma instância de conteúdo](#delivering-a-content-instance)) ou exportadas (consulte [Criação de uma instância de conteúdo](#creating-a-content-instance)).

## Criação de uma entrega via gerenciamento de conteúdo {#creating-a-delivery-via-content-management}

É possível referenciar um template de conteúdo em um delivery tendo em conta o uso de campos de entrada para inserir conteúdo. Uma guia adicional é incluída no assistente do delivery para definir o conteúdo do delivery.

![](assets/s_ncs_content_deliver_a_content.png)

O layout será aplicado automaticamente com base nas configurações selecionadas. Para visualizá-lo, clique em **[!UICONTROL HTML preview]** (ou **[!UICONTROL Text preview]**) e selecione um recipient para testar os elementos de personalização.

![](assets/s_ncs_content_deliver_a_content_html.png)

Para obter mais informações, consulte o exemplo de implementação completa: [Criação de conteúdo no assistente de entrega](use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## Criação de uma instância de conteúdo {#creating-a-content-instance}

É possível criar conteúdo diretamente na árvore do Adobe Campaign para ser usado em workflows, exportado ou inserido diretamente em novos deliveries.

Siga as etapas abaixo:

1. Selecione o nó **[!UICONTROL Resources > Contents]** da árvore, clique com o botão direito do mouse e escolha **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Selecione os templates de publicação que estarão ativos para esta pasta.

   ![](assets/s_ncs_content_folder_templates.png)

1. Agora você pode criar novo conteúdo usando o botão **[!UICONTROL New]** acima da lista de conteúdo.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Insira os campos no formulário.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Em seguida, clique na guia **[!UICONTROL HTML preview]** para exibir a renderização. Os campos de personalização obtidos do banco de dados não são inseridos aqui.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Uma vez criado, o conteúdo será adicionado à lista de conteúdos disponíveis. Clique no link **[!UICONTROL Properties]** para alterar seu rótulo, status ou visualizar seu histórico.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Se necessário, quando o conteúdo for aprovado, ele poderá ser gerado usando o botão apropriado na barra de ferramentas.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >Você pode autorizar a geração de conteúdos não aprovados. Para fazer isso, altere a opção relevante no template de publicação. Para obter mais informações, consulte [Criação e configuração do template](publication-templates.md#creating-and-configuring-the-template).

   O conteúdo HTML e texto é gerado por padrão na pasta da **publicação** da instância do Adobe Campaign. Você pode alterar a pasta da publicação graças à opção **NcmPublishingDir**.

## Entrega de uma instância de conteúdo {#delivering-a-content-instance}

Para criar e entregar uma instância de conteúdo, um template do delivery precisa ser vinculado ao template de publicação usado para gerar esse conteúdo. Para obter mais informações, consulte [Delivery](publication-templates.md#delivery).

Além disso, a pasta de armazenamento de conteúdo deve ser dedicada ao conteúdo obtido deste template de publicação (quando uma pasta de conteúdo permite gerar vários tipos de conteúdo, os deliveries não podem ser criados automaticamente).

Para criar automaticamente um baseado no conteúdo selecionado, clique no ícone **[!UICONTROL Delivery]** Delivery e escolha o template.

![](assets/s_ncs_content_folder_create_the_delivery.png)

O conteúdo de texto e HTML é inserido automaticamente.
