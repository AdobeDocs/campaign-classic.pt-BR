---
solution: Campaign Classic
product: campaign
title: Comportamento JSP
description: Comportamento JSP
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---


# Comportamento JSP{#jsp-behavior}

Se determinados trabalhos **jsp** não forem executados com êxito, você deverá forçá-los a recompilar.

Para isso, insira os seguintes comandos:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

Os trabalhos **jsp** serão regenerados na próxima vez que você se conectar.
