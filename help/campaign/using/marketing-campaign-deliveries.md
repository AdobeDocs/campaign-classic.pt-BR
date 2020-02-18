---
title: Entregas da campanha de marketing
seo-title: Entregas da campanha de marketing
description: Entregas da campanha de marketing
seo-description: Saiba mais sobre entregas de campanha de marketing
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eee744eb5bc7a43fd412ffb01f0546385146a978

---


# Entregas da campanha de marketing {#marketing-campaign-deliveries}

As entregas podem ser criadas através do painel de campanha, um workflow de campanha ou diretamente através da visão geral das remessas.

## Criar entregas {#creating-deliveries}

To create a delivery linked to a campaign, click the **[!UICONTROL Add a delivery]** link in the campaign dashboard.

![](assets/campaign_op_add_delivery.png)

As configurações sugeridas são apropriadas para os diferentes tipos de delivery (mala direta, e-mail, canais móveis, fax ou telefone).

>[!NOTE]
>
>Para obter mais informações sobre como criar e configurar fornecimentos, consulte a seção [Enviar Mensagens](../../delivery/using/communication-channels.md) .

## Seleção da população do target {#selecting-the-target-population}

Para cada delivery, o gerente de campanha definirá:

* O target principal. Para obter mais informações, consulte [Criar a meta principal em um fluxo de trabalho](#building-the-main-target-in-a-workflow) e [Selecionar a população](#selecting-the-target-population)alvo.
* O grupo de controle. Para obter mais informações, consulte [Definição de um grupo](#defining-a-control-group)de controle.
* Os seed addresses. Para obter mais informações, consulte [esta seção](../../delivery/using/about-seed-addresses.md).

Algumas dessas informações são herdadas do template.

>[!NOTE]
>
>Os modelos de campanha são apresentados nos modelos [do](../../campaign/using/marketing-campaign-templates.md#campaign-templates)Campaign.

Para criar o target do delivery, você pode definir critérios de filtragem para os recipients no banco de dados. Este modo de seleção de recipient é apresentado na seção [Enviar Mensagens](../../delivery/using/steps-defining-the-target-population.md) .

### Exemplo: entrega para um grupo de recipients {#example--delivering-to-a-group-of-recipients}

Você pode importar uma população para uma lista e depois direcionar essa lista nas remessas.

1. To do this, edit the concerned delivery and click the **[!UICONTROL To]** link to change the targeted population.

1. Na **[!UICONTROL Main target]** guia, selecione a **[!UICONTROL Defined via the database]** opção e clique **[!UICONTROL Add]** para selecionar destinatários.

![](assets/s_user_target_group_add.png)

1. Escolha **[!UICONTROL A list of recipients]** e clique **[!UICONTROL Next]** para selecioná-lo.

![](assets/s_user_target_group_next.png)

### Criação do target principal em um workflow {#building-the-main-target-in-a-workflow}

O alvo principal de um delivery também pode ser definido no workflow de definição de metas: esse ambiente gráfico permite criar um destino usando queries, testes e operadores: união, correção de duplicidade, compartilhamento etc.

O guia [Automating with workflows](../../workflow/using/executing-a-workflow.md#architecture) inclui uma descrição detalhada de como o módulo de workflow opera.

>[!IMPORTANT]
>
>Você não pode configurar mais de 28 workflows na mesma campanha. Acima desse limite, os workflows adicionais não estão visíveis na interface e podem gerar erros.

#### Criação de um workflow para construção do target {#creating-a-targeting-workflow}

A definição de alvos pode ser criada por meio de uma combinação de condições de filtragem em uma sequência gráfica em um workflow. Você pode criar populações e subpopulações que serão direcionadas de acordo com suas necessidades. To display the workflow editor, click the **[!UICONTROL Targeting and workflows]** tab in the campaign dashboard.

![](assets/s_ncs_user_edit_op_wf_link.png)

A população do target é extraída do banco de dados do Adobe Campaign através de uma ou mais queries colocadas em um workflow. Para saber como criar uma query, consulte [esta seção](../../workflow/using/query.md).

Você pode iniciar queries e compartilhar populações por meio de caixas como União, Intersecção, Compartilhamento, Exclusão, etc.

Selecione os objetos nas listas à esquerda do espaço de trabalho e vincule a eles para construir o target.

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

No diagrama, vincule as queries de definição de metas e agendamento necessárias para a construção de target no diagrama. Você pode executar o direcionamento enquanto a construção está em andamento para verificar a população extraída do banco de dados.

>[!NOTE]
>
>Examples and procedure for defining queries are presented in [this section](../../workflow/using/query.md).

A seção à esquerda do editor contém uma biblioteca de objetos gráficos que representam atividades. A primeira guia contém as atividades de definição de metas e a segunda contém as atividades de controle de fluxo, que são usadas ocasionalmente para coordenar as atividades de definição de metas.

As funções de execução e formatação do workflow de direcionamento são acessíveis pela barra de ferramentas do editor de diagrama.

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>As atividades disponíveis para criar o diagrama e todos os recursos de exibição e layout estão detalhados no guia [Automating with workflows](../../workflow/using/executing-a-workflow.md#architecture).

Você pode criar vários workflows para construção do target para uma única campanha. Para adicionar um workflow:

1. Go to the upper left-hand section of the workflow creation zone, right-click, and select **[!UICONTROL Add]**. You can also use the **[!UICONTROL New]** button located above this zone.

   ![](assets/s_ncs_user_add_a_wf.png)

1. Select the **[!UICONTROL New workflow]** template and name this workflow.
1. Click **[!UICONTROL OK]** to confirm creation of the workflow, and then create the diagram for this workflow.

#### Execução de um fluxo de trabalho {#executing-a-workflow}

Targeting workflows can be launched manually via the **[!UICONTROL Start]** button in the toolbar, provided that you have the appropriate rights.

O direcionamento pode ser programado para execução automática de acordo com um agendamento (agendador) ou um evento (sinal externo, importação de arquivo, etc.).

As ações relacionadas à execução do workflow de definição de metas (inicialização, parada, pausa etc.) são processos **assíncronos** : o comando é salvo e entrará em vigor assim que o servidor estiver disponível para aplicá-lo.

Os ícones da barra de ferramentas permitem tomar medidas referentes à execução do workflow de direcionamento.

* Iniciar ou reiniciar

   * The **[!UICONTROL Start]** icon lets you launch the targeting workflow. Quando você clica nesse ícone, todas as atividades sem uma transição de entrada são ativadas (exceto saltos de ponto de extremidade).

      ![](assets/s_user_segmentation_start.png)

      O servidor considera a solicitação, conforme mostrado pelo status:

      ![](assets/s_user_segmentation_start_status.png)

      The process status changes to **[!UICONTROL Started]**.

   * Você pode reiniciar o workflow de definição de metas por meio do ícone de barra de ferramentas apropriado. This command may be useful if the **[!UICONTROL Start]** icon is not available, for example when targeting workflow stopping is in progress. In this case, click the **[!UICONTROL Restart]** icon to anticipate the restart. O servidor considera a solicitação, como mostra o status:

      ![](assets/s_user_segmentation_restart_status.png)

      Em seguida, o processo entra em **[!UICONTROL Started]** status.

* Parar ou pausar

   * Os ícones da barra de ferramentas permitem interromper ou pausar um workflow de direcionamento em andamento.

      When you click **[!UICONTROL Pause]**, operations in progress **[!UICONTROL are not]** paused, but no other activity is launched until the next restart.

      ![](assets/s_user_segmentation_pause.png)

      O servidor considera o comando, como mostra o status:

      ![](assets/s_user_segmentation_pause_status.png)

      Você também pode pausar um workflow de direcionamento automaticamente quando a execução atinge uma atividade específica. To do this, right-click the activity from which targeting workflow is to be paused, and select **[!UICONTROL Enable but do not execute]**.

      ![](assets/s_user_segmentation_donotexecute.png)

      Essa configuração é exibida por um ícone especial.

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >Essa opção é útil durante as fases avançadas de criação e teste de campanhas de definição de metas.

      Clique em **[!UICONTROL Start]** para retomar a execução.

   * Click the **[!UICONTROL Stop]** icon to stop the execution in progress.

      ![](assets/s_user_segmentation_stop.png)

      O servidor considera o comando, como mostra o status:

      ![](assets/s_user_segmentation_stop_status.png)
   Você também pode interromper um workflow de definição de metas automaticamente quando a execução atinge uma atividade. To do this, right-click the activity from which targeting workflow will be stopped, and select **[!UICONTROL Do not activate]**.

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   Essa configuração é exibida por um ícone especial.

   >[!NOTE]
   >
   >Essa opção é útil durante as fases avançadas de criação e teste de campanhas de definição de metas.

* Interrupção incondicional

   In the Explorer, select **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]** to access and act on every campaign workflows.

   You can unconditionally stop your workflow by clicking the **[!UICONTROL Actions]** icon and selecting **[!UICONTROL Unconditional]** stop. Esta ação encerra o workflow da campanha.

   ![](assets/s_user_segmentation_stop_unconditional.png)

### Definindo um grupo de controle {#defining-a-control-group}

Um grupo de controle é uma população que não receberá o delivery; ele é usado para rastrear o comportamento após o delivery e o impacto da campanha fazendo uma comparação com o comportamento da população do target, que recebeu o delivery.

O grupo de controle pode ser extraído do target principal e/ou vir de um grupo ou query específica.

#### Ativar o grupo de controle para uma campanha {#activating-the-control-group-for-a-campaign}

Você pode definir um grupo de controle no nível da campanha, caso em que o grupo de controle será aplicado a cada entrega da campanha em questão.

1. Edite a campanha em questão e clique na **[!UICONTROL Edit]** guia.
1. Clique em **[!UICONTROL Advanced campaign settings]**.

   ![](assets/s_ncs_user_edit_op_target.png)

1. Selecione a **[!UICONTROL Enable and edit control group configuration]** opção.
1. Clique em **[!UICONTROL Edit...]** para configurar o grupo de controle.

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

O procedimento de configuração é apresentado em [Extrair o grupo de controle do alvo](#extracting-the-control-group-from-the-main-target) principal e [Adicionar uma população](#adding-a-population).

#### Ativar o grupo de controle para uma entrega {#activating-the-control-group-for-a-delivery}

Você pode definir um grupo de controle no nível da entrega, caso em que o grupo de controle será aplicado a cada entrega da campanha em questão.

Por padrão, a configuração do grupo de controle definida no nível da campanha se aplica a cada delivery dessa campanha. Entretanto, você pode adaptar o grupo de controle de um delivery individual.

>[!NOTE]
>
>Se você tiver definido um grupo de controle para uma campanha e também configurá-lo para um delivery vinculado a essa campanha, somente o grupo de controle definido para o delivery será aplicado.

1. Edite a entrega em questão e clique no **[!UICONTROL To]** link na **[!UICONTROL Email parameters]** seção.

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. Clique na **[!UICONTROL Control group]** guia e selecione **[!UICONTROL Enable and edit control group configuration]**.
1. Clique em **[!UICONTROL Edit...]** para configurar o grupo de controle.

O procedimento de configuração é apresentado em [Extrair o grupo de controle do alvo](#extracting-the-control-group-from-the-main-target) principal e [Adicionar uma população](#adding-a-population).

#### Extração do grupo de controle do target principal {#extracting-the-control-group-from-the-main-target}

Você pode extrair recipients do target principal do delivery. Nesse caso, os recipients serão retirados do target das ações de delivery afetadas por essa configuração. Essa extração pode ser aleatória ou pode ser resultado da classificação de recipients.

![](assets/s_ncs_user_extract_from_target_population.png)

To extract a control group, enable the control group for the campaign or delivery and select one of the following options: **[!UICONTROL Activate random sampling]** or **[!UICONTROL Keep only the first records after sorting]**.

* **[!UICONTROL Activate random sampling]** : esta opção aplica amostragem aleatória aos destinatários na população-alvo. Se você definir o limite como 100, o grupo de controle será constituído de 100 recipients selecionados aleatoriamente da população direcionada. A amostragem aleatória depende do mecanismo de banco de dados.
* **[!UICONTROL Keep only the first records after sorting]** : essa opção permite definir uma limitação com base em uma ou mais ordens de classificação. If you select the **[!UICONTROL Age]** field as a sorting criterion and then define 100 as a threshold, the control group will be made up of the 100 youngest recipients. Por exemplo, pode ser interessante definir um grupo de controle que inclua recipients que façam poucas compras ou recipients que façam compras frequentes e comparar seu comportamento com os recipients contatados.

Click **[!UICONTROL Next]** to define the sorting order (if necessary) and select the recipient limitation mode.

![](assets/s_ncs_user_edit_op_target_param.png)

Essa configuração é equivalente a uma atividade de compartilhamento no workflow, que permite dividir o target em subconjuntos. O grupo de controle é um desses subconjuntos. Consulte [esta seção](../../workflow/using/executing-a-workflow.md#architecture) para obter mais informações.

### Adicionar uma população {#adding-a-population}

Você pode definir uma nova população a ser usada como um grupo de controle. Essa população pode vir de um grupo de recipients ou você pode criá-la por meio de uma query específica.

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>O editor de query do Adobe Campaign é apresentado  [nesta seção](../../workflow/using/query.md).

## Iniciar um delivery {#starting-a-delivery}

Depois que todas as aprovações tiverem sido concedidas, o delivery estará pronto para ser iniciado. O procedimento de delivery depende do tipo de delivery. Para entregas por email ou canais móveis, consulte [Iniciar uma entrega](#starting-an-online-delivery)online e para entregas por mala direta, consulte [Iniciar uma entrega](#starting-an-offline-delivery)offline.

### Iniciar um delivery on-line {#starting-an-online-delivery}

Once all approval requests have been granted, the delivery status changes to **[!UICONTROL Pending confirmation]** and can be started by an operator. Quando apropriado, o operador (ou grupo de operadores) do Adobe Campaign designado como revisor para iniciar o delivery é notificado de que um delivery está pronto para ser iniciado.

>[!NOTE]
>
>Se um operador ou grupo de operadores específico for designado para iniciar um delivery nas propriedades do delivery, você também poderá permitir que o operador responsável pelo delivery confirme o delivery. Para fazer isso, ative a opção **NMS_ActivateOwnerConfirmation** inserindo **1** como o valor. As opções são gerenciadas no nó **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** no Adobe Campaign explorer.
>  
>Para desativar essa opção, insira **0** como valor. O processo de confirmação de delivery funcionará como padrão: somente o operador ou grupo de operadores designado ao delivery nas propriedades de delivery (ou um administrador) poderá confirmar e realizar o delivery.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

As informações também aparecem no painel de campanha. The **[!UICONTROL Confirm delivery]** link lets you start the delivery.

![](assets/s_ncs_user_edit_del_to_start.png)

Uma mensagem de confirmação permite que você proteja esta ação.

### Iniciar um delivery off-line {#starting-an-offline-delivery}

Once all approvals have been granted, the delivery status changes to **[!UICONTROL Pending extraction]**. Os arquivos de extração são criados por um workflow especial, que em uma configuração padrão, inicia automaticamente quando um delivery de mala direta está com extração pendente. Quando um processo está em andamento, ele é exibido no painel e pode ser editado através do link.

>[!NOTE]
>
>Os fluxos de trabalho técnicos relativos aos processos de campanha são apresentados na [Lista de fluxos de trabalho](../../workflow/using/campaign.md)do processo de campanha.

**Etapa 1 - Aprovação de arquivo**

Após executar o workflow de extração com sucesso, o arquivo de extração deve ser aprovado (fornecido de forma que a aprovação do arquivo de extração tenha sido selecionada nas configurações do delivery).

Para obter mais informações, consulte [Aprovação de um arquivo](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file)de extração.

**Etapa 2 - Aprovação da mensagem para o provedor de serviços**

* Depois que o arquivo de extração for aprovado, você poderá gerar a prova de e-mail de notificação do roteador. Esta mensagem de e-mail é construída com base em um template de delivery. Deve ser aprovado.

   >[!NOTE]
   >
   >Esta etapa só estará disponível se o envio e a aprovação de provas tiverem sido habilitados na janela de aprovações.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* Clique no **[!UICONTROL Send a proof]** botão para criar as provas.

   O target da prova deve ser definido com antecedência.

   Você pode criar quantas provas forem necessárias. These are accessed via the **[!UICONTROL Direct mail...]** link of the delivery detail.

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* O status da entrega muda para **[!UICONTROL To submit]**. Click the **[!UICONTROL Submit proofs]** button to start the approval process.

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* The delivery status changes to **[!UICONTROL Proof to validate]** and a button lets you accept or reject approval.

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   Você pode aceitar ou rejeitar esta aprovação ou retornar à etapa de extração.

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* O arquivo de extração é enviado ao roteador e o delivery é concluído.

### Cálculo de custos e estoques {#calculation-of-costs-and-stocks}

A extração de arquivo inicia duas operações: cálculo de orçamento e cálculo de estoque. As entradas do orçamento são atualizadas.

* The **[!UICONTROL Budget]** tab lets you manage the budgets for the campaign. The total of the cost entries is shown in the **[!UICONTROL Calculates cost]** field of the campaign&#39;s main tab and the program it belongs to. Os montantes também são refletidos no orçamento da campanha.

   O custo real será calculado de acordo com as informações fornecidas pelo roteador. Apenas mensagens enviadas são faturadas.

* As ações são definidas no **[!UICONTROL Administration > Campaign management > Stocks]** nó da árvore e as estruturas de custo no **[!UICONTROL Administration > Campaign management > Service providers]** nó.

   As linhas de estoque estão visíveis na seção de estoque. Para definir o estoque inicial, abra uma linha de estoque. O estoque é reduzido sempre que um delivery ocorre. Você pode definir um nível de alerta e notificações.

>[!NOTE]
>
>Para obter mais informações sobre cálculos de custos e gerenciamento de ações, consulte [Provedores, ações e orçamentos](../../campaign/using/providers--stocks-and-budgets.md).

## Gerenciar documentos associados {#managing-associated-documents}

Você pode associar vários documentos a uma campanha: relatório, foto, página da Web, diagrama, etc. Esses documentos podem estar em qualquer formato (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF etc.). To link documents with a campaign, see [Adding documents](#adding-documents).

>[!IMPORTANT]
>
>Esse modo é reservado para documentos pequenos.

Em uma campanha que você também pode consultar outros itens, como cupons promocionais, ofertas especiais relacionadas a uma filial específica ou loja, etc. Quando esses elementos estão incluídos em um outline, eles podem ser associados a um delivery de mala direta. See [Associating and structuring resources linked via a delivery outline](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Se você estiver usando o MRM, também poderá gerenciar uma biblioteca de recursos de marketing disponíveis para vários participantes de trabalho colaborativo. Consulte [Gerenciamento de recursos](../../campaign/using/managing-marketing-resources.md)de marketing.

### Adicionar documentos {#adding-documents}

Os documentos podem ser associados no nível da campanha (documentos contextuais) ou no nível do programa (documentos gerais).

A **[!UICONTROL Documents]** guia contém:

* A lista de todos os documentos necessários para o conteúdo (template, imagens etc.) que pode ser baixado localmente pelos operadores do Adobe Campaign com direitos adequados,
* Documentos contendo informações para o roteador, se houver.

The documents are linked to the program or the campaign via the **[!UICONTROL Edit > Documents]** tab.

![](assets/s_ncs_user_op_add_document.png)

Você também pode adicionar um documento a uma campanha através do link oferecido em seu painel.

![](assets/add_a_document_in_op.png)

Click the **[!UICONTROL Details]** icon to view the content of a file and to add information:

![](assets/s_ncs_user_op_add_document_details.png)

In the dashboard, documents associated with the campaign are grouped in the **[!UICONTROL Document(s)]** section, as in the following example:

![](assets/s_ncs_user_op_edit_document.png)

Eles também podem ser editados e modificados nessa visualização.

### Associar e estruturar recursos vinculados por meio de um delivery outline {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>Os contornos de entrega são usados exclusivamente no contexto de campanhas de mala direta.

Um delivery outline indica um conjunto estruturado de elementos (documentos, ramificações/lojas, cupons promocionais etc.) criados na empresa e para uma campanha específica.

Esses elementos são agrupados em delivery outlines e um delivery outline específico será associado a um delivery; ele será referenciado no arquivo de extração enviado ao **provedor de serviços** para ser anexada ao delivery. Por exemplo, você pode criar um delivery outline que se refere a uma unidade e aos folhetos de marketing que ela usa.

Para uma campanha, delivery outlines permitem que você estruture elementos externos a serem associados ao delivery de acordo com determinados critérios: a unidade relacionada, a oferta promocional concedida, o convite para um evento local etc.

#### Criar uma estrutura de tópicos {#creating-an-outline}

To create an outline, click the **[!UICONTROL Delivery outlines]** sub-tab in the **[!UICONTROL Edit > Documents]** tab of the concerned campaign.

>[!NOTE]
>
>Se essa guia não estiver presente, significa que esse recurso não está disponível para esta campanha. Consulte a configuração do template de campanha.
>   
>For more on this, refer to [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Next, click **[!UICONTROL Add a delivery outline]** and create the hierarchy of outlines for the campaign:

1. Right-click the root of the tree and select **[!UICONTROL New > Delivery outlines]**.
1. Clique com o botão direito do mouse no contorno que acabou de criar e selecione **[!UICONTROL New > Item]** ou **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

Uma estrutura pode conter itens e campos de personalização, recursos e ofertas:

* Os itens podem ser documentos físicos, por exemplo, que são referenciados e descritos aqui e serão anexados ao delivery.
* Os campos de personalização permitem que você crie elementos de personalização relacionados a remessas em vez de recipients. Assim, é possível criar valores a serem usados em entregas para uma meta específica (oferta de boas-vindas, desconto, etc.) Eles são criados no Adobe Campaign e importados para o outline por meio do **[!UICONTROL Import personalization fields...]** link.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   They can also be created directly in the outline by clicking the **[!UICONTROL Add]** icon to the right of the list zone.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* The resources are marketing resources generated in the marketing resource dashboard accessed via the **[!UICONTROL Resources]** link of the **[!UICONTROL Campaigns]** universe.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Para obter mais informações sobre recursos de marketing, consulte [Gerenciamento de recursos](../../campaign/using/managing-marketing-resources.md)de marketing.

#### Selecionar uma estrutura {#selecting-an-outline}

Para cada delivery, você pode selecionar o outline para associar na seção reservada para o outline da extração, como no exemplo a seguir:

![](assets/s_ncs_user_op_select_composition.png)

A estrutura selecionada é então exibida na seção inferior da janela. Ele pode ser editado usando o ícone à direita do campo ou alterado usando a lista suspensa:

![](assets/s_ncs_user_op_select_composition_b.png)

The **[!UICONTROL Summary]** tab of the delivery also displays this information:

![](assets/s_ncs_user_op_select_composition_c.png)

#### Resultado da extração {#extraction-result}

No arquivo extraído e enviado ao provedor de serviços, o nome da estrutura e, quando apropriado, suas características (custo, descrição etc.) são adicionados ao conteúdo de acordo com as informações no template de exportação associado ao provedor de serviços.

No seguinte exemplo, o rótulo, custo estimado e descrição do outline associado ao delivery serão adicionados no arquivo de extração.

![](assets/s_ncs_user_op_composition_in_export_template.png)

O modelo de exportação deve estar associado ao provedor de serviços selecionado para o delivery. See [Creating service providers and their cost structures](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Para saber mais sobre exportações, consulte a seção [Introdução](../../platform/using/generic-imports-and-exports.md) .
