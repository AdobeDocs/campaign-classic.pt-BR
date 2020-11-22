---
solution: Campaign Classic
product: campaign
title: Configuração
description: Configuração
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 1%

---


# Configuração{#configuration}

## Alteração da porta de escuta syslogd {#changing-the-syslogd-listening-port}

Por padrão, a porta de escuta **syslogd** é 666 (udp). Você pode alterá-la usando uma variável de ambiente, se necessário.

Depois de configurada, essa variável é considerada por todos os módulos Adobe Campaign.

### No Linux {#in-linux}

Edite o arquivo **customer.sh** e adicione a seguinte linha:

```
export TRACE_ADDR=localhost:<listening port>
```

### No Windows {#in-windows}

É necessário criar a variável de ambiente **TRACE_ADDR.** com o valor **localhost** : **`<listening port="" />`**.

>[!IMPORTANT]
>
>Recomendamos a execução de alguns testes para garantir que sua plataforma funcione depois que você criar essa variável de ambiente.

## Configuração de zonas de segurança {#configuring-security-zones}

Cada operador precisa estar vinculado a uma zona para fazer logon em uma instância e o IP do operador deve ser incluído nos endereços ou conjuntos de endereços definidos na zona de segurança. A configuração da zona técnica é realizada no arquivo de configuração do servidor Adobe Campaign. A vinculação de um operador a uma zona de segurança deve ser definida no console ( **[!UICONTROL Administration > Access management > Operators]** nó).

>[!NOTE]
>
>For more on configuring security zones, refer to [this section](../../installation/using/configuring-campaign-server.md#defining-security-zones).
