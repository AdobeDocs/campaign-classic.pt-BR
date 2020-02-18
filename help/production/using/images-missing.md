---
title: Imagens ausentes
seo-title: Imagens ausentes
description: Imagens ausentes
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# Imagens ausentes{#images-missing}

Na versão 17.9, vários arquivos (ícones em particular) foram movidos.

Para clientes hospedados, não há impacto. Para instalações locais, leia o seguinte.

**Usuários do Apache:**

Não há impacto para os usuários do Apache se eles usarem o **apache_neolane.conf fornecido**

**Usuários do IIS:**

Para usuários do IIS (no Windows), vários ícones aparecerão ausentes no console após a atualização da compilação. Etapas adicionais de atualização do IIS são necessárias:

1. Após a atualização da compilação, clique duas vezes em **is_neolane_setup.vbs** localizado no diretório de instalação da Campanha. O caminho padrão é C:\Program Files (x86)\Adobe\Adobe Campaign v7\tomcat-7\conf
1. Reinicie o site do IIS que foi atualizado pela etapa anterior.

