---
product: campaign
title: Sobre integrações do Campaign
description: Use outras soluções da Adobe e combine suas diferentes funcionalidades com o Campaign
feature: Overview
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '733'
ht-degree: 100%

---

# Introdução às integrações do Adobe Campaign {#about-campaign-integrations}



A Adobe Experience Cloud é um conjunto abrangente das melhores soluções integradas, criadas em uma plataforma de dados comum com um conjunto comum de serviços principais avançados.

Saiba mais sobre as integrações funcionais disponíveis entre o Adobe Campaign, as [soluções da Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html?lang=pt-BR) e os [serviços principais](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=pt-BR). Em seguida, é possível modernizar as implementações da solução e implementar a Experience Cloud para que você possa usar recursos como atributos do cliente e públicos.

![](assets/ExCloud-solutions.png)

A lista completa de soluções e serviços principais da Adobe que podem ser integrados ao Adobe Campaign, bem como a documentação associada, estão disponíveis [nesta seção](#experience-cloud-integrations).

>[!CAUTION]
>
>A maioria dessas integrações exige a implementação do Sistema de gerenciamento de identidades (IMS) da Adobe para fazer logon via Adobe ID. [Saiba mais nesta página](../../integrations/using/about-adobe-id.md).
>

## Vincular soluções {#working-with-experience-cloud-solutions}

Várias soluções podem ser vinculadas à Adobe Experience Cloud. Uma **organização** é a entidade-cliente que permite a um administrador configurar grupos e usuários e controlar o logon único (SSO) na Adobe Experience Cloud. A organização funciona como uma empresa de login que abrange todos os produtos e soluções da Experience Cloud. Na maioria das vezes, uma organização é o nome da sua empresa. No entanto, uma empresa pode ter muitas organizações.

A gestão de organização e a vinculação às contas da Adobe Experience Cloud são detalhadas no [portal de ajuda da Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=pt-BR)

## Gerenciamento de identidade e cookies {#id-and-cookies}

Quando o Adobe Campaign é instalado ou integrado a uma instalação existente com a Adobe Experience Cloud, o [serviço de identidade da Adobe Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=pt-BR) está habilitado. Esse serviço substitui o cookie permanente usado primeiro e mais importante pelo Adobe Campaign para suas funcionalidades de rastreamento.

O Serviço de identidade da Adobe Experience Cloud (ID Service) fornece uma ID contínua e universal que identifica seus visitantes em todas as soluções na Experience Cloud.

Um identificador de visitante único será atribuído aos destinatários que geram logs de rastreamento. Essa ID será salva no campo **[!UICONTROL Requester UUID (@sourceID)]** da tabela **[!UICONTROL nms:trackingLogRcp]**. **Os dados de rastreamento dos destinatários existentes antes do serviço de ID de visitante foram implementados e, portanto, não serão mais utilizáveis**.

A ID será reconhecida pelas outras soluções da Adobe Experience Cloud com o mesmo CNAME. [Saiba mais](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html?lang=pt-BR)

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
   <td> <strong>Plataforma de dados do cliente em tempo real (RTCDP) da Adobe</strong><br /> </td> 
   <td> A integração entre o Adobe Campaign e a Plataforma de dados do cliente em tempo real (RTCDP) da Adobe permite compartilhar dados de segmentos e importar públicos para o Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Saiba mais</a> sobre o Campaign – integração da Plataforma de dados do cliente em tempo real da Adobe</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Sistema de gerenciamento de identidade (IMS) da Adobe - Adobe ID</strong><br />  </td> 
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
   <td> <strong>Adobe Analytics Connector</strong><br /> </td> 
   <td> <strong>O Adobe Analytics Connector</strong> permite que o Adobe Campaign e o Adobe Analytics interajam por meio de segmentos relacionados ao comportamento do usuário após uma campanha de email. Por outro lado, ele envia indicadores e atributos de campanhas de email entregues pelo Adobe Campaign para o Adobe Analytics.<br /> <p><a href="../../platform/using/gs-aa.md">Saiba mais</a> sobre a integração do Campaign com o Analytics Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
