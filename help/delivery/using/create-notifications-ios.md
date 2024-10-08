---
product: campaign
title: Criar uma notificação por push para dispositivos iOS
description: Saiba como criar notificações por push para iOS
feature: Push
role: User, Developer, Data Engineer
exl-id: 4520504a-0d9f-4ea7-a5a8-0c07948af4f0
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: ht
source-wordcount: '971'
ht-degree: 100%

---

# Criar notificações para iOS{#create-notifications-ios}

Esta seção detalha os elementos específicos para a entrega de notificações do iOS. Os conceitos globais sobre a criação de entregas são apresentados [nesta seção](steps-about-delivery-creation-steps.md).

Comece criando uma nova entrega.

![](assets/nmac_delivery_1.png)

Para criar uma notificação por push para dispositivos iOS, siga as etapas abaixo:

1. Selecione o modelo de entrega **[!UICONTROL Deliver on iOS]**.

   ![](assets/nmac_delivery_ios_1.png)

1. Para definir o target da notificação, clique no link **[!UICONTROL To]** e, em seguida, clique em **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >O processo detalhado ao selecionar a população do target de uma entrega é apresentado [nesta seção](steps-defining-the-target-population.md).
   >
   >Para obter mais informações sobre o uso de campos de personalização, consulte [esta seção](about-personalization.md).
   >
   >Para obter mais informações sobre a inclusão de uma lista de seeds, consulte [Sobre seed addresses](about-seed-addresses.md).

1. Selecione **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, depois o serviço relevante para o aplicativo móvel (Neotrips, neste caso) e clique na versão iOS do aplicativo.

   ![](assets/nmac_delivery_ios_3.png)

1. Escolha seu **[!UICONTROL Notification type]**: **[!UICONTROL General notification (Alert, Sound, Badge)]** ou **[!UICONTROL Silent notification]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >O modo **Push silencioso** permite que uma notificação &quot;silenciosa&quot; seja enviada a um aplicativo móvel. O usuário não está ciente da chegada da notificação. Ele é transferido diretamente para o aplicativo.

1. No campo **[!UICONTROL Title]**, insira o rótulo do título que deve aparecer na lista de notificações disponível no centro de notificações.

   Este campo permite a definição do valor do parâmetro **title** do conteúdo de notificação do iOS.

1. Você pode adicionar um **[!UICONTROL Subtitle]**, que é o valor do parâmetro de subtítulo do conteúdo de notificação do iOS. Consulte [esta seção](configuring-the-mobile-application.md).

1. Insira o conteúdo da mensagem na seção **[!UICONTROL Message content]** do assistente. O uso de campos de personalização é apresentado na seção [Sobre a personalização](about-personalization.md).

   ![](assets/nmac_delivery_ios_5.png)

1. Clique no ícone **[!UICONTROL Insert emoticon]** para inserir emoticons à notificação via push. Para personalizar a lista de emoticons, consulte [esta seção](customizing-emoticon-list.md)

