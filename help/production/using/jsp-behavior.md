---
title: Comportamento JSP
seo-title: Comportamento JSP
description: Comportamento JSP
seo-description: null
page-status-flag: never-activated
uuid: b9e9f348-968c-46e0-8340-df1f1fcaf3a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 5dcc4090-effe-479e-8d5c-67e6a6542fbb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Comportamento JSP{#jsp-behavior}

Se determinados trabalhos **jsp** não forem executados com êxito, você deverá forçá-los a recompilar.

Para isso, insira os seguintes comandos:

```
nlserver stop web
cd nl6/tomcat-7
rm -r work/
nlserver start web
```

Os trabalhos **jsp** serão regenerados na próxima vez que você se conectar.
