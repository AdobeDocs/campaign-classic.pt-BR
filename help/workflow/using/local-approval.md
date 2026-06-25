---
product: campaign
title: Aprovação local
description: Aprovação local
feature: Workflows
hide: true
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
TQID: https://experienceleague.adobe.com/V2s1XUP8-VeljwRdwE2-Ad-mFD3JAcEW6kEldXglVho
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 645
ht-degree: 100%

---

# Aprovação local{#local-approval}



Quando integrado em um fluxo de trabalho de segmentação, a atividade **[!UICONTROL Local approval]** permite configurar um processo de aprovação de destinatário antes do envio da entrega.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>Para usar essa atividade, você precisa ter adquirido o módulo Marketing distribuído, que é uma opção do Campaign. Verifique o contrato de licença.

Para obter um exemplo da atividade **[!UICONTROL Local approval]** com um modelo de distribuição, consulte [Uso da atividade de aprovação local](using-the-local-approval-activity.md).

Comece inserindo um rótulo para a atividade e o campo **[!UICONTROL Action to execute]**:

![](assets/local_validation_1.png)

* Selecione a opção **[!UICONTROL Target approval notification]** para enviar um email de notificação para supervisores locais antes da entrega, pedindo sua aprovação dos destinatários atribuídos a eles.

  ![](assets/local_validation_intro_2.png)

* **Consulta incremental**: permite executar um query e planejar sua execução. Consulte a seção [Consulta incremental](incremental-query.md).

  ![](assets/local_validation_intro_3.png)

## Notificação de aprovação de target {#target-approval-notification}

Nesse caso, a atividade **[!UICONTROL Local approval]** é colocada entre o direcionamento e a entrega upstream:

![](assets/local_validation_2.png)

Os campos a serem inseridos no caso de uma notificação para aprovação de target são:

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**: selecione a opção **[!UICONTROL Specified in the transition]** se estiver usando uma atividade do tipo **[!UICONTROL Split]** para limitar a população de destino. Nesse caso, o modelo de distribuição é inserido na atividade de Split. Se você não estiver limitando a população de destino, selecione a opção **[!UICONTROL Explicit]** aqui e insira o modelo de distribuição no campo **[!UICONTROL Data distribution]**.

  Para obter mais informações sobre como criar um modelo de distribuição de dados, consulte [Limitação do número de registros de subconjunto por distribuição de dados](split.md#limiting-the-number-of-subset-records-per-data-distribution).

* **[!UICONTROL Approval management]**

   * Selecione o modelo de entrega e o assunto que será usado para a notificação por email. Um modelo padrão está disponível: **[!UICONTROL Local approval notification]**. Você também pode adicionar uma descrição que aparecerá acima das listas de destinatários nas notificações de aprovação e de feedback.
   * Especifique o **[!UICONTROL Approval type]** que corresponda ao prazo final de aprovação (data ou prazo final do início da aprovação). Nesta data, o fluxo de trabalho começa novamente e os destinatários que não foram aprovados não serão considerados na segmentação. Depois que as notificações forem enviadas, a atividade será colocada em fila para que os supervisores locais possam aprovar seus contatos.

     >[!NOTE]
     >
     >Por padrão, quando o processo de aprovação é iniciado, a atividade fica pendente por três dias.

     Você também pode adicionar um ou mais lembretes para informar aos supervisores locais que o prazo final está se aproximando. Para fazer isso, clique em **[!UICONTROL Add a reminder]**.

* **[!UICONTROL Complementary set]**: a opção **[!UICONTROL Generate complement]** permite gerar um segundo conjunto que inclui todos os targets não aprovados.

  >[!NOTE]
  >
  >Essa opção está desabilitada por padrão.

## Relatório de feedback de entrega {#delivery-feedback-report}

Nesse caso, a atividade **[!UICONTROL Local approval]** é disponibilizada após a entrega:

![](assets/local_validation_4.png)

No caso de um relatório de feedback de entrega, os seguintes campos devem ser inseridos:

![](assets/local_validation_workflow_4.png)

* Selecione a opção **[!UICONTROL Specified in the transition]** se a entrega foi inserida durante uma atividade anterior. Selecione **[!UICONTROL Explicit]** para especificar a entrega na atividade de aprovação local.
* Selecione o modelo de entrega e o objeto do email de notificação. Há um modelo padrão: **[!UICONTROL Local approval notification]**.

## Exemplo: aprovação de uma entrega de fluxo de trabalho {#example--approving-a-workflow-delivery}

Este exemplo mostra como configurar um processo de aprovação para uma entrega de fluxo de trabalho. Para obter mais informações sobre como criar fluxos de trabalho de entrega, consulte a seção [Exemplo: fluxo de trabalho de entrega](delivery.md#example--delivery-workflow).

Um operador pode aprovar uma entrega de duas formas: usando a página da Web vinculada na mensagem de email ou através do console.

* Aprovação da Web

  O email enviado para operadores do grupo Administrador permite aprovar o target da entrega. A mensagem usa o texto definido e a expressão JavaScript é substituída pelo valor calculado (neste caso, &#39;574&#39;)

  Para aprovar a entrega, clique no link relevante e entre no console do Adobe Campaign.

  ![](assets/new-workflow-valid-webaccess.png)

  Escolha e clique no botão **[!UICONTROL Submit]**.

  ![](assets/new-workflow-valid-webaccess-confirm.png)

* Aprovação através do console

  Na estrutura de árvore, o nó **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** contém a lista de tarefas a serem aprovadas pelo operador conectado atualmente. A lista deve exibir uma linha. Clique duas vezes na linha para responder. A janela a seguir é exibida:

![](assets/new-workflow-7.png)

Selecione **Yes** e depois clique em **[!UICONTROL Approve]**. Uma mensagem informará que a resposta foi registrada.

Volte para a tela fluxo de trabalho. Após aproximadamente dez segundos, o diagrama é exibido da seguinte maneira:

![](assets/new-workflow-8.png)

O fluxo de trabalho executou a tarefa **[!UICONTROL Delivery control]**, que nesse caso significa iniciar a entrega criada anteriormente. O fluxo de trabalho foi concluído sem erros.
