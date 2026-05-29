---
product: campaign
title: Selecionar um target mapping
description: Saiba como fazer target mapping
feature: Delivery Templates
hide: true
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
TQID: https://experienceleague.adobe.com/VpmfQdFoJ2Lfzetqx-s5MAdFdTTEsHxz2ISL15wNXIo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 177
ht-degree: 100%

---

# Selecionar um target mapping{#selecting-a-target-mapping}

Por padrão, modelos de entrega direcionam **[!UICONTROL Recipients]**. O target mapping, portanto, usa os campos da tabela **nms:recipient**. O Adobe Campaign oferece outros target mapping para suas entregas, para serem usados conforme suas necessidades.

![](assets/delivery_select_mapping.png)

Esses mappings são os seguintes:

| Nome | Uso | Esquema padrão |
|---|---|---|
| Recipients | Entregar aos destinatários do banco de dados do Adobe Campaign | nms:recipient |
| Visitantes | Entregue aos visitantes cujos perfis foram coletados por meio de referências (marketing viral) ou por meio de redes sociais (X, anteriormente conhecido como Twitter, Facebook), por exemplo. | mns:visitor |
| Subscrições | Entregar aos destinatários que assinam um serviço de informações, como um boletim informativo | nms:subscription |
| Assinaturas do visitante | Entregar aos visitantes que são inscritos em um serviço de informações | nms:visitorSub |
| Serviço | Publicar em uma conta do X ou em uma página do Facebook | nms:service |
| Operadores | Entregar aos operadores do Adobe Campaign | nms:operator |
| Arquivo externo | Entregar por meio de um arquivo que contenha todas as informações necessárias para a entrega | Nenhum esquema vinculado, nenhum target inserido |

>[!NOTE]
>
>Você também pode criar novos target mapping. Essa operação é reservada para usuários avançados. Para obter mais informações, consulte [esta seção](../../configuration/using/target-mapping.md).
