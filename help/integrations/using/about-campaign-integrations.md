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
ht-degree: 100%

---

# Introdução às integrações do Adobe Campaign {#about-campaign-integrations}

A Adobe Experience Cloud é um conjunto abrangente das melhores soluções integradas e criadas com base em uma plataforma de dados comum e um conjunto comum de soluções e aplicativos avançados.

Saiba mais sobre as integrações funcionais disponíveis para o Adobe Campaign e as soluções da Adobe Experience Cloud [nesta página](https://experienceleague.adobe.com/pt-br/docs/core-services/interface/administration/integrations){_blank}.

A lista completa de soluções da Adobe e serviços de aplicativos que podem ser integrados ao Adobe Campaign, bem como a documentação associada, está disponível [nesta seção](#experience-cloud-integrations).

>[!CAUTION]
>
>Essas integrações exigem a implementação do Adobe Identity Management System (IMS) para fazer logon com uma Adobe ID. [Saiba mais nesta página](../../integrations/using/about-adobe-id.md).
>

## Vincular soluções {#working-with-experience-cloud-solutions}

Várias soluções podem ser vinculadas à Adobe Experience Cloud. Uma **organização** é a entidade-cliente que permite a um administrador configurar grupos e usuários e controlar o logon único (SSO) na Adobe Experience Cloud. A organização funciona como uma empresa de login que abrange todos os produtos e soluções da Experience Cloud. Na maioria das vezes, uma organização é o nome da sua empresa. No entanto, uma empresa pode ter muitas organizações.

O gerenciamento da organização e a vinculação de contas da Adobe Experience Cloud são detalhados no [portal de ajuda da Adobe Experience Cloud](https://experienceleague.adobe.com/pt-br/docs/core-services/interface/administration/organizations){_blank}.

## Gerenciamento de identidade e cookies {#id-and-cookies}

Ao instalar o Adobe Campaign ou integrar uma instalação existente com a Adobe Experience Cloud, o [serviço de identidade da Adobe Experience Cloud](https://experienceleague.adobe.com/pt-br/docs/id-service/using/home){_blank} é habilitado. Esse serviço substitui o cookie permanente usado primeiro e mais importante pelo Adobe Campaign para suas funcionalidades de rastreamento.

O Serviço de identidade da Adobe Experience Cloud (ID Service) fornece uma ID contínua e universal que identifica seus visitantes em todas as soluções na Experience Cloud.

Um identificador de visitante único será atribuído aos destinatários que geram logs de rastreamento. Essa ID será salva no campo **[!UICONTROL Requester UUID (@sourceID)]** da tabela **[!UICONTROL nms:trackingLogRcp]**. **Os dados de rastreamento dos destinatários existentes antes do serviço de ID de visitante foram implementados e, portanto, não serão mais utilizáveis**.

A ID será reconhecida pelas outras soluções da Adobe Experience Cloud com o mesmo CNAME. [Saiba mais](https://experienceleague.adobe.com/pt-br/docs/id-service/using/reference/analytics-reference/cname){_blank}.

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
   <td> Configure a integração entre o Adobe Campaign e a Adobe Real-time Customer Data Platform (RTCDP) para compartilhar dados de segmentos e importar públicos-alvo para o Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Saiba mais</a> sobre o Campaign – integração da Plataforma de dados do cliente em tempo real da Adobe</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Sistema de gerenciamento de identidade (IMS) da Adobe - Adobe ID</strong><br />  </td> 
   <td> Configure o Adobe IMS para se conectar ao Adobe Campaign com a mesma Adobe ID das outras soluções da Adobe Experience Cloud.<br /> Para usar determinadas funcionalidades vinculadas às integrações da Adobe Experience Cloud, é necessário fazer logon com uma Adobe ID.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Saiba mais</a> sobre a implementação da Adobe ID com o Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Configure essa integração para criar conteúdos de email ou formulários mapeados para o banco de dados do Adobe Campaign diretamente no <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Saiba mais</a> sobre a integração Adobe Campaign – Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Configure essa integração para inserir imagens que são computadas dinamicamente pelo <strong>Adobe Target</strong> ao abrir o email criado e enviado pelo Adobe Campaign.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Saiba mais</a> sobre a integração do Adobe Campaign e Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Configure essa integração para compartilhar públicos-alvo entre as soluções e os aplicativos da Adobe Experience Cloud que você usa.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Saiba mais</a> sobre as integrações do Adobe Campaign e Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Ativos</strong><br /> </td> 
   <td> Configure essa integração para inserir ativos da sua biblioteca da Adobe Experience Cloud em emails e landing pages criadas no Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Saiba mais</a> sobre a integração do Adobe Campaign e o Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Configure essa integração para inserir ativos de sua biblioteca do <strong>AEM Assets</strong> em emails e landing pages criadas no Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Saiba mais</a> sobre a integração Adobe Campaign – AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Configure a integração dos <strong>Adobe Experience Cloud Triggers</strong>e o Adobe Campaign para enviar emails personalizados a clientes como uma resposta a comportamentos específicos que são detectados no site pelo Adobe Analytics.<br /> <p><a href="about-triggers.md">Saiba mais</a> sobre a integração do Adobe Campaign e o Experience Cloud Triggers.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics Connector</strong><br /> </td> 
   <td> Configure essa integração para permitir que o Adobe Campaign e o Adobe Analytics interajam entre si por meio de segmentos relacionados ao comportamento do usuário após uma campanha de email. Por outro lado, ele envia indicadores e atributos de campanhas de email entregues pelo Adobe Campaign para o Adobe Analytics.<br /> <p><a href="../../integrations/using/gs-aa.md">Saiba mais</a> sobre a integração do Campaign com o Analytics Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
