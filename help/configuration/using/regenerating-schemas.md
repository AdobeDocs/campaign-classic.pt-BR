---
solution: Campaign Classic
product: campaign
title: Regeneração de schemas
description: Regeneração de schemas
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

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
