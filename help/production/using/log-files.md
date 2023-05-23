---
product: campaign
title: Arquivos de log
description: Arquivos de log
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---

# Arquivos de log{#log-files}



Os arquivos de log são organizados da seguinte maneira:

![](assets/d_ncs_directory.png)

Each **nlserver** O módulo gera um arquivo de log salvo no seguinte diretório: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

A variável **syslogd nlserver** O módulo salva os logs no disco. Esse módulo é semelhante ao Unix **syslog daemon**, mas foi adaptado para compatibilidade entre Unix e Windows. Os outros módulos do Adobe Campaign não salvam seus registros no disco; eles delegam essa tarefa à **syslogd** enviando pacotes UDP.

Por padrão, a plataforma Adobe Campaign tem a variável **syslogd** módulo instalado nele, mas é possível usar outro **syslog daemon**. Esse módulo cria os arquivos de log no **log** diretório.

Os logs dos módulos de várias instâncias são armazenados no seguinte diretório: **`<installation directory>`/var/default/log/**. O mesmo arquivo de log é compartilhado por todas as instâncias (por exemplo, **web.log**).

Os logs dos outros módulos são armazenados em uma subpasta chamada em homenagem à instância. Cada instância tem seus próprios arquivos de log.

Os arquivos de log de várias instâncias são listados na seguinte tabela:

| Arquivo | Descrição |
|---|---|
| web.log | Logs do módulo da Web (console do cliente, relatórios, API SOAP etc.) |
| webmdl.log | Logs do módulo de redirecionamento |
| watchdog.log | Logs do módulo de monitoramento do processo do Adobe Campaign |
| trackinglogd.log | Logs de rastreamento |

Os arquivos de log de instância mono são listados na tabela a seguir:

| Arquivo | Descrição |
|---|---|
| mta.log | logs do módulo mta |
| mtachild.log | Logs de processamento de entrega de mensagens |
| wfserver.log | Logs do módulo de servidor de workflow |
| runwf.log | Logs de execução de fluxo de trabalho |
| inMail.log | Log do módulo de email de devolução |
| logins.log | Registra todas as tentativas de logon no Adobe Campaign (com ou sem sucesso) |

>[!IMPORTANT]
>
>A variável **redirecionar** o diretório só existe em servidores de redirecionamento. A variável **url** subdiretório contém as correspondências dos URLs a serem redirecionados e o subdiretório **log** contém os logs de rastreamento. Para gerar logs de rastreamento, a variável **trackinglogd** o módulo deve estar em execução.

Para otimização de desempenho e armazenamento, o arquivo logins.log é dividido em vários arquivos, um a cada dia (logins.yy-mm-dd.log) com um máximo de 365 arquivos retidos. O número de dias pode ser alterado no serverConf.xml, em syslogd (**maxNumberOfLoginsFiles** opção). Consulte a documentação no [arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md#syslogd).

Por padrão, os registros são limitados a dois arquivos de 10 MB por módulo e por instância. O segundo arquivo é chamado: **`<modulename>`_2.log**. Portanto, o tamanho dos logs é limitado a 2&#42;10 MB por módulo e por instância.

No entanto, você pode manter arquivos maiores. Para habilitar isso, altere o valor de **maxFileSizeMb=&quot;10&quot;** configuração no **syslogd** nó do **conf/serverConf.xml** arquivo. Esse valor representa o tamanho máximo de um arquivo de log, em MB.

Se quiser manter mais níveis de detalhes nos logs, inicie os módulos do Adobe Campaign com o **-verboso** parâmetro:

**nlserver start `<MODULE>`@`<INSTANCE>` -verboso**
