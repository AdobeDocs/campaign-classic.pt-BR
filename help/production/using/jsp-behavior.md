---
product: campaign
title: Comportamento JSP
description: Comportamento JSP
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# Comportamento JSP{#jsp-behavior}

![](../../assets/v7-only.svg)

Se certos **jsp** As tarefas não são executadas com êxito, é necessário forçá-las a recompilar.

Para isso, insira os seguintes comandos:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

O **jsp** As tarefas são regeneradas na próxima vez que você se conectar.
