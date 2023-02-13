---
product: campaign
title: Introdução a origens e destinos
description: Saiba mais sobre origens e destinos da Adobe Experience Platform.
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
source-git-commit: 89a18ae9ec57376d6ebec6c416c7562f960eb882
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 100%

---

# Trabalhar com origens e destinos {#rtcdp}

![](../../assets/v7-only.svg)

## Sobre origens e destinos

Com a Adobe Experience Platform, você pode compartilhar dados entre o Campaign Classic e a Plataforma de dados do cliente em tempo real (RTCDP) da Adobe. Isso permite direcionar os públicos da Adobe Experience Platform nos workflows do Campaign e enviar de volta para a Plataforma de dados do cliente em tempo real da Adobe relacionados a esses públicos, como envios, aberturas e cliques.

* Com **Destinos**, assimile públicos da Adobe Experience Platform no Campaign Classic. Isso permite ativar os dados conhecidos e desconhecidos para suas campanhas de marketing.
* Com **Origens**, exporte dados do Campaign Classic (por exemplo, envios, aberturas e cliques) para a Adobe Experience Platform. Isso permite centralizar os dados coletados de origens diferentes em um único local e usar os insights obtidos com eles para fazer mais.

>[!IMPORTANT]
>
>Lembre-se dos limites de armazenamento SFTP, armazenamento do banco de dados e perfil ativo conforme o contrato do Adobe Campaign ao fazer essa integração.

Para obter uma visão geral mais detalhada da Plataforma de dados do cliente em tempo real da Adobe, Origens e Fontes, consulte estas páginas:

* [Plataforma de dados do cliente em tempo real da Adobe](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=pt-BR)
* [Documentação de destinos](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=pt-BR)
* [Documentação de origens](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=pt-BR)

## Conectar o Campaign Classic à Adobe Experience Platform

Para compartilhar dados entre a Adobe Experience Platform e o Campaign Classic, primeiro é necessário conectar o Adobe Campaign como um **Destino** e conectar seu local de armazenamento de blobs do AWS S3 ou Azure como uma **Origem** na Adobe Experience Platform.

Após configurar os conectores, é possível configurar uma importação ou exportação de dados para o Campaign Classic usando workflows.

![](assets/rtcdp-schema.png)

Para obter mais detalhes sobre como configurar esses processos de importação e exportação, consulte estas seções:

* [Assimilar segmentos da Adobe Experience Platform no Campaign](../../integrations/using/ingest-aep-data.md)
* [Exportar dados do Campaign para a Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
