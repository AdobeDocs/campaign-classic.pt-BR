---
solution: Campaign Classic
product: campaign
title: Rede, banco de dados e SSL/TLS
description: Saiba mais sobre as práticas recomendadas de configuração de rede, banco de dados e SSL/TLS.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 33%

---


# Rede, banco de dados e SSL/TLS {#network-database}

## Configuração de rede

Uma coisa muito importante a se verificar ao implantar um tipo de arquitetura local é a [configuração de rede](../../installation/using/network-configuration.md). Certifique-se de que o servidor Tomcat NÃO esteja diretamente acessível fora do servidor:

* Feche a porta Tomcat (8080) em IPs externos (deve funcionar no host local)
* Não mapeie a porta HTTP padrão (80) para a do Tomcat (8080)

Quando possível, use um canal seguro: POP3S em vez de POP3 (ou POP3 sobre TLS).

## Banco de dados

É indispensável que a segurança do mecanismo de banco de dados seja seguida.

### Configuração SSL/TLS*

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

Você também pode usar um python script [sslyze](https://github.com/nabla-c0d3/sslyze/releases) que faz ambos.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
