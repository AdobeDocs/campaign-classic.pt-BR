---
product: campaign
title: Comportamento JSP
description: Comportamento JSP
feature: Monitoring
badge-v7-prem: label="No local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 34%

---

# Comportamento JSP{#jsp-behavior}



Se determinadas **jsp** os trabalhos não são executados com êxito, é necessário forçá-los a recompilar.

Para isso, insira os seguintes comandos:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

A variável **jsp** os processos são gerados novamente na próxima vez que você se conectar.
