---
solution: Campaign Classic
product: campaign
title: Arquivos temporários
description: Arquivos temporários
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---


# Arquivos temporários{#temporary-files}

As mensagens de erro, como as seguintes, podem ser exibidas (principalmente em logs do delivery) quando o sistema é colocado em produção:

*Não é possível renomear o arquivo &#39;/tmp/tmp0000.tmp&#39; para /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, link inválido entre dispositivos) (iRc=-52)*

A causa é a seguinte:

A Adobe Campaign gera arquivos temporários em **/tmp** e os renomeia para movê-los para **/usr/local/neolane/nl6/var**. Este erro ocorre quando ambas as pastas (**/tmp** e **/usr/local/neolane/nl6/var**, que é na verdade um link simbólico para **/var/nl6**) correspondem a dispositivos diferentes. O comando **df** é usado para verificação.

Para corrigir esse problema, os arquivos temporários devem ser gerados no mesmo dispositivo que o destino. Por exemplo, executando:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

e depois adicionando:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

