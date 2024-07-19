---
product: campaign
title: Configuração do Developer Console para Adobe Experience Cloud Triggers
description: Saiba como configurar o Developer Console para Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 100%

---

# Configuração do Developer Console para Adobe Experience Cloud Triggers {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## Pré-requisitos {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

Antes de iniciar esta implementação, verifique se você tem:

* um **identificador de organização** válido: o ID da organização é o identificador exclusivo da Adobe Experience Cloud, que é usado, por exemplo, para o serviço de VisitorID e para o Logon único (SSO) no IMS. [Saiba mais](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=pt-BR)
* um **Acesso de desenvolvedor** para sua organização. O administrador de sistema da organização precisa seguir o procedimento **Adicionar desenvolvedores a um único perfil de produto** detalhado [nesta página](https://helpx.adobe.com/br/enterprise/using/manage-developers.html) para fornecer acesso de desenvolvedor ao `Analytics - {tenantID}` do Perfil do produto do Adobe Analytics que está associado ao Triggers.

## Etapa 1: criar/atualizar projeto OAuth {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> A credencial de conta de serviço (JWT) está sendo descontinuada pela Adobe. As integrações do Campaign com soluções e aplicativos Adobe agora devem usar a credencial de servidor para servidor OAuth. </br>
>
> * Se você implementou integrações de entrada com o Campaign, é necessário migrar a conta técnica conforme detalhado [nesta documentação](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). As credenciais da conta de serviço (JWT) existentes continuarão funcionando até 27 de janeiro de 2025.</br>
>
> * Se você tiver implementado integrações de saída, como a integração do Campaign com o Analytics ou a integração dos acionadores da Experience Cloud, elas continuarão a funcionar até 27 de janeiro de 2025. No entanto, antes dessa data, você deve atualizar o ambiente do Campaign para a v7.4.1 e migrar sua conta técnica para o OAuth. 

Para continuar com a configuração do conector do Adobe Analytics, acesse o Adobe Developer Console e crie um projeto OAuth de “servidor para servidor”.

Consulte [esta página](oauth-technical-account.md#oauth-service) para obter a documentação detalhada.

## Etapa 2: adicionar as credenciais do projeto no Adobe Campaign {#add-credentials-campaign}

Siga as etapas detalhadas [nesta página](oauth-technical-account.md#add-credentials) para adicionar suas credenciais do projeto OAuth no Adobe Campaign.

## Etapa 3: atualizar a tag “pipelined” {#update-pipelined-tag}

Para atualizar a tag [!DNL pipelined], é necessário atualizar o tipo de autenticação para o projeto do Developer Console no arquivo de configuração **config-&lt; instance-name >.xml** da seguinte maneira:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Em seguida, execute um `config -reload` e reinicie o [!DNL pipelined] para aplicar as alterações.
