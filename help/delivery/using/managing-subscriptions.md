---
title: Gerenciamento de assinaturas
seo-title: Gerenciamento de assinaturas
description: Gerenciamento de assinaturas
seo-description: null
page-status-flag: never-activated
uuid: a2c526fa-3080-4dd5-9628-f0e7040f93cd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 9a61fe74-f779-4f23-be25-3d9a8e95704a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Gerenciamento de assinaturas{#managing-subscriptions}

## Sobre os serviços de informações {#about-information-services}

Um serviço de informação compreende:

* Registro e subscrições (aceitação),
* Cancelar registro, cancelar subscrições voluntariamente (opt-out) ou cancelamento de subscrições automático (serviço por tempo limitado, por exemplo, como uma oferta de avaliação),
* Mecanismos de confirmação e cancelamento de subscrições (mecanismos simples com confirmação, opt-in duplo etc.),
* Controle de histórico do assinante.

Como um recurso padrão, esses serviços incluem relatórios estatísticos específicos: rastreamento de assinante, nível de fidelidade, tendências de cancelamento de subscrições etc.

Para emails, os links obrigatórios de cancelamento de subscrições são gerados automaticamente e o processo inteiro das opções de aceitação/recusa é totalmente automatizado, com o rastreamento de histórico para garantir total conformidade com as normas em vigor.

Há três modos de serviço de subscrição/unsubscription:

1. manual
1. por importação (somente subscrição),
1. por meio de um formulário da web

>[!NOTE]
>
>Uma amostra para criar um formulário de subscrição com opt-in duplo está detalhada [nesta seção](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

## Criação de um serviço de informação {#creating-an-information-service}

É possível criar e gerenciar subscrições de serviços de informações com mensagens de confirmação associadas ou entregas automáticas aos assinantes.

Para acessar o mapa dos serviços de informações, vá para o **[!UICONTROL Profiles and Targets]** universo e clique no **[!UICONTROL Services and Subscriptions]** link.

![](assets/s_ncs_user_services_new.png)

Para editar um serviço existente, clique em seu respectivo nome. To create a service, click the **[!UICONTROL Create]** button located above the list.

![](assets/s_ncs_user_services_add.png)

* Enter the name of the service in the **[!UICONTROL Label]** field and select the delivery channel: email, mobile, Facebook, Twitter, or mobile applications.

   >[!NOTE]
   >
   >As subscrições do Facebook e do Twitter estão detalhadas [nesta seção](../../social/using/about-social-marketing.md). As assinaturas de aplicativos móveis estão detalhadas em [Sobre o canal](../../delivery/using/about-mobile-app-channel.md)de aplicativos móveis.

* Para um serviço de tipo de email, selecione o **Modo de delivery**. The possible modes are: **[!UICONTROL Newsletter]** or **[!UICONTROL Viral]**.
* Você pode enviar **mensagens de confirmação** para uma subscrição ou unsubscription. To do this, select the delivery templates to be used to create the corresponding deliveries from the **[!UICONTROL Subscription]** and **[!UICONTROL Unsubscription]** fields. These templates must be configured with a **[!UICONTROL Subscription]** type target mapping, without a defined target. Consulte a seção [Sobre canal](../../delivery/using/about-email-channel.md)de email.
* Por padrão, as subscrições são ilimitadas. You can deselect the **[!UICONTROL Unlimited]** option to define a validity duration for the service. A duração pode ser especificada em dias (**[!UICONTROL d]** ) ou meses (**[!UICONTROL m]** ).

Depois que o serviço for salvo, ele será adicionado à lista Serviços e assinaturas: Clique no nome para editá-lo. Várias guias estão disponíveis. The **[!UICONTROL Subscriptions]** tab lets you look at the list of subscribers to the information service (**[!UICONTROL Active subscriptions]** tab) or the subscription/unsubscription history (**[!UICONTROL History]** tab). Além disso, é possível adicionar e excluir assinantes a partir desta guia. See [Adding and deleting subscribers](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

The **[!UICONTROL Detail...]** button lets you look at the subscription properties for the selected recipient.

Você pode modificar as propriedades de subscrição de um recipient.

![](assets/s_ncs_user_services_modify.png)

No painel, clique na **[!UICONTROL Reports]** guia para rastrear assinaturas: alterações nos níveis de assinatura, número total de assinantes, etc. É possível arquivar relatórios e analisar históricos nesta guia.

## Adição e exclusão de assinantes {#adding-and-deleting-subscribers}

From the **[!UICONTROL Subscriptions]** tab of an information service click **[!UICONTROL Add]** to add subscribers. You can also right-click the list of subscribers and select **[!UICONTROL Add]**. Select the folder in which the profiles to be subscribed are stored, and then select the profiles to subscribe and click **[!UICONTROL OK]** to validate.

To delete subscribers, select them and click **[!UICONTROL Delete]**. You can also right-click the subscriber list and select **[!UICONTROL Delete]**.

In both cases, you can send a confirmation message to the users concerned if a delivery template for unsubscriptions has been attached to the service (see [Creating an information service](#creating-an-information-service)). Um aviso permite validar ou não este delivery:

![](assets/s_ncs_user_services_update.png)

See [Subscription and unsubscription mechanisms](#subscription-and-unsubscription-mechanisms).

## Fazendo delivery aos assinantes de um serviço {#delivering-to-the-subscribers-of-a-service}

Para fazer delivery aos assinantes de um serviço de informação, é possível direcionar os assinantes ao serviço de informação relacionado, como no exemplo a seguir:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>The target mapping must be **[!UICONTROL Subscriptions]**.

Selecione **[!UICONTROL Subscribers of an information service]** e clique em **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Select the targeted information service and click **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

The **[!UICONTROL Preview]** tab lets you view the list of subscribers to the selected information service.

## Mecanismos de subscrição e unsubscription {#subscription-and-unsubscription-mechanisms}

Você pode configurar mecanismos de subscrição e unsubscription para automatizar o gerenciamento de processos e de assinantes.

>[!NOTE]
>
>É possível enviar uma mensagem de confirmação para os assinantes novos.\
>The content of this message is defined in the information service configuration via the **[!UICONTROL Subscription]** or **[!UICONTROL Unsubscription]** fields.
>
>As mensagens de confirmação são criadas por meio dos templates de delivery especificados nesses campos. These target mappings must be **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Subscrever um recipient a um serviço {#subscribing-a-recipient-to-a-service}

Para registrar recipients para um serviço de informação, é possível:

* Manually add the service: to do this, from the **[!UICONTROL Subscriptions]** tab of their profile, click **[!UICONTROL Add]** and select the information service concerned.

   Para obter mais informações, consulte a seção sobre edição de perfil [nesta seção](../../platform/using/editing-a-profile.md).

* Subscrever automaticamente um conjunto de assinantes a este serviço. A lista de recipients pode vir de uma operação de filtragem, grupo, pasta, importação ou seleção direta usando o mouse. Para inscrever esses recipients, selecione os perfis e clique com o botão direito do mouse. Selecione **[!UICONTROL Actions > Subscribe selection to a service...]**, selecione o serviço em questão e inicie a operação.
* Importar recipients e inscrevê-los automaticamente em um serviço de informação. Para fazer isso, selecione o serviço na última etapa do assistente de importação.

   Para obter mais informações, consulte [esta seção](../../platform/using/importing-data.md#import-wizard).

* Usar um formulário da Web para que os recipients possam subscrever-se a um serviço.

   Para obter mais informações, consulte [esta seção](../../web/using/about-web-applications.md).

* Creating a targeting workflow and using a **[!UICONTROL Subscription service]** box.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   Workflows e como usá-los estão detalhados [nesta seção](../../workflow/using/about-workflows.md).

### Cancelamento de subscrição de um recipient a um serviço {#unsubscribing-a-recipient-from-a-service}

#### Cancelamento manual de subscrição {#manual-unsubscribing}

por lei, deliveries de email devem conter um link para cancelamento. Os recipients podem clicar neste link para atualizar seu perfil e ser excluídos do envio dos futuros deliveries.

The default unsubscription link is inserted via the last button in the toolbar of the content editor provided in the delivery wizard (see [About personalization](../../delivery/using/about-personalization.md)). Quando o recipient clica nesse link, o perfil passa a ser não autorizado (recusado), significando que este recipient não será mais direcionado por qualquer ação de delivery.

Os recipients podem, no entanto, optar por cancelar a subscrição de um serviço sem cancelar a subscrição de todos os serviços. To allow this, you can use a web form (refer to [this section](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) or insert a personalized unsubscription link (see [Personalization blocks](../../delivery/using/personalization-blocks.md)).

Também é possível cancelar a subscrição de um recipient manualmente no perfil do recipient. To do this, click the **[!UICONTROL Subscriptions]** tab of the recipient concerned, select the information service(s) concerned, and click **[!UICONTROL Delete]**.

Por fim, é possível cancelar a subscrição de um ou mais recipients por meio do serviço de informação relacionado. To do this, click the **[!UICONTROL Subscriptions]** tab of the service, select the recipients concerned and click **[!UICONTROL Delete]**.

#### Cancelamento automático de subscrição {#automatic-unsubscription}

Um serviço de informação pode ter uma duração limitada. Os recipients terão a subscrição cancelada automaticamente quando o período de validade expirar. This period is specified in the **[!UICONTROL Edit]** tab of the service properties. Ele é expresso em dias.

![](assets/s_ncs_user_services_delay.png)

Você também pode configurar um workflow de cancelamento de subscrições para uma população. To do this, follow the same procedure as for a subscription workflow, but select the **[!UICONTROL Unsubscription]** option. See [Subscribing a recipient to a service](#subscribing-a-recipient-to-a-service).

### Rastreamento do assinante {#subscriber-tracking}

You can track the changes in subscriptions to the information services using the **[!UICONTROL Reports]** link on the dashboard.

![](assets/s_ncs_user_services_report.png)
