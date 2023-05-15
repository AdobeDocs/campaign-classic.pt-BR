---
product: campaign
title: Precisão do log
description: Precisão do log
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# Precisão do log{#log-precision}



Você pode aplicar esse processo a todos os módulos Adobe Campaign para aumentar a precisão do log.

Ela envolve reiniciar os processos com um nível mais alto de logs.

>[!IMPORTANT]
>
>Este procedimento cancela os serviços em andamento neste módulo.

O Adobe Campaign pode operar com dois níveis de log:

1. O **Verbose** é o primeiro nível após o nível padrão. O comando a seguir o ativa:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Verifique se o erro realmente ocorreu e reinicie o processo da maneira normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. O **TraceFilter** , que permite salvar o maior número de logs. Ela é ativada pelo seguinte comando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Se você usar **trefilter:&#42;**, todos os tipos de log são ativados: ncm, rdr, nms, jst, tempo, wdbc, ldap, soap, xtk, xtkquery, sessão, xtkwriter, rede, pop3, inmail\
   >Os tipos de log mais úteis são: **wdbc** (exibe todas as consultas SQL), **sabão** (exibe todas as chamadas SOAP), **ldap** (exibe todas as consultas LDAP após a autenticação), **xtkquery** (exibe a lista de todos os querydef).\
   >Você pode usá-los individualmente (**tracefilter:soap,wdbc** por exemplo). Você também pode ativá-los e optar por excluir alguns outros: **-tracefilter:&#42;,!soap**

   Verifique se o erro realmente ocorreu e reinicie o processo da maneira normal:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>Os registros desses comandos são armazenados no arquivo de log do módulo.

Este é um exemplo específico para o módulo da Web. Os outros módulos funcionam como indicado acima.

Antes de enviar este comando, verifique se nenhuma tarefa em andamento será afetada:

```
nlserver pdump -who
```

Em seguida, desligue e reinicie o módulo em **TraceFilter** modo:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Outro exemplo:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>O **Tracefile** permite salvar os logs. Nos exemplos acima, os logs são salvos no **var/`<instance-name>`/mta_debug.log** e **var/default/web_debug.log** arquivos.

>[!IMPORTANT]
>
>No Windows, não adicione a opção LD_PRELOAD. O seguinte comando é suficiente:\
>nlserver web -tomcat -verbose -tracefilter:&#42;

Verifique se o problema ocorre novamente e reinicie o módulo:

```
nlserver restart web -tomcat -noconsole
```

Todas as informações estão disponíveis no arquivo **/usr/local/neolane/nl6/var/default/log/web.log**.
