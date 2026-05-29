---
product: campaign
title: Problema de assinatura de URLs rastreados
description: Problema de assinatura de URLs rastreados
feature: Technote
hide: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
TQID: https://experienceleague.adobe.com/qZr50JJz-Z0qffT8ZR1Y4PrBC31Oqz5BkgBpg-ScnJM
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
feature_v2: []
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 387
ht-degree: 34%

---

# Problema de assinatura de URLs rastreados {#tracked-urls}



Após alterações recentes, os URLs rastreados podem falhar quando a assinatura do URL estiver ativa no Campaign. Algumas caixas de correio podem ser mais afetadas do que outras, já que algumas empresas têm ferramentas de segurança específicas que podem afetar links e alterar o mecanismo de assinatura do URL.

Como consequência, a Adobe recomenda desativar o mecanismo de assinatura para links de rastreamento. Este procedimento corrige links de rastreamento antigos, exceto os recebidos com um escape duplo.

Observe que os links de unsubscription podem falhar como qualquer outro link, a frequência é variável de host para host, mas é inferior a 1%.

**Você será afetado?**

Para melhorar a segurança, o mecanismo de assinatura para rastrear links em emails foi introduzido no [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - abril de 2020 - e é habilitado por padrão para todos os clientes, a partir da Build 19.1.4 (9032@3a9dc9c) e do Campaign 20.2.

Se seu ambiente estiver sendo executado em uma das versões listadas abaixo, você poderá ser afetado:

* Gold Standard 8 a 11. [Saiba mais](../../rn/using/gold-standard.md#gs-8)
* Versões do Campaign 21.1.1 (build 9277) a 21.1.2 (build 9282). [Saiba mais](../../rn/using/latest-release.md)
* Versões do Campaign 20.3.1 (compilação 9228) para 20.3.3 (compilação 9234).
* Versões do Campaign 20.2.1 (build 9178) a 20.2.4 (build 9187).
* Versões do Campaign 20.1.1 (build 9122) a 21.1.3 (build 9124).
* Versões do Campaign 19.2.2 (build 9080) a 19.2.3 (build 9081).
* Versões do Campaign 19.1.5 (build 9033) a 19.1.7 (build 9036).


Saiba como verificar sua versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Como atualizar?**

Como um **cliente hospedado**, a Adobe estará trabalhando com você para atualizar sua configuração em breve.

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
>O arquivo **config-`<instance>`.xml** substitui as configurações de **serverConf.xml**. Se o **signEmailLinks** estiver presente no **config-`<instance>`.xml** (onde **instance** é o nome da sua instância), ele também deverá ser transformado em **false**.
>

**Qual é o impacto?**

A manutenção requer no máximo 25 minutos de inatividade, e durante esse período todas as entregas, links de rastreamento e chamadas de API não funcionarão.

Quando a atualização estiver concluída, todos os links funcionarão conforme esperado.

>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>
