---
product: campaign
title: Imagens ausentes
description: Imagens ausentes
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 11%

---

# Imagens ausentes{#images-missing}



Na versão 17.9, vários arquivos (ícones em particular) foram movidos.

Para clientes hospedados, não há impacto. Para instalações no local, leia o seguinte.

**Usuários do Apache:**

Não há impacto para os usuários do Apache se eles usarem os **apache_neolane.conf**.

**Usuários do IIS:**

Para usuários do IIS (no Windows), vários ícones aparecerão ausentes no console após a atualização de build. Etapas adicionais de atualização do IIS são necessárias:

1. Após a atualização da build, clique duas vezes em **iis_neolane_setup.vbs** localizado no diretório de instalação do Campaign. O caminho padrão é C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Reinicie o site do IIS que foi atualizado pela etapa anterior.
