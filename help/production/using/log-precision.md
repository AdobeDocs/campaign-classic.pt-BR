---
title: Precisão do log
seo-title: Precisão do log
description: Precisão do log
seo-description: null
page-status-flag: never-activated
uuid: 8396bc4f-2954-40bb-b511-61802e60e123
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: c6c39b7d-7bbd-4789-b1ea-b938153e9679
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---


# Precisão do log{#log-precision}

É possível aplicar esse processo a todos os módulos Adobe Campaign para aumentar a precisão do log.

Envolve o relançamento dos processos com um nível mais alto de registros.

>[!IMPORTANT]
>
>Este procedimento cancela os serviços em andamento neste módulo.

A Adobe Campaign pode operar com dois níveis de log:

1. O modo **Verboso** é o primeiro nível após o nível padrão. O seguinte comando o ativa:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Verifique se o erro realmente ocorreu e reinicie o processo da maneira normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. O modo **TraceFilter** , que permite salvar o maior número de logs. Ele é ativado pelo seguinte comando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Se você usar **tracefilter:***, todos os tipos de log serão ativados: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   Os tipos de log mais úteis são: **wdbc** (exibe todos os query SQL), **soap** (exibe todas as chamadas SOAP), **ldap** (exibe todos os query LDAP após a autenticação), **xtkquery** (exibe a lista de todos os querydef).\
   Você pode usá-los individualmente (**tracefilter:soap,wdbc** , por exemplo). Você também pode ativar todos e optar por excluir alguns outros: **-tracefilter:*,!soap**

   Verifique se o erro realmente ocorreu e reinicie o processo da maneira normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
Os registros desses comandos são armazenados no arquivo de log do módulo.

Este é um exemplo específico do módulo Web. Os outros módulos operam conforme indicado acima.

Antes de enviar este comando, verifique se nenhuma tarefa em andamento será afetada.

```
nlserver pdump -who
```

Em seguida, desligue e reinicie o módulo no modo **TraceFilter** .

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Outro exemplo:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
O modo **Tracefile** permite salvar os logs. Nos exemplos acima, os registros são salvos nos arquivos **var/`<instance-name>`/mta_debug.log** e **var/default/web_debug.log** .

>[!IMPORTANT]
No Windows, não adicione a opção LD_PRELOAD. O seguinte comando é suficiente:\
nlserver web -tomcat -verbose -tracefilter:*

Verifique se o problema ocorre novamente e reinicie o módulo:

```
nlserver restart web -tomcat -noconsole
```

Todas as informações estão disponíveis no arquivo **/usr/local/neolane/nl6/var/default/log/web.log**.
