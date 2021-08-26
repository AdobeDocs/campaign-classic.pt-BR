---
product: campaign
title: Problemas de exibição de imagem
description: Problemas de exibição de imagem
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# Problemas de exibição de imagem{#image-display-issues}

![](../../assets/v7-only.svg)

Se você enfrentar problemas de exibição de imagem em uma mensagem enviada, os motivos podem estar vinculados a um local incorreto:

* Os locais podem não corresponder ou as imagens podem não ter sido enviadas corretamente para o servidor de rastreamento duplicado: verifique sua configuração.
* As imagens podem não residir na pasta de recursos públicos na instância de marketing: carregue as imagens na pasta de recursos para resolver o problema.
* Se você trabalhar em uma arquitetura mid-sourcing: verificar imagens são carregadas sem erros quando provas são enviadas (as informações são exibidas nos logs de análise).

Como solucionar problemas:

1. Envie uma prova que mostrará as imagens.
1. Valide se a configuração dos recursos na configuração da instância está correta.
1. Verifique a pasta de recursos públicos ou, se não estiver na pasta de recursos públicos, a pasta referenciada no delivery.
