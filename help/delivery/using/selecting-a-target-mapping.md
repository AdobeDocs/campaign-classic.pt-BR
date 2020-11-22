---
solution: Campaign Classic
product: campaign
title: Seleção de target mapping
description: Seleção de target mapping
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 100%

---


# Seleção de target mapping{#selecting-a-target-mapping}

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
>Você também pode criar novos target mapping. Essa operação é reservada para usuários avançados. Para obter mais informações, consulte o [Guia de Configuração](../../configuration/using/target-mapping.md).
