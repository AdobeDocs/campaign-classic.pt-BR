---
title: Problemas de exibição de imagem
seo-title: Problemas de exibição de imagem
description: Problemas de exibição de imagem
seo-description: null
page-status-flag: never-activated
uuid: 8fc51459-ee46-4c05-8011-f0651e6b451b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: dfccfe8c-b826-4648-9a0b-23d7e6a4808a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Problemas de exibição de imagem{#image-display-issues}

Se você enfrentar problemas de exibição de imagem em uma mensagem enviada, os motivos podem estar vinculados ao local incorreto:

* os locais podem não corresponder ou as imagens podem não ter sido enviadas corretamente para o servidor de rastreamento duplicado: verifique sua configuração.
* as imagens podem não residir na pasta de recursos públicos na instância de marketing: carregue as imagens na pasta de recursos para resolver o problema.
* se você trabalha em uma arquitetura de mid-sourcing: verifique se as imagens estão sendo carregadas sem erros quando as provas são enviadas (as informações são exibidas nos registros de análise).

Como solucionar problemas:

1. Envie uma prova que mostrará as imagens.
1. Validar se a configuração dos recursos na configuração da instância está correta.
1. Verifique a pasta de recursos públicos ou - se ela não estiver na pasta de recursos públicos - a pasta referenciada na entrega.

