---
product: campaign
title: Gerar esquemas novamente
description: Saiba como regenerar esquemas do Campaign
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 7%

---

# Gerar esquemas novamente{#regenerating-schemas}

Ao modificar um esquema e salvar as modificações, o esquema estendido é gerado automaticamente. No entanto, talvez seja necessário gerar esquemas novamente manualmente para aplicar modificações. Para fazer isso:

1. Selecione os esquemas que precisam ser gerados novamente.
1. Clique com o botão direito do mouse e escolha **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Clique em **[!UICONTROL OK]** para confirmar e iniciar o processo.

Em seguida, você pode verificar a estrutura do schema gerado nas guias Preview e Documentation. Para obter mais informações, consulte [Princípios](../../configuration/using/data-schemas.md#principles) seção.

>[!NOTE]
>
>Se for necessário forçar a regeneração de todos os esquemas, por exemplo, para resolver determinados problemas de dependência nos links reversos, inicie o seguinte comando no servidor de aplicativos do Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>Em seguida, reinicie o servidor de aplicativos do Adobe Campaign e desconecte/reconecte ao console do cliente.
