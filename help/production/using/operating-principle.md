---
title: Princípio operacional
seo-title: Princípio operacional
description: Princípio operacional
seo-description: null
page-status-flag: never-activated
uuid: a15929ca-5b1f-499a-a883-43fd0a318c98
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 5e9c17ad-14d2-4173-9fc9-0e48a21426c8
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 1%

---


# Princípio operacional{#operating-principle}

Tecnicamente, a plataforma Adobe Campaign é baseada em vários módulos.

Há muitos módulos Adobe Campaign. Alguns operam continuamente, enquanto outros são iniciados ocasionalmente para executar tarefas administrativas (por exemplo, para configurar a conexão do banco de dados) ou para executar uma tarefa recorrente (por exemplo, consolidando informações de rastreamento).

Há três tipos de módulos Adobe Campaign:

* Módulos de várias instâncias: um único processo é executado para todas as instâncias. Isso se aplica aos seguintes módulos: **web**, **syslogd**, **trackinglogd** e **watchdog** (atividade do arquivo **config-default.xml** ).
* Módulos de mono-instância: um processo é executado por instância. Isso se aplica aos seguintes módulos: **mta**, **wfserver**, **inMail**, **sms** e **stat** (atividade do arquivo **`<instance>`** config-.xml).
* Módulos do utilitário: são módulos executados ocasionalmente para executar operações ocasionais ou recorrentes (**limpeza**, **configuração**, download de logs de rastreamento etc.).

A administração do módulo é executada usando a ferramenta de linha de comando **nlserver** instalada no diretório **bin** da pasta de instalação.

A sintaxe geral da ferramenta **nlserver** é a seguinte:

**nlserver `<command>``<command arguments>`**

Para a lista de módulos disponíveis, use o comando **nlserver** .

Os módulos disponíveis são detalhados na tabela a seguir:

| Comando | Descrição |
|---|---|
| aliasCleansing | Padronização dos valores de lista discriminada |
| faturamento | Envio do relatório de atividade do sistema para billing@neolane.net |
| limpeza | Limpeza do banco de dados: exclui dados obsoletos do banco de dados e executa uma atualização das estatísticas usadas pelo otimizador do mecanismo de banco de dados. |
| configuração | Modificando a configuração do servidor |
| base | Cópia de um banco de dados |
| exportação | Exportar para linha de comando: permite enviar para a linha de comando um modelo de exportação criado no console do cliente Adobe Campaign |
| fileconvert | Conversão de um arquivo de tamanho de conjunto |
| importação | Importando para linha de comando: permite enviar para a linha de comando um modelo de importação criado no console do cliente Adobe Campaign. |
| inMail | Analisador de correio de entrada |
| instalação | Disponibilidade do ficheiro de instalação do cliente |
| javascript | Execução de scripts JavaScript, com acesso a APIs SOAP. |
| trabalho | Processamento de linha de comando |
| fusão | Mesclagem de formulário |
| midSourcing | Recuperação de informações sobre o delivery |
| monitor | XML Exibindo o status dos processos do servidor e tarefas programadas, por instância. |
| mta | Mensagem de transferência do agente principal |
| package | Importação ou exportação de arquivos de pacote de entidade |
| pdump | Exibição de status de processo do servidor |
| preparação | Preparação de uma ação de delivery |
| reiniciar | Reinicialização parcial do servidor |
| pântano | Execução de uma instância de fluxo de trabalho |
| desligamento | Encerramento total do sistema |
| sms | Processamento de notificação SMS |
| sql | Execução de script SQL |
| start | Start adicionais |
| stat | Mantém as estatísticas de conexão MTA |
| stop | Desligamento parcial do sistema |
| submitda | Envio de uma ação de delivery |
| syslogd | Servidor de gravação de log e trace |
| rastreamento | Consolidação e recuperação de logs de rastreamento |
| trackinglogd | Rastreamento de gravação e remoção de log do servidor |
| cão de guarda | Instância de inicialização e monitoramento |
| web | Servidor de aplicativos (HTTP e SOAP) |
| wfserver | Servidor de fluxo de trabalho |

>[!IMPORTANT]
>
>Há um último módulo: o módulo de rastreamento e retransmissão vinculado ao servidor de aplicativos que, por questões de desempenho, é integrado por mecanismos nativos em um servidor da Web Apache ou IIS por meio de uma biblioteca dinâmica. Não há comando do Adobe Campaign que permita que você start ou administre este módulo. Portanto, você deve usar os comandos do próprio servidor Web.

O uso do módulo e a sintaxe de seus parâmetros são exibidos usando o seguinte comando: **nlserver `[module]` -?**

Exemplo:

**configuração nlserver -?**

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
-monoinstance : initialises for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```

