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
source-git-commit: a0698ad55afb391bdc652a00b43b20df6fb9851b

---


# Configurações específicas por tipo de banco de dados {#specific-configurations-by-database-type}

Dependendo dos bancos de dados externos que você deseja acessar do Adobe Campaign, você precisará realizar algumas configurações específicas. Essas configurações envolvem basicamente a instalação de drivers e a declaração de variáveis de ambiente pertencentes a cada RDBMS no servidor do Adobe Campaign.

Como regra geral, você precisa instalar a camada de cliente correspondente no banco de dados externo no servidor do Adobe Campaign.

>[!NOTE]
>
>Versões compatíveis são listadas na [Matriz de Compatibilidade do Campaign](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

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

## Configurar acesso ao Floco de neve {#configure-access-to-snowflake}

>[!NOTE]
>
>O conector de floco de neve está disponível para implantações locais e hospedadas. Para obter mais informações, consulte esta [página](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Floco de neve no CentOS {#snowflake-centos}

1. Baixe os drivers ODBC para Floco de neve. Drivers para Floco de neve podem ser encontrados [aqui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm).

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
1. No Campaign Classic, configure sua conta externa Snowflake no Campaign Classic. A partir do **[!UICONTROL Explorer]**, desenrole o **[!UICONTROL Administration]** menu.

1. Desdobre o **[!UICONTROL Platform]** menu e clique em **[!UICONTROL External accounts]**.

1. Selecione a conta externa pronta para uso. **[!UICONTROL Snowflake]**

1. To configure the **[!UICONTROL Snowflake]** external account:

   * **[!UICONTROL Server]**

      URL do servidor Snowflake.

   * **[!UICONTROL Account]**

      Nome do usuário.

   * **[!UICONTROL Password]**

      Senha da conta do usuário.

   * **[!UICONTROL Database]**

      Nome do banco de dados.
   ![](assets/snowflake.png)

1. Clique na **[!UICONTROL Parameters]** guia e no **[!UICONTROL Deploy function]** botão para criar funções.

   ![](assets/snowflake_2.png)

O conector suporta as seguintes opções:

| Opção | Valor | Descrição |
|---|---|---|
| esquema de trabalho |  | Esquema de banco de dados a ser usado para tabelas de trabalho |
| depósito |  | Nome do depósito padrão a ser usado. Isso substituirá o padrão do usuário. |
| TimeZoneName |  | Por padrão vazio, o que significa que o fuso horário do sistema do servidor de aplicativos do Campaign Classic é usado. A opção pode ser usada para forçar o parâmetro de sessão TIMEZONE. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | 0, 1-7 | Por padrão, defina como 0. (Parâmetro de sessão WEEK_START) <br>Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | TRUE/FALSE | Por padrão, defina como TRUE. Esta opção pode ser usada para desativar os resultados em cache do Floco de neve (parâmetro de sessão USE_CACHED_RESULTS) <br>Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Floco de neve em Debian {#snowflake-debian}

1. Baixe os drivers ODBC para Floco de neve. Drivers para Floco de neve podem ser encontrados [aqui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html).

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

1. No Campaign Classic, configure sua conta externa Snowflake no Campaign Classic. A partir do **[!UICONTROL Explorer]**, desenrole o **[!UICONTROL Administration]** menu.

1. Desdobre o **[!UICONTROL Platform]** menu e clique em **[!UICONTROL External accounts]**.

1. Selecione a conta externa pronta para uso. **[!UICONTROL Snowflake]**

1. To configure the **[!UICONTROL Snowflake]** external account:

   * **[!UICONTROL Server]**

      URL do servidor Snowflake.

   * **[!UICONTROL Account]**

      Nome do usuário.

   * **[!UICONTROL Password]**

      Senha da conta do usuário.

   * **[!UICONTROL Database]**

      Nome do banco de dados
   ![](assets/snowflake.png)

1. Clique na **[!UICONTROL Parameters]** guia e no **[!UICONTROL Deploy function]** botão para criar funções.

   ![](assets/snowflake_2.png)

O conector suporta as seguintes opções:

| Opção | Valor | Descrição |
|---|---|---|
| esquema de trabalho |   | Esquema de banco de dados a ser usado para tabelas de trabalho |
| depósito |   | Nome do depósito padrão a ser usado. Isso substituirá o padrão do usuário. |
| TimeZoneName |   | Por padrão vazio, o que significa que o fuso horário do sistema do servidor de aplicativos do Campaign Classic é usado. A opção pode ser usada para forçar o parâmetro de sessão TIMEZONE. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | 0, 1-7 | Por padrão, defina como 0. (Parâmetro de sessão WEEK_START) <br>Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | TRUE/FALSE | Por padrão, defina como TRUE. Esta opção pode ser usada para desativar os resultados em cache do Floco de neve (parâmetro de sessão USE_CACHED_RESULTS) <br>Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Floco de neve no Windows {#snowflake-windows}

1. Baixe o driver [ODBC para Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Observe que você precisa de privilégios de nível de administrador para instalar o driver. Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configure o driver ODBC. Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. Depois que o driver ODBC for instalado e configurado, será necessário configurar sua conta externa do Floco de neve no Campaign Classic. A partir do **[!UICONTROL Explorer]**, desenrole o **[!UICONTROL Administration]** menu.

1. Desdobre o **[!UICONTROL Platform]** menu e clique em **[!UICONTROL External accounts]**.

1. Selecione a conta externa pronta para uso. **[!UICONTROL Snowflake]**

1. To configure the **[!UICONTROL Snowflake]** external account:

   * **[!UICONTROL Server]**

      URL do servidor Snowflake.

   * **[!UICONTROL Account]**

      Nome do usuário.

   * **[!UICONTROL Password]**

      Senha da conta do usuário.

   * **[!UICONTROL Database]**

      Nome do banco de dados
   ![](assets/snowflake.png)

1. Clique na **[!UICONTROL Parameters]** guia e no **[!UICONTROL Deploy function]** botão para criar funções.

   ![](assets/snowflake_2.png)

O conector suporta as seguintes opções:

| Opção | Valor | Descrição |
|---|---|---|
| esquema de trabalho |   | Esquema de banco de dados a ser usado para tabelas de trabalho |
| depósito |   | Nome do depósito padrão a ser usado. Isso substituirá o padrão do usuário. |
| TimeZoneName |   | Por padrão vazio, o que significa que o fuso horário do sistema do servidor de aplicativos do Campaign Classic é usado. A opção pode ser usada para forçar o parâmetro de sessão TIMEZONE. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | 0, 1-7 | Por padrão, defina como 0. (Parâmetro de sessão WEEK_START) <br>Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | TRUE/FALSE | Por padrão, defina como TRUE. Esta opção pode ser usada para desativar os resultados em cache do Floco de neve (parâmetro de sessão USE_CACHED_RESULTS) <br>Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

## Configure access to Hadoop 3.0 {#configure-access-to-hadoop-3}

A conexão com um banco de dados externo do Hadoop no FDA requer as seguintes configurações no servidor do Adobe Campaign. Observe que essa configuração está disponível para Windows e Linux.

1. Baixe os drivers ODBC para Hadoop, dependendo da versão do sistema operacional. Os drivers podem ser encontrados nesta [página](https://www.cloudera.com/downloads.html).

1. Em seguida, é necessário instalar os drivers ODBC e criar um DSN para sua conexão Hive. A instrução pode ser encontrada [aqui](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Após baixar e instalar os drivers ODBC, é necessário reiniciar o Campaign Classic. Para fazer isso, execute o seguinte comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. No Campaign Classic, configure sua conta externa do Hadoop no Campaign Classic. A partir do **[!UICONTROL Explorer]**, desenrole o **[!UICONTROL Administration]** menu.

1. Desdobre o **[!UICONTROL Platform]** menu e clique em **[!UICONTROL External accounts]**.

1. Clique **[!UICONTROL Create]** e selecione **[!UICONTROL External database]** como Tipo de conta.

1. To configure the **[!UICONTROL  Hadoop]** external account:

   * **[!UICONTROL Type]**

      ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**

      Nome do DNS.

   * **[!UICONTROL Account]**

      Nome do usuário.

   * **[!UICONTROL Password]**

      Senha da conta do usuário.

   * **[!UICONTROL Database]**

      Nome do banco de dados se não for especificado no DSN. Pode ser deixado em branco se especificado no DSN.

   * **[!UICONTROL Time zone]**

      Fuso horário do servidor
   ![](assets/hadoop3.png)

O conector suporta as seguintes opções ODBC:

| Nome | Valor |
|---|---|
| ODBCMgr | iODBC |
| depósito | 1/2/4 |

O conector também suporta as seguintes opções de Colmeia:

| Nome | Valor | Descrição |
|---|---|---|
| globalKey | Blob do Azure ou chave de acesso do DataLake | Para wasb:// ou wasbs:// carregadores em massa (isto é, se a ferramenta de carregamento em massa começar com wasb:// ou wasbs://). <br>É a chave de acesso para blob ou bucket DataLake para carregamento em massa. |
| hdfsPort | número da porta <br>definido por padrão como 8020 | Para carregamento em massa de HDFS (isto é, se a ferramenta de carregamento em massa começar com webhdfs:// ou webhdfss://). |
| bucketsNumber | 20 | Número de compartimentos ao criar uma tabela clusterizada. |
| fileFormat | PARQUET | Formato de arquivo padrão para tabelas de trabalho. |

## Configure access to Hadoop 2.1 {#configure-access-to-hadoop}

For more information on how to configure your Hadoop external database in FDA, refer to this [article](https://helpx.adobe.com/campaign/kb/access-hadoop-2.html).

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

1. Crie a conta externa do Hadoop, conforme detalhado na seção [Criação de uma conexão](#creating-a-shared-connection) compartilhada.

### Para Linux {#for-linux}

1. Instale o unixodbc para Linux.

   ```
   apt-get install unixodbc
   ```

1. Download and install ODBC drivers for Apache Hive from HortonWorks: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

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

   A configuração de autenticação depende da configuração Hive/Hadoop. Por exemplo, para o HD Insight, use AuthMech=6 para autenticação de usuário/senha, conforme descrito [aqui](http://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

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

1. Crie a conta externa do Hadoop, conforme detalhado na seção [Criação de uma conexão](#creating-a-shared-connection) compartilhada.

## Configuração do acesso ao Netezza {#configure-access-to-netezza}

A conexão com um banco de dados externo Netezza no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign.

1. Instale os drivers ODBC do Netezza, de acordo com o sistema operacional que você utiliza:

   * **nz-linuxclient-v7.2.0.0.tar.gz para Linux.** Selecione a pasta que corresponde ao seu sistema operacional (linux ou linux64) e inicie o comando unpack. Você pode deixar a instalação a ser realizada no repositório sugerido por padrão: &quot;/usr/local/nz&quot;.
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
   * **ODBCINI**: local do arquivo odbc.ini (por exemplo, /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: localização do arquivo odbc.ini. Netezza também exige essa segunda variável para utilizar o arquivo odbc.ini.

1. Crie a conta externa do Netezza, conforme detalhado na seção [Criação de uma conexão](#creating-a-shared-connection) compartilhada.

>[!NOTE]
>
>As operações em schemas que contêm chaves primárias geradas automaticamente não são consideradas.
>
>A tabela utilizará a cláusula **Organizar em** no primeiro índice definido no schema. Como esta cláusula é limitada de 1 até 4 colunas com Netezza, este índice não pode conter mais de 4 colunas.

## Configuração do acesso ao Oracle {#configure-access-to-oracle}

A conexão com um banco de dados externo Oracle no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign:

### Para Linux {#for-linux-1}

1. Instale o cliente completo do Oracle correspondente à sua versão do Oracle.
1. Adicione suas definições de TNS à instalação. To do this, specify them in a **tnsnames.ora** file in the /etc/oracle repository. Crie o repositório, caso ele não exista.

   Em seguida, crie uma nova variável de ambiente TNS_ADMIN: exporte TNS_ADMIN=/etc/oracle e reinicie a máquina.

1. Integre o Oracle ao seu servidor do Adobe Campaign (nlserver). To do this, check that the **customer.sh** file is present in the &quot;nl6&quot; folder of the Adobe Campaign server tree structure and that it includes the links to the Oracle libraries.

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
1. In the C:Oracle folder, create a **tnsnames.ora** file containing your TNS definition.

   Adicione uma variável de ambiente TNS_ADMIN com C:Oracle como valor e reinicie a máquina.

## Configuração do acesso ao Sybase IQ {#configure-access-to-sybase-iq}

A conexão com um banco de dados externo Sybase IQ no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign:

1. Verifique se o pacote unixodbc está no servidor.
1. Instale o **iq_odbc**. Um erro pode ocorrer no final da instalação. Esse erro pode ser ignorado.
1. Instale o **iq_client_common**. Um erro Java pode ocorrer no final da instalação. Esse erro pode ser ignorado.
1. Configure o driver ODBC. A configuração pode ser realizada nos arquivos padrão: /etc/odbc.ini para parâmetros gerais e /etc/odbcinst.ini para declaração de drivers:

   * **/etc/odbc.ini** (substitua valores como `<server_alias>` caracteres por seus):

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

1. Crie uma nova conta externa FDA, conforme descrito na seção [Criação de uma conexão](#creating-a-shared-connection) compartilhada. For Sybase IQ, the server name corresponds to the ODBC connection (`<server_alias>`) defined in step 5. Não é necessariamente o nome do próprio servidor.

>[!NOTE]
>
>Para o Windows, você deve instalar o cliente Sybase IQ no servidor do Adobe Campaign e criar uma conexão ODBC. Certifique-se de criar uma fonte de dados do sistema quando o servidor do Adobe Campaign (nlserver) estiver sendo executado como um serviço no Windows.

## Configuração do acesso ao Teradata {#configure-access-to-teradata}

A conexão com um banco de dados externo Teradata no FDA exige determinadas configurações adicionais no servidor do Adobe Campaign. Para obter mais informações sobre como configurar o banco de dados Teradata, consulte este [artigo](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html).

1. Instale o driver [ODBC para Teradata](http://downloads.teradata.com/download/connectivity/odbc-driver/linux).

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

      &quot;InstallDir&quot; corresponds to the location of the **odbcinst.ini** file.

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

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 e /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: local do arquivo odbc.ini (por exemplo, /etc/odbc.ini).
   * **NLSPATH**: localização do arquivo opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

## Configuração do acesso ao SAP HANA {#configure-access-to-sap-hana}

A conexão com um banco de dados externo SAP HANA no FDA exige determinadas configurações adicionais no servidor do Adobe Campaign:

1. Instale os drivers ODBC para SAP HANA, de acordo com o sistema operacional que você usa:

   * **hdb_client_linux.tgz para Linux.** Após descompactado, inicie o comando hdbinst e siga as instruções para finalizar a instalação dos drivers.
   * **hdb_client_windows.zip para Windows.** Unzip the file and start the executable: **hdbinst.exe**. Siga as instruções do assistente para concluir a instalação dos drivers.

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

      &quot;InstallDir&quot; corresponds to the location of the **odbcinst.ini** file.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Especifique as variáveis de ambiente do servidor do Adobe Campaign:

   * **LD_LIBRARY_PATH**: Ele deve incluir o link para seu cliente SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) por padrão.
   * **ODBCINI**: local do arquivo odbc.ini (por exemplo, /etc/odbc.ini).

1. Crie a conta externa SAP Hana, conforme detalhado na seção [Criação de uma conexão](#creating-a-shared-connection) compartilhada.
