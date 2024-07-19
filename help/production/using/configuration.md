---
product: campaign
title: Configuração adicional
description: Configuração
feature: Monitoring, Configuration
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 7%

---

# Configuração{#configuration}



## Alterando a porta de escuta do syslogd {#changing-the-syslogd-listening-port}

Por padrão, a porta de escuta **syslogd** é 666 (udp). Você pode alterá-la usando uma variável de ambiente, se necessário.

Após a configuração, essa variável é considerada por todos os módulos do Adobe Campaign.

### No Linux {#in-linux}

Edite o arquivo **customer.sh** e adicione a seguinte linha:

```
export TRACE_ADDR=localhost:<listening port>
```

### No Windows {#in-windows}

Você precisa criar a variável de ambiente **TRACE_ADDR** com o valor **localhost**: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Recomendamos executar alguns testes para verificar se sua plataforma está funcionando após a criação dessa variável de ambiente.

## Configuração de zonas de segurança {#configuring-security-zones}

Cada operador precisa ser vinculado a uma zona para fazer logon em uma instância e o operador IP deve ser incluído nos endereços ou conjuntos de endereços definidos na zona de segurança. A configuração da zona técnica é realizada no arquivo de configuração do servidor do Adobe Campaign. A vinculação de um operador a uma zona de segurança deve ser definida no console ( nó **[!UICONTROL Administration > Access management > Operators]**).

>[!NOTE]
>
>Para saber mais sobre como configurar zonas de segurança, consulte [esta seção](../../installation/using/security-zones.md).
