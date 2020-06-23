---
title: Sobre integrações do Campaign
description: Saiba mais sobre as integrações funcionais disponíveis entre a versão atual do Adobe Campaign e as soluções da Adobe Experience Cloud
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c3737b22c7bf4e614c5a2fbe8e8fd954d3ece8a
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 96%

---


# Sobre integrações do Campaign {#about-campaign-integrations}

A Adobe Experience Cloud é um conjunto abrangente das melhores soluções integradas, criadas em uma plataforma de dados comum com um conjunto comum de serviços principais avançados.

Saiba mais sobre as integrações funcionais disponíveis entre o Adobe Campaign, as [soluções da Adobe Experience Cloud](https://docs.adobe.com/content/help/pt-BR/core-services/interface/marketing-cloud-integrations.html) e os [serviços principais](https://docs.adobe.com/content/help/pt-BR/core-services/interface/about-core-services/core-services.html). Em seguida, é possível modernizar as implementações da solução e implementar a Experience Cloud para que você possa usar recursos como atributos do cliente e públicos.

A lista completa de soluções e serviços principais da Adobe que podem ser integrados ao Adobe Campaign, bem como a documentação associada, estão disponíveis [nesta seção](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>A maioria dessas integrações requer o login por meio de uma Adobe ID (IMS). Para obter mais informações sobre essa implementação, consulte [esta página](../../integrations/using/about-adobe-id.md).
>
>Observe que a implementação do IMS é um processo complexo, que pode ser longo. É estritamente reservado para os administradores técnicos do Adobe Campaign.

## Vincular suas soluções {#working-with-experience-cloud-solutions}

Dependendo do seu ambiente, várias soluções podem ser vinculadas à Adobe Experience Cloud. Elas são vinculadas como Organizações. Uma **organização** é a entidade que permite a um administrador configurar grupos e usuários e controlar o logon único na Experience Cloud. A organização funciona como uma empresa de login que abrange todos os produtos e soluções da Experience Cloud. Na maioria das vezes, uma organização é o nome da sua empresa. No entanto, uma empresa pode ter muitas organizações.

A gestão de organização e a vinculação às contas da Adobe Experience Cloud são detalhadas no [portal de ajuda da Adobe Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)

>[!CAUTION]
>
>Quando o Adobe Campaign é recém-instalado ou é integrado a uma instalação existente com a Adobe Experience Cloud, o [serviço da Experience Cloud ID](https://docs.adobe.com/content/help/en/id-service/using/home.html) está habilitado. Esse serviço substitui o cookie permanente usado primeiro e mais importante pelo Adobe Campaign para suas funcionalidades de rastreamento.
>
>Uma ID de visitante exclusiva será atribuída aos recipients que geram logs de rastreamento. Essa ID será salva no campo **[!UICONTROL Requester UUID (@sourceID)]** da tabela **[!UICONTROL nms:trackingLogRcp]**. Os dados de rastreamento dos recipients existentes antes do serviço de ID de visitante foram implementados e, portanto, não serão mais utilizáveis.
>
>A ID será reconhecida pelas outras soluções da Adobe Experience Cloud com o mesmo [CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html).

## Integrações da Experience Cloud {#experience-cloud-integrations}

A tabela a seguir fornece acesso à documentação disponível da integração da Experience Cloud.

<table> 
 <thead> 
  <tr> 
   <th> Solução e serviços principais<br /> </th> 
   <th> Casos de uso<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Plataforma de dados do cliente em tempo real da Adobe</strong><br /> </td> 
   <td> A integração entre o Adobe Campaign e a Plataforma de dados do cliente em tempo real da Adobe permite que você compartilhe dados de segmentos e importe públicos para o Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Saiba mais</a> sobre o Campaign - Integração da plataforma de dados do cliente em tempo real da Adobe.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS – Adobe ID</strong><br /> </td> 
   <td> Permite conexão ao Adobe Campaign com a mesma Adobe ID para as outras soluções da Adobe Experience Cloud.<br /> Uma Adobe ID deve ser usada para fazer logon para usar determinadas funcionalidades vinculadas às integrações da Adobe Experience Cloud, principalmente os Serviços Principais.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Saiba mais</a> sobre a implementação da Adobe ID com o Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Permite criar conteúdo de email ou formulários mapeados para o banco de dados do Adobe Campaign diretamente no <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Saiba mais</a> sobre a integração Adobe Campaign – Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Permite inserir imagens que são dinamicamente calculadas pelo <strong>Adobe Target</strong> quando o email criado e enviado pelo Adobe Campaign é aberto.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Saiba mais</a> sobre a integração Adobe Campaign – Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Serviço principal de pessoas</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Permite compartilhar públicos entre as soluções da Adobe Experience Cloud e o núcleo que você usa.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Saiba mais</a> sobre as integrações Adobe Campaign – Serviços principais de pessoas e Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Serviço principal de ativos</strong><br /> </td> 
   <td> Permite inserir ativos da biblioteca da Adobe Experience Cloud em emails e landing pages criadas no Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Saiba mais</a> sobre a integração Adobe Campaign – Serviços principais de ativos</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Permite inserir ativos a partir da sua biblioteca <strong>AEM Assets</strong> em emails e landing pages criadas no Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Saiba mais</a> sobre a integração Adobe Campaign – AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> A integração entre o <strong>serviço principal Triggers</strong> e o Adobe Campaign permite enviar emails personalizados para seus clientes como uma reação a comportamentos específicos que são rastreados em seu site pelo Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/br/campaign/kb/triggers-and-campaign.html">Saiba mais</a> sobre a integração Adobe Campaign – Experience Cloud Triggers.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics – Data Connectors</strong><br /> </td> 
   <td> <strong>Data connectors</strong> (anteriormente conhecido como Adobe Genesis) permite que o Adobe Campaign e o Adobe Analytics se relacionam por meio de segmentos com o comportamento de usuário após uma campanha de email. Por outro lado, ele envia indicadores e atributos de campanhas de email entregues pelo Adobe Campaign para o Adobe Analytics – Data Connector.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Saiba mais</a> sobre a integração Campaign – Data Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

