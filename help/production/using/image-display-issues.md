---
solution: Campaign Classic
product: campaign
title: Problemas de exibição de imagem
description: Problemas de exibição de imagem
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# Problemas de exibição de imagem{#image-display-issues}

Se você enfrentar problemas de exibição de imagem em uma mensagem enviada, os motivos podem estar vinculados ao local incorreto:

* Os locais podem não corresponder ou as imagens podem não ter sido enviadas corretamente para o servidor de rastreamento de duplicados: verifique sua configuração.
* As imagens podem não residir na pasta do recurso público na instância de marketing: carregue as imagens na pasta de recursos para resolver o problema.
* Se você trabalha em uma arquitetura de mid-sourcing: verifique se as imagens estão sendo carregadas sem erros quando as provas são enviadas (as informações são exibidas nos registros de análises).

Como solucionar problemas:

1. Envie uma prova que mostre as imagens.
1. Validar se a configuração dos recursos na configuração da instância está correta.
1. Verifique a pasta recursos públicos ou, se não estiver na pasta recursos públicos, a pasta referenciada no delivery.
