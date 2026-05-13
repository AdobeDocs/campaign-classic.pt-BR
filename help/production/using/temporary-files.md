---
product: campaign
title: Arquivos temporários
description: Arquivos temporários
feature: Monitoring
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
TQID: https://experienceleague.adobe.com/eZnGm-WK-etrLLbJ-aeuSqakYAfPNBQd2q3JlEd4rE8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 164
ht-degree: 21%

---

# Arquivos temporários{#temporary-files}



Mensagens de erro como a seguir podem ser exibidas (principalmente em logs de entrega) quando o sistema é colocado em produção:

*Não é possível renomear o arquivo &#39;/tmp/tmp0000.tmp&#39; como /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, link entre dispositivos inválido) (iRc=-52)*

A causa é a seguinte:

O Adobe Campaign gera arquivos temporários em **/tmp** e os renomeia para movê-los para **/usr/local/neolane/nl6/var**. Este erro ocorre quando ambas as pastas (**/tmp** e **/usr/local/neolane/nl6/var**, que é, na verdade, um link simbólico para **/var/nl6**) correspondem a dispositivos diferentes. O comando **df** é usado para verificação.

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
