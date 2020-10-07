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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 100%

---


# Direitos de acesso ao banco de dados remoto {#remote-database-access-rights}

Primeiro, para que o usuário possa realizar operações em um banco de dados externo por meio do FDA, esse último deve ter um direito nomeado específico no Adobe Campaign.

1. Selecione o nó **[!UICONTROL Administration > Access Management > Named Rights]** no Adobe Campaign Explorer.
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
* **CREATE/DROP** para **TABLE/INDEX/PROCEDURE/FUNCTION** (apenas para tabelas de trabalho geradas pelo Adobe Campaign),
* **EXPLAIN** (recomendado): para monitorar desempenhos em caso de problemas,
* **WRITE Data** (dependendo do cenário de integração).

O administrador do banco de dados precisa combinar esses direitos com os direitos específicos de cada mecanismo de banco de dados. Para obter mais informações, consulte a seção a seguir.

## Direitos FDA {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Conexão com o banco de dados remoto** | Privilégios de USAGE ON WAREHOUSE, USAGE ON DATABASE e USAGE ON SCHEMA | Criar um usuário vinculado à conta AWS | Privilégio CRIAR SESSÃO | Permissão CONECTAR | Privilégio CONECTAR | Criar um usuário vinculado a um host remoto que tenha TODOS OS PRIVILÉGIOS |
| **Criar tabelas** | Privilégio CRIAR TABELA NO SCHEMA | Privilégio CRIAR | Privilégio CRIAR TABELA | Permissão CRIAR TABELA | Privilégio CRIAR | Privilégio CRIAR |
| **Criar índices** | N/D | Privilégio CRIAR | Privilégio ÍNDICE ou CRIAR QUALQUER ÍNDICE | Permissão ALTERAR | Privilégio CRIAR | Privilégio ÍNDICE |
| **Criar funções** | Privilégio CRIAR FUNÇÃO NO SCHEMA | Privilégio plpythonu USO EM IDIOMA para poder chamar scripts python externos | Privilégio CRIAR PROCEDIMENTO ou CRIAR QUALQUER PROCEDIMENTO | Permissão CRIAR FUNÇÃO | Privilégio USO | Privilégio CRIAR ROTINA |
| **Criar procedimentos** | N/D | Privilégio plpythonu USO EM IDIOMA para poder chamar scripts python externos | Privilégio CRIAR PROCEDIMENTO ou CRIAR QUALQUER PROCEDIMENTO | Permissão CRIAR PROCEDIMENTO | Privilégio USO (procedimentos são funções) | Privilégio CRIAR ROTINA |
| **Remover objetos (tabelas, índices, funções, procedimentos)** | Propriedade do objeto | Ter o objeto ou ser um superusuário | Privilégio SOLTAR QUALQUER &lt; object > | Permissão ALTERAR | Tabela: proprietário da tabela Índice: propriedade da Função índice: propriedade da função | Privilégio SOLTAR  |
| **Monitoramento de execuções** | Privilégio MONITORAR no objeto necessário | Não é necessário nenhum privilégio para usar o comando EXPLICAR | Privilégio INSERIR e SELECIONAR e o que é necessário para executar a instrução em que o PLANO DE EXPLICAR se baseia | Permissão MOSTRAR O PLANO | Não é necessário nenhum privilégio para usar a instrução EXPLICAR | Privilégio SELECIONAR |
| **Gravação de dados** | Privilégios INSERIR e/ou ATUALIZAR (que depende da operação de gravação) | Privilégios INSERIR e ATUALIZAR | Privilégios INSERIR e ATUALIZAR ou INSERIR e ATUALIZAR QUALQUER TABELA | Permissões INSERIR e ATUALIZAR | Privilégios INSERIR e ATUALIZAR | Privilégios INSERIR e ATUALIZAR |
| **Carregamento de dados em tabelas** | Privilégios CRIAR ETAPA NO SCHEMA, SELECIONAR e INSERIR na tabela do direcionamento | Privilégios SELECIONAR e INSERIR | Privilégios SELECIONAR e INSERIR | Permissões INSERIR, ADMINISTRAR OPERAÇÕES EM MASSA e ALTERAR TABELA | Privilégios SELECIONAR e INSERIR | Privilégio ARQUIVAR |
| **Acesso aos dados do cliente** | Privilégio(s) SELECIONAR em (FUTURO) TABELA(S) ou VISUALIZAÇÃO(es) | Privilégio SELECIONAR | Privilégio SELECIONAR ou SELECIONAR QUALQUER TABELA | Permissão SELECIONAR  | Privilégio SELECIONAR | Privilégio SELECIONAR |
| **Acesso aos metadados** | Privilégio SELECIONAR no ESQUEMA de INFORMATION_SCHEMA | Privilégio SELECIONAR | Não é necessário nenhum privilégio para usar a instrução DESCREVER | Permissão DEFINIÇÃO DE VISUALIZAÇÃO | Não é necessário nenhum privilégio para usar o comando &quot;\d table&quot; | Privilégio SELECIONAR |

