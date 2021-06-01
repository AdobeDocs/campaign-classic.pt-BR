---
product: campaign
title: Configuração
description: Configuração
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 1%

---

# Configuração{#configuration}

## Alteração da porta de escuta do syslogd {#changing-the-syslogd-listening-port}

Por padrão, a porta de escuta **syslogd** é 666 (udp). Você pode alterá-la usando uma variável de ambiente, se necessário.

Depois de configurada, essa variável é considerada por todos os módulos Adobe Campaign.

### No Linux {#in-linux}

Edite o arquivo **customer.sh** e adicione a seguinte linha:

```
export TRACE_ADDR=localhost:<listening port>
```

### No Windows {#in-windows}

É necessário criar a variável de ambiente **TRACE_ADDR** com o valor **localhost**: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Recomendamos executar alguns testes para garantir que sua plataforma funcione após a criação dessa variável de ambiente.

## Configuração de zonas de segurança {#configuring-security-zones}

Cada operador precisa ser vinculado a uma zona para fazer logon em uma instância e o IP do operador deve ser incluído nos endereços ou conjuntos de endereços definidos na zona de segurança. A configuração da zona técnica é realizada no arquivo de configuração do servidor do Adobe Campaign. A vinculação de um operador a uma zona de segurança deve ser definida no console (nó **[!UICONTROL Administration > Access management > Operators]** ).

>[!NOTE]
>
>Para obter mais informações sobre como configurar zonas de segurança, consulte [esta seção](../../installation/using/security-zones.md).
