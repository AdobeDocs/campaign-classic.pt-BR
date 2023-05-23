---
product: campaign
title: Configuração adicional
description: Configuração
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# Configuração{#configuration}



## Alterando a porta de escuta do syslogd {#changing-the-syslogd-listening-port}

Por padrão, a variável **syslogd** porta de escuta 666 (udp). Você pode alterá-la usando uma variável de ambiente, se necessário.

Após a configuração, essa variável é considerada por todos os módulos do Adobe Campaign.

### No Linux {#in-linux}

Edite o **customer.sh** e adicione a seguinte linha:

```
export TRACE_ADDR=localhost:<listening port>
```

### No Windows {#in-windows}

É necessário criar o **TRACE_ADDR** variável de ambiente com o **localhost** valor: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Recomendamos executar alguns testes para verificar se sua plataforma está funcionando após a criação dessa variável de ambiente.

## Configuração de zonas de segurança {#configuring-security-zones}

Cada operador precisa ser vinculado a uma zona para fazer logon em uma instância e o operador IP deve ser incluído nos endereços ou conjuntos de endereços definidos na zona de segurança. A configuração da zona técnica é realizada no arquivo de configuração do servidor do Adobe Campaign. A vinculação de um operador a uma zona de segurança deve ser definida no console ( **[!UICONTROL Administration > Access management > Operators]** nó).

>[!NOTE]
>
>Para obter mais informações sobre a configuração de zonas de segurança, consulte [nesta seção](../../installation/using/security-zones.md).
