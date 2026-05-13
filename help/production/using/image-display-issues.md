---
product: campaign
title: Problemas de exibição de imagem
description: Problemas de exibição de imagem
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
TQID: https://experienceleague.adobe.com/aBPQb0Yp8o7goe2CS4h6ydnZV5gjPYINHMxGcc-d140
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 134
ht-degree: 6%

---

# Problemas de exibição de imagem{#image-display-issues}



Se você enfrentar problemas de exibição de imagem em uma mensagem enviada, os motivos podem estar vinculados ao local incorreto:

* Os locais podem não corresponder ou as imagens podem não ter sido enviadas corretamente para o servidor de rastreamento duplicado: verifique a configuração.
* As imagens podem não residir na pasta de recurso público na instância de marketing: carregue as imagens na pasta de recursos para resolver o problema.
* Se você trabalhar em uma arquitetura mid-sourcing: as imagens de verificação são carregadas sem erros quando as provas são enviadas (as informações são exibidas nos logs de análise).

Como solucionar problemas:

1. Envie uma prova que mostrará as imagens.
1. A validação da configuração de recursos na configuração da instância está correta.
1. Verifique a pasta public resources ou, se não estiver na pasta public resources, a pasta referenciada no delivery.
