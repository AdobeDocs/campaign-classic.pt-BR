---
product: campaign
title: Precisão do log
description: Precisão do log
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
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
   >Se você usar **tracefilter:***, todos os tipos de log serão ativados: ncm, rdr, nms, jst, tempo, wdbc, ldap, soap, xtk, xtkquery, sessão, xtkwriter, rede, pop3, inmail\
   >Os tipos de log mais úteis são: **wdbc** (exibe todas as consultas SQL), **soap** (exibe todas as chamadas SOAP), **ldap** (exibe todas as consultas LDAP após a autenticação), **xtkquery** (exibe a lista de todas as querydef).\
   >Você pode usá-los individualmente (**tracefilter:soap,wdbc** por exemplo). Você também pode ativá-los e optar por excluir alguns outros: **-tracefilter:*,!soap**

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
>nlserver web -tomcat -verbose -tracefilter:*

Verifique se o problema ocorre novamente e reinicie o módulo:

```
nlserver restart web -tomcat -noconsole
```

Todas as informações estão disponíveis no arquivo **/usr/local/neolane/nl6/var/default/log/web.log**.
