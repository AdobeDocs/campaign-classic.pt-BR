---
title: Regeneração de schemas
seo-title: Regeneração de schemas
description: Regeneração de schemas
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 8%

---


# Regeneração de schemas{#regenerating-schemas}

Quando você modifica um schema e salva as modificações, o schema estendido é gerado automaticamente. No entanto, talvez seja necessário regenerar schemas manualmente para aplicar modificações. Para fazer isso:

1. Selecione os schemas que precisam ser regenerados.
1. Clique com o botão direito do mouse e escolha **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Clique em **[!UICONTROL OK]** para confirmar e iniciar o processo.

Você pode verificar a estrutura do schema gerado nas guias Anterior e Documentação. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>Se for necessário forçar a regeneração de todos os schemas, por exemplo, para resolver certos problemas de dependência nos links inversos, você pode iniciar o seguinte comando do servidor de aplicativos Adobe Campaign:
>
>**nlserver config -postupgrade -instance:`&lt;nome_da_instância>&#39; -force**
>
>Em seguida, reinicie o servidor de aplicativos Adobe Campaign e desconecte/reconecte-se ao console do cliente.
