---
product: campaign
title: Arquivos de log
description: Arquivos de log
feature: Monitoring
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
TQID: https://experienceleague.adobe.com/ueoodkXqvcxSjb4Q2NOKXrTgZIiQEGvBiW8JQF-PFss
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 470
ht-degree: 8%

---

# Arquivos de log{#log-files}



Os arquivos de log são organizados da seguinte maneira:

![](assets/d_ncs_directory.png)

Cada módulo **nlserver** gera um arquivo de log salvo no seguinte diretório: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

O módulo **nlserver syslogd** salva os logs no disco. Este módulo é semelhante ao **syslog daemon** do Unix, mas foi adaptado para compatibilidade entre Unix e Windows. Os outros módulos do Adobe Campaign não salvam seus logs no disco. Eles delegam essa tarefa ao módulo **syslogd** enviando pacotes UDP.

Por padrão, a plataforma Adobe Campaign tem o módulo **syslogd** instalado, mas é possível usar outro **syslog daemon**. Este módulo cria os arquivos de log no diretório **log**.

Os logs dos módulos de várias instâncias são armazenados no seguinte diretório: **`<installation directory>`/var/default/log/**. O mesmo arquivo de log é compartilhado por todas as instâncias (por exemplo, **web.log**).

Os logs dos outros módulos são armazenados em uma subpasta chamada em homenagem à instância. Cada instância tem seus próprios arquivos de log.

Os arquivos de log de várias instâncias são listados na seguinte tabela:

| Arquivo | Descrição |
|---|---|
| web.log | Logs do módulo da Web (console do cliente, relatórios, API do SOAP etc.) |
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
>O diretório **redirecionador** existe apenas nos servidores de redirecionamento. O subdiretório **url** contém as correspondências das URLs a serem redirecionadas, e o subdiretório **log** contém os logs de rastreamento. Para gerar logs de rastreamento, o módulo **trackinglogd** deve estar em execução.

Para otimização de desempenho e armazenamento, o arquivo logins.log é dividido em vários arquivos, um a cada dia (logins.yy-mm-dd.log) com um máximo de 365 arquivos retidos. O número de dias pode ser alterado no serverConf.xml, em syslogd (opção **maxNumberOfLoginsFiles**). Consulte a documentação no [arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md#syslogd).

Por padrão, os registros são limitados a dois arquivos de 10 MB por módulo e por instância. O segundo arquivo é chamado: **`<modulename>`_2.log**. Portanto, o tamanho dos logs é limitado a 2&#42;10MB por módulo e por instância.

No entanto, você pode manter arquivos maiores. Para habilitar isso, altere o valor da configuração **maxFileSizeMb=&quot;10&quot;** no nó **syslogd** do arquivo **conf/serverConf.xml**. Esse valor representa o tamanho máximo de um arquivo de log, em MB.

Se quiser manter mais níveis de detalhes nos logs, inicie os módulos do Adobe Campaign com o parâmetro **-verbose**:

**ninício do lserver `<MODULE>`@`<INSTANCE>` -verbose**
