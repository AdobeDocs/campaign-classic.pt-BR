---
title: Apêndices
seo-title: Apêndices FDA
description: Apêndices FDA
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 353f5df040087175c9f211308704f1af1844ef2c
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 1%

---


# Apêndices {#fda-appendices}

## Configurações adicionais do Teradata {#teradata-configuration}

### Compatibilidade {#teradata-compatibility}

**Baseado em Unicode**

| Versão do banco de dados | Versão do driver | Versão mínima de Campanha necessária | Observação |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | Em Linux: Query com carimbo de data e hora podem falhar (corrigidos na compilação 8937 para 18.4 e 8977 para 18.10) No modo de depuração, podem ocorrer avisos relativos ao uso de memória ruim no driver. |
| 15 | 16 | Campaign Classic 17.9 | Configuração recomendada para um banco de dados Teradata 15 no Linux. |
| 16 | 16 | Campaign Classic 18.10 | Caracteres Unicode com pares substitutos não são totalmente manipulados. O uso de caracteres substitutos nos dados deve funcionar. O uso de substitutos em uma condição de filtragem de um query não funcionará sem essa alteração. |
| 16 | 15 | não suportado |   |

**Baseado em Latim1**

As versões anteriores ao Adobe Campaign Classic 17.9 só suportavam o banco de dados Teradata Latin-1.

A partir do Adobe Campaign Classic 17.9, agora oferecemos suporte por padrão ao banco de dados Teradata em Unicode.

Os clientes com um banco de dados Latin-1 Teradata migrando para uma versão recente do Campaign Classic terão que adicionar o parâmetro APICharSize=1 nas opções da conta externa.

### Configuração do banco de dados {#database-configuration}

#### Configuração do usuário {#user-configuration}

Os seguintes direitos são obrigatórios: crie/solte/execute procedimentos personalizados, crie/solte/insira/selecione tabelas. Você também pode precisar criar funções de modo de usuário se quiser usar as funções md5 e sha2 na instância do Adobe Campaign.

Certifique-se de configurar o fuso horário correto. Deve corresponder ao que será definido na conta externa criada na instância Adobe Campaign.

O Adobe Campaign não definirá um modo de proteção (fallback) nos objetos que ele criará no banco de dados. Talvez seja necessário definir um padrão no usuário que o Adobe Campaign usará para se conectar ao banco de dados Teradata usando o seguinte query:

| desativar fallback padrão |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### Instalação MD5 {#md5-installation}

