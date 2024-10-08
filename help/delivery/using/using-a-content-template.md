---
product: campaign
title: Usar um modelo de conteúdo
description: Usar um modelo de conteúdo
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: ht
source-wordcount: '436'
ht-degree: 100%

---

# Usar um modelo de conteúdo{#using-a-content-template}



## Sobre modelos de conteúdo {#about-content-templates}

Os templates de conteúdo podem ser referenciados e usados nas entregas diretamente. Consulte [Criação de uma entrega via gestão de conteúdo](#creating-a-delivery-via-content-management)

Eles também podem ser usados para criar instâncias de conteúdo. Depois de criadas, essas instâncias estão prontas para serem entregues (consulte [Delivery de uma instância de conteúdo](#delivering-a-content-instance)) ou exportadas (consulte [Criação de uma instância de conteúdo](#creating-a-content-instance)).

## Criação de uma entrega via gerenciamento de conteúdo {#creating-a-delivery-via-content-management}

É possível referenciar um modelo de conteúdo em uma entrega tendo em conta o uso de campos de entrada para inserir conteúdo. Outra guia é adicionada ao assistente de entrega para definir o conteúdo da entrega.

![](assets/s_ncs_content_deliver_a_content.png)

O layout será aplicado automaticamente com base nas configurações selecionadas. Para visualizá-lo, clique em **[!UICONTROL HTML preview]** (ou **[!UICONTROL Text preview]**) e selecione um destinatário para testar os elementos de personalização.

![](assets/s_ncs_content_deliver_a_content_html.png)

Para mais informações, consulte o exemplo de implementação completa: [Criar conteúdo no assistente de entrega](use-case-creating-content-management.md#creating-content-in-the-delivery-assistant).

## Criação de uma instância de conteúdo {#creating-a-content-instance}

É possível criar conteúdo diretamente na árvore do Adobe Campaign para ser usado em workflows, exportado ou inserido diretamente em novas entregas.

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

Para criar e entregar uma instância de conteúdo, um template do delivery precisa ser vinculado ao template de publicação usado para gerar esse conteúdo. Para obter mais informações, consulte [Entrega](publication-templates.md#delivery).

Além disso, a pasta de armazenamento de conteúdo deve ser dedicada ao conteúdo obtido deste template de publicação (quando uma pasta de conteúdo permite gerar vários tipos de conteúdo, as entregas não podem ser criadas automaticamente).

Para criar automaticamente uma entrega baseada no conteúdo selecionado, clique no ícone **[!UICONTROL Delivery]** e escolha o template.

![](assets/s_ncs_content_folder_create_the_delivery.png)

O conteúdo de texto e HTML é inserido automaticamente.
