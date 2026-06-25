---
product: campaign
title: Criar e gerenciar grupos de operadores
description: Saiba como conceder acesso a grupos de operadores
badge: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
TQID: https://experienceleague.adobe.com/FZhH7zDL3g3tG8Ar40XJQWE-2O9Rs5-KD-NliQ6wH3M
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2: id: f529d0bd-1401-4c88-9833-43228cc1d40fid: d6330382-c886-4f7a-a4f7-74e3f36c0d9cid: f5293531-9312-4099-bfa3-9e67df6a8750id: efa38731-2723-4334-8d8b-a778af834835
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 573
ht-degree: 100%

---

# Criar e gerenciar grupos de operadores {#operator-groups}

>[!NOTE]
>
>Estes procedimentos aplicam-se somente a operadores conectados ao Campaign por meio da **autenticação nativa herdada**. A partir do Campaign Classic v7.3.1, todos os operadores deverão usar o [Adobe Identity Management System (IMS)](https://helpx.adobe.com/br/enterprise/using/identity.html){target="_blank"} para conectar-se ao Campaign. [Saiba mais](../../technotes/using/migrate-users-to-ims.md)
>
>Ao conectar-se ao Campaign com o seu Adobe ID, a seção a seguir não se aplica mais. Saiba como configurar permissões com o Adobe IMS na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=pt-BR){target="_blank"}.

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

   * **[!UICONTROL ADMINISTRATION]**: direito a executar/criar/editar/excluir qualquer objeto, como fluxo de trabalho, entrega, scripts, etc.

1. **[!UICONTROL Delivery operators]**

   Os operadores nesse grupo são responsáveis pelo gerenciamento de entregas: eles permitem o acesso aos principais recursos necessários para a criação e preparação de entregas (tipologias de campanha, mapeamentos de entrega, modelos padrão, blocos de personalização, etc.).

   Esse grupo contém os seguintes direitos nomeados:

   * **[!UICONTROL PREPARE DELIVERIES]**: Direito de criar, editar e iniciar a análise de entrega,
   * **[!UICONTROL START DELIVERIES]**: Direito de aprovar entregas anteriormente analisadas.

1. **[!UICONTROL Campaign managers]**

   Os operadores neste grupo podem gerenciar campanhas de marketing: isso permite acessar os objetos vinculados às campanhas (planos, programas, fluxos de trabalho, orçamentos etc.) dentro da estrutura do **[!UICONTROL Campaign]** (módulo opcional do Adobe Campaign).

   Esse grupo contém os seguintes direitos nomeados:

   * **[!UICONTROL INSERT FOLDERS]**: direito de inserir pastas à árvore do Adobe Campaign (se você tiver o direito de editar ramificações),
   * **[!UICONTROL WORKFLOW]**: direito de usar fluxos de trabalho.

   >[!NOTE]
   >
   >Esse grupo não permite que os operadores iniciem entregas.

1. **[!UICONTROL Content contributors]**

   Os operadores nesse grupo podem acessar as pastas de conteúdo, dentro da estrutura de **[!UICONTROL Content management]** (módulo opcional do Adobe Campaign). Esse grupo não concede direitos adicionais.

1. **[!UICONTROL Access to reports]**

   Esse grupo é reservado para operadores externos, para habilitar os ícones de Relatório, Cronograma e Fórum no Painel do Campaign para um operador específico.

1. **[!UICONTROL Workflow execution]**

   Esse grupo permite atribuir aos operadores o direito de gerenciar fluxos de trabalho que não estão relacionados a campanhas.

1. **[!UICONTROL Workflow supervisors]**

   Os operadores nesse grupo recebem uma notificação por e-mail no caso de alertas relativos aos fluxos de trabalho da campanha.

1. Gerenciamento local / central

   Esses grupos permitem a utilização de **[!UICONTROL Distributed marketing]** (módulo opcional do Adobe Campaign).

1. **[!UICONTROL Offer managers]**

   Os operadores nesse grupo podem criar e manter ofertas. Para obter mais informações, consulte esta [página](../../interaction/using/operator-profiles.md).
Esse grupo contém os seguintes direitos nomeados:

   * **[!UICONTROL INSERT FOLDERS]**: direito de inserir pastas à árvore do Adobe Campaign (se você tiver o direito de editar ramificações),
   * **[!UICONTROL EDIT FOLDERS]**: direito de alterar as propriedades da pasta, como nome interno, rótulo, imagem associada, pedido de subpastas etc.
