---
product: campaign
title: Trabalhar com o Adobe Campaign e o Adobe Analytics
description: Trabalhar com o Adobe Campaign e o Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
source-git-commit: a38d53f4b37aadbc53446b5e399af2eae56c12af
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 29%

---

# Trabalhar com o Adobe Campaign e o Adobe Analytics {#adobe-analytics-connector-gs}

O Adobe Analytics Connector permite que o Adobe Campaign e o Adobe Analytics interajam por meio do pacote **[!UICONTROL Web Analytics connectors]**. Ele encaminha dados para o Adobe Campaign na forma de segmentos relativos ao comportamento do usuário após uma campanha. Por outro lado, ele envia indicadores e atributos de campanhas de entregues pelo Adobe Campaign ao Adobe Analytics.

## Medidas de proteção e pré-requisitos {#adobe-analytics-connector-guardrails}

Antes de começar a trabalhar com o conector Adobe Campaign-Adobe Analytics, considere as medidas de proteção e os pré-requisitos a seguir.

* Para essa integração, é necessário conectar ao Campaign com o Adobe Identity Management System (IMS). [Saiba mais](../../integrations/using/about-adobe-id.md).

* O Adobe Analytics Connector não é compatível com as mensagens transacionais (Centro de mensagens).

* O complemento do conector do Web Analytics deve ser instalado em seu ambiente, por meio do pacote dedicado.

   * Para implementações híbridas e no local, siga as etapas de provisionamento detalhadas nesta [página](adobe-analytics-provisioning.md).
   * Como um usuário Hoster ou Managed Cloud Service, entre em contato com a Adobe para conectar o Campaign com os serviços e as soluções da Adobe Experience Cloud.


## Configuração e utilização {#adobe-analytics-connector-usage}

Para habilitar esta integração, você deve criar sua conta técnica do Adobe conforme detalhada em [esta página](oauth-technical-account.md).

Saiba como trabalhar com o Adobe Campaign e o Adobe Analytics na [documentação do Adobe Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.
