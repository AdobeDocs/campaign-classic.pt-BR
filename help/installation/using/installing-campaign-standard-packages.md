---
title: Instalação de pacotes padrão do Campaign Classic
seo-title: Instalação de pacotes padrão do Campaign Classic
description: Instalação de pacotes padrão do Campaign Classic
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: efef031d9c662daac6634ff7cc0d05d9d512443b

---


# Instalação de pacotes padrão do Campaign Classic{#installing-campaign-standard-packages}

## Sobre pacotes padrão {#campaign-standard-packages}

Pacotes são um conjunto de recursos que podem ser instalados de acordo com suas necessidades. Eles permitirão que você adicione mais opções à sua instância.

>[!CAUTION]
>
>You may only install packages corresponding the options mentioned in your license contract.
>
>Depois que um pacote é instalado, não é possível desinstalá-lo. A instalação de um novo pacote pode afetar toda a sua plataforma: deve ser testado e validado antes da implantação final.

Para instalar um pacote padrão:

1. Acesse o assistente de importação do pacote **[!UICONTROL Tools > Advanced > Package import...]** no console do cliente Adobe Campaign.
1. Select **[!UICONTROL Install a standard package]**.
1. Na lista exibida, verifique os pacotes que deseja instalar.
   >[!NOTE]
   >
   >If a package is greyed out, you cannot install it. Isso significa que ele já está instalado ou não é compatível com sua instância. For example, you cannot install the **Mid-sourcing platform** package on a marketing instance. You will find this information in the table below.
1. Clique em **[!UICONTROL Next]**, em seguida, **[!UICONTROL Start]** para start da instalação do pacote.

   Once the packages are installed, the progress bar shows **100%** and you can see the following message in the installation logs: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** the installation window.

Os pacotes agora estão instalados.

### List of out-of-the-box Packages {#list-of-standard-packages}

A tabela a seguir lista todos os pacotes padrão com sua descrição, o tipo de instância em que eles podem ser instalados (Marketing, Mid etc.) and additional information.

