---
product: campaign
title: Regenerar schemas
description: Saiba como regenerar esquemas do Campaign
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 2%

---

# Regenerar schemas{#regenerating-schemas}

![](../../assets/v7-only.svg)

Ao modificar um schema e salvar as modificações, o schema estendido é gerado automaticamente. No entanto, talvez seja necessário gerar novamente schemas manualmente para aplicar modificações. Para fazer isso:

1. Selecione os esquemas que devem ser regenerados.
1. Clique com o botão direito do mouse e escolha **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Clique em **[!UICONTROL OK]** para confirmar e iniciar o processo.

Em seguida, você pode verificar a estrutura do schema gerado nas guias Preview e Documentation . Para obter mais informações, consulte [Princípios](../../configuration/using/data-schemas.md#principles) seção.

>[!NOTE]
>
>Se for necessário forçar a regeneração de todos os esquemas, por exemplo, para resolver determinados problemas de dependência nos links inversos, é possível iniciar o seguinte comando no servidor de aplicativos do Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>Em seguida, reinicie o servidor de aplicativos do Adobe Campaign e desconecte/reconecte ao console do cliente.