Se você quiser usar funções md5 na instância do Adobe Campaign, será necessário instalar a função user mode no banco de dados do Teradata a partir desta [página](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

O sha1 do arquivo baixado é o seguinte: 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Para instalar o md5:

1. Descompacte o arquivo md5_20080530.zip.

1. Vá para o diretório md5/src.

1. Conecte-se ao seu banco de dados Teradata usando bteq.

1. Execute o seguinte comando bteq:

   ```
   .run file = hash_md5.btq
   ```

#### Instalação do SHA2 {#sha2-installation}

Se você quiser usar funções sha2 na instância do Adobe Campaign, será necessário instalar a função user mode no banco de dados do Teradata a partir desta [página](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

O sha1 do arquivo baixado é o seguinte: e87438d37424836358bd3902cf1adeb629349780.

Para instalar o sha2:

1. Descompacte o arquivo teradata-udf-sha2-1.0.zip.

1. Vá para o diretório teradata-udf-sha2-1.0/src.

1. Conecte-se ao seu banco de dados Teradata usando bteq.

1. Execute os dois comandos bteq a seguir:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### Instalação UDF_UTF16TO8 {#UDF-UTF16TO8-installation}

Se você quiser usar funções udf_utf16to8 na sua instância do Adobe Campaign, será necessário instalar a função user mode no banco de dados do Teradata a partir do kit **de ferramentas unicode** Teradata desta [página](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

O sha1 do arquivo baixado é o seguinte: e58235f434f52c71316a577cb48e20b97d24f470.

Para instalar o udf_utf16to8:

1. Descompacte o arquivo utk_release1.7.0.0.zip.

1. Procure o arquivo udf_utf16to8.o nos arquivos extraídos e navegue até o diretório que contém o arquivo. Deve ser nomeado utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Conecte-se ao seu banco de dados Teradata usando bteq.

1. Digite o seguinte comando bteq:

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   
### Configuração do servidor de Campanha para Linux {#campaign-server-linux}

O seguinte é necessário para a instalação do driver:

* Driver do Teradata ODBC, que pode ser encontrado nesta [página](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Ferramentas e utilitários Teradata (usados para o carregamento em massa), que podem ser encontrados nesta [página](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Nomes de arquivos e sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f 44 fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Se não houver nenhum pacote para sua distribuição Linux, você poderá instalar conforme explicado em um CentOS 7 (por exemplo, usando o docker) e, em seguida, copiar o conteúdo de /opt/teradata em seu servidor Adobe Campaign.

#### Instalação do driver ODBC {#odbc-installation}

Para instalar o driver ODBC:

1. Extraia o arquivo tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Vá para o diretório tdodbc1620.

1. Talvez seja necessário corrigir o script de configuração:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Execute setup_wrapper.sh.

#### Instalação de ferramentas e utilitários do Teradata {#teradata-tools-installation}

Para instalar Ferramentas:

1. Extraia o arquivo TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Vá para o diretório TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Execute setup_wrapper.sh.

1. Vá para o diretório TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Execute setup_wrapper.sh.

1. Vá para o diretório TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Execute setup_wrapper.sh.

1. Um arquivo libtelapi.so deve estar disponível em /opt/teradata/client/16.20/lib64.

#### Configuração do driver {#driver-configuration}

Para saber mais sobre a configuração do driver, consulte esta [seção](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### Variáveis de Ambiente {#environment-varaiables}

Para saber mais sobre as variáveis de ambiente do servidor Adobe Campaign, consulte esta [seção](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

### Configuração do servidor de Campanha para Windows #campanha-server-windows}

Primeiro, é necessário baixar as Ferramentas e utilitários Teradata para Windows. Você pode baixá-lo desta [página](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Instale o driver ODBC e a Base de Transporte Paralelo Teradata. Ele instalará o telapi.dll usado para fazer carregamento em massa no banco de dados Teradata.

Verifique se o caminho do driver e dos utilitários está na variável PATH que o nlserver terá durante a execução. Por padrão, o caminho é C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Programa Files\Teradata\Client\15.10\bin on 64 bit).

### Solução de problemas de Conta externa {#external-account-troubleshooting}

Se o seguinte erro for exibido durante o teste da conexão **TIM-030008 Data &#39;2&#39;: caractere(s) ausente(s) (iRc=-53)** certifique-se de que o driver ODBC esteja instalado corretamente e que LD_LIBRARY_PATH (Linux) / PATH (Windows) esteja definido para o servidor de Campanha.

Erro **ODB-240000 ODBC:[Nome da fonte de dados Microsoft][ODBC Driver Manager]não encontrado e nenhum driver padrão especificado.** ocorre com o Windows se você usar um driver 16.X. Adobe Campaign espera que os teradata sejam nomeados como &#39;{teradata}&#39; em odbcinst.ini.
Se você tiver uma versão de servidor 18.10 Adobe Campaign, poderá adicionar ODBCDRiverName=&quot;Teradata Database ODBC Driver 16.10&quot; nas opções da conta externa. O número da versão pode ser alterado, o nome exato pode ser encontrado executando o odbcad32.exe e acessando a guia Drivers.
Para a versão abaixo de 18.10, é necessário copiar a seção Teradata de odbcinst.ini criada pela instalação do driver para uma nova seção chamada Teradata; neste caso, o regedit pode ser usado.

Se sua base estiver em latin1, você terá que adicionar APICharSize=1 nas opções.

### Fuso horário {#timezone}

Os Teradata usam nomes de fuso horário que não são padrão, você pode encontrar a lista no site [](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA)Teradata. O Adobe Campaign tentará converter o fuso horário fornecido na configuração externa em algo que o Teradata entenda. Se uma correspondência não for encontrada, o fuso horário do closet GMT+X (ou GMT-X) será encontrado para a sessão, com um aviso no registro.

A conversão é feita ao ler um arquivo chamado teradata_timezone.txt que deve estar no seguinte diretório de datakit: /usr/local/neolane/nl6/datakit em linux. Se você editar esse arquivo, entre em contato com a equipe do Adobe Campaign para fazer a alteração no código fonte; caso contrário, esse arquivo será substituído durante a próxima atualização da Campanha.

O fuso horário usado para conexão será indicado ao executar o nlserver com o switch -verbose, por exemplo:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Se o fuso horário usado não for o correto, uma opção chamada &quot;TimeZoneName&quot; pode ser adicionada à conta externa. Nesse caso, use o Valor Teradata, por exemplo &quot;TimeZoneName=Europe Central&quot;.

Ao usar carga em massa ou &quot;carga rápida&quot; em documentos Teradata, a Campanha não indica o fuso horário. Portanto, é recomendável definir o fuso horário padrão do usuário que a Campanha usará para se conectar:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## Configuração do MySQL 5.7 {#mysql-57-configuration}

### Configuração do servidor {#server-configuration-mysql}

A configuração do servidor não requer nenhuma etapa de instalação específica. O Adobe Campaign deve funcionar com um banco de dados latin1, padrão no MySQL ou unicode.

### Instalação do driver {#driver-installation-mysql}

#### Debian {#debian-mysql}

Baixe mysql-apt-config.deb desta [página](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

Instale a biblioteca do cliente:

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows [#windows-mysql}

Baixe o conector C desta [página](https://dev.mysql.com/downloads/connector/c). Recomendamos baixar a versão 5.7.

Verifique se o diretório que contém libmysqlclient.dll foi adicionado à variável de ambiente PATH que o nlserver usará.

#### CentOS {#centos-mysql}

Baixe mysql57-community-release.noarch.rpm desta [página](https://dev.mysql.com/downloads/repo/yum).

Instale a biblioteca do cliente:

$ yum install mysql57-community-release-el7-9.noarch.rpm$ yum install mysql-community-libs

### configuração da Conta externa {#external-account-mysql}

A configuração da conta externa não requer etapas específicas. Verifique se o fuso horário e Usar dados unicode estão definidos de acordo com o banco de dados.
