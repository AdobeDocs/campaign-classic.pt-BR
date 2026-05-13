---
product: campaign
title: Gerar esquemas novamente
description: Saiba como regenerar esquemas do Campaign
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
TQID: https://experienceleague.adobe.com/gkWtbp4Vw-wY5yHsd4xJbDx04u3aPhdg-8kB5OXZu94
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 131
ht-degree: 2%

---

# Gerar esquemas novamente{#regenerating-schemas}

Ao modificar um esquema e salvar as modificações, o esquema estendido é gerado automaticamente. No entanto, talvez seja necessário gerar esquemas novamente manualmente para aplicar modificações. Para isso:

1. Selecione os esquemas que precisam ser gerados novamente.
1. Clique com o botão direito do mouse e escolha **[!UICONTROL Actions > Regenerate selected schemas...]**.
1. Clique em **[!UICONTROL OK]** para confirmar e iniciar o processo.

Em seguida, você pode verificar a estrutura do schema gerado nas guias Preview e Documentation. Para obter mais informações, consulte a seção [Princípios](../../configuration/using/data-schemas.md#principles).

>[!NOTE]
>
>Se for necessário forçar a regeneração de todos os esquemas, por exemplo, para resolver determinados problemas de dependência nos links reversos, inicie o seguinte comando no servidor de aplicativos do Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;nome_da_instância>` -force`
>
>Em seguida, reinicie o servidor de aplicativos do Adobe Campaign e desconecte/reconecte ao console do cliente.
