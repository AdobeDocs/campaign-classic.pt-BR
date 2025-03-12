---
product: campaign
title: Workflow de entrega entre canais
description: Saiba mais sobre os workflows de entrega entre canais
feature: Workflows, Channels Activity
hide: true
hidefromtoc: true
exl-id: dfd36d2c-44ff-49a9-80b4-09eaf3377072
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '670'
ht-degree: 100%

---

# Workflow de entrega entre canais{#cross-channel-delivery-workflow}



Esse caso de uso apresenta um exemplo envolvendo um workflow de entrega entre canais. O conceito geral de entregas entre canais é apresentado [nesta seção](cross-channel-deliveries.md).

O objetivo é segmentar um público dos destinatários do banco de dados em diferentes grupos com o objetivo de enviar um e-mail para um grupo e uma mensagem SMS para outro grupo.

As principais etapas de implementação para este caso de uso são as seguintes:

1. Criação de uma atividade **[!UICONTROL Query]** para segmentar seu público.
1. Criação de uma atividade **[!UICONTROL Email delivery]** contendo um link para uma oferta.
1. Usar uma atividade **[!UICONTROL Split]** para:

   * Enviar outro e-mail para os destinatários que não abriram o primeiro e-mail.
   * Enviar um SMS para os destinatários que abriram o e-mail, mas não clicaram no link da oferta.
   * Adicionar ao banco de dados os destinatários que abriram o e-mail e clicaram no link.

![](assets/wkf_cross-channel_7.png)

## Etapa 1: Direcionamento de público {#step-1--targeting-the-audience}

Para definir seu target, crie uma query para identificar os destinatários.

1. Crie uma campanha. Para obter mais informações, consulte [esta seção](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. Na guia **[!UICONTROL Targeting and workflows]** da campanha, adicione uma atividade de **Query** ao workflow. Para obter mais informações sobre o uso dessa atividade, consulte [esta seção](query.md).
1. Defina os destinatários que receberão suas entregas. Por exemplo, selecione os membros &quot;Ouro&quot; como a target dimension.
1. Adicione as condições do filtro à sua query. Neste exemplo, selecione destinatários que tenham um endereço de e-mail e um número de celular.

   ![](assets/wkf_cross-channel_3.png)

1. Salve as alterações.

## Etapa 2: Criação de um email incluindo uma oferta {#step-2--creating-an-email-including-an-offer}

1. Crie uma atividade **[!UICONTROL Email delivery]** e clique duas vezes nela no workflow para editá-la. Para obter mais informações sobre criar e-mails, consulte [esta seção](../../delivery/using/about-email-channel.md).
1. Crie a mensagem e insira um link incluindo uma oferta no conteúdo.

   ![](assets/wkf_cross-channel_1.png)

   Para obter mais informações sobre como integrar uma oferta ao corpo de uma mensagem, consulte [esta seção](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine).

1. Salve as alterações.
1. Clique com o botão direito do mouse na atividade **[!UICONTROL Email delivery]** para abri-la.
1. Selecione a opção **[!UICONTROL Generate an outbound transition]** para recuperar a população e os logs de rastreamento.

   ![](assets/wkf_cross-channel_2.png)

   Isso permitirá usar essas informações para enviar outra entrega dependendo dos comportamentos dos destinatários ao receberem o primeiro e-mail.

1. Adicione uma atividade **[!UICONTROL Wait]** para dar alguns dias para os destinatários abrirem o email.

   ![](assets/wkf_cross-channel_4.png)

## Etapa 3: Segmentação do público resultante {#step-3--segmenting-the-resulting-audience}

Depois que seu target for identificado e sua primeira entrega for criada, será necessário segmentar o target em diferentes populações usando condições de filtro.

1. Adicione uma atividade **Split** ao workflow e abra-a. Para obter mais informações sobre o uso dessa atividade, consulte [esta seção](split.md).
1. Crie três segmentos a partir da população upstream processado na query.

   ![](assets/wkf_cross-channel_6.png)

1. Para o primeiro subconjunto, selecione a opção **[!UICONTROL Add a filtering condition on the inbound population]** e clique em **[!UICONTROL Edit]**.

   ![](assets/wkf_cross-channel_8.png)

1. Selecione **[!UICONTROL Recipients of a delivery]** como o filtro de restrição e clique em **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_9.png)

1. Nas configurações de filtro, selecione **[!UICONTROL Recipients who have not opened or clicked (email)]** na lista suspensa **[!UICONTROL Behavior]** e selecione o email, incluindo a oferta que você deseja enviar na lista de entrega. Clique em **[!UICONTROL Finish]**.

   ![](assets/wkf_cross-channel_10.png)

1. Continue de forma semelhante no segundo subconjunto e selecione **[!UICONTROL Recipients who have not clicked (email)]** na lista suspensa **[!UICONTROL Behavior]**.

   ![](assets/wkf_cross-channel_11.png)

1. Para o terceiro subconjunto, depois de selecionar o **[!UICONTROL Add a filtering condition on the inbound population]** e clicar em **[!UICONTROL Edit]**, selecione a opção **[!UICONTROL Use a specific filtering dimension]**.
1. Selecione **[!UICONTROL Recipient tracking log]** na lista suspensa **[!UICONTROL Filtering dimension]**, destaque **[!UICONTROL Filtering conditions]** na **[!UICONTROL List of restriction filters]** e clique em **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_12.png)

1. Selecione as condições do filtro como mostrado a seguir:

   ![](assets/wkf_cross-channel_13.png)

1. Clique em **[!UICONTROL Finish]** para salvar as alterações.

## Etapa 4: Finalização do workflow {#step-4--finalizing-the-workflow}

1. Adicione as atividades relevantes ao workflow após os três subconjuntos resultantes da atividade **[!UICONTROL Split]**:

   * Adicione uma atividade **[!UICONTROL Email delivery]** para enviar um email de lembrete para o primeiro subconjunto.
   * Adicione uma atividade **[!UICONTROL Mobile delivery]** para enviar uma mensagem SMS ao segundo subconjunto.
   * Adicione uma atividade **[!UICONTROL List update]** para adicionar os destinatários correspondentes ao banco de dados.

1. Clique duas vezes nas atividades de entrega no seu workflow para editá-las. Para obter mais informações sobre como criar um e-mail e um SMS, consulte o [canal de e-mail](../../delivery/using/about-email-channel.md) e o [canal de SMS](../../delivery/using/sms-channel.md).
1. Clique duas vezes na atividade **[!UICONTROL List update]** e selecione a opção **[!UICONTROL Generate an outbound transition]**.

   É possível exportar os destinatários resultantes do Adobe Campaign para o Adobe Experience Cloud. Por exemplo, é possível usar o público no Adobe Target adicionando uma atividade **[!UICONTROL Update shared audience]** ao workflow. Para obter mais informações, consulte [Exportação de um público](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience).

1. Clique no botão **Start** na barra de ações para executar o workflow.

A população direcionada pela atividade **Consulta** será segmentada para receber um e-mail ou uma entrega SMS de acordo com os comportamentos dos destinatários. A população restante será adicionada ao banco de dados usando a atividade **[!UICONTROL List update]**.
