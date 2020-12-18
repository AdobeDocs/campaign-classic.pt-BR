---
solution: Campaign Classic
product: campaign
title: Arquivos de log
description: Arquivos de log
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---


# Arquivos de log{#log-files}

Os arquivos de registro são organizados da seguinte forma:

![](assets/d_ncs_directory.png)

Cada módulo **nlserver** gera um arquivo de log salvo no seguinte diretório: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

O módulo **nlserver syslogd** salva os registros no disco. Este módulo é semelhante ao Unix **syslog daemon**, mas foi adaptado para compatibilidade entre Unix e Windows. Os outros módulos Adobe Campaign não salvam seus registros no disco; eles delegam essa tarefa ao módulo **syslogd** enviando pacotes UDP.

Por padrão, a plataforma Adobe Campaign tem o módulo **syslogd** instalado nela, mas é possível usar outro **syslog daemon**. Este módulo cria os arquivos de log no diretório **log**.

Os registros dos módulos de várias instâncias são armazenados no seguinte diretório: **`<installation directory>`/var/default/log/**. O mesmo arquivo de log é compartilhado por todas as instâncias (por exemplo, **web.log**).

Os registros dos outros módulos são armazenados em uma subpasta nomeada após a instância. Cada instância tem seus próprios arquivos de log.

Os arquivos de log de várias instâncias são listados na seguinte tabela:

| Arquivo | Descrição |
|---|---|
| web.log | Registros do módulo da Web (console do cliente, relatórios, API SOAP etc.) |
| webmdl.log | Registros do módulo de redirecionamento |
| watchdog.log | Logs do módulo de monitoramento de processos da Adobe Campaign |
| trackinglogd.log | Logs de rastreamento |

Os arquivos de log de instância mono estão listados na seguinte tabela:

| Arquivo | Descrição |
|---|---|
| mta.log | registros do módulo mta |
| mtachild.log | Registros de processamento do delivery de mensagens |
| wfserver.log | Logs do módulo do servidor de fluxo de trabalho |
| runwf.log | Logs de execução do fluxo de trabalho |
| inMail.log | Registro do módulo de e-mail de rejeição |
| logins.log | Registra todas as tentativas de login no Adobe Campaign (bem-sucedidas ou não) |

>[!IMPORTANT]
>
>O diretório **redir** existe apenas em servidores de redirecionamento. O subdiretório **url** contém as correspondências dos URLs a serem redirecionados e o subdiretório **log** contém os logs de rastreamento. Para gerar logs de rastreamento, o módulo **trackinglogd** deve estar em execução.

Para otimização de desempenho e armazenamento, o arquivo logins.log é dividido em vários arquivos, um a cada dia (logins.yy-mm-dd.log) com um máximo de 365 arquivos retidos. O número de dias pode ser alterado em serverConf.xml, em syslogd (**maxNumberOfLoginsFiles** opção). Consulte a documentação no arquivo de configuração do servidor [a1/>.](../../installation/using/the-server-configuration-file.md#syslogd)

Por padrão, os registros são limitados a dois arquivos de 10 MB por módulo e por instância. O segundo arquivo é chamado: **`<modulename>`_2.log**. O tamanho dos registros é, portanto, limitado a 2*10MB por módulo e por instância.

Entretanto, é possível manter arquivos maiores. Para habilitar isso, altere o valor da configuração **maxFileSizeMb=&quot;10&quot;** no nó **syslogd** do arquivo **conf/serverConf.xml**. Este valor representa o tamanho máximo em MB de um arquivo de log.

Se desejar manter níveis adicionais de detalhes nos registros, você pode start os módulos Adobe Campaign com o parâmetro **-verbose**:

**start nlserver  `<MODULE>`@`<INSTANCE>` -verbose**
