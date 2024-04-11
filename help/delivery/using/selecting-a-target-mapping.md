---
product: campaign
title: Selecionar um target mapping
description: Saiba como fazer target mapping
badge-v8: label="Também se aplica à versão v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Delivery Templates
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 97%

---

# Selecionar um target mapping{#selecting-a-target-mapping}

Por padrão, templates de entrega têm como target **[!UICONTROL Recipients]**. O target mapping, portanto, usa os campos da tabela **nms:recipient.** O Adobe Campaign oferece outros target mapping para suas entregas, para serem usados conforme suas necessidades.

![](assets/delivery_select_mapping.png)

Esses mappings são os seguintes:

| Nome | Uso | Schema padrão |
|---|---|---|
| Recipients | Entregar aos destinatários do banco de dados do Adobe Campaign | nms:recipient |
| Visitantes | Entregue aos visitantes cujos perfis foram coletados por meio de referências (marketing viral) ou por meio de redes sociais (X, anteriormente conhecido como Twitter, Facebook), por exemplo. | mns:visitor |
| Subscrições | Entregar aos destinatários que assinam um serviço de informações, como um boletim informativo | nms:subscription |
| Assinaturas do visitante | Entregar aos visitantes que são inscritos em um serviço de informações | nms:visitorSub |
| Serviço | Publicar em uma conta do X ou em uma página do Facebook | nms:service |
| Operadores | Entregar aos operadores do Adobe Campaign | nms:operator |
| Arquivo externo | Entregar por meio de um arquivo que contenha todas as informações necessárias para a entrega | Nenhum schema vinculado, nenhum target inserido |

>[!NOTE]
>
>Você também pode criar novos target mapping. Essa operação é reservada para usuários avançados. Para obter mais informações, consulte [esta seção](../../configuration/using/target-mapping.md).
