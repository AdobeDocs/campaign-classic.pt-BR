---
product: campaign
title: Precisão do log
description: Precisão do log
feature: Monitoring
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
TQID: https://experienceleague.adobe.com/-AC3ZgKzganqlheg99fMRyJiYNQkHSnIogq5F-Z9xMQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 346
ht-degree: 10%

---

# Precisão do log{#log-precision}



Você pode aplicar esse processo a todos os módulos do Adobe Campaign para aumentar a precisão do log.

Envolve a reinicialização dos processos com um nível mais alto de registros.

>[!IMPORTANT]
>
>Este procedimento cancela os serviços em andamento neste módulo.

O Adobe Campaign pode operar com dois níveis de log:

1. O modo **Verbose** é o primeiro nível após o nível padrão. O comando a seguir o ativa:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Verifique se o erro realmente ocorreu e reinicie o processo da maneira normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. O modo **TraceFilter**, que permite salvar o maior número de logs. Ela é ativada pelo seguinte comando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Se você usar **tracefilter:&#42;**, todos os tipos de log serão ativados: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   >Os tipos de log mais úteis são: **wdbc** (exibe todas as consultas SQL), **soap** (exibe todas as chamadas SOAP), **ldap** (exibe todas as consultas LDAP após a autenticação), **xtkquery** (exibe a lista de todas as querydef).\
   >Você pode usá-los individualmente (**tracefilter:soap,wdbc**, por exemplo). Você também pode ativar todos eles e optar por excluir alguns outros: **-tracefilter:&#42;,!soap**

   Verifique se o erro realmente ocorreu e reinicie o processo da maneira normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>Os logs desses comandos são armazenados no arquivo de log do módulo.

Este é um exemplo específico do módulo Web. Os outros módulos operam como indicado acima.

Antes de enviar este comando, verifique se nenhum trabalho em andamento será afetado:

```
nlserver pdump -who
```

Em seguida, desligue e reinicie o módulo no modo **TraceFilter**:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Outro exemplo:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>O modo **Tracefile** permite salvar os logs. Nos exemplos acima, os logs são salvos nos arquivos **var/`<instance-name>`/mta_debug.log** e **var/default/web_debug.log**.

>[!IMPORTANT]
>
>No Windows, não adicione a opção LD_PRELOAD. O seguinte comando é suficiente:\
>nlserver web -tomcat -verbose -tracefilter:&#42;

Verifique se o problema ocorre novamente e reinicie o módulo:

```
nlserver restart web -tomcat -noconsole
```

Todas as informações estão disponíveis no arquivo **/usr/local/neolane/nl6/var/default/log/web.log**.
