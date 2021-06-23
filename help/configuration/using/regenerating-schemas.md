---
product: campaign
title: Regeneração de esquemas
description: Regeneração de esquemas
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: e3e2ac09de6a9e846e9f9262d522b9395a725648
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 7%

---

# Regeneração de esquemas{#regenerating-schemas}

Ao modificar um schema e salvar as modificações, o schema estendido é gerado automaticamente. No entanto, talvez seja necessário gerar novamente schemas manualmente para aplicar modificações. Para fazer isso:

1. Selecione os esquemas que devem ser regenerados.
1. Clique com o botão direito do mouse e escolha **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Clique em **[!UICONTROL OK]** para confirmar e iniciar o processo.

Em seguida, você pode verificar a estrutura do schema gerado nas guias Previw e Documentation . Para obter mais informações, consulte a seção [Principles](../../configuration/using/data-schemas.md#principles) .

>[!NOTE]
>
>Se for necessário forçar a regeneração de todos os esquemas, por exemplo, para resolver determinados problemas de dependência nos links inversos, é possível iniciar o seguinte comando no servidor de aplicativos do Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>Em seguida, reinicie o servidor de aplicativos do Adobe Campaign e desconecte/reconecte ao console do cliente.
