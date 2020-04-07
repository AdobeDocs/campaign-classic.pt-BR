---
title: Acesso a um banco de dados externo
seo-title: Acesso a um banco de dados externo
description: Acesso a um banco de dados externo
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6143f23e05f4528a9d76aece3a6e41165e2f95d4

---


# Direitos de acesso ao banco de dados remoto {#remote-database-access-rights}

Primeiro, para que o usuário possa realizar operações em um banco de dados externo por meio do FDA, esse último deve ter um direito nomeado específico no Adobe Campaign.

1. Select the **[!UICONTROL Administration > Access Management > Named Rights]** node in the Adobe Campaign explorer.
1. Crie um novo direito especificando o rótulo escolhido.
1. O campo **[!UICONTROL Name]** deve ter o seguinte formato **user:base@server**, onde:

   * **user** corresponde ao nome do usuário no banco de dados externo.
   * **base** corresponde ao nome do banco de dados externo.
   * **server** corresponde ao nome do servidor de banco de dados externo.

      >[!NOTE]
      >
      >A parte **:base** é opcional no Oracle.

1. Salve o direito nomeado e o vincule ao usuário escolhido a partir do nó **[!UICONTROL Administration > Access Management > Operators]** do Adobe Campaign Explorer.

Em seguida, para processar os dados contidos em um banco de dados externo, o usuário do Adobe Campaign deve ter pelo menos direitos &quot;Write&quot; no banco de dados. Assim, ele poderá criar worktables. Eles são excluídos automaticamente pelo Adobe Campaign.

Em geral, são necessários os seguintes direitos:

* **CONNECT**: conexão ao banco de dados remoto,
* **READ Data**: acesso somente leitura a tabelas com dados do cliente,
* **READ &#39;MetaData&#39;**: acesso aos catálogos de dados do servidor para obter a estrutura da tabela,
* **LOAD**: carregamento em massa em tabelas de trabalho (necessário ao trabalhar em coleções e associações),
* **CRIAR/SOLTAR** para **TABELA/ÍNDICE/PROCEDIMENTO/FUNÇÃO** (apenas para tabelas de trabalho geradas pelo Adobe Campaign),
* **EXPLAIN** (recomendado): para monitorar desempenhos em caso de problemas,
* **WRITE Data** (dependendo do cenário de integração).

O administrador do banco de dados precisa combinar esses direitos com os direitos específicos de cada mecanismo de banco de dados. Para obter mais informações, consulte a seção abaixo.

## Direitos FDA {#fda-rights}

|   | Floco de neve | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Conexão com o banco de dados remoto** | USO NO WAREHOUSE, USO NO BANCO DE DADOS E USO NOS privilégios DO SCHEMA | Criar um usuário vinculado à conta AWS | privilégio CRIAR SESSÃO | Permissão CONNECT | Privilégio CONNECT | Criar um usuário vinculado a um host remoto que tenha TODOS OS PRIVILÉGIOS |
| **Criação de tabelas** | privilégio CRIAR TABELA NO SCHEMA | CRIAR privilégio | Privilégio CRIAR TABELA | permissão CRIAR TABELA | CRIAR privilégio | CRIAR privilégio |
| **Criação de índices** | N/A | CRIAR privilégio | ÍNDICE ou privilégio CRIAR QUALQUER ÍNDICE | permissão ALTER | CRIAR privilégio | Privilégio INDEX |
| **Criação de funções** | CRIAR FUNÇÃO NO privilégio de SCHEMA | USO EM IDIOMA - privilégio de plug-in para poder chamar scripts python externos | privilégio CRIAR PROCEDIMENTO ou CRIAR QUALQUER PROCEDIMENTO | permissão CRIAR FUNÇÃO | Privilégio de uso | Privilégio CRIAR ROTINA |
| **Criação de procedimentos** | N/A | USO EM IDIOMA - privilégio de plug-in para poder chamar scripts python externos | privilégio CRIAR PROCEDIMENTO ou CRIAR QUALQUER PROCEDIMENTO | permissão CRIAR PROCEDIMENTO | Privilégio de USO (os procedimentos são funções) | Privilégio CRIAR ROTINA |
| **Remoção de objetos (tabelas, índices, funções, procedimentos)** | Propriedade do objeto | Possuir o objeto ou ser um superusuário | SOLTE QUALQUER privilégio &lt; object > | permissão ALTER | Tabela: proprietário da tabela Índice: propriedade da função index: propriedade da função | Privilégio DROP |
| **Monitoramento de execuções** | Privilégio MONITOR no objeto desejado | Nenhum privilégio necessário para usar o comando EXPLAIN | INSERIR e SELECIONAR privilégio e privilégio necessário para executar a instrução em que o PLANO EXPLAIN se baseia | permissão SHOWPLAN | Nenhum privilégio necessário para usar a instrução EXPLAIN | SELECIONAR privilégio |
| **Gravação de dados** | Privilégios INSERT e/ou UPDATE (dependendo da operação de gravação) | Privilégios INSERIR e UPDATE | INSERIR e ATUALIZAR ou INSERIR e ATUALIZAR QUAISQUER privilégios de TABELA | Permissões INSERIR e ATUALIZAR | Privilégios INSERIR e UPDATE | Privilégios INSERIR e UPDATE |
| **Carregamento de dados em tabelas** | CRIAR ETAPA NO SCHEMA, SELECIONAR e INSERIR nos privilégios da tabela do público alvo | SELECIONAR e INSERIR privilégios | SELECIONAR e INSERIR privilégios | INSERIR, ADMINISTRAR OPERAÇÕES EM MASSA e ALTERAR permissões de TABELA | SELECIONAR e INSERIR privilégios | Privilégio de ARQUIVO |
| **Acesso aos dados do cliente** | SELECIONAR em (FUTURO) TABELA(S) ou privilégio(s) de VISUALIZAÇÃO(es) | SELECIONAR privilégio | SELECIONE ou SELECIONE QUALQUER privilégio DE TABELA | SELECIONAR permissão | SELECIONAR privilégio | SELECIONAR privilégio |
| **Acesso aos metadados** | SELECIONAR no privilégio de SCHEMA INFORMATION_SCHEMA | SELECIONAR privilégio | Nenhum privilégio necessário para usar a instrução DESCRIBE | Permissão de DEFINIÇÃO DE VISUALIZAÇÃO | Nenhum privilégio necessário para usar o comando &quot;\d tabela&quot; | SELECIONAR privilégio |

