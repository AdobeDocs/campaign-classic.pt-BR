---
solution: Campaign Classic
product: campaign
title: Configuração do acesso ao Teradata
description: Saiba como configurar o acesso ao Teradata no FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 83%

---


# Configuração do acesso ao Teradata {#configure-access-to-teradata}

Use a opção Campanha [Federated Data Acces](../../installation/using/about-fda.md) (FDA) para processar informações armazenadas em bancos de dados externos. Siga as etapas abaixo para configurar o acesso ao Teradata.

1. Instalar e configurar drivers [Teradata](#teradata-config)
1. Configure a [conta externa](#teradata-external) Teradata na Campanha
1. Configurar configuração [](#teradata-additional-configurations) adicional para Teradata e servidor de Campanha

## Configuração teradata {#teradata-config}

É necessário instalar drivers para a Teradata para que a conexão com a Campanha seja implementada.

1. Instale o driver [ODBC para Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   É composto de três pacotes que podem ser instalados no Red Hat (ou no CentOS)/Suse na seguinte ordem:

   * TeraGSS
   * tdicu1510 (instale-o usando setup_wrapper.sh)
   * tdodbc1510 (instale-o usando setup_wrapper.sh)

1. Configure o driver ODBC. A configuração pode ser realizada nos arquivos padrão: **/etc/odbc.ini** para parâmetros gerais e /etc/odbcinst.ini para declaração de drivers:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; corresponde ao local do arquivo **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. Especifique as variáveis de ambiente do servidor do Adobe Campaign:

   * **LD_LIBRARY_PATH**: opt/teradata/client/15.10/lib64 e /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: local do arquivo odbc.ini (por exemplo /etc/odbc.ini).
   * **NLSPATH**: local do arquivo opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>A conexão com um banco de dados externo da Teradata em FDA requer etapas adicionais de configuração no servidor Adobe Campaign. [Saiba mais](#teradata-additional-configurations).


## Conta externa Teradata{#teradata-external}

A conta externa do Teradata permite conectar sua instância do Campaign ao banco de dados externo do Teradata.

1. Na Campanha **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. Para configurar a conta externa do **[!UICONTROL Teradata]**, você deve especificar:

   * **[!UICONTROL Type]**: Escolha o **[!UICONTROL Teradata]** tipo.

   * **[!UICONTROL Server]**: URL ou nome do seu servidor Teradata

   * **[!UICONTROL Account]**: Nome da conta utilizada para acessar o banco de dados Teradata

   * **[!UICONTROL Password]**: Senha utilizada para conectar ao banco de dados Teradata

   * **[!UICONTROL Database]**: Nome da base de dados (opcional)

   * **[!UICONTROL Options]**: Opções a serem passadas pelo Teradata. Use o seguinte formato: &#39;parameter=value&#39;. Use uma semitruna como separador entre valores.

   * **[!UICONTROL Timezone]**: Fuso horário definido no Teradata. [Saiba mais](#timezone)

### Faixas de query

Quando vários usuários do Adobe Campaign se conectam à mesma conta externa FDA do Teradata, a guia **[!UICONTROL Query banding]** permite definir uma faixa de query, ou seja, um conjunto de pares de chave-valor em uma sessão.

![](assets/ext_account_20.png)

Quando essa opção é configurada, cada vez que um usuário Campanha executa um query no banco de dados Teradata, a Adobe Campaign enviará metadados, que consistem em uma lista de chaves, associados a esse usuário. Esses dados podem ser usados pelos administradores do Teradata para fins de auditoria ou para gerenciar direitos de acesso.

>[!NOTE]
>
>Para obter mais informações sobre a **[!UICONTROL Query banding]**, consulte a [documentação do Teradata](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

Para configurar a Query, siga as etapas abaixo:

1. Use the  **[!UICONTROL Default]** to enter a default query band that will be used if a user has no associated query band. Se este campo estiver vazio, os usuários sem faixa de query não poderão utilizar o Teradata.

1. Use the **[!UICONTROL Users]** field to specify a query band for each user. Você pode adicionar quantos pares chave/valor forem necessários, por exemplo, priority=1;workload=high. Se o usuário não tiver nenhuma faixa de query atribuída, o campo **[!UICONTROL Default]** será aplicado.

1. Marque a caixa **[!UICONTROL Active]** para ativar esse recurso

#### Solução de problemas de conta externa {#external-account-troubleshooting}

Se o seguinte erro for exibido durante o teste da conexão **TIM-030008 Data &#39;2&#39;: missing character(s) (iRc=-53)** verifique se o driver ODBC está instalado corretamente e se LD_LIBRARY_PATH (Linux) / PATH (Windows) está definido para o servidor do Campaign.

Erro **ODB-240000 ODBC: [Nome da fonte de dados Microsoft][ODBC Driver Manager] não encontrado e nenhum driver padrão especificado.** ocorre com o Windows se você usar um driver 16.X. O Adobe Campaign espera que o teradata seja nomeados como &#39;{teradata}&#39; em odbcinst.ini.

* A partir da Campanha 18.10, é possível adicionar ODBCDRiverName=&quot;Teradata Database ODBC Driver 16.10&quot; nas opções da conta externa. O número da versão pode mudar; o nome exato pode ser encontrado executando o odbcad32.exe e acessando a guia Drivers.

* Se estiver usando uma versão de Campanha mais antiga, será necessário copiar a seção Teradata de odbcinst.ini criada pela instalação do driver para uma nova seção chamada Teradata. Regedit pode ser usado neste caso. If your base is in latin1, you will have to add **APICharSize=1** in the options.

## Configurações adicionais {#teradata-additional-configurations}

<!--
### Compatibility {#teradata-compatibility}

**Based in Unicode**

| Database version | Driver version |  Minimal Campaign version required |  Note |
|:-:|:-:|:-:|:-:|
| 15  |  15 |  Campaign Classic 17.9 | Under Linux: Queries with timestamp may fail (fixed in build 8937 for 18.4 and 8977 for 18.10) In debug mode, warnings relative to bad memory usage in the driver may occur. |
| 15  | 16  | Campaign Classic 17.9  | Recommended setup for a Teradata 15 database under Linux.  |
|  16 | 16  | Campaign Classic 18.10 |  Unicode characters with surrogate pairs are not fully handled. Using surrogate characters in data should work. Using surrogates in a filtering condition of a query will not work without this change. |
| 16  |  15 |  Campaign Classic 19.0 |  &nbsp; |

**Based in Latin1**

Versions previous to Adobe Campaign Classic 17.9 only supported Teradata Latin-1 database.

Starting from Adobe Campaign Classic 17.9, we now support by default Teradata database in Unicode.

Customers with a Latin-1 Teradata database migrating to a recent Campaign Classic release will have to add the parameter APICharSize=1 in the options of the external account.
-->

### Configuração do usuário {#user-configuration}

Os seguintes direitos são obrigatórios no banco de dados externo: crie/solte/execute procedimentos personalizados, crie/solte/insira/selecione tabelas. Você também pode precisar criar funções de modo de usuário se quiser usar as funções md5 e sha2 na instância do Adobe Campaign.

Configure o fuso horário correto. Ele deve corresponder ao que será definido na conta externa criada na instância do Adobe Campaign.

O Adobe Campaign não definirá um modo de proteção (fallback) nos objetos que ele criará no banco de dados. Talvez seja necessário definir um padrão no usuário que o Adobe Campaign usará para se conectar ao banco de dados Teradata usando o seguinte query:

| desativar fallback padrão |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### Instalação MD5 {#md5-installation}

Se você quiser usar funções md5 na instância do Adobe Campaign, será necessário instalar a função user mode no banco de dados do Teradata nessa [página](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

O sha1 do arquivo baixado é o seguinte: 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Para instalar o md5:

1. Descompacte o arquivo md5_20080530.zip.

1. Vá para o diretório md5/src.

1. Conecte-se ao banco de dados Teradata usando bteq.

1. Execute o seguinte comando bteq:

   ```
   .run file = hash_md5.btq
   ```

### Instalação do SHA2 {#sha2-installation}

Se você quiser usar funções sha2 na instância do Adobe Campaign, será necessário instalar a função user mode no banco de dados do Teradata nessa [página](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

O sha1 do arquivo baixado é o seguinte: e87438d37424836358bd3902cf1adeb629349780.

Para instalar o sha2:

1. Descompacte o arquivo teradata-udf-sha2-1.0.zip.

1. Vá para o diretório teradata-udf-sha2-1.0/src.

1. Conecte-se ao banco de dados Teradata usando bteq.

1. Execute os dois comandos bteq a seguir:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### Instalação UDF_UTF16TO8 {#UDF-UTF16TO8-installation}

Se você quiser usar funções udf_utf16to8 na sua instância do Adobe Campaign, será necessário instalar a função user mode no banco de dados do Teradata com o **kit de ferramentas Teradata unicode** dessa[página](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

O sha1 do arquivo baixado é o seguinte: e58235f434f52c71316a577cb48e20b97d24f470.

Para instalar o udf_utf16to8:

1. Descompacte o arquivo utk_release1.7.0.0.zip.

1. Procure o arquivo udf_utf16to8.o nos arquivos extraídos e navegue até o diretório que contém o arquivo. Ele deve ser chamado utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Conecte-se ao banco de dados Teradata usando bteq.

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
   ```

## Configuração do servidor do Campaign para Linux {#campaign-server-linux}

Para a instalação do driver é necessário:

* Driver Teradata ODBC, que pode ser encontrado nesta [página](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Ferramentas e utilitários Teradata (usados para o carregamento em massa), que podem ser encontrados nesta [página](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Nomes de arquivos e sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Se não houver nenhum pacote para sua distribuição Linux, você poderá instalar conforme explicado em CentOS 7 (por exemplo, usando docker) e em seguida, copiar o conteúdo de /opt/teradata no servidor do Adobe Campaign.

### Instalação do driver ODBC {#odbc-installation}

Para instalar o driver ODBC:

1. Extraia o arquivo tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Vá para o diretório tdodbc1620.

1. Talvez seja necessário corrigir o script de configuração:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Execute setup_wrapper.sh.

### Instalação de ferramentas e utilitários do Teradata {#teradata-tools-installation}

Para instalar ferramentas:

1. Extraia o arquivo TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Vá para o diretório TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Execute setup_wrapper.sh.

1. Vá para o diretório TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Execute setup_wrapper.sh.

1. Vá para o diretório TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Execute setup_wrapper.sh.

1. Um arquivo libtelapi.so deve estar disponível em /opt/teradata/client/16.20/lib64.

## Configuração do servidor do Campaign para Windows {#campaign-server-windows}

Primeiro, é necessário baixar as Ferramentas e utilitários do Teradata para Windows. Você pode baixá-los nesta [página](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Instale o driver ODBC e a Base de transporte paralelo do Teradata. Ele instalará o telapi.dll usado para fazer o carregamento em massa no banco de dados Teradata.

Verifique se o caminho do driver e dos utilitários está na variável PATH que o nlserver terá durante a execução. Por padrão, o caminho é C:\Program Files (x86)\Teradata\Client\15.10\bin em Windows 32 bits ou C:\Program Files\Teradata\Client\15.10\bin em 64 bit).

## Fuso horário {#timezone}

O Teradata usa nomes de fusos horários que não são padrão. Você pode encontrar a lista no [site do Teradata](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). O Adobe Campaign tentará converter o fuso horário fornecido na configuração externa em algo que o Teradata entenda. Se uma correspondência não for encontrada, o fuso horário ausente GMT+X (ou GMT-X) será encontrado para a sessão, com um aviso no log.

A conversão é feita ao ler um arquivo chamado teradata_timezone.txt que deve estar no seguinte diretório datakit: /usr/local/neolane/nl6/datakit em linux. Se você editar esse arquivo, entre em contato com a equipe do Adobe Campaign para fazer a alteração no código fonte; caso contrário, esse arquivo será substituído durante a próxima atualização do Campaign.

O fuso horário usado para conexão será indicado ao executar o nlserver com o switch -verbose, por exemplo:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Se o fuso horário usado não for o correto, uma opção chamada &quot;TimeZoneName&quot; poderá ser adicionada à conta externa. Nesse caso, use o Valor do Teradata, por exemplo &quot;TimeZoneName=Europe Central&quot;.

Ao usar carregamento em massa ou &quot;carregamento rápido&quot; em documentos Teradata, o Campaign não pode indicar o fuso horário. Portanto, é recomendável definir o fuso horário padrão do usuário que o Campaign usará para se conectar:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
