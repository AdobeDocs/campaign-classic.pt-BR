---
product: campaign
title: Configuração adicional
description: Configuração
feature: Monitoring, Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
TQID: https://experienceleague.adobe.com/gzcQquM9q71NIOt8mScgRpLtwffxvopslrrpLxxIang
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 12%
---
# Configuração{#configuration}



## Alterando a porta de escuta do syslogd {#changing-the-syslogd-listening-port}

Por padrão, a porta de escuta **syslogd** é 666 (udp). Você pode alterá-la usando uma variável de ambiente, se necessário.

Após a configuração, essa variável é considerada por todos os módulos do Adobe Campaign.

### No Linux {#in-linux}

Edite o arquivo **customer.sh** e adicione a seguinte linha:

```sql
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
