---
solution: Campaign Classic
product: campaign
title: Imagens ausentes
description: Imagens ausentes
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---


# Imagens ausentes{#images-missing}

Na versão 17.9, vários arquivos (ícones em particular) foram movidos.

Para clientes hospedados, não há impacto. Para instalações no local, leia o seguinte.

**Usuários do Apache:**

Não há impacto para os usuários do Apache se eles usarem o **apache_neolane.conf** fornecido.

**Usuários do IIS:**

Para usuários do IIS (no Windows), vários ícones aparecerão ausentes no console após a atualização da compilação. Etapas adicionais de atualização do IIS são necessárias:

1. Após a atualização da compilação, clique no duplo **iis_neolane_setup.vbs** localizado no diretório de instalação da Campanha. O caminho padrão é C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Reinicie o site do IIS que foi atualizado pela etapa anterior.
