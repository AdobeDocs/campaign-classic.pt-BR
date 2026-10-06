---
product: campaign
title: Imagens ausentes
description: Imagens ausentes
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
TQID: 'https://experienceleague.adobe.com/GDlcjvzSGP70FlVGHmnhJHsqC3SFG5Y-kQOohR00j8c'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%
---
# Imagens ausentes{#images-missing}



Na versão 17.9, vários arquivos (ícones em particular) foram movidos.

Para clientes hospedados, não há impacto. Para instalações no local, leia o seguinte.

**Usuários do Apache:**

Não há impacto para usuários do Apache se eles usarem o **apache_neolane.conf** fornecido.

**Usuários do IIS:**

Para usuários do IIS (no Windows), vários ícones aparecerão ausentes no console após a atualização de build. Etapas adicionais de atualização do IIS são necessárias:

1. Após a atualização da build, clique duas vezes em **iis_neolane_setup.vbs**, localizado no diretório de instalação do Campaign. O caminho padrão é C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Reinicie o site do IIS que foi atualizado pela etapa anterior.