<table> 
 <thead> 
  <tr> 
   <th> Package </th> 
   <th> Descrição </th> 
   <th> Instance type </th> 
   <th> More info </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivery<br /> </td> 
   <td> Monitors deliveries and eventual issues encountered when messages are sent.<br /> </td> 
   <td> Todos</td> 
   <td> <a href="../../delivery/using/monitoring-a-delivery.md">Saiba mais</a></td> 
  </tr> 
  <tr> 
   <td> Marketing campaigns (Campaign)<br /> </td> 
   <td> Defines, optimizes, executes and analyzes communications and marketing campaigns.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../campaign/using/designing-marketing-campaigns.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> Controls marketing actions in a collaborative mode by providing management and tracking of the tasks, budgets and marketing resources.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../campaign/using/about-marketing-resource-management.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Offer engine (interaction)<br /> </td> 
   <td> Responds in real time during an interaction with a given contact (a customer or target) by making them a single or several adapted offers. <br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../interaction/using/interaction-and-offer-management.md">saiba mais</a></td> 
  </tr> 
  <tr> 
   <td> Controlo do motor de oferta com instância de execução<br /> </td> 
   <td> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <tr> 
   <td> Offer engine for execution instances<br /> </td> 
   <td> </td> 
   <td> Meio, Execução <br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Social networks (Social Marketing) <br /> </td> 
   <td> Synchronizes Adobe Campaign with Twitter and Facebook.<br /> </td> 
   <td> Todos</td> 
   <td> <a href="../../social/using/about-social-marketing.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Transactional message control (Message Center - Control)<br /> </td> 
   <td> Manages trigger messages generated from events triggered from information systems.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../message-center/using/about-transactional-messaging.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Transactional message execution (Message Center - Execution) <br /> </td> 
   <td> Ensures higher availability and better load management.<br /> </td> 
   <td> Execução<br /> </td> 
   <td> Opcional, <a href="../../message-center/using/about-transactional-messaging.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Canal LINE<br /> </td> 
   <td> Envia delivery usando o canal LINE com Adobe Campaign,<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, obrigatório para o centro de mensagens</td> 
  </tr> 
  <tr> 
   <td> Direct Mail channel<br /> </td> 
   <td> Envia delivery para Adobe Campaign com o canal de mala direta.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/about-direct-mail-channel.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Mobile channel (SMS) <br /> </td> 
   <td> Sends deliveries using the Mobile/SMS channel with Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/sms-channel.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Telephone channel<br /> </td> 
   <td> Sends deliveries using the Telephone channel with Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <tr> 
   <td> Fax channel<br /> </td> 
   <td> Sends deliveries using the fax channel with Adobe Campaign.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional</td> 
  </tr> 
  <tr> 
   <td> Canal de aplicativo móvel<br /> </td> 
   <td> Usa a plataforma Adobe Campaign para enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos. <br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/about-mobile-app-channel.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Gerenciador de conteúdo<br /> </td> 
   <td> Cria boletins informativos ou site recorrentes e, em seguida, valida e publica suas mensagens.<br /> </td> 
   <td> </td> 
   <td> <a href="../../delivery/using/about-content-management.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> pesquisas on-line (Gerenciador de Pesquisas)<br /> </td> 
   <td> Creates and manages online forms to add or modify profile information, to subscribe, to unsubscribe or a competition entry form.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../web/using/about-surveys.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Permite analisar e medir dados, calcular estatísticas, simplificar e otimizar a criação e o cálculo de relatórios. Além disso, é possível criar relatórios e populações de públicos alvos. <br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../reporting/using/about-cubes.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Gestor de Resposta<br /> </td> 
   <td> Mede o sucesso e a rentabilidade de campanhas de marketing ou apresentações da oferta para todos os canais de comunicação.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../campaign/using/about-response-manager.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Access to external data (Federated Data Access)<br /> </td> 
   <td> Provides the Federated Data Access (FDA) option in order to process information stored in one or more external databases so that you can access external data without changing the structure of Adobe Campaign data.<br /> </td> 
   <td> Todos<br /> </td> 
   <td> Opcional, <a href="../../workflow/using/accessing-an-external-database--fda-.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Otimização de campanha<br /> </td> 
   <td> Controla, filtros e monitora o envio de delivery para que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, em conformidade com as políticas de comunicação de empresa. <br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../campaign/using/about-campaign-typologies.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Monitoramento da entregabilidade (Entregabilidade por email)<br /> </td> 
   <td> Measures the success of your campaigns reaching your recipients' inbox without bouncing, or being marked as spam.<br /> </td> 
   <td> Todos </td> 
   <td> Opcional, <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Coupon Management<br /> </td> 
   <td> Creates a set of coupons to add to upcoming marketing offers.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/personalized-coupons.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Renderização da caixa de entrada (IR)<br /> </td> 
   <td> Permite que você pré-visualização a mensagem enviada nos diferentes contextos em que ela pode ser recebida e verifique a compatibilidade em desktops e aplicativos principais. You need a Litmus account.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Opcional, <a href="../../delivery/using/inbox-rendering.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing Central/local (Marketing distribuído)<br /> </td> 
   <td> Implements cooperative campaigns between central entities (headquarters, marketing departments, etc.) and local entities (sales points, regional agencies, etc.).<br /> </td> 
   <td> Marketing </td> 
   <td> Opcional, <a href="../../campaign/using/about-distributed-marketing.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Conectores CRM<br /> </td> 
   <td> Provides various CRM connectors for linking your Adobe Campaign platform to your third-party systems.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../platform/using/crm-connectors.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Web Analytics connectors<br /> </td> 
   <td> Allows Adobe Campaign and Adobe Analytics to interact through the Web Analytics connectors package.<br /> </td> 
   <td> Marketing </td> 
   <td> Not compatible with Transactional messaging, <a href="../../platform/using/adobe-analytics-data-connector.md">Learn More</a> </td> 
  </tr> 
  <tr> 
   <td> Integração com o AEM<br /> </td> 
   <td> Permite que você gerencie o conteúdo de seus delivery de e-mail, bem como seus formulários diretamente no Adobe Experience Manager, para se beneficiar das funcionalidades de edição de conteúdo do AEM e das capacidades do delivery Adobe Campaign.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../integrations/using/about-adobe-experience-manager.md">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Integração de Audiência compartilhadas da Adobe Marketing Cloud<br /> </td> 
   <td> Allows you to exchange and share audiences/segments with Adobe Experience Cloud solutions and core services.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Exige IMS, <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Integração com a Adobe Marketing Cloud<br /> </td> 
   <td> Permite importar e exportar audiências/segmentos de diferentes soluções da Adobe Marketing Cloud para o Adobe Campaign. </td> 
   <td> Marketing</td> 
   <td> Opcional, <a href="../../integrations/using/configuring-ims.md#installing-the-package">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Regulamento de proteção de dados de privacidade<br /> </td> 
   <td> Contém funcionalidade adicional para ajudar com sua conformidade com privacidade no Campaign Classic.<br /> </td> 
   <td> Todos</td> 
   <td> <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">Saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> Detalhes da instalação e configuração de um servidor mid-sourcing, bem como a implantação de uma instância que permite que terceiros enviem mensagens no modo mid-sourcing.<br /> </td> 
   <td> Marketing </td> 
   <td> Opcional, <a href="../../installation/using/mid-sourcing-server.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> Plataforma Mid-sourcing<br /> </td> 
   <td> Essa configuração é uma solução intermediária ideal entre uma configuração hospedada (ASP) e a internalização. Os componentes de execução voltados para o exterior são executados em um servidor "mid-sourcing" hospedado no Adobe Campaign.<br /> </td> 
   <td> Mid-sourcing </td> 
   <td> Opcional, <a href="../../installation/using/mid-sourcing-server.md">saiba mais</a> </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Pontes Adobe Campaign v7 e Adobe Campaign Standard. É um recurso integrado no Campaign v7 que replica automaticamente os dados no Campaign Standard, unindo o melhor das duas aplicações. <br /> </td> 
   <td> Marketing </td> 
   <td> Opcional, <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">saiba mais</a> </td> 
  </tr> 
 </tbody> 
