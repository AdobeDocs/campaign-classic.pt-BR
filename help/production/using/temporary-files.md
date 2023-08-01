---
product: campaign
title: Arquivos temporários
description: Arquivos temporários
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Aplicável somente ao Campaign Classic v7"
badge-v7-prem: label="no local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 14%

---

# Arquivos temporários{#temporary-files}



Mensagens de erro como a seguir podem ser exibidas (principalmente em logs de entrega) quando o sistema é colocado em produção:

*Não é possível renomear o arquivo &#39;/tmp/tmp0000.tmp&#39; como /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, link entre dispositivos inválido) (iRc=-52)*

A causa é a seguinte:

O Adobe Campaign gera arquivos temporários em **/tmp**, e os renomeia para movê-los para **/usr/local/neolane/nl6/var**. Esse erro ocorre quando ambas as pastas (**/tmp** e **/usr/local/neolane/nl6/var**, que é, na verdade, um vínculo simbólico com **/var/nl6**) correspondem a diferentes dispositivos. A variável **df** é utilizado para verificação.

Para corrigir esse problema, os arquivos temporários devem ser gerados no mesmo dispositivo do destino.

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
