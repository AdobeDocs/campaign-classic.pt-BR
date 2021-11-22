---
product: campaign
title: Arquivos de log
description: Arquivos de log
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---

# Arquivos de log{#log-files}

![](../../assets/v7-only.svg)

Os arquivos de log são organizados da seguinte maneira:

![](assets/d_ncs_directory.png)

Cada **nlserver** O módulo gera um arquivo de log salvo no seguinte diretório: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

O **nlserver syslogd** O módulo salva os logs no disco. Esse módulo é semelhante ao Unix **daemon do syslog**, mas foi adaptado para compatibilidade entre Unix e Windows. Os outros módulos Adobe Campaign não salvam seus registros no disco; eles delegam essa tarefa à **syslogd** enviando pacotes UDP para ele.

Por padrão, a plataforma do Adobe Campaign tem a variável **syslogd** instalado nele, mas é possível usar outro **daemon do syslog**. Esse módulo cria os arquivos de log no **log** diretório.

Os registros de módulos de várias instâncias são armazenados no seguinte diretório: **`<installation directory>`/var/default/log/**. O mesmo arquivo de log é compartilhado por todas as instâncias (por exemplo, **web.log**).

Os logs dos outros módulos são armazenados em uma subpasta chamada após a instância. Cada instância tem seus próprios arquivos de log.

Os arquivos de log de várias instâncias são listados na tabela a seguir:

| Arquivo | Descrição |
|---|---|
| web.log | Logs do módulo da Web (console do cliente, relatórios, API SOAP etc.) |
| webmdl.log | Logs do módulo de redirecionamento |
| watchdog.log | Logs do módulo de monitoramento do processo Adobe Campaign |
| trackinglogd.log | Logs de rastreamento |

Os arquivos de log de mono-instance são listados na seguinte tabela:

| Arquivo | Descrição |
|---|---|
| mta.log | logs do módulo mta |
| mtachild.log | Logs de processamento de delivery de mensagens |
| wfserver.log | Logs do módulo do servidor de workflow |
| runwf.log | Logs de execução do workflow |
| inMail.log | Log do módulo de email de devolução |
| logins.log | Registra todas as tentativas de logon no Adobe Campaign (bem-sucedidas ou não) |

>[!IMPORTANT]
>
>O **retro** O diretório existe apenas em servidores de redirecionamento. O **url** O subdiretório contém as correspondências dos URLs a serem redirecionados e o subdiretório **log** contém os logs de rastreamento. Para gerar logs de rastreamento, a variável **trackinglogd** deve estar em execução.

Para otimização de desempenho e armazenamento, o arquivo logins.log é dividido em vários arquivos, um a cada dia (logins.yy-mm-dd.log) com no máximo 365 arquivos retidos. O número de dias pode ser alterado no serverConf.xml, em syslogd (**maxNumberOfLoginsFiles** ). Consulte a documentação no [arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md#syslogd).

Por padrão, os logs são limitados a dois arquivos de 10 MB por módulo e por instância. O segundo arquivo é chamado: **`<modulename>`_2.log**. O tamanho dos logs, portanto, é limitado a 2*10MB por módulo e por instância.

No entanto, você pode manter arquivos maiores. Para habilitar isso, altere o valor da variável **maxFileSizeMb=&quot;10&quot;** na configuração do **syslogd** nó do **conf/serverConf.xml** arquivo. Este valor representa o tamanho máximo em MB de um arquivo de log.

Se quiser manter mais níveis de detalhes nos logs, você poderá iniciar os módulos Adobe Campaign com a variável **-verbose** parâmetro:

**nlserver start `<MODULE>`@`<INSTANCE>` -verbose**
