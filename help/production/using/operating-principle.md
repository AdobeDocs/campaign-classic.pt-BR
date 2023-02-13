---
product: campaign
title: Princípio operacional
description: Princípio operacional
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 30f2451849dec0f640915e81c36d0a9c5f466d6c
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# Princípio operacional{#operating-principle}

![](../../assets/v7-only.svg)

Tecnicamente, a plataforma Adobe Campaign é baseada em vários módulos.

Há muitos módulos Adobe Campaign. Alguns operam continuamente, enquanto outros são iniciados ocasionalmente para executar tarefas administrativas (por exemplo, para configurar a conexão do banco de dados) ou para executar uma tarefa recorrente (por exemplo, consolidando informações de rastreamento).

Existem três tipos de módulos Adobe Campaign:

* Módulos de várias instâncias: um único processo é executado para todas as instâncias. Isso se aplica aos seguintes módulos: **web**, **syslogd**, **trackinglogd** e **vigia** (atividades da **config-default.xml** arquivo ).
* Módulos de instância única: um processo é executado por instância. Isso se aplica aos seguintes módulos: **mta**, **wfserver**, **inMail**, **sms** e **stat** (atividades da **config-`<instance>`.xml** arquivo ).
* Módulos do utilitário: são módulos executados ocasionalmente para executar operações ocasionais ou recorrentes (**cleanup**, **configuração**, download de logs de rastreamento etc.).

A administração do módulo é executada usando a ferramenta de linha de comando **nlserver** instalado no **compartimento** diretório da pasta de instalação.

A sintaxe geral da variável **nlserver** A ferramenta é a seguinte:

**nlserver `<command>``<command arguments>`**

Para obter a lista de módulos disponíveis, use o **nlserver** comando.

Os módulos disponíveis são detalhados na tabela a seguir:

| Comando | Descrição |
|---|---|
| aliasCleansing | Padronização dos valores de enumeração |
| faturamento | Envio do relatório de atividades do sistema para billing@neolane.net |
| cleanup | Limpando o banco de dados: exclui dados obsoletos do banco de dados e executa uma atualização das estatísticas usadas pelo otimizador do mecanismo de banco de dados. |
| configuração | Modificação da configuração do servidor |
| exportar | Exportando para linha de comando: permite enviar para a linha de comando um modelo de exportação criado no console do cliente do Adobe Campaign |
| fileconvert | Conversão de um arquivo de tamanho de conjunto |
| importar | Importando para linha de comando: permite enviar para a linha de comando um modelo de importação criado no console do cliente do Adobe Campaign. |
| inMail | Analisador de email de entrada |
| instalação | Disponibilidade do arquivo de instalação do cliente |
| javascript | Execução de scripts JavaScript, com acesso a APIs SOAP. |
| trabalho | Processamento de linha de comando |
| mesclar | Mesclagem de formulário |
| midSourcing | Recuperação de informações de delivery no modo mid-sourcing |
| monitor | XML Exibição do status de processos de servidor e tarefas agendadas, por instância. |
| mta | Mensagem de transferência do agente principal |
| pacote | Importação ou exportação de arquivos de pacote de entidade |
| pdump | Exibição dos status do processo do servidor |
| preparação | Preparação de uma ação de delivery |
| reiniciar | Reinicialização parcial do servidor |
| runwf | Execução de uma instância de workflow |
| desligamento | Desligamento completo do sistema |
| sms | Processamento de notificação por SMS |
| sql | Execução do script SQL |
| start | Inicializações adicionais |
| stat | Mantém estatísticas de conexão MTA |
| stop | Desligamento parcial do sistema |
| submitda | Envio de uma ação de delivery |
| syslogd | Servidor de registro e gravação de rastreamento |
| rastreamento | Consolidação e recuperação de logs de rastreamento |
| trackinglogd | Servidor de gravação e limpeza do log de rastreamento |
| vigia | Inicialização e instância de monitoramento |
| web | Servidor de aplicativos (HTTP e SOAP) |
| wfserver | Servidor de workflow |

>[!IMPORTANT]
>
>Há um último módulo: o módulo de rastreamento e retransmissão vinculado ao servidor de aplicativos que, por questões de desempenho, é integrado por mecanismos nativos em um servidor Web Apache ou IIS por meio de uma biblioteca dinâmica. Não há um comando do Adobe Campaign que permita iniciar ou administrar esse módulo. Portanto, você deve usar os comandos do próprio servidor da Web.

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
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
