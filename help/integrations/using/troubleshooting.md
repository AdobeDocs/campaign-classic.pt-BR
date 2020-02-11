---
title: Solução de problemas
seo-title: Solução de problemas
description: Solução de problemas
seo-description: null
page-status-flag: never-activated
uuid: fb51ad18-221b-4058-b206-ca2ca045c507
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f3ff8c8e-22b0-4d61-9f26-11f5ca3bc0be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Solução de problemas{#troubleshooting}

No caso de erro, verifique se os seguintes elementos estão configurados corretamente:

* **Contas externas**

   In **[!UICONTROL Administration > Platform > External accounts]**, make sure that the following external SFTP accounts are correctly configured. Os servidores SFTP mencionados devem ter sido configurados na Adobe Experience
           Cloud pelo seu consultor.

   * **[!UICONTROL importSharedAudience]** : Conta SFTP dedicada à importação de audiências.
   * **[!UICONTROL exportSharedAudience]** : Conta SFTP dedicada à exportação de audiências.

* **Fonte de dados da Adobe Marketing Cloud (AMC)**

   In **[!UICONTROL Administration > Platform > AMC Data sources]**, check that the AMC Data source is set properly.

Alguns dados podem faltar ao compartilhar um público através do Serviço principal de pessoas ou ao importar um público. Somente registros dos quais a ID (&#39;ID do visitante&#39; ou &#39;ID declarada&#39;) podem ser reconciliadas com a dimensão de perfil são transferidas. Os IDs dos segmentos de Serviço principal de pessoas que não são reconhecidos pelo Adobe Campaign não são importados.
