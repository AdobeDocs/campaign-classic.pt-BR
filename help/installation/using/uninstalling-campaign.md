---
product: campaign
title: Desinstalação do Campaign
description: Saiba como desinstalar o Campaign
feature: Installation
badge-v7-only: label="v7" type="Informative" tooltip="Aplicável somente ao Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 27%

---

# Desinstalação do Campaign{#uninstalling-campaign}



>[!CAUTION]
>
>Esses procedimentos serão desinstalados permanentemente no Adobe Campaign. Todos os dados serão perdidos.

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
