---
solution: Campaign Classic
product: campaign
title: Solução de problemas
description: Solução de problemas
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '130'
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

Alguns dados podem faltar ao compartilhar um público através do Serviço principal de pessoas ou ao importar um público. Somente registros dos quais a ID (&#39;ID do visitante&#39; ou &#39;ID declarada&#39;) podem ser reconciliadas com a dimensão de perfil são transferidas. Os IDs dos segmentos de Serviço principal de pessoas que não são reconhecidos pelo Adobe Campaign não são importados.