|   | DB2 UDB | Teradata | InfiniDB | Sybase IQ / Sybase ASE | Netezza | Greenplum | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Conexão com o banco de dados remoto** | Autoridade CONECTAR | Privilégio CONECTAR | Criar um usuário vinculado a um host remoto que tenha TODOS OS PRIVILÉGIOS | Não é necessário nenhuma permissão para usar a declaração CONECTAR. | Não é necessário nenhum privilégio | Privilégio CONECTAR | Privilégio CONECTAR |
| **Criar tabelas** | Autoridade CRIAR TABELA | Palavra-chave CRIAR TABELA ou TABELA | Privilégio CRIAR | Autoridade RECURSOS e a permissão CRIAR | Privilégio TABELA | Privilégio CRIAR | Privilégio CRIAR |
| **Criar índices** | Privilégio ÍNDICE | Palavra-chave CRIAR ÍNDICE ou ÍNDICE | Privilégio ÍNDICE | Autoridade RECURSOS e a permissão CRIAR | Privilégio ÍNDICE | Privilégio CRIAR | Privilégio CRIAR |
| **Criar funções** | Autoridade ESQUEMA_IMPLÍCITO ou privilégio CRIAR EM | Palavra-chave CRIAR FUNÇÃO ou FUNÇÃO | Privilégio CRIAR ROTINA | Autoridade RECURSOS ou autoridade DBA para funções Java | Privilégio FUNÇÃO | Privilégio USO | Privilégio CRIAR FUNÇÃO |
| **Criar procedimentos** | Autoridade ESQUEMA_IMPLÍCITO ou privilégio CRIAR EM | Palavra-chave CRIAR PROCEDIMENTO ou PROCEDIMENTO | Privilégio CRIAR ROTINA | Autoridade RECURSOS | Privilégio PROCEDIMENTO | Privilégio USO | Privilégio CRIAR FUNÇÃO |
| **Remover objetos (tabelas, índices, funções, procedimentos)** | Privilégio SOLTAR ou privilégio CONTROLE ou proprietário do objeto | SOLTAR &lt; object > ou a palavra-chave relacionada a objetos | Privilégio SOLTAR  | Propriedade do objeto ou da autoridade do DBA | Privilégio SOLTAR | Propriedade do objeto | Propriedade do objeto |
| **Monitoramento de execuções** | Autoridade EXPLICAR | Não é necessário nenhum privilégio para usar a instrução EXPLICAR | Privilégio SELECIONAR | Somente um administrador do sistema pode executar o sp_showplan | Não é necessário nenhum privilégio para usar a instrução EXPLICAR | Não é necessário nenhum privilégio para usar a instrução EXPLICAR | Não é necessário nenhum privilégio para usar a instrução EXPLICAR |
| **Gravação de dados** | Privilégios INSERIR e ATUALIZAR ou autoridade ACESSO AOS DADOS | Privilégios INSERIR e ATUALIZAR | Privilégios INSERIR e ATUALIZAR | Permissões INSERIR e ATUALIZAR | Privilégios INSERIR e ATUALIZAR | Privilégios INSERIR e ATUALIZAR | Privilégios INSERIR e ATUALIZAR |
| **Carregamento de dados em tabelas** | Autoridade CARREGAMENTO | Privilégios SELECIONAR e INSERIR para usar as instruções COPIAR PARA e COPIAR DE respectivamente | Privilégio ARQUIVAR | Seja o proprietário da tabela ou da permissão ALTERAR. Dependendo da opção -gl, CARREGAR TABELA só pode ser executado se o usuário tiver a autoridade do DBA | Privilégios SELECIONAR e INSERIR | Privilégios SELECIONAR e INSERIR | Privilégios SELECIONAR e INSERIR |
| **Acesso aos dados do cliente** | Privilégios INSERIR/ATUALIZAR ou autoridade ACESSO AOS DADOS | Privilégio SELECIONAR | Privilégio SELECIONAR | Permissão SELECIONAR | Privilégio SELECIONAR | Privilégio SELECIONAR | Privilégio SELECIONAR |
| **Acesso aos metadados** | Não é necessário nenhuma autorização para usar a instrução DESCREVER | Privilégio MOSTRAR | Privilégio SELECIONAR | Não é necessária nenhuma permissão para usar a instrução DESCREVER | Não é necessário nenhum privilégio para usar o comando &quot;\d table&quot; | Não é necessário nenhum privilégio para usar o comando &quot;\d table&quot; | Não é necessário nenhum privilégio para usar o comando MOSTRAR |