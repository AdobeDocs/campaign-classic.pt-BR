---
product: campaign
title: Configuração adicional
description: Configuração
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# Configuração{#configuration}

![](../../assets/v7-only.svg)

## Alterando a porta de escuta do syslogd {#changing-the-syslogd-listening-port}

Por padrão, a variável **syslogd** a porta de escuta é 666 (udp). Você pode alterá-la usando uma variável de ambiente, se necessário.

Depois de configurada, essa variável é considerada por todos os módulos Adobe Campaign.

### No Linux {#in-linux}

Edite o **customer.sh** e adicione a seguinte linha:

```
export TRACE_ADDR=localhost:<listening port>
```

### No Windows {#in-windows}

É necessário criar o **TRACE_ADDR** variável de ambiente com a variável **localhost** valor: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Recomendamos executar alguns testes para garantir que sua plataforma funcione após a criação dessa variável de ambiente.

## Configuração de zonas de segurança {#configuring-security-zones}

Cada operador precisa ser vinculado a uma zona para fazer logon em uma instância e o IP do operador deve ser incluído nos endereços ou conjuntos de endereços definidos na zona de segurança. A configuração da zona técnica é realizada no arquivo de configuração do servidor do Adobe Campaign. A vinculação de um operador a uma zona de segurança deve ser definida no console ( **[!UICONTROL Administration > Access management > Operators]** nó ).

>[!NOTE]
>
>Para obter mais informações sobre a configuração de zonas de segurança, consulte [esta seção](../../installation/using/security-zones.md).
