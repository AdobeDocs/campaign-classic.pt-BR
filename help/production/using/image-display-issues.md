---
product: campaign
title: Problemas de exibição de imagem
description: Problemas de exibição de imagem
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 11%

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