|   | DB2 UDB | TeraData | InfiniDB | IQ do Sybase / ASE do Sybase | Netezza | Greenplum | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Conexão com o banco de dados remoto** | Autoridade CONNECT | Privilégio CONNECT | Criar um usuário vinculado a um host remoto que tenha TODOS OS PRIVILÉGIOS | Nenhuma permissão é necessária para usar a declaração CONNECT | Nenhum privilégio necessário | Privilégio CONNECT | Privilégio CONNECT |
| **Criação de tabelas** | Autoridade CREATETAB | Palavra-chave CRIAR TABELA ou TABELA | CRIAR privilégio | Autoridade de RECURSOS e permissão CRIAR | Privilégio TABELA | CRIAR privilégio | CRIAR privilégio |
| **Criação de índices** | Privilégio INDEX | Palavra-chave CREATE INDEX ou INDEX | Privilégio INDEX | Autoridade de RECURSOS e permissão CRIAR | Privilégio INDEX | CRIAR privilégio | CRIAR privilégio |
| **Criação de funções** | Autoridade IMPLICIT_SCHEMA ou privilégio CREATEIN | Palavra-chave CRIAR FUNÇÃO ou FUNÇÃO | Privilégio CRIAR ROTINA | Autoridade de RECURSOS ou autoridade de DBA para funções Java | privilégio FUNÇÃO | Privilégio de uso | privilégio CRIAR FUNÇÃO |
| **Criação de procedimentos** | Autoridade IMPLICIT_SCHEMA ou privilégio CREATEIN | Palavra-chave CRIAR PROCEDIMENTO ou PROCEDIMENTO | Privilégio CRIAR ROTINA | Autoridade de recursos | Privilégio DE PROCEDIMENTO | Privilégio de uso | privilégio CRIAR FUNÇÃO |
| **Remoção de objetos (tabelas, índices, funções, procedimentos)** | Privilégio DROPIN ou privilégio CONTROL ou proprietário do objeto | DROP &lt; object > ou palavra-chave relacionada a objetos | Privilégio DROP | Propriedade do objeto ou da autoridade do DBA | Privilégio DROP | Propriedade do objeto | Propriedade do objeto |
| **Monitoramento de execuções** | EXPLICAR autoridade | Nenhum privilégio necessário para usar a instrução EXPLAIN | SELECIONAR privilégio | Somente um administrador do sistema pode executar sp_showplan | Nenhum privilégio necessário para usar a instrução EXPLAIN | Nenhum privilégio necessário para usar a instrução EXPLAIN | Nenhum privilégio necessário para usar a instrução EXPLAIN |
| **Gravação de dados** | Privilégios INSERIR e ATUALIZAR ou autoridade DATAACCESS | Privilégios INSERIR e UPDATE | Privilégios INSERIR e UPDATE | Permissões INSERIR e ATUALIZAR | Privilégios INSERIR e UPDATE | Privilégios INSERIR e UPDATE | Privilégios INSERIR e UPDATE |
| **Carregamento de dados em tabelas** | Autoridade de carregamento | SELECIONE e INSIRA privilégios para usar respectivamente as instruções COPIAR PARA e COPIAR DE | Privilégio de ARQUIVO | Seja o proprietário da tabela ou da permissão ALTER. Dependendo da opção -gl, CARREGAR TABELA só poderá ser executado se o usuário tiver a autoridade do DBA | SELECIONAR e INSERIR privilégios | SELECIONAR e INSERIR privilégios | SELECIONAR e INSERIR privilégios |
| **Acesso aos dados do cliente** | Privilégios INSERIR/ATUALIZAR ou autoridade de acesso a dados | SELECIONAR privilégio | SELECIONAR privilégio | SELECIONAR permissão | SELECIONAR privilégio | SELECIONAR privilégio | SELECIONAR privilégio |
| **Acesso aos metadados** | Nenhuma autorização é necessária para usar a declaração DESCRIBE | EXIBIR privilégio | SELECIONAR privilégio | Nenhuma permissão é necessária para usar a instrução DESCRIBE | Nenhum privilégio necessário para usar o comando &quot;\d tabela&quot; | Nenhum privilégio necessário para usar o comando &quot;\d tabela&quot; | Nenhum privilégio necessário para usar o comando SHOW |