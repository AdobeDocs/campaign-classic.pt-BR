---
product: campaign
title: Introdução a origens e destinos
description: Saiba mais sobre origens e destinos da Adobe Experience Platform
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
TQID: https://experienceleague.adobe.com/xPpBR6NrQ315FIw1beLnw4c0gyLzEoYWzIXDljDg9H4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 100%

---

# Trabalhar com origens e destinos {#rtcdp}



## Sobre origens e destinos

Com a Adobe Experience Platform, você pode compartilhar dados entre o Campaign Classic e a Plataforma de dados do cliente em tempo real (RTCDP) da Adobe. Isso permite direcionar os públicos-alvos da Adobe Experience Platform nos workflows do Campaign e enviar de volta para a Plataforma de dados do cliente em tempo real da Adobe relacionados a esses públicos-alvos, como envios, aberturas e cliques.

* Com **Destinos**, assimile públicos-alvos da Adobe Experience Platform no Campaign Classic. Isso permite ativar os dados conhecidos e desconhecidos para suas campanhas de marketing.
* Com **Origens**, exporte dados do Campaign Classic (por exemplo, envios, aberturas e cliques) para a Adobe Experience Platform. Isso permite centralizar os dados coletados de origens diferentes em um único local e usar os insights obtidos com eles para fazer mais.

>[!IMPORTANT]
>
>Lembre-se dos limites de armazenamento SFTP, armazenamento do banco de dados e perfil ativo conforme o contrato do Adobe Campaign ao fazer essa integração.

Para obter uma visão geral mais detalhada da Plataforma de dados do cliente em tempo real da Adobe, Origens e Fontes, consulte estas páginas:

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=pt-BR)
* [Documentação de destinos](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=pt-BR)
* [Documentação de origens](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=pt-BR)

## Conectar o Campaign Classic à Adobe Experience Platform

Para compartilhar dados entre a Adobe Experience Platform e o Campaign Classic, primeiro é necessário conectar o Adobe Campaign como um **Destino** e conectar seu local de armazenamento de blobs do AWS S3 ou Azure como uma **Origem** na Adobe Experience Platform.

Após configurar os conectores, é possível configurar uma importação ou exportação de dados para o Campaign Classic usando fluxos de trabalho.

![](assets/rtcdp-schema.png)

Para obter mais detalhes sobre como configurar esses processos de importação e exportação, consulte estas seções:

* [Assimilar segmentos da Adobe Experience Platform no Campaign](../../integrations/using/ingest-aep-data.md)
* [Exportar dados do Campaign para a Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
