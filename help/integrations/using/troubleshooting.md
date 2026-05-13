---
product: campaign
title: Solução de problemas
description: Solução de problemas
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
TQID: https://experienceleague.adobe.com/4de9cxyepP-REa2OTWniBFWInphApeUM79sZuFGcynI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
  - id: a8512b64-d668-4084-b4f0-34baa899e306
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 136
ht-degree: 100%

---

# Solução de problemas{#troubleshooting}



No caso de erro, verifique se os seguintes elementos estão configurados corretamente:

* **Contas externas**

  Em **[!UICONTROL Administration > Platform > External accounts]**, verifique se as contas externas SFTP a seguir estão configuradas corretamente. Os servidores SFTP mencionados devem ter sido configurados na Adobe Experience Cloud pelo seu consultor.

   * **[!UICONTROL importSharedAudience]**: conta SFTP dedicada à importação de públicos-alvos.
   * **[!UICONTROL exportSharedAudience]**: conta SFTP dedicada à exportação de públicos-alvos.

* **Fonte de dados da Adobe Experience Cloud (AMC)**

  Em **[!UICONTROL Administration > Platform > AMC Data sources]**, verifique se a fonte de dados da AMC está definida corretamente.

Ao compartilhar um público-alvo através da Experience Cloud ou importar um público-alvo, pode haver ausência de alguns dados. Somente registros cuja ID (“ID do visitante” ou “ID declarada”) pode ser reconciliada com a dimensão de perfil são transferidos. As IDs de segmentos não reconhecidos pelo Adobe Campaign não são importadas.
