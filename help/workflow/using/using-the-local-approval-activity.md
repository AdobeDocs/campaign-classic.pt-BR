---
title: O uso da atividade de aprovação local
seo-title: O uso da atividade de aprovação local
description: O uso da atividade de aprovação local
seo-description: null
page-status-flag: never-activated
uuid: 6003aaed-543d-4e6b-b1f2-ad4e9757bff3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: c143d8c3-c3ce-470c-8812-4b19cdb8afbf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# O uso da atividade de aprovação local{#using-the-local-approval-activity}

The **[!UICONTROL Local approval]** activity integrated into a targeting workflow lets you set up a recipient approval process before the delivery is sent.

>[!CAUTION]
>
>Para usar essa função, é necessário adquirir o módulo Marketing Distribuído, que é uma opção do Campaign. Verifique o contrato de licença.

Para configurar esse caso de uso, criamos o seguinte workflow para construção do target:

![](assets/local_validation_workflow.png)

As principais etapas do ciclo de aprovação de conteúdo são:

1. The population resulting from targeting can be limited thanks to a **[!UICONTROL Split]** type activity using a data distribution model.

   ![](assets/local_validation_intro_1.png)

1. The **[!UICONTROL Local approval]** activity then takes over and sends a notification email to each local supervisor. A atividade permanece pendente até que cada supervisor local aprove os recipients atribuídos a eles.

   ![](assets/local_validation_intro_4.png)

1. Ao atingir o prazo final para aprovação, o workflow será iniciado novamente. In this example, the **[!UICONTROL Delivery]** activity starts and the delivery is sent to the approved targets.

   >[!NOTE]
   >
   >Ao atingir o prazo final, os recipients que não tiverem sido aprovados serão excluídos do target.

   ![](assets/local_validation_intro_6.png)

1. A few days later, the second **[!UICONTROL Local approval]** type activity sends a notification email to each local supervisor with a summary of the actions carried out by their contacts (clicks, opens, etc.).

   ![](assets/local_validation_intro_5.png)

## Step 1: Creating the data distribution template {#step-1--creating-the-data-distribution-template-}

O template de distribuição de dados permite limitar o público resultante do target com base no agrupamento de dados, permitindo atribuir cada valor a um supervisor local. In this example, we have defined the **[!UICONTROL Email address domain]** field as a distribution field and assigned a domain to each local supervisor

Para obter mais informações sobre como criar um modelo de distribuição de dados, consulte [Limitação do número de registros de subconjunto por distribuição](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)de dados.

1. Para criar o modelo de distribuição de dados, vá para o **[!UICONTROL Resources > Campaign management > Data distribution]** nó e clique em **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. Select the **[!UICONTROL General]** tab.

   ![](assets/local_validation_data_distribution_2.png)

1. Insira o **[!UICONTROL Label]** e o **[!UICONTROL Distribution context]**. In this example, we have selected the **[!UICONTROL Recipient]** targeting schema and the **[!UICONTROL Email domain]** field as a distribution field. A lista de recipients será dividida por domínio.
1. In the **[!UICONTROL Distribution type]** field, select how the target limitation value will be expressed in the **[!UICONTROL Distribution]** tab. Aqui, escolhemos **[!UICONTROL Percentage]**.
1. In the **[!UICONTROL Approval storage]** field, enter the storage schema of the approvals that match the targeting schema in use. Aqui vamos usar o schema de armazenamento padrão: **[!UICONTROL Local approval of recipients]**.
1. Em seguida, clique no **[!UICONTROL Advanced parameters]** link.

   ![](assets/local_validation_data_distribution_3.png)

