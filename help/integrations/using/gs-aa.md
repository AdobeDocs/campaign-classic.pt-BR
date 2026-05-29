---
product: campaign
title: Trabalhar com o Adobe Campaign e o Adobe Analytics
description: Trabalhar com o Adobe Campaign e o Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
TQID: https://experienceleague.adobe.com/YuvP0m31wL-WlocUXU3rWovOiwLiA5XrEsnBLlW3nY8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 209
ht-degree: 27%

---

# Trabalhar com o Adobe Campaign e o Adobe Analytics {#adobe-analytics-connector-gs}

O Adobe Analytics Connector permite que o Adobe Campaign e o Adobe Analytics interajam por meio do pacote **[!UICONTROL Web Analytics connectors]**. Ele encaminha dados para o Adobe Campaign na forma de segmentos relativos ao comportamento do usuário após uma campanha. Por outro lado, ele envia indicadores e atributos de campanhas de entregues pelo Adobe Campaign ao Adobe Analytics.

## Medidas de proteção e pré-requisitos {#adobe-analytics-connector-guardrails}

Antes de começar a trabalhar com o conector Adobe Campaign-Adobe Analytics, considere as medidas de proteção e os pré-requisitos a seguir.

* Para essa integração, é necessário conectar ao Campaign com o Adobe Identity Management System (IMS). [Saiba mais](../../integrations/using/about-adobe-id.md).

* O Adobe Analytics Connector não é compatível com as mensagens transacionais (Centro de mensagens).

* O complemento do conector do Web Analytics deve ser instalado em seu ambiente, por meio do pacote dedicado.

   * Para implementações híbridas e no local, siga as etapas de provisionamento detalhadas nesta [página](adobe-analytics-provisioning.md).
   * Como um usuário do Hoster ou do Managed Cloud Services, entre em contato com a Adobe para conectar o Campaign com os serviços e as soluções da Adobe Experience Cloud.


## Configuração e utilização {#adobe-analytics-connector-usage}

Para habilitar esta integração, você deve criar sua conta técnica do Adobe conforme detalhada em [esta página](oauth-technical-account.md).

Saiba como trabalhar com o Adobe Campaign e o Adobe Analytics na [documentação do Adobe Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.
