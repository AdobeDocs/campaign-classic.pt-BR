---
product: campaign
title: Rede, banco de dados e SSL/TLS
description: Saiba mais sobre rede, banco de dados e práticas recomendadas de configuração SSL/TLS
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
TQID: https://experienceleague.adobe.com/PLGVcm4QYeU0A1uEhlDEfweZ275xpxtxo91r4aidr1I
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 138
ht-degree: 34%

---

# Rede, banco de dados e SSL/TLS {#network-database}

## Configuração de rede

Uma coisa muito importante a se verificar ao implantar um tipo de arquitetura local é a [configuração de rede](../../installation/using/network-configuration.md). Certifique-se de que o servidor Tomcat NÃO está diretamente acessível fora do servidor:

* Feche a porta Tomcat (8080) em IPs externos (deve funcionar no host local)
* Não mapeie a porta HTTP padrão (80) para a porta Tomcat (8080)

Quando for possível, use um canal seguro: POP3S em vez de POP3 (ou POP3 sobre TLS).

## Banco de dados

Você deve aplicar as práticas recomendadas de segurança do mecanismo de banco de dados.

## Configuração SSL/TLS

Para a verificação do certificado, é possível usar o openssl. Para verificação das cifras ativas, é possível usar o nmap:

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

Você também pode usar um python script [sslyze](https://github.com/nabla-c0d3/sslyze/releases) que faz as duas coisas.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
