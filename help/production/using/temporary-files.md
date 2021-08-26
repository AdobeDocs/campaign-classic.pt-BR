---
product: campaign
title: Arquivos temporários
description: Arquivos temporários
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# Arquivos temporários{#temporary-files}

![](../../assets/v7-only.svg)

Mensagens de erro como as seguintes podem ser exibidas (principalmente em logs do delivery) quando o sistema é colocado em produção:

*Não é possível renomear o arquivo &#39;/tmp/tmp0000.tmp&#39; para /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, link inválido entre dispositivos) (iRc=-52)*

A causa é a seguinte:

O Adobe Campaign gera arquivos temporários em **/tmp** e os renomeia para movê-los para **/usr/local/neolane/nl6/var**. Esse erro ocorre quando ambas as pastas (**/tmp** e **/usr/local/neolane/nl6/var**, que é de fato um link simbólico para **/var/nl6**) correspondem a dispositivos diferentes. O comando **df** é usado para verificação.

Para corrigir esse problema, os arquivos temporários devem ser gerados no mesmo dispositivo que o destino.

Por exemplo, execute o seguinte:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Em seguida, adicione:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
