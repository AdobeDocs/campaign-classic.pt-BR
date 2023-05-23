---
product: campaign
title: Princípio operacional
description: Princípio operacional
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# Princípio operacional{#operating-principle}



Tecnicamente, a plataforma Adobe Campaign é baseada em vários módulos.

Há muitos módulos do Adobe Campaign. Alguns operam continuamente, enquanto outros são iniciados ocasionalmente para executar tarefas administrativas (por exemplo, configurar a conexão de banco de dados) ou para executar uma tarefa recorrente (por exemplo, consolidar informações de rastreamento).

Há três tipos de módulos do Adobe Campaign:

* Módulos de várias instâncias: um único processo é executado para todas as instâncias. Isso se aplica aos seguintes módulos: **web**, **syslogd**, **trackinglogd** e **watchdog** (atividades do **config-default.xml** arquivo).
* Módulos de instância única: um processo é executado por instância. Isso se aplica aos seguintes módulos: **mta**, **wfserver**, **inMail**, **sms** e **stat** (atividades do **config-`<instance>`.xml** arquivo).
* Módulos de utilitários: são módulos executados ocasionalmente para executar operações ocasionais ou recorrentes (**cleanup**, **config**, download de logs de rastreamento etc.).

A administração do módulo é executada usando a ferramenta de linha de comando **nlserver** instalado no **compartimento** diretório da pasta de instalação.

A sintaxe geral do **nlserver** é a seguinte:

**nlserver `<command>``<command arguments>`**

Para obter a lista de módulos disponíveis, use o **nlserver** comando.

Os módulos disponíveis são detalhados na tabela a seguir:

| Comando | Descrição |
|---|---|
| aliasCleansing | Padronização dos valores de enumeração |
| faturamento | Envio do relatório de atividades do sistema para billing@neolane.net |
| cleanup | Cleansing the database: exclui dados obsoletos do banco de dados e executa uma atualização das estatísticas usadas pelo otimizador do mecanismo de banco de dados. |
| config | Modificando a configuração do servidor |
| exportar | Exportar para linha de comando: permite enviar para a linha de comando um modelo de exportação criado no console do cliente do Adobe Campaign |
| fileconvert | Conversão de um arquivo de tamanho definido |
| importar | Importar para linha de comando: permite enviar para a linha de comando um modelo de importação criado no console do cliente do Adobe Campaign. |
| inMail | Analisador de email de entrada |
| installsetup | Disponibilidade do arquivo de instalação do cliente |
| javascript | Execução de scripts JavaScript, com acesso a APIs SOAP. |
| tarefa | Processamento de linha de comando |
| mesclar | Mesclagem de formulários |
| midSourcing | Recuperação de informações de entrega no modo de mid-sourcing |
| monitor | XML Exibição do status de processos de servidor e tarefas agendadas, por instância. |
| mta | Mensagem de transferência do agente principal |
| pacote | Importação ou exportação de arquivos de pacote de entidade |
| despejo | Exibição dos status do processo do servidor |
| prepareda | Preparação de uma ação de entrega |
| reiniciar | Reinicialização parcial do servidor |
| runwf | Execução de uma instância de fluxo de trabalho |
| desligar | Desligamento completo do sistema |
| sms | Processamento de notificação por SMS |
| sq | Execução de script SQL |
| start | Inícios adicionais |
| stat | Mantém estatísticas de conexão do MTA |
| stop | Desligamento parcial do sistema |
| enviado | Submetendo uma ação de entrega |
| syslogd | Servidor de gravação de log e rastreamento |
| rastreamento | Consolidação e recuperação de logs de rastreamento |
| trackinglogd | Servidor de gravação e limpeza do log de rastreamento |
| watchdog | Instância de inicialização e monitoramento |
| web | Servidor de aplicativos (HTTP e SOAP) |
| wfserver | Servidor de fluxo de trabalho |

>[!IMPORTANT]
>
>Há um último módulo: o módulo de rastreamento e retransmissão vinculado ao servidor de aplicativos que, por motivos de desempenho, é integrado via mecanismos nativos em um servidor Web Apache ou IIS por meio de uma biblioteca dinâmica. Não há nenhum comando do Adobe Campaign que permita iniciar ou administrar esse módulo. Portanto, você deve usar os comandos do próprio servidor Web.

O uso do módulo e a sintaxe de seus parâmetros são exibidos usando o seguinte comando: **nlserver `[module]` -?**

Exemplo:

**Configuração nlserver -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
