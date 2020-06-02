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
translation-type: ht
source-git-commit: 04684fd2933ef19a8ebfd6cbe77e78a34c66ffe3
workflow-type: ht
source-wordcount: '2496'
ht-degree: 100%

---


# Configurações específicas por tipo de banco de dados {#specific-configurations-by-database-type}

Dependendo dos bancos de dados externos que você deseja acessar do Adobe Campaign, você precisará realizar algumas configurações específicas. Essas configurações envolvem basicamente a instalação de drivers e a declaração de variáveis de ambiente pertencentes a cada RDBMS no servidor do Adobe Campaign.

Como regra geral, você precisa instalar a camada de cliente correspondente no banco de dados externo no servidor do Adobe Campaign.

>[!NOTE]
>
>Versões compatíveis são listadas na [Matriz de Compatibilidade do Campaign](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

<!--
## Configure access to Azure Synapse {#configure-access-to-azure-synapse}

### Azure Synapse on CentOS {#azure-centos}

1. Download mysql57-community-release.noarch.rpm. You can find it in this [page](https://dev.mysql.com/downloads/repo/yum).

1. Install the client library:

    ```
    $ yum install mysql57-community-release-el7-9.noarch.rpm
    $ yum install mysql-community-libs
    ```

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

### Azure Synapse on Debian {#azure-debian}

1. Download mysql-apt-config.deb. You can find it in this [page](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

1. Install the client library:

    ```
    $ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
    $ apt update
    $ apt install libmysqlclient20
    ```

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

### Azure Synapse on Windows {#azure-windows}

1. Download the C connector. You can find it in this [page](https://dev.mysql.com/downloads/connector/c).

1. Make sure the directory that contains libmysqlclient.dll is added to the PATH environment variable that nlserver will use.

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

-->

## Configuração do acesso ao Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake]O conector de está disponível para implantações locais e hospedadas. Para obter mais informações, consulte [este artigo](https://helpx.adobe.com/br/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Snowflake no CentOS {#snowflake-centos}

1. Baixe os drivers ODBC para o [!DNL Snowflake]. [Clique aqui](https://sfc-repo.snowflakecomputing.com/br/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) para iniciar o download.
1. Em seguida, é necessário instalar os drivers ODBC no CentOs com o seguinte comando:

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. Após baixar e instalar os drivers ODBC, é necessário reiniciar o Campaign Classic. Para fazer isso, execute o seguinte comando:

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. No Campaign Classic, você pode configurar a conta externa do [!DNL Snowflake]. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Selecione a conta externa do **[!UICONTROL Snowflake]** incorporada.

1. Configure a conta externa do **[!UICONTROL Snowflake]**, você deve especificar:

   * **[!UICONTROL Server]**: URL do servidor [!DNL Snowflake]

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados
   ![](assets/snowflake.png)

1. Clique na guia **[!UICONTROL Parameters]** e depois no botão **[!UICONTROL Deploy functions]** para criar as funções.

   ![](assets/snowflake_2.png)

O conector é compatível com as seguintes opções:

| Opção | Descrição |
|---|---|
| schema de trabalho | schema de banco de dados que deve ser usado para tabelas de trabalho |
| depósito | Nome do depósito padrão que deve ser usado. Ele substituirá o padrão do usuário. |
| TimeZoneName | É vazio por padrão, o que significa que o fuso horário do sistema do servidor de aplicativos Campaign Classic é usado. A opção pode ser usada para forçar o parâmetro da sessão FUSO HORÁRIO. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parâmetro de sessão WEEK_START. Por padrão, defina como 0. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.com/br/sql-reference/parameters.html#week-start). |
| UseCachedResult | Parâmetro de sessão USE_CACHED_RESULTS. Por padrão, defina como VERDADEIRO. Esta opção pode ser usada para desativar os resultados em cache do Snowflake. <br>Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Snowflake no Debian {#snowflake-debian}

1. Baixe os drivers ODBC para o [!DNL Snowflake]. [Clique aqui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) para iniciar o download.

1. Em seguida, é necessário instalar os drivers ODBC no Debian com o seguinte comando:

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. Após baixar e instalar os drivers ODBC, é necessário reiniciar o Campaign Classic. Para fazer isso, execute o seguinte comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. No Campaign Classic, você pode configurar a conta externa do [!DNL Snowflake]. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Selecione a conta externa do **[!UICONTROL Snowflake]** incorporada.

1. Para configurar a conta externa do **[!UICONTROL Snowflake]**, você deve especificar:

   * **[!UICONTROL Server]**: URL do servidor [!DNL Snowflake]

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados
   ![](assets/snowflake.png)

1. Clique na guia **[!UICONTROL Parameters]** e depois no botão **[!UICONTROL Deploy functions]** para criar as funções.

   ![](assets/snowflake_2.png)

O conector é compatível com as seguintes opções:

| Opção | Descrição |
|---|---|
| schema de trabalho | schema de banco de dados que deve ser usado para tabelas de trabalho |
| depósito | Nome do depósito padrão que deve ser usado. Ele substituirá o padrão do usuário. |
| TimeZoneName | É vazio por padrão, o que significa que o fuso horário do sistema do servidor de aplicativos Campaign Classic é usado. A opção pode ser usada para forçar o parâmetro da sessão FUSO HORÁRIO. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parâmetro de sessão WEEK_START. Por padrão, defina como 0.  <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | Parâmetro de sessão USE_CACHED_RESULTS. Por padrão, defina como VERDADEIRO. Esta opção pode ser usada para desativar os resultados em cache do Snowflake. <br>Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Snowflake no Windows {#snowflake-windows}

1. Instale o [driver ODBC para Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Observe que é necessário ter os privilégios de nível de administrador para instalar o driver. Para obter mais informações, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configure o driver ODBC. Para obter mais informações, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. No Campaign Classic, você pode configurar a conta externa do [!DNL Snowflake]. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Selecione a conta externa do **[!UICONTROL Snowflake]** incorporada.

1. Para configurar a conta externa do **[!UICONTROL Snowflake]**, você deve especificar:

   * **[!UICONTROL Server]**: URL do servidor [!DNL Snowflake]

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados
   ![](assets/snowflake.png)

1. Clique na guia **[!UICONTROL Parameters]** e depois no botão **[!UICONTROL Deploy functions]** para criar as funções.

   ![](assets/snowflake_2.png)

O conector é compatível com as seguintes opções:

| Opção | Descrição |
|---|---|---|
| schema de trabalho | schema de banco de dados que deve ser usado para tabelas de trabalho |
| depósito | Nome do depósito padrão que deve ser usado. Ele substituirá o padrão do usuário. |
| TimeZoneName | É vazio por padrão, o que significa que o fuso horário do sistema do servidor de aplicativos Campaign Classic é usado. A opção pode ser usada para forçar o parâmetro da sessão FUSO HORÁRIO. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parâmetro de sessão WEEK_START. Por padrão, defina como 0. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | Por padrão, defina como VERDADEIRO. Esta opção pode ser usada para desativar os resultados em cache do Snowflake (parâmetro de sessão USE_CACHED_RESULTS) <br>Para obter mais informações, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

## Configuração do acesso ao Hadoop 3.0 {#configure-access-to-hadoop-3}

A conexão com um banco de dados externo do Hadoop no FDA exige as seguintes configurações no servidor do Adobe Campaign. Observe que essa configuração está disponível para Windows e Linux.

1. Baixe os drivers ODBC para Hadoop de acordo com a versão do sistema operacional. Os drivers podem ser encontrados [nesta página](https://www.cloudera.com/br/downloads.html).

1. Em seguida, é necessário instalar os drivers ODBC e criar um DSN para a conexão Hive. As instruções podem ser encontradas [nesta página](https://docs.cloudera.com/br/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Após baixar e instalar os drivers ODBC, é necessário reiniciar o Campaign Classic. Para fazer isso, execute o seguinte comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. No Campaign Classic, você pode configurar a conta externa do Snowflake. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clique **[!UICONTROL Create]** e selecione **[!UICONTROL External database]** como tipo de Conta.

1. Para configurar a conta externa do **[!UICONTROL  Hadoop]**, é necessário especificar:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Nome do DNS

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: nome do banco de dados, se não estiver especificado no DSN. Pode ficar em branco, se estiver especificado no DSN

   * **[!UICONTROL Time zone]**: Fuso horário do servidor
   ![](assets/hadoop3.png)

O conector é compatível com as seguintes opções ODBC:

| Nome | Valor |
|---|---|
| ODBCMgr | iODBC |
| depósito | 1/2/4 |

O conector também é compatível com as seguintes opções de Hive:

| Nome | Valor | Descrição |
|---|---|---|
| bulkKey | Azure blob ou chave de acesso do DataLake | Para wasb:// ou wasbs:// carregadores em massa (isto é, se a ferramenta de carregamento em massa inicia com wasb:// ou wasbs://).. <br>É a chave de acesso para blob ou bucket DataLake para carregamento em massa. |
| hdfsPort | número da porta <br>definido por padrão como 8020 | Para carregamento em massa de HDFS (isto é, se a ferramenta de carregamento em massa inicia com webhdfs:// ou webhdfss://). |
| bucketsNumber | 20 | Número de buckets ao criar uma tabela agregada. |
| fileFormat | PARQUET | Formato de arquivo padrão para tabelas de trabalho. |

## Configuração do acesso ao Hadoop 2.1 {#configure-access-to-hadoop}

### Para Windows {#for-windows}

1. Instale os drivers ODBC e [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) para Windows.
1. Crie o DSN (Nome da Fonte de Dados) executando a ferramenta DataSource Administrador ODBC. Um exemplo de DSN de Sistema para Hive é fornecido para você modificar.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Crie a conta externa do Hadoop, conforme detalhado na seção [desta página](../../platform/using/external-accounts.md#hadoop-external-account).

### Para Linux {#for-linux}

1. Instale o unixodbc para Linux.

   ```
   apt-get install unixodbc
   ```

1. Baixe e instale os drivers ODBC para Apache Hive a partir do HortonWorks: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. Verifique o local dos arquivos ODBC.

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. Crie o DSN (Data Source Name) e edite o arquivo odbc.ini. Em seguida, crie um DSN para a conexão do Hive.

   Veja um exemplo do HDInsight para configurar uma conexão chamada &quot;viral&quot;:

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >O parâmetro **UseNativeQuery** é muito importante. O Campaign tem reconhecimento de Hive e não funcionará corretamente, a menos que UseNativeQuery esteja definida. Normalmente, o driver ou o Hive SQL Connector irá reescrever queries e alterar a ordem da coluna.

   A configuração de autenticação depende da configuração Hive/Hadoop. Por exemplo, para o HD Insight, use AuthMech=6 para autenticação de usuário/senha, conforme descrito [aqui](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. Exporte as variáveis.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Instalação de drivers Hortonworks via /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini.

   Você precisa usar UTF-16 para poder se conectar com o Campaign e unix-odbc (libodbcinst).

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. Agora você pode testar sua conexão usando isql.

   ```
   isql vorac
   isql vorac -v
   ```

1. Crie a conta externa do Hadoop, conforme detalhado na seção [desta página](../../platform/using/external-accounts.md#hadoop-external-account).

## Configuração do acesso ao Netezza {#configure-access-to-netezza}

A conexão com um banco de dados externo Netezza no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign.

1. Instale os drivers ODBC do Netezza, de acordo com o sistema operacional que você utiliza:

   * **nz-linuxclient-v7.2.0.0.tar.gz para Linux.** Selecione a pasta que corresponde ao seu sistema operacional (linux ou linux64) e inicie o comando unpack. Você pode deixar a instalação ser executada no repositório sugerido por padrão: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip para Windows.** Descompacte o arquivo e inicie o script executável que corresponde ao seu sistema operacional: nzodbcsetup.exe ou nzodbcsetup64.exe. Siga as instruções do assistente para concluir a instalação dos drivers.

1. Configure o driver ODBC. A configuração pode ser realizada nos arquivos padrão: **/etc/odbc.ini** para parâmetros gerais e **/etc/odbcinst.ini** para declaração de drivers.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; corresponde ao local do arquivo odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Especifique as variáveis de ambiente do servidor do Adobe Campaign:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib e /usr/local/nz/lib64. &quot;/usr/local/nz&quot; corresponde ao repositório de instalação oferecido por padrão ao instalar os drivers. Aqui você precisa especificar o repositório selecionado para a instalação.
   * **ODBCINI**: local do arquivo odbc.ini (por exemplo /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: local do arquivo odbc.ini. Netezza também exige essa segunda variável para utilizar o arquivo odbc.ini.

1. No Campaign Classic, você pode configurar a conta externa do Netezza. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Netezza]**, você deve especificar:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: o URL do servidor Netezza

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados

>[!NOTE]
>
>As operações em schemas que contêm chaves primárias geradas automaticamente não são consideradas.
>
>A tabela utilizará a cláusula **Organizar em** no primeiro índice definido no schema. Como esta cláusula é limitada de 1 até 4 colunas com Netezza, este índice não pode conter mais de 4 colunas.

## Configuração do acesso ao Oracle {#configure-access-to-oracle}

A conexão com um banco de dados externo Oracle no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign:

### Para Linux {#for-linux-1}

1. Instale o cliente completo do Oracle correspondente à sua versão do Oracle.
1. Adicione suas definições de TNS à instalação. Para fazer isso, especifique em um arquivo **tnsnames.ora** no repositório /etc/oracle. Crie o repositório, caso ele não exista.

   Em seguida, crie uma nova variável de ambiente TNS_ADMIN: exporte TNS_ADMIN=/etc/oracle e reinicie a máquina.

1. Integre o Oracle ao seu servidor do Adobe Campaign (nlserver). Para fazer isso, verifique se o arquivo **customer.sh** está na pasta &quot;nl6&quot; da estrutura da árvore do servidor do Adobe Campaign e se inclui os links para as bibliotecas Oracle.

   Por exemplo, para um cliente em 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Esses valores (particularmente ORACLE_HOME) dependem dos repositórios de instalação. Verifique sua estrutura de árvore antes de fazer referência a esses valores.

1. Instale as bibliotecas necessárias para Oracle:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

### Para Windows {#for-windows-1}

1. Instale o software cliente Oracle.
1. Na pasta C:\Oracle, crie um arquivo **tnsnames.ora** contendo sua definição TNS.

   Adicione uma variável de ambiente TNS_ADMIN com C:\Oracle como valor e reinicie o computador.

## Configuração do acesso ao Sybase IQ {#configure-access-to-sybase-iq}

A conexão com um banco de dados externo Sybase IQ no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign:

1. Verifique se o pacote unixodbc está no servidor.
1. Instale o **iq_odbc**. Um erro pode ocorrer no final da instalação. Esse erro pode ser ignorado.
1. Instale o **iq_client_common**. Um erro Java pode ocorrer no final da instalação. Esse erro pode ser ignorado.
1. Configure o driver ODBC. A configuração pode ser realizada nos arquivos padrão: /etc/odbc.ini para parâmetros gerais e /etc/odbcinst.ini para declaração de drivers:

   * **/etc/odbc.ini** (substitua os valores como caracteres `<server_alias>`pelos seus próprios):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Adicione o caminho para a nova biblioteca libodbc16.so na variável LD_LIBRARY_PATH. Para fazer isso:

   * Se você estiver usando um arquivo customer.sh para declarar seu caminho: adicione o caminho /opt/sybase/IQ-16_0/lib64 para a variável LD_LIBRARY_PATH.
   * Caso contrário, use um comando Unix.

1. No Campaign Classic, você pode configurar a conta externa do Sybase IQ. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Sybase IQ]**, você deve especificar:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Corresponde à conexão ODBC (`<server_alias>`) definida na etapa 5. Não é necessariamente o nome do próprio servidor.

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados

>[!NOTE]
>
>Para o Windows, você deve instalar o cliente Sybase IQ no servidor do Adobe Campaign e criar uma conexão ODBC. Crie uma fonte de dados do sistema quando o servidor do Adobe Campaign (nlserver) está em execução como um serviço no Windows.

## Configuração do acesso ao Teradata {#configure-access-to-teradata}

A conexão com um banco de dados externo Teradata no FDA exige determinadas configurações adicionais no servidor do Adobe Campaign. Para obter mais informações sobre como configurar o banco de dados Teradata, consulte este [artigo](https://helpx.adobe.com/br/campaign/kb/campaign_fda_teradata.html).

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

1. No Campaign Classic, você pode configurar a conta externa do Teradata. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Teradata]**, você deve especificar:

   * **[!UICONTROL Type]**: Teradata

   * **[!UICONTROL Server]**: O URL do servidor Teradata

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados

## Configuração do acesso ao SAP HANA {#configure-access-to-sap-hana}

A conexão com um banco de dados externo SAP HANA no FDA exige determinadas configurações adicionais no servidor do Adobe Campaign:

1. Instale os drivers ODBC para SAP HANA, de acordo com o sistema operacional que você usa:

   * **hdb_client_linux.tgz para Linux.** Após descompactado, inicie o comando hdbinst e siga as instruções para finalizar a instalação dos drivers.
   * **hdb_client_windows.zip para Windows.** Descompacte o arquivo e inicie o executável: **hdbinst.exe**. Siga as instruções do assistente para concluir a instalação dos drivers.

1. Configure o driver ODBC. A configuração pode ser realizada nos arquivos padrão: /etc/odbc.ini para parâmetros gerais e /etc/odbcinst.ini para declaração de drivers.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot; corresponde ao local do arquivo **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Especifique as variáveis de ambiente do servidor do Adobe Campaign:

   * **LD_LIBRARY_PATH**: deve incluir o link para o cliente SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) por padrão.
   * **ODBCINI**: local do arquivo odbc.ini (por exemplo /etc/odbc.ini).

1. No Campaign Classic, você pode configurar a conta externa do SAP Hana. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL SAP Hana]**, você deve especificar:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL do servidor SAP Hana

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário
