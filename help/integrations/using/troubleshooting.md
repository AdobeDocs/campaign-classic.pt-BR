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
hidefromtoc: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: ht
source-wordcount: '136'
ht-degree: 100%

---

# Solução de problemas{#troubleshooting}



No caso de erro, verifique se os seguintes elementos estão configurados corretamente:

* **Contas externas**

  Em **[!UICONTROL Administration > Platform > External accounts]**, verifique se as contas externas SFTP a seguir estão configuradas corretamente. Os servidores SFTP mencionados devem ter sido configurados na Adobe Experience Cloud pelo seu consultor.

   * **[!UICONTROL importSharedAudience]**: conta SFTP dedicada à importação de públicos.
   * **[!UICONTROL exportSharedAudience]**: conta SFTP dedicada à exportação de públicos.

* **Fonte de dados da Adobe Experience Cloud (AMC)**

  Em **[!UICONTROL Administration > Platform > AMC Data sources]**, verifique se a fonte de dados da AMC está definida corretamente.

Ao compartilhar um público-alvo através da Experience Cloud ou importar um público-alvo, pode haver ausência de alguns dados. Somente registros cuja ID (“ID do visitante” ou “ID declarada”) pode ser reconciliada com a dimensão de perfil são transferidos. As IDs de segmentos não reconhecidos pelo Adobe Campaign não são importadas.
