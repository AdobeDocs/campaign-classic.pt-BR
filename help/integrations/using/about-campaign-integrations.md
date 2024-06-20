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
source-git-commit: 597d24fa780a324507c56c55a5309b6ee1cf46eb
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 46%

---

# Introdução às integrações do Adobe Campaign {#about-campaign-integrations}

O Adobe Experience Cloud é um conjunto abrangente das melhores soluções integradas disponíveis no setor, que aproveita a plataforma de dados comum com um conjunto de soluções e aplicativos avançados.

Saiba mais sobre as integrações funcionais disponíveis entre o Adobe Campaign e as soluções da Adobe Experience Cloud no [esta página](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/integrations){_blank}.

A lista completa de soluções e serviços de aplicativos Adobe que podem ser integrados ao Adobe Campaign, bem como a documentação associada, estão disponíveis em [nesta seção](#experience-cloud-integrations).

>[!CAUTION]
>
>Essas integrações exigem a implementação do Adobe Identity Management System (IMS) para fazer logon por meio de uma Adobe ID. [Saiba mais nesta página](../../integrations/using/about-adobe-id.md).
>

## Vincular soluções {#working-with-experience-cloud-solutions}

Várias soluções podem ser vinculadas à Adobe Experience Cloud. Uma **organização** é a entidade-cliente que permite a um administrador configurar grupos e usuários e controlar o logon único (SSO) na Adobe Experience Cloud. A organização funciona como uma empresa de login que abrange todos os produtos e soluções da Experience Cloud. Na maioria das vezes, uma organização é o nome da sua empresa. No entanto, uma empresa pode ter muitas organizações.

A gestão de organização e a vinculação às contas do Adobe Experience Cloud são detalhadas na seção [Portal de ajuda do Adobe Experience Cloud](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations){_blank}.

## Gerenciamento de identidade e cookies {#id-and-cookies}

Ao instalar o Adobe Campaign ou integrar uma instalação existente com o Adobe Experience Cloud, a variável [Serviço de identidade da Adobe Experience Cloud](https://experienceleague.adobe.com/en/docs/id-service/using/home){_blank} está ativado. Esse serviço substitui o cookie permanente usado primeiro e mais importante pelo Adobe Campaign para suas funcionalidades de rastreamento.

O Serviço de identidade da Adobe Experience Cloud (ID Service) fornece uma ID contínua e universal que identifica seus visitantes em todas as soluções na Experience Cloud.

Um identificador de visitante único será atribuído aos destinatários que geram logs de rastreamento. Essa ID será salva no campo **[!UICONTROL Requester UUID (@sourceID)]** da tabela **[!UICONTROL nms:trackingLogRcp]**. **Os dados de rastreamento dos destinatários existentes antes do serviço de ID de visitante foram implementados e, portanto, não serão mais utilizáveis**.

A ID será reconhecida pelas outras soluções da Adobe Experience Cloud com o mesmo CNAME. [Saiba mais](https://experienceleague.adobe.com/en/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Integrações da Experience Cloud {#experience-cloud-integrations}

A tabela a seguir fornece acesso à documentação disponível da integração da Experience Cloud.

<table> 
 <thead> 
  <tr> 
   <th> Soluções e aplicativos<br /> </th> 
   <th> Casos de uso<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Plataforma de dados do cliente em tempo real (RTCDP) da Adobe</strong><br /> </td> 
   <td> Configure a integração entre o Adobe Campaign e o Adobe Real-time Customer Data Platform (RTCDP) para compartilhar dados de segmentos e importar públicos para o Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Saiba mais</a> sobre o Campaign – integração da Plataforma de dados do cliente em tempo real da Adobe</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Sistema de gerenciamento de identidade (IMS) da Adobe - Adobe ID</strong><br />  </td> 
   <td> Configure o Adobe IMS para se conectar ao Adobe Campaign com o mesmo Adobe ID para as outras soluções da Adobe Experience Cloud.<br /> Um Adobe ID deve ser usado para fazer logon para usar determinadas funcionalidades vinculadas às integrações do Adobe Experience Cloud.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Saiba mais</a> sobre a implementação da Adobe ID com o Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Configure essa integração para criar conteúdo de email ou formulários mapeados para o banco de dados do Adobe Campaign diretamente no <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Saiba mais</a> sobre a integração Adobe Campaign – Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Configure essa integração para inserir imagens que são dinamicamente calculadas pelo <strong>Adobe Target</strong> quando o email criado e enviado pelo Adobe Campaign é aberto.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Saiba mais</a> sobre a integração Adobe Campaign – Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Configure essa integração para compartilhar públicos entre as soluções da Adobe Experience Cloud e os aplicativos que você usa.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Saiba mais</a> sobre as integrações Adobe Campaign - Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets</strong><br /> </td> 
   <td> Configure essa integração para inserir ativos da biblioteca do Adobe Experience Cloud em emails e landing pages criadas no Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Saiba mais</a> sobre a integração Adobe Campaign - Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Configure essa integração para inserir ativos do <strong>AEM Assets</strong> em emails e landing pages criadas no Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Saiba mais</a> sobre a integração Adobe Campaign – AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Configurar a integração entre <strong>Adobe Experience Cloud Triggers</strong> e Adobe Campaign para enviar emails personalizados para seus clientes como uma reação a comportamentos específicos que são rastreados em seu site pelo Adobe Analytics.<br /> <p><a href="about-triggers.md">Saiba mais</a> sobre a integração Adobe Campaign – Experience Cloud Triggers.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics Connector</strong><br /> </td> 
   <td> Configure essa integração para permitir que o Adobe Campaign e o Adobe Analytics interajam por meio de segmentos relacionados ao comportamento do usuário após uma campanha de email. Por outro lado, ele envia indicadores e atributos de campanhas de email entregues pelo Adobe Campaign para o Adobe Analytics.<br /> <p><a href="../../integrations/using/gs-aa.md">Saiba mais</a> sobre a integração do Campaign com o Analytics Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
