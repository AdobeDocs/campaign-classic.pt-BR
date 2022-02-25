---
product: campaign
title: Deliveries de campanha de marketing
description: Saiba mais sobre deliveries de campanha de marketing
feature: Resource Management, Cross Channel Orchestration
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: ht
source-wordcount: '1487'
ht-degree: 100%

---

# Entregas de campanha de marketing {#marketing-campaign-deliveries}

![](../../assets/common.svg)

As entregas podem ser criadas por meio do painel da campanha, de um fluxo de trabalho de campanha ou diretamente na visão geral das entregas.

Quando criados a partir de uma campanha, os deliveries serão vinculados a essa campanha e consolidados em seu nível.

![](assets/do-not-localize/how-to-video.png)[ Descubra este recurso no vídeo](#create-email-video)

## Criar entregas {#creating-deliveries}

Para criar uma entrega vinculada a uma campanha, clique no link **[!UICONTROL Add a delivery]** no painel da campanha.

![](assets/campaign_op_add_delivery.png)

As configurações sugeridas são adequadas aos diferentes tipos de delivery: correspondência direta, email, canais móveis. [Saiba mais](../../delivery/using/steps-about-delivery-creation-steps.md).

## Iniciar um delivery {#starting-a-delivery}

Depois que todas as aprovações tiverem sido concedidas, o delivery estará pronto para ser iniciado. O procedimento de delivery depende do tipo de delivery. Para deliveries de email ou canais móveis, consulte [Iniciar um delivery online](#starting-an-online-delivery) e para deliveries por correspondência direta, consulte [Iniciar um delivery offline](#starting-an-offline-delivery).

### Iniciar um delivery online {#starting-an-online-delivery}

Depois que todas as solicitações de aprovação tiverem sido concedidas, o status do delivery será alterado para **[!UICONTROL Pending confirmation]** e ele poderá ser iniciado por um operador. Quando apropriado, o operador (ou grupo de operadores) do Adobe Campaign designado como revisor para iniciar o delivery é notificado de que um delivery está pronto para ser iniciado.

>[!NOTE]
>
>Se um operador ou grupo de operadores específico for designado para iniciar um delivery nas propriedades do delivery, você também poderá permitir que o operador responsável pelo delivery confirme o delivery. Para fazer isso, ative a opção **NMS_ActivateOwnerConfirmation** inserindo **1** como o valor. As opções são gerenciadas no nó **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** no explorador do Adobe Campaign.
>  
>Para desativar essa opção, insira **0** como valor. O processo de confirmação de delivery funcionará como padrão: somente o operador ou grupo de operadores designado ao delivery nas propriedades de delivery (ou um administrador) poderá confirmar e realizar o delivery.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

As informações também aparecem no painel de campanha. O link **[!UICONTROL Confirm delivery]** permite iniciar o delivery.

![](assets/s_ncs_user_edit_del_to_start.png)

Uma mensagem de confirmação permite que você proteja esta ação.

### Iniciar um delivery offline {#starting-an-offline-delivery}

Após todas as aprovações serem concedidas, o status do delivery será alterado para **[!UICONTROL Pending extraction]**. Os arquivos de extração são criados por um workflow especial, que em uma configuração padrão, inicia automaticamente quando um delivery de mala direta está com extração pendente. Quando um processo está em andamento, ele é exibido no painel e pode ser editado através do link.

>[!NOTE]
>
>Os workflows técnicos relacionados ao pacote do Campaign são apresentados na [Lista de workflows técnicos](../../workflow/using/about-technical-workflows.md).

**Etapa 1 - Aprovação de arquivo**

Após executar o workflow de extração com sucesso, o arquivo de extração deve ser aprovado (fornecido de forma que a aprovação do arquivo de extração tenha sido selecionada nas configurações do delivery).

Para obter mais informações, consulte [Aprovação de um arquivo de extração](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**Etapa 2 - Aprovação da mensagem para o provedor de serviços**

* Depois que o arquivo de extração for aprovado, é possível gerar a prova do email de notificação do roteador. Esta mensagem de email é construída com base em um template de delivery. Deve ser aprovado.

   >[!NOTE]
   >
   >Esta etapa só estará disponível se o envio e a aprovação de provas tiverem sido habilitados na janela de aprovações.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* Clique no botão **[!UICONTROL Send a proof]** para criar as provas.

   O target da prova deve ser definido com antecedência.

   Você pode criar quantas provas forem necessárias. Elas são acessadas por meio do link **[!UICONTROL Direct mail...]** dos detalhes de delivery.

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* O status do delivery é alterado para **[!UICONTROL To submit]**. Clique no botão **[!UICONTROL Submit proofs]** para iniciar o processo de aprovação.

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* O status do delivery muda para **[!UICONTROL Proof to validate]**, e um botão permite aceitar ou rejeitar a aprovação.

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   Você pode aceitar ou rejeitar esta aprovação ou retornar à etapa de extração.

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* O arquivo de extração é enviado ao roteador e o delivery é concluído.

### Cálculo de custos e estoques {#calculation-of-costs-and-stocks}

A extração de arquivo inicia duas operações: cálculo de orçamento e cálculo de estoque. As entradas do orçamento são atualizadas.

* A guia **[!UICONTROL Budget]** permite gerenciar os orçamentos da campanha. O total das entradas de custo é exibido no campo **[!UICONTROL Calculates cost]** da guia principal da campanha e o programa ao qual ele pertence. Os montantes também são refletidos no orçamento da campanha.

   O custo real será calculado de acordo com as informações fornecidas pelo roteador. Apenas mensagens enviadas são faturadas.

* Os estoques são definidos no nó **[!UICONTROL Administration > Campaign management > Stocks]** da árvore, e as estruturas de custo no nó **[!UICONTROL Administration > Campaign management > Service providers]**.

   As linhas de estoque estão visíveis na seção de estoque. Para definir o estoque inicial, abra uma linha de estoque. O estoque é reduzido sempre que um delivery ocorre. Você pode definir um nível de alerta e notificações.

>[!NOTE]
>
>Para obter mais informações sobre cálculos de custos e gerenciamento de estoque, consulte [Provedores, estoques e orçamentos](../../campaign/using/providers--stocks-and-budgets.md).

## Gerenciar documentos associados {#managing-associated-documents}

Você pode associar vários documentos a uma campanha: relatório, foto, página da Web, diagrama etc. Esses documentos podem estar em qualquer formato (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF etc.). Saiba como vincular documentos a uma campanha [nesta seção](../../campaign/using/marketing-campaign-assets.md).

>[!IMPORTANT]
>
>Esse modo é reservado para documentos pequenos.

Em uma campanha que você também pode consultar outros itens, como cupons promocionais, ofertas especiais relacionadas a uma filial específica ou loja, etc. Quando esses elementos estão incluídos em um outline, eles podem ser associados a um delivery de mala direta. [Saiba mais](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Se você estiver usando o MRM, também poderá gerenciar uma biblioteca de recursos de marketing disponíveis para vários participantes de trabalho colaborativo. Consulte [Gerenciar recursos de marketing](../../mrm/using/managing-marketing-resources.md).

### Adicionar documentos {#adding-documents}

Os documentos podem ser associados no nível da campanha (documentos contextuais) ou no nível do programa (documentos gerais).

A guia **[!UICONTROL Documents]** contém:

* A lista de todos os documentos necessários para o conteúdo (template, imagens etc.) que pode ser baixado localmente pelos operadores do Adobe Campaign com direitos adequados,
* Documentos contendo informações para o roteador, se houver.

Os documentos são vinculados ao programa ou à campanha através da guia **[!UICONTROL Edit > Documents]**.

![](assets/s_ncs_user_op_add_document.png)

Você também pode adicionar um documento a uma campanha através do link oferecido em seu painel.

![](assets/add_a_document_in_op.png)

Clique no ícone **[!UICONTROL Details]** para exibir o conteúdo de um arquivo e adicionar informações:

![](assets/s_ncs_user_op_add_document_details.png)

No painel, os documentos associados à campanha são agrupados na seção **[!UICONTROL Document(s)]**, como no exemplo a seguir:

![](assets/s_ncs_user_op_edit_document.png)

Eles também podem ser editados e modificados nessa visualização.

### Associar e estruturar recursos vinculados por meio de um delivery outline {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>Delivery outlines são usados exclusivamente no contexto de campanhas de mala direta.

Um delivery outline indica um conjunto estruturado de elementos (documentos, ramificações/lojas, cupons promocionais etc.) criados na empresa e para uma campanha específica.

Esses elementos são agrupados em delivery outlines e um delivery outline específico será associado a um delivery; ele será referenciado no arquivo de extração enviado ao **provedor de serviços** para ser anexada ao delivery. Por exemplo, você pode criar um delivery outline que se refere a uma unidade e aos folhetos de marketing que ela usa.

Para uma campanha, delivery outlines permitem que você estruture elementos externos a serem associados ao delivery de acordo com determinados critérios: a unidade relacionada, a oferta promocional concedida, o convite para um evento local etc.

#### Criar um outline {#creating-an-outline}

Para criar um outline, clique na guia **[!UICONTROL Delivery outlines]** da campanha relacionada e depois clique na subguia **[!UICONTROL Edit > Documents]**.

>[!NOTE]
>
>Se essa guia não estiver presente, significa que esse recurso não está disponível para esta campanha. Consulte a configuração do template de campanha.
>   
>Para obter mais informações, consulte [templates de campanha](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Em seguida, clique em **[!UICONTROL Add a delivery outline]** e crie a hierarquia de outlines para a campanha:

1. Clique com o botão direito do mouse na raiz da árvore e selecione **[!UICONTROL New > Delivery outlines]**.
1. Clique com o botão direito do mouse no outline recém criado e selecione **[!UICONTROL New > Item]** ou **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

Uma estrutura pode conter itens e campos de personalização, recursos e ofertas:

* Os itens podem ser documentos físicos, por exemplo, que são referenciados e descritos aqui e serão anexados ao delivery.
* Os campos de personalização permitem que você crie elementos de personalização relacionados a remessas em vez de recipients. Assim, é possível criar valores que serão usados em deliveries para um target específico (oferta de boas-vindas, desconto, etc.) Eles são criados no Adobe Campaign e importados para o outline por meio do link **[!UICONTROL Import personalization fields...]**.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   Eles também podem ser criados diretamente no outline clicando no ícone **[!UICONTROL Add]** à direita da zona de lista.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* Os recursos são de marketing, gerados no painel de recurso de marketing acessado por meio do link **[!UICONTROL Resources]** da guia **[!UICONTROL Campaigns]**.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Para obter mais informações sobre recursos de marketing, consulte [Gerenciamento de recursos de marketing](../../mrm/using/managing-marketing-resources.md).

#### Selecionar um outline {#selecting-an-outline}

Para cada delivery, você pode selecionar o outline para associar na seção reservada para o outline da extração, como no exemplo a seguir:

![](assets/s_ncs_user_op_select_composition.png)

A estrutura selecionada é então exibida na seção inferior da janela. Ele pode ser editado usando o ícone à direita do campo ou alterado usando a lista suspensa:

![](assets/s_ncs_user_op_select_composition_b.png)

A guia **[!UICONTROL Summary]** do delivery também exibe essas informações:

![](assets/s_ncs_user_op_select_composition_c.png)

#### Resultado da extração {#extraction-result}

No arquivo extraído e enviado ao provedor de serviços, o nome da estrutura e, quando apropriado, suas características (custo, descrição etc.) são adicionados ao conteúdo de acordo com as informações no template de exportação associado ao provedor de serviços.

No seguinte exemplo, o rótulo, custo estimado e descrição do outline associado ao delivery serão adicionados no arquivo de extração.

![](assets/s_ncs_user_op_composition_in_export_template.png)

O modelo de exportação deve estar associado ao provedor de serviços selecionado para o delivery. Consulte [Criação de provedores de serviços e suas estruturas de custo](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Para saber mais sobre exportações, consulte a seção [Introdução](../../platform/using/get-started-data-import-export.md) .

#### Tutorial em vídeo {#create-email-video}

Este vídeo explica como criar uma campanha e um email no Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

Vídeos extras explicativos do Campaign estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