</table>

### Pacote do Centro de mensagens {#message-center-package}

Para adicionar um canal de delivery (canal móvel, canal de aplicativo móvel etc.), isso deve ser realizado antes da instalação do pacote do Centro de mensagens. Se você tiver iniciado um projeto do Centro de mensagens no canal de e-mail e, no meio do projeto, decidir adicionar um novo canal, siga estas etapas:

1. Install the channel you wish, for example the **Mobile channel**, using the package import wizard ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Import the file ( **[!UICONTROL Tools > Advanced > Import package > File]**), and select:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. Na página **[!UICONTROL XML data content to import]**, mantenha somente o template do delivery do Centro de mensagens correspondente ao canal anexado. Por exemplo, se você tiver adicionado o canal **** Mobile, mantenha somente o elemento **entidades** correspondente ao modelo **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). If you have added the **Mobile App Channel**, keep only the **iOS transactional message** templates (iosTriggerMessage) and **Android transactional message** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

### Pacote LINE {#line-package}

Para poder enviar delivery usando o canal LINE com o Adobe Campaign, é necessário instalar o pacote LINE.

A instalação do pacote LINE é uma instalação padrão detalhada na seção [Importando pacotes](../../platform/using/working-with-data-packages.md#importing-packages) .

![](assets/line_config_1.png)

>[!CAUTION]
>
>Os templates do delivery do Centro de mensagens para LINHA não estarão disponíveis se os pacotes do Centro de mensagens estiverem instalados antes da LINHA.
