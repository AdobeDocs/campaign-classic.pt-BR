---
title: Arquivos temporários
seo-title: Arquivos temporários
description: Arquivos temporários
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Arquivos temporários{#temporary-files}

Se mensagens de erro como as seguintes forem exibidas (principalmente nos registros de entrega) quando o sistema for colocado em produção:

**Não é possível renomear o arquivo &#39;/tmp/tmp0000.tmp&#39; para /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, link inválido entre dispositivos) (iRc=-52)**

A causa é a seguinte:

O Adobe Campaign gera arquivos temporários em **/tmp** e os renomeia para movê-los para **/usr/local/neolane/nl6/var**. Esse erro ocorre quando ambas as pastas (**/tmp** e **/usr/local/neolane/nl6/var**, que é na verdade um link simbólico para **/var/nl6**) correspondem a dispositivos diferentes. O comando **df** é usado para verificação.

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

