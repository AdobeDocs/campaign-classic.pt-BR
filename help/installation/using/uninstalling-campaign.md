---
product: campaign
title: Desinstalação do Campaign
description: Saiba como desinstalar o Campaign
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 30%

---

# Desinstalação do Campaign{#uninstalling-campaign}

![](../../assets/v7-only.svg)

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

Consulte esta [página](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Não se esqueça de remover a pasta de instalação do Campaign.
