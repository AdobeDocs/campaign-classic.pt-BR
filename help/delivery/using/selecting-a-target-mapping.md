---
product: campaign
title: Selecionar um target mapping
description: Saiba como fazer target mapping
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 100%

---

# Selecionar um target mapping{#selecting-a-target-mapping}



Por padrão, templates de delivery têm como target **[!UICONTROL Recipients]**. O target mapping, portanto, usa os campos da tabela **nms:recipient.** O Adobe Campaign oferece outros target mapping para seus deliveries, para serem usados conforme suas necessidades.

![](assets/delivery_select_mapping.png)

Esses mappings são os seguintes:

| Nome | Uso | Schema padrão |
|---|---|---|
| Recipients | Enviar delivery aos recipients do banco de dados do Adobe Campaign | nms:recipient |
| Visitantes | Enviar delivery aos visitantes cujos perfis foram coletados por meio de referência (marketing viral) ou por meio de redes sociais (Facebook, Twitter), por exemplo. | mns:visitor |
| Subscrições | Enviar delivery aos recipients que assinam um serviço de informações, como um boletim informativo | nms:subscription |
| Assinaturas do visitante | Enviar delivery aos visitantes que são inscritos em um serviço de informações | nms:visitorSub |
| Serviço | Publicar em uma conta do Twitter ou uma página do Facebook | nms:service |
| Operadores | Enviar delivery aos operadores do Adobe Campaign | nms:operator |
| Arquivo externo | Enviar delivery por meio de um arquivo que contenha todas as informações necessárias para o delivery | Nenhum schema vinculado, nenhum target inserido |

>[!NOTE]
>
>Você também pode criar novos target mapping. Essa operação é reservada para usuários avançados. Para obter mais informações, consulte [esta seção](../../configuration/using/target-mapping.md).
