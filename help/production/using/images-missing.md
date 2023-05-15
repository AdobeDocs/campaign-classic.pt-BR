---
product: campaign
title: Imagens ausentes
description: Imagens ausentes
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---

# Imagens ausentes{#images-missing}



Na versão 17.9, vários arquivos (ícones em particular) foram movidos.

Para clientes hospedados, não há impacto. Para instalações locais, leia o seguinte.

**Usuários do Apache:**

Não haverá impacto para os usuários do Apache se eles usarem o **apache_neolane.conf**.

**Usuários do IIS:**

Para usuários do IIS (no Windows), vários ícones aparecerão ausentes no console após a atualização da build. Etapas adicionais de atualização do IIS são necessárias:

1. Após a atualização da build, clique duas vezes em **iis_neolane_setup.vbs** localizado no diretório de instalação do Campaign. O caminho padrão é C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Reinicie o site do IIS que foi atualizado pela etapa anterior.
