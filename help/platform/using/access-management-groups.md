---
product: campaign
title: Criar e gerenciar grupos de operadores
description: Saiba como conceder acesso a grupos de operadores
feature: Access Management
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '498'
ht-degree: 100%

---

# Criar e gerenciar grupos de operadores {#operator-groups}

![](../../assets/common.svg)

Os grupos de operadores são criados por meio do nó **[!UICONTROL Administration > Access management > Operator groups]** na árvore.

## Criar um novo grupo de operadores {#creating-a-new-operator-group}

Para criar um novo grupo de operadores, siga as etapas abaixo:

1. Clique no botão **[!UICONTROL New]** à direita da lista de grupos ou clique com o botão direito do mouse na lista e escolha **[!UICONTROL New]**.
1. Na janela inferior da seção, na guia **[!UICONTROL General]**, digite o nome e uma descrição para esse grupo nos campos correspondentes.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Clique na guia **[!UICONTROL Content]** para definir autorizações para esse grupo.
1. Clique no botão **[!UICONTROL Add]** para selecionar um direito designado ou um operador para associar ao grupo.
1. Clique na lista suspensa ou na pasta à direita do campo **[!UICONTROL Folder]** para localizar os direitos ou operadores designados para associar a esse grupo.
1. Selecione os direitos ou operadores a serem adicionados e clique em **[!UICONTROL OK]** para validar.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Repita essa operação para adicionar outros direitos ou operadores.

1. Clique no botão **[!UICONTROL Save]** para adicionar o grupo à lista.

## Grupos padrão {#default-groups}

Os grupos de operadores padrão são:

1. **[!UICONTROL Administrator]**

   Os operadores neste grupo têm acesso total à instância. Os administradores funcionais são usuários que podem acessar as partes mais técnicas da interface. Eles assumem a função **[!UICONTROL Administration]** e garantem que a plataforma esteja configurada.

   Esse grupo contém os seguintes direitos nomeados:

   * **[!UICONTROL ADMINISTRATION]**: direito a executar/criar/editar/excluir qualquer objeto, como workflow, delivery, scripts, etc.

1. **[!UICONTROL Delivery operators]**

   Os operadores nesse grupo são responsáveis pelo gerenciamento de deliveries: eles permitem o acesso aos principais recursos necessários para a criação e preparação de deliveries (tipologias de campanha, mapeamentos de delivery, templates padrão, blocos de personalização, etc.).

   Esse grupo contém os seguintes direitos nomeados:

   * **[!UICONTROL PREPARE DELIVERIES]**: Direito de criar, editar e iniciar a análise de delivery,
   * **[!UICONTROL START DELIVERIES]**: Direito de aprovar deliveries anteriormente analisados.

1. **[!UICONTROL Campaign managers]**

   Os operadores nesse grupo podem gerenciar campanhas de marketing: permite acessar os objetos vinculados às campanhas (planos, programas, workflows, orçamentos, etc.) no âmbito da estrutura de **[!UICONTROL Campaign]** (módulo opcional do Adobe Campaign).

   Esse grupo contém os seguintes direitos nomeados:

   * **[!UICONTROL INSERT FOLDERS]**: direito de inserir pastas à árvore do Adobe Campaign (se você tiver o direito de editar ramificações),
   * **[!UICONTROL WORKFLOW]**: direito de usar workflows.
   >[!NOTE]
   >
   >Esse grupo não permite que os operadores iniciem deliveries.

1. **[!UICONTROL Content contributors]**

   Os operadores nesse grupo podem acessar as pastas de conteúdo, dentro da estrutura de **[!UICONTROL Content management]** (módulo opcional do Adobe Campaign). Esse grupo não concede direitos adicionais.

1. **[!UICONTROL Access to reports]**

   Esse grupo é reservado para operadores externos, para acessar os relatórios do delivery por meio de um acesso à Web.

1. **[!UICONTROL Workflow execution]**

   Esse grupo permite atribuir aos operadores o direito de gerenciar workflows que não estão relacionados a campanhas.

1. **[!UICONTROL Workflow supervisors]**

   Os operadores nesse grupo recebem uma notificação por e-mail no caso de alertas relativos aos workflows da campanha.

1. Gerenciamento local / central

   Esses grupos permitem a utilização de **[!UICONTROL Distributed marketing]** (módulo opcional do Adobe Campaign).

1. **[!UICONTROL Offer managers]**

   Os operadores neste grupo podem criar e manter ofertas. Para obter mais informações sobre essas operações, consulte esta [página](../../interaction/using/operator-profiles.md).
Esse grupo contém os seguintes direitos nomeados:

   * **[!UICONTROL INSERT FOLDERS]**: direito de inserir pastas à árvore do Adobe Campaign (se você tiver o direito de editar ramificações),
   * **[!UICONTROL EDIT FOLDERS]**: direito de alterar as propriedades da pasta, como nome interno, rótulo, imagem associada, pedido de subpastas etc.