1. Keep the **[!UICONTROL Approve the targeted messages]** option checked so that all recipients are pre-selected from the list of recipients to approve.
1. In the **[!UICONTROL Delivery label]** field, we&#39;ve left the default expression (compute string of the delivery). O rótulo padrão do delivery será usado na notificação de feedback.
1. In the **[!UICONTROL Grouping field]** section, we have selected the **[!UICONTROL Gender]** field as a grouping field for displaying recipients in the approval and feedback notifications.
1. Na **[!UICONTROL Edit targeted messages]** seção, selecionamos o aplicativo da **[!UICONTROL Edit recipients]** Web e o **[!UICONTROL recipientId]** parâmetro. Nas notificações de aprovação e de feedback, os recipients serão clicáveis e apontarão para a URL da aplicação Web. The additional URL parameter will be **[!UICONTROL recipientId]**.
1. Em seguida, clique na **[!UICONTROL Distribution]** guia. Para cada domínio, insira os seguintes campos:

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**: digite o valor do nome do domínio.
   * **[!UICONTROL Percentage / Fixed]**: para cada domínio, insira o máximo. número de destinatários para os quais você deseja enviar a entrega. Neste exemplo, queremos limitar o delivery a 10% por domínio.
   * **[!UICONTROL Label]**: digite o rótulo do domínio a ser exibido nas notificações de aprovação e feedback.
   * **[!UICONTROL Group or operator]**: selecione o operador ou grupo de operadores atribuídos ao domínio.

      >[!CAUTION]
      >
      >Verifique se os operadores receberam os direitos apropriados.

## Step 2: Creating the targeting workflow {#step-2--creating-the-targeting-workflow}

Para configurar esse caso de uso, criamos o seguinte workflow para construção do target:

![](assets/local_validation_workflow.png)

As seguintes atividades foram adicionadas:

* Duas **[!UICONTROL Query]** atividades,
* Uma **[!UICONTROL Intersection]** atividade,
* Uma **[!UICONTROL Split]** atividade,
* Uma **[!UICONTROL Local approval]** atividade,
* Uma **[!UICONTROL Delivery]** atividade,
* Uma **[!UICONTROL Wait]** atividade,
* Uma segunda **[!UICONTROL Local approval]** atividade,
* Uma **[!UICONTROL End]** atividade.

### Queries, Intersecção e Split {#queries--intersection-and-split}

O target de upstream é composto de dois queries, uma intersecção e um Split. The population resulting from targeting can be limited using a **[!UICONTROL Split]** activity using a data distribution template.

For more on configuring a split activity, refer to [Split](../../workflow/using/split.md). A criação de um modelo de distribuição de dados é detalhada em [Limitação do número de registros do subconjunto por distribuição](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)de dados.

If you do not want to limit the population from the query, you do not have to use the **[!UICONTROL Query]**, **[!UICONTROL Intersection]**, and **[!UICONTROL Split]** activities. In this case, complete the data distribution template in the first **[!UICONTROL Local approval]** activity.

1. Na **[!UICONTROL Record count limitation]** seção, selecione a **[!UICONTROL Limit the selected records]** opção e clique no **[!UICONTROL Edit]** link.

   ![](assets/local_validation_split_1.png)

1. Selecione a **[!UICONTROL Keep only the first records after sorting]** opção e clique em **[!UICONTROL Next]**.

   ![](assets/local_validation_split_1bis.png)

1. In the **[!UICONTROL Sort columns]** section, add the field which the sort is applied to. Here, we have chosen the **[!UICONTROL Email]** field. Clique em **[!UICONTROL Next]**.

   ![](assets/local_validation_split_2.png)

