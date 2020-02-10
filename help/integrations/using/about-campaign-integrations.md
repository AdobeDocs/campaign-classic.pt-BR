---
title: Sobre integrações do Campaign
description: Saiba mais sobre as integrações funcionais disponíveis entre a versão atual do Adobe Campaign e [soluções da Adobe Experience Cloud]
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
source-git-commit: 2e16d4de068f8cb1e61069aa53626f7bf7021466

---


# Sobre integrações do Campaign{#about-campaign-integrations}

Saiba mais sobre as integrações funcionais disponíveis entre a versão atual do Adobe Campaign e as [soluções da Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/mcloud/marketing-cloud-integrations.html) e [serviços principais](https://marketing.adobe.com/resources/help/en_US/mcloud/core-services-landing.html) .

A Adobe Experience Cloud é um conjunto abrangente das melhores soluções integradas, criadas em uma plataforma de dados comum com um conjunto comum de serviços principais avançados.

Descubra a lista completa de soluções e serviços principais da Adobe que podem ser integrados ao Adobe Campaign, bem como a documentação associada, [nesta página](#experience-cloud-integrations).

>[!CAUTION]
>
>A maioria dessas integrações requer o login por meio de uma Adobe ID (IMS). Para obter mais informações sobre essa implementação, consulte [esta página](../../integrations/using/about-adobe-id.md).
>
>A implementação IMS é um processo complexo, que deve ser planejado anteriormente, já que pode ser demorado. É estritamente reservado para os administradores técnicos do Adobe Campaign.

## Trabalhando com soluções da Experience Cloud {#working-with-experience-cloud-solutions}

Dependendo do seu ambiente, várias soluções podem ser vinculadas à Adobe Experience Cloud. Elas são vinculadas como Organizações. Uma **organização** é a entidade que permite a um administrador configurar grupos e usuários e controlar o logon único na Experience Cloud. A organização funciona como uma empresa de login que abrange todos os produtos e soluções da Experience Cloud. Na maioria das vezes, uma organização é o nome da sua empresa. No entanto, uma empresa pode ter muitas organizações.

A gestão de organização e a vinculação às contas da Adobe Experience Cloud são detalhadas no [portal de ajuda da Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html)

>[!CAUTION]
>
>Quando o Adobe Campaign é recém-instalado ou é integrado a uma instalação existente com a Adobe Experience Cloud, o [serviço da Experience Cloud ID](https://marketing.adobe.com/resources/help/en_US/mcvid/) está habilitado. Esse serviço substitui o cookie permanente usado primeiro e mais importante pelo Adobe Campaign para suas funcionalidades de rastreamento.
>
>Uma ID de visitante exclusiva será atribuída aos recipients que geram logs de rastreamento. Essa ID será salva no **[!UICONTROL Requester UUID (@sourceID)]** campo da **[!UICONTROL nms:trackingLogRcp]** tabela. Os dados de rastreamento dos recipients existentes antes do serviço de ID de visitante foram implementados e, portanto, não serão mais utilizáveis.
>
>A ID será reconhecida pelas outras soluções da Adobe Experience Cloud com o mesmo [CNAME](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_cname.html).

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
   <td> <strong>Adobe Campaign Standard</strong> (oferta principal)<br /> </td> 
   <td> Permite replicar dados para o <strong>Campaign Standard</strong>, unindo o melhor de ambos os aplicativos. O Campaign Classic v7 tem ferramentas avançadas para gerenciar o banco de dados de marketing principal. A replicação de dados do Campaign Classic v7 permite que o Campaign Standard aproveite os dados avançados em um ambiente fácil de usar.<br /><p> <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Saiba mais</a> sobre o Adobe Campaign Classic - integração do Adobe Campaign Standard.</p><br /></td> 
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
   <td> <strong>Serviço</strong><br /> principal de pessoas <strong>Adobe Audience Manager</strong><br /> </td> 
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
   <td> A integração entre o <strong>serviço principal Triggers</strong> e o Adobe Campaign permite enviar emails personalizados para seus clientes como uma reação a comportamentos específicos que são rastreados em seu site pelo Adobe Analytics. Para obter mais informações, consulte o seguinte <a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">artigo</a>.<br /> <p><a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">Saiba mais</a> sobre a integração Adobe Campaign – Experience Cloud Triggers.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics – Data Connectors</strong><br /> </td> 
   <td> <strong>Data connectors</strong> (anteriormente conhecido como Adobe Genesis) permite que o Adobe Campaign e o Adobe Analytics se relacionam por meio de segmentos com o comportamento de usuário após uma campanha de email. Por outro lado, ele envia indicadores 
                e atributos de campanhas de email entregues pelo Adobe Campaign para o Adobe Analytics – 
                Data Connector.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Saiba mais</a> sobre a integração Campaign – Data Connectors.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Plataforma de dados do cliente em tempo real da Adobe</strong><br /> </td> 
   <td> A integração entre o Adobe Campaign e a Plataforma de dados do cliente em tempo real da Adobe permite que você compartilhe dados de segmentos e importe públicos para o Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Saiba mais</a> sobre o Campaign - Integração da plataforma de dados do cliente em tempo real da Adobe.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