1. Na guia **[!UICONTROL Sound and Badge]**, é possível editar as seguintes opções:

   * **[!UICONTROL Clean Badge]**: ative essas opções para atualizar o valor do selo.

   * **[!UICONTROL Value]**: defina um número que será usado para exibir o número de novas informações não lidas diretamente no ícone do aplicativo.

   * **[!UICONTROL Critical alert mode]**: ative essa opção para adicionar som à sua notificação, mesmo que o telefone do usuário esteja configurado no modo de foco ou se o iPhone estiver sem áudio.

   * **[!UICONTROL Name]**: selecione o som a ser reproduzido pelo terminal móvel quando a notificação for recebida.

   * **[!UICONTROL Volume]**: volume do som, de 0 a 100.

   >[!NOTE]
   >
   >Os sons devem ser incluídos no aplicativo e definidos quando o serviço for criado. Consulte [esta seção](configuring-the-mobile-application.md#configuring-external-account-ios).

   ![](assets/nmac_delivery_ios_6.png)

1. Na guia **[!UICONTROL Application variables]**, suas **[!UICONTROL Application variables]** são adicionadas automaticamente. Elas permitem definir o comportamento da notificação: por exemplo, é possível configurar uma tela de aplicativo específica para ser exibida quando o usuário ativar a notificação.

   Para obter mais informações, consulte [esta seção](configuring-the-mobile-application.md).

1. Na guia **[!UICONTROL Advanced]**, é possível editar as seguintes opções gerais:

   * **[!UICONTROL Mutable content]**: habilite essa opção para permitir que o aplicativo móvel baixe conteúdo de mídia.

   * **[!UICONTROL Thread-id]**: identificador usado para agrupar notificações relacionadas.

   * **[!UICONTROL Category]**: nome da ID da categoria que exibirá botões de ação. Essas notificações fornecem ao usuário uma maneira mais rápida de realizar tarefas diferentes em resposta a uma notificação sem abrir o aplicativo ou navegar até ele.

   ![](assets/nmac_delivery_ios_7.png)

1. Para notificações sensíveis ao tempo, é possível especificar as seguintes opções:

   * **[!UICONTROL Target content ID]**: identificador usado para definir qual janela de aplicativo será apresentada quando a notificação for aberta.

   * **[!UICONTROL Launch image]**: nome do arquivo de imagem que será exibido na inicialização. Se o usuário optar por iniciar seu aplicativo, a imagem selecionada será exibida em vez da tela de inicialização do aplicativo.

   * **[!UICONTROL Interruption level]**:

      * **[!UICONTROL Active]**: selecionado por padrão; o sistema apresenta a notificação imediatamente, ativa a tela e pode reproduzir um som. As notificações não interrompem os modos de foco.

      * **[!UICONTROL Passive]**: o sistema adiciona a notificação à lista de notificações sem ativar a tela ou reproduzir um som. As notificações não interrompem os modos de foco.

      * **[!UICONTROL Time sensitive]**: o sistema apresenta a notificação imediatamente, ativa a tela, pode reproduzir um som e interrompe os modos de foco. Esse nível não requer uma permissão especial da Apple.

      * **[!UICONTROL Critical]**: o sistema apresenta a notificação imediatamente, ativa a tela e ignora os modos de foco e a opção de mudo. Observe que esse nível requer uma permissão especial da Apple.

   * **[!UICONTROL Relevance score]**: defina uma pontuação de relevância de 0 a 100. O sistema usa essa opção para classificar as notificações no resumo de notificações.

   ![](assets/nmac_delivery_ios_8.png)

1. Quando a notificação estiver configurada, clique na guia **[!UICONTROL Preview]** para visualizar a notificação.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >O estilo de notificação (banner ou alerta) não é definido no Adobe Campaign. Isso depende da configuração selecionada pelo usuário nas configurações do iOS. No entanto, o Adobe Campaign permite a visualização de cada tipo de estilo de notificação. Clique na seta na parte inferior direita para alternar entre os estilos.
   >
   >A pré-visualização utiliza a aparência e comportamento do iOS 10.

Para enviar uma prova e a entrega final, use o mesmo processo que as entregas de email. [Saiba mais](steps-validating-the-delivery.md)

Após enviar as mensagens, você pode monitorar e rastrear suas entregas. Para obter mais informações, consulte essas seções.

* [Quarentenas de notificação por push](understanding-quarantine-management.md#push-notification-quarantines)
* [Monitoramento de uma entrega](about-delivery-monitoring.md)
* [Compreensão de falhas de entrega](understanding-delivery-failures.md)

## Criação de uma notificação avançada do iOS {#creating-ios-delivery}

Com o iOS 10 ou superior, é possível gerar notificações ricas. O Adobe Campaign pode enviar notificações usando variáveis que permitirão ao dispositivo exibir uma notificação rica.

Em seguida, é necessário criar uma nova entrega e vinculá-la ao aplicativo para dispositivos móveis criado.

1. Vá até **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Clique em **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecione **[!UICONTROL Deliver on iOS (ios)]** na lista suspensa **[!UICONTROL Delivery template]**. Adicione um **[!UICONTROL Label]** à entrega.

1. Clique em **[!UICONTROL To]** para definir a população como target. Por padrão, o target mapping **[!UICONTROL Subscriber application]** é aplicado. Clique em **[!UICONTROL Add]** para selecionar o serviço criado anteriormente.

   ![](assets/nmac_ios_9.png)

1. Na janela **[!UICONTROL Target type]**, selecione **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** e clique em **[!UICONTROL Next]**.

1. Na lista suspensa **[!UICONTROL Service]**, selecione o serviço criado anteriormente e, em seguida, o aplicativo que deseja direcionar e clique em **[!UICONTROL Finish]**.

   ![](assets/nmac_ios_6.png)

1. Edite a notificação avançada.

   ![](assets/nmac_ios_7.png)

1. Na guia **[!UICONTROL Application variables]**, as **[!UICONTROL Application variables]** são adicionadas automaticamente, dependendo do que foi adicionado durante as etapas de configuração.

   >[!NOTE]
   >
   >As variáveis do aplicativo devem ser definidas no código do aplicativo móvel e inseridas durante a criação do serviço. Para obter mais informações, consulte [esta seção](configuring-the-mobile-application.md).

   ![](assets/nmac_ios_10.png)

1. Na guia **[!UICONTROL Advanced]**, marque a caixa **[!UICONTROL Mutable content]** para permitir que o aplicativo móvel baixe conteúdo de mídia.

1. Clique em **[!UICONTROL Save]** e envie a entrega.

A imagem e a página da Web devem ser exibidas na notificação por push quando recebida nos dispositivos iOS móveis dos inscritos.

![](assets/nmac_ios_8.png)