1. Selecione a **[!UICONTROL By data distribution]** opção, selecione o modelo de distribuição criado anteriormente (consulte a [Etapa 1: Criando o modelo](#step-1--creating-the-data-distribution-template-)de distribuição de dados) e clique em **[!UICONTROL Finish]**.

   ![](assets/local_validation_split_3.png)

No template de distribuição, limitamos o público a 10% por valor de agrupamento, que coincide com os valores exibidos no workflow (340 como entrada e 34 como output).

![](assets/local_validation_intro_1.png)

### Notificação de aprovação {#approval-notification}

The **[!UICONTROL Local approval]** activity lets you send a notification to each local supervisor.

Para obter mais informações sobre como configurar a **[!UICONTROL Local approval]** atividade, consulte Aprovação [](../../workflow/using/local-approval.md)local.

![](assets/local_validation_workflow_2.png)

Os seguintes campos precisam ser inseridos:

1. Na **[!UICONTROL Action to execute]** seção, selecione a **[!UICONTROL Target approval notification]** opção.
1. Na **[!UICONTROL Distribution context]** seção, selecione a **[!UICONTROL Specified in the transition]** opção.

   If you don&#39;t want to limit the targeted population, select the **[!UICONTROL Explicit]** option here and enter the distribution template created previously in the **[!UICONTROL Data distribution]** field.

1. In the **[!UICONTROL Notification]** section, select the delivery template and the subject to be used for the notification email. Aqui, escolhemos o template padrão: **[!UICONTROL Local approval notification]**.
1. In the **[!UICONTROL Approval schedule]** section, we&#39;ve kept the default approval deadline (3 days) and added a reminder. O delivery será enviado 3 dias após o início da aprovação. Ao atingir o prazo final de aprovação, os recipients que não foram aprovados não serão considerados.

The notification email sent by the **[!UICONTROL Local approval]** activity to local supervisors is as follows:

![](assets/local_validation_intro_2.png)

### Aguardar {#wait}

A atividade de espera permite adiar o início da segunda atividade de aprovação local que enviará a notificação de feedback de delivery. No **[!UICONTROL Duration]** campo, inserimos o **[!UICONTROL 5d]** valor (5 dias). As ações executadas por recipients por cinco dias após o envio do delivery serão incluídas na notificação de feedback.

![](assets/local_validation_workflow_3.png)

### Notificação de feedback {#feedback-notification}

The second **[!UICONTROL Local approval]** activity lets you send a delivery feedback notification to each local supervisor.

![](assets/local_validation_workflow_4.png)

Os seguintes campos precisam ser inseridos.

1. Na **[!UICONTROL Action to execute]** seção, escolha **[!UICONTROL Delivery feedback report]**.
1. Na **[!UICONTROL Delivery]** seção, escolha **[!UICONTROL Specified in the transition]**.
1. In the **[!UICONTROL Notification]** section, select the delivery template and the subject to be used for the notification email.

Once the deadline configured in the wait activity is reached, the second **[!UICONTROL Local approval]** type activity sends the following notification email to each local supervisor:

![](assets/local_validation_intro_3.png)

### Controle de aprovação pelo administrador {#approval-tracking-by-the-administrator}

Toda vez que a atividade de aprovação local começa, uma tarefa de aprovação é criada. O administrador pode controlar cada tarefa de aprovação.

Go to the targeting workflow of your campaign and click the **[!UICONTROL Local approval tasks]** tab.

![](assets/local_validation_admin_1.png)

The list of local approval tasks can also be accessed via the **[!UICONTROL Approval tasks]** tab of the data distribution template.

![](assets/local_validation_admin_2.png)

Select the task you want to monitor and click the **[!UICONTROL Detail]** button. The **[!UICONTROL General]** tab of the local approval task lets you view information on the task. Se necessário, você pode alterar a aprovação e as datas de lembrete.

![](assets/local_validation_admin_3.png)

Essa guia exibe as seguintes informações:

* o rótulo da tarefa e sua ID
* o template de distribuição usado
* o número de mensagens de target
* o workflow e campanha vinculados
* o cronograma da tarefa

The **[!UICONTROL Distribution]** tab for the task lets you view the approval logs, their status, the number of messages targeted, the approval date, as well as the operator who approved the delivery.

![](assets/local_validation_admin_4.png)

Select an approval log and click the **[!UICONTROL Detail]** button to display more information. The **[!UICONTROL General]** tab of the local approval log lets you view general log information. Você também pode alterar o status de aprovação.

![](assets/local_validation_admin_5.png)

Essa guia exibe as seguintes informações:

* a tarefa de aprovação vinculada
* o estado de aprovação (**[!UICONTROL Approved]** ou **[!UICONTROL Pending]**)
* o template de distribuição usado
* o supervisor local que aprovou e a data de aprovação
* o número de mensagens de target e aprovadas

The **[!UICONTROL Targeted]** tab of the approval log displays the list of targeted recipients and their approval status. Você pode alterar este status, se necessário.

![](assets/local_validation_admin_6.png)

