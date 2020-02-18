---
title: Regeneração de esquemas
seo-title: Regeneração de esquemas
description: Regeneração de esquemas
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Regeneração de esquemas{#regenerating-schemas}

Quando você modifica um esquema e salva as modificações, o esquema estendido é gerado automaticamente. No entanto, talvez seja necessário regenerar esquemas manualmente para aplicar modificações. Para fazer isso:

1. Selecione os esquemas que precisam ser regenerados.
1. Clique com o botão direito do mouse e escolha **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Clique em **[!UICONTROL OK]** para confirmar e iniciar o processo.

Você pode verificar a estrutura do esquema gerado nas guias Anterior e Documentação. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>Se for necessário forçar a regeneração de todo o esquema, por exemplo, para resolver certos problemas de dependência nos links inversos, você pode iniciar o seguinte comando no servidor de aplicativos do Adobe Campaign:
>
>**nlserver config -postupgrade -instance:`&lt;nome_da_instância>&#39; -force**
>
>Você deve reiniciar o servidor de aplicativos do Adobe Campaign e desconectar/reconectar ao console do cliente.
