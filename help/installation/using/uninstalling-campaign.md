---
title: Desinstalação do Campaign
seo-title: Desinstalação do Campaign
description: Desinstalação do Campaign
seo-description: null
page-status-flag: never-activated
uuid: 4e95a576-a2fe-41dd-a03d-e4a3120f8788
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 702253cc-3e1a-44ad-9340-b8588ee86bad
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '35'
ht-degree: 42%

---


# Desinstalação do Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>Esses procedimentos desinstalarão permanentemente o Adobe Campaign. Todos os dados serão perdidos.

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

Consulte esta [página](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Não se esqueça de remover a pasta de instalação da Campanha.
