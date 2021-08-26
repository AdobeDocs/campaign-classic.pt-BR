---
product: campaign
title: Nota técnica
description: Nota técnica
hide: true
hidefromtoc: true
source-git-commit: 53ac193211a1d98c45e97bf01ab0ad843b8f8f02
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 36%

---

# Problema de assinatura de URLs rastreados {#tracked-urls}

![](../../assets/v7-only.svg)

Após alterações recentes, os URLs rastreados podem falhar quando a assinatura do URL está ativa no Campaign. Algumas caixas de correio podem ser mais afetadas do que outras, já que algumas empresas têm ferramentas de segurança específicas que podem afetar links e alterar o mecanismo de assinatura do URL.

Como consequência, o Adobe recomenda desativar o mecanismo de assinatura para links de rastreamento. Esse procedimento corrige os links de rastreamento antigos, exceto os recebidos com um escape duplo.

Observe que os links de unsubscription podem falhar como qualquer outro link, a frequência é variável de host para host, mas é inferior a 1%.

**Você será afetado?**

Para melhorar a segurança, o mecanismo de assinatura para rastrear links em emails foi introduzido no [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - abril de 2020 - e é ativado por padrão para todos os clientes que iniciam a Build 19.1.4 (9032@3a9dc9c) e o Campaign 20.2.

Se seu ambiente estiver em execução em uma das versões listadas abaixo, você poderá ser afetado:

* Gold Standard 8 a 11. [Saiba mais](../../rn/using/gold-standard.md#gs-8)
* Campanha 21.1.1 (build 9277) para versões 21.1.2 (build 9282). [Saiba mais](../../rn/using/latest-release.md)
* Campanha 20.3.1 (build 9228) a versões 20.3.3 (build 9234). [Saiba mais](../../rn/using/release--20-3.md)
* Campanha 20.2.1 (build 9178) a versões 20.2.4 (build 9187). [Saiba mais](../../rn/using/release--20-2.md)
* Campanha 20.1.1 (build 9122) para versões 21.1.3 (build 9124). [Saiba mais](../../rn/using/release--20-1.md)
* Campanha 19.2.2 (build 9080) a versões 19.2.3 (build 9081). [Saiba mais](../../rn/using/release--19-2.md)
* Campanha 19.1.5 (build 9033) para versões 19.1.7 (build 9036). [Saiba mais](../../rn/using/release--19-1.md)

Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Como **cliente hospedado**, o Adobe trabalhará com você para atualizar sua configuração em breve.

Como um **cliente local/híbrido**, você precisa atualizar sua configuração.

Siga a etapa abaixo:

1. No [arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md) (serverConf.xml), altere **signEmailLinks** para **false**.
1. Reinicie o serviço **nlserver**.
1. No servidor de rastreamento, reinicie o servidor da Web (apache2 em Debian, httpd em CentOS/RedHat, IIS no Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>O arquivo **config-`<instance>`.xml** substitui as configurações **serverConf.xml**. Se **signEmailLinks** estiver presente no **config-`<instance>`.xml** (onde **instance** é o nome da sua instância), também deverá ser definido como **false**.

**Qual é o impacto?**

A manutenção requer no máximo 25 minutos de inatividade, e durante esse período todos os deliveries, links de rastreamento e chamadas de API não funcionarão.

Quando a atualização estiver concluída, todos os links funcionarão conforme esperado.

>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
