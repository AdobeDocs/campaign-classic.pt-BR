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
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Acesso a um banco de dados externo{#accessing-an-external-database}

## Sobre o Federated Data Access {#about-federated-data-access}

O Adobe Campaign oferece a opção de **Federated Data Access** (FDA) para processar as informações armazenadas em um ou mais bancos de dados externos: é possível acessar os dados externos sem alterar a estrutura dos dados do Adobe Campaign.

>[!CAUTION]
>
>O módulo **Federated Data Access** (FDA) é opcional. Verifique o contrato de licença do Adobe Campaign.
>  
>Além disso, o acesso a um banco de dados externo por meio do FDA é possível somente para instalações locais ou híbridas.

### Princípio operacional {#operating-principle}

A opção FDA permite coletar dados das fontes SQL e detectar automaticamente a estrutura das tabelas de destino.

Para usar essa funcionalidade, é necessário:

1. Ter um banco de dados externo compatível com o módulo FDA do Adobe Campaign. A lista de sistemas de banco de dados e versões compatíveis está detalhada na [matriz de compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). Os usuários também devem ter as [permissões necessárias](#remote-database-access-rights) no Adobe Campaign e no banco de dados externo.
1. [Instalar os drivers](#specific-configurations-by-database-type) que correspondem ao banco de dados no servidor do Adobe Campaign.
1. [Criar e configurar uma conta externa](#connecting-to-the-database) que permita estabelecer a conexão entre o Adobe Campaign e o banco de dados externo. Para obter mais informações sobre contas externas disponíveis, consulte esta [página](../../platform/using/external-accounts.md).
1. [Criar o schema de leitura](#creating-the-data-schema) do banco de dados externo no Adobe Campaign. Isso permite reconhecer a estrutura de dados do banco de dados externo.
1. Eventualmente, [crie um novo target mapping](#defining-data-mapping) do schema criado anteriormente, no caso em que os recipients de seus deliveries vêm do banco de dados externo. Isso apresenta determinadas limitações, principalmente em relação à personalização de deliveries.

Após criar o schema de leitura de dados, é possível processar os dados nos workflows do Adobe Campaign. Para obter mais informações, consulte [esta seção](../../workflow/using/executing-a-workflow.md#architecture).

### Práticas recomendadas {#best-practices-and-recommendations}

A opção FDA é feita para manipular os dados em bancos de dados externos em modo de lote em workflows. Usando o FDA em outro contexto, por exemplo, para operações unitárias, devem ser realizadas com precaução (personalização, interação, deliveries em tempo real e etc.).

Antes de começar a explorar seu banco de dados externo, realize testes de desempenho para detectar possíveis problemas e otimizar usando essa opção.

Evite o máximo possível as operações que precisam usar o banco de dados tanto do Adobe Campaign quanto externo. Para fazer isso, é possível:

* Exportar o banco de dados do Adobe Campaign para o banco de dados externo e executar as operações somente do banco de dados externo antes de importar novamente os resultados para o Adobe Campaign.
* Coletar os dados do banco de dados externo do Adobe Campaign e executar as operações no local.

Se você quiser realizar a personalização de deliveries usando dados do banco de dados externo, colete os dados para usar em um workflow para torná-lo disponível em uma tabela temporária. Em seguida, use os dados da tabela temporária para personalizar seu delivery.

### Limitações {#limitations}

A opção FDA está sujeita à limitação do sistema de banco de dados externo que você usa.

Por motivos de desempenho, não recomendamos utilizar essa funcionalidade para realizar operações unitárias (personalização de delivery, módulo de interação, tempo real).

## Configurações específicas por tipo de banco de dados {#specific-configurations-by-database-type}

Dependendo dos bancos de dados externos que você deseja acessar do Adobe Campaign, você precisará realizar algumas configurações específicas. Essas configurações envolvem basicamente a instalação de drivers e a declaração de variáveis de ambiente pertencentes a cada RDBMS no servidor do Adobe Campaign.

Como regra geral, você precisa instalar a camada de cliente correspondente no banco de dados externo no servidor do Adobe Campaign.

>[!NOTE]
>
>Versões compatíveis são listadas na [Matriz de Compatibilidade do Campaign](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA) .

### Configuração do acesso ao Hadoop {#configure-access-to-hadoop}

A conexão com um banco de dados externo Hadoop no FDA exige as seguintes configurações no servidor do Adobe Campaign.

#### Para Windows {#for-windows}

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

#### Para Linux {#for-linux}

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

### Configuração do acesso ao MySQL {#configure-access-to-mysql}

Para obter mais informações sobre como configurar o banco de dados do MySQL , consulte este [artigo](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html).

### Configuração do acesso ao Netezza {#configure-access-to-netezza}

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

### Configuração do acesso ao Oracle {#configure-access-to-oracle}

A conexão com um banco de dados externo Oracle no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign:

#### Para Linux {#for-linux-1}

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

#### Para Windows {#for-windows-1}

1. Instale o software cliente Oracle.
1. In the C:Oracle folder, create a **tnsnames.ora** file containing your TNS definition.

   Adicione uma variável de ambiente TNS_ADMIN com C:Oracle como valor e reinicie a máquina.

### Configuração do acesso ao Sybase IQ {#configure-access-to-sybase-iq}

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
>Para o Windows, você deve instalar o cliente Sybase IQ no servidor do Adobe Campaign e criar uma conexão ODBC. Certifique-se de criar uma fonte de dados do sistema quando o servidor do Adobe Campaign (nlserver) estiver em execução como um serviço no Windows.

### Configuração do acesso ao Teradata {#configure-access-to-teradata}

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

### Configuração do acesso ao SAP HANA {#configure-access-to-sap-hana}

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

   * **LD_LIBRARY_PATH**: Ele deve incluir o link para seu cliente SAP Hana (por padrão, /usr/sap/hdbclient/ [libodbcHDB.so](http://libodbchdb.so/) ).
   * **ODBCINI**: local do arquivo odbc.ini (por exemplo, /etc/odbc.ini).

1. Crie a conta externa SAP Hana, conforme detalhado na seção [Criação de uma conexão](#creating-a-shared-connection) compartilhada.

## Direitos de acesso ao banco de dados remoto {#remote-database-access-rights}

Primeiro, para que o usuário possa realizar operações em um banco de dados externo por meio do FDA, esse último deve ter um direito nomeado específico no Adobe Campaign.

1. Selecione o **[!UICONTROL Administration > Access Management > Named Rights]** nó no Adobe Campaign explorer.
1. Crie um novo direito especificando o rótulo escolhido.
1. The **[!UICONTROL Name]** field must take the following format **user:base@server**, where :

   * **user** corresponde ao nome do usuário no banco de dados externo.
   * **base** corresponde ao nome do banco de dados externo.
   * **server** corresponde ao nome do servidor de banco de dados externo.

      >[!NOTE]
      >
      >A parte **:base** é opcional no Oracle.

1. Save the named right then link it to your chosen user from the **[!UICONTROL Administration > Access Management > Operators]** node of the Adobe Campaign explorer.

Em seguida, para processar os dados contidos em um banco de dados externo, o usuário do Adobe Campaign deve ter pelo menos direitos &quot;Write&quot; no banco de dados. Assim, ele poderá criar worktables. Eles são excluídos automaticamente pelo Adobe Campaign.

Em geral, são necessários os seguintes direitos:

* **CONNECT**: conexão ao banco de dados remoto,
* **READ Data**: acesso somente leitura a tabelas com dados do cliente,
* **READ &#39;MetaData&#39;**: acesso aos catálogos de dados do servidor para obter a estrutura da tabela,
* **LOAD**: carregamento em massa em tabelas de trabalho (necessário ao trabalhar em coleções e associações),
* **CREATE/DROP** para **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **EXPLAIN** (recomendado): para monitorar desempenhos em caso de problemas,
* **WRITE Data** (dependendo do cenário de integração).

>[!NOTE]
>
>O administrador do banco de dados precisa combinar esses direitos com os direitos específicos de cada mecanismo de banco de dados. Para obter mais informações, consulte os [direitos específicos do RDBMS](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html).

## Conexão com o banco de dados {#connecting-to-the-database}

Para habilitar uma conexão com o banco de dados externo, você deve indicar os parâmetros de conexão, ou seja, a fonte de dados direcionada e o nome da tabela com os dados que exigem carregamento.

>[!CAUTION]
>
>O usuário do Adobe Campaign precisa de direitos específicos para o banco de dados externo e o servidor de aplicativos do Adobe Campaign para processar dados de um banco de dados externo. Para obter mais informações, consulte a seção Direitos [de acesso ao banco de dados](#remote-database-access-rights) remoto.
>
>Para evitar mau funcionamento, os operadores que acessam dados compartilhados remotos devem trabalhar em espaços separados.

### Criação de uma conexão compartilhada {#creating-a-shared-connection}

Para habilitar uma conexão com um banco de dados externo compartilhado, desde que essa conexão esteja ativa, o banco de dados pode ser acessado pelo Adobe Campaign.

1. The configuration must be defined beforehand via the **[!UICONTROL Administration > Platform > External accounts]** node.
1. Clique no **[!UICONTROL New]** botão e selecione o **[!UICONTROL External database]** tipo.
1. Define the **[!UICONTROL Connection]** parameters of the external database.

   For connections to an **ODBC** type database the **[!UICONTROL Server]** field must contain the name of the ODBC data source and not the server name. Além disso, algumas configurações adicionais podem ser necessárias, dependendo dos bancos de dados usados. Consulte a seção Configurações [específicas por tipo](#specific-configurations-by-database-type) de banco de dados.

1. Once the parameters are entered, click the **[!UICONTROL Test the connection]** button to approve them.

   ![](assets/wf-external-account-create.png)

1. If necessary, uncheck the **[!UICONTROL Enabled]** option to disable access to this database without deleting its configuration.
1. Para permitir que o Adobe Campaign acesse esse banco de dados, você deve implantar as funções SQL. Clique na **[!UICONTROL Parameters]** guia e no **[!UICONTROL Deploy functions]** botão.

   ![](assets/wf-external-account-functions.png)

You can define specific work tablespaces for the tables and for the index in the **[!UICONTROL Parameters]** tab.

### Criação de uma conexão com autenticação do Windows {#creating-a-connection-with-windows-authentication}

Você também pode se conectar por meio do FDA, usando a autenticação do Windows. Para fazer isso:

* Verifique se o serviço do Adobe Campaign é executado por uma conta do Windows diferente da conta de sistema local.
* Verifique se o operador do Adobe Campaign dispõe de direitos suficientes para o servidor de aplicativos do Adobe Campaign e para o banco de dados externo.
* Create the corresponding external account without specifying the **[!UICONTROL Account]** and the **[!UICONTROL Password]**. Especifique somente o nome do banco de dados.

### Como criar uma conexão temporária {#creating-a-temporary-connection}

Você pode definir diretamente uma conexão com um banco de dados externo a partir de atividades do workflow. Nesse caso, ele estará em um banco de dados externo local, reservado para ser usado em um workflow atual, ou seja, não será salvo nas contas externas. Esse tipo de conexão pontual pode ser criada em diferentes atividades do fluxo de trabalho, especialmente **[!UICONTROL Query]** a atividade, a **[!UICONTROL Data loading (RDBMS)]**, a **[!UICONTROL Enrichment]** atividade ou a **[!UICONTROL Split]** atividade.

>[!CAUTION]
>
>Esse tipo de configuração não é recomendado, mas pode ser utilizado periodicamente para coletar dados. No entanto, você deve criar uma conta externa, conforme apresentada na seção [Criação de uma conexão compartilhada](#creating-a-shared-connection).

Por exemplo, na atividade de query, as etapas para criar uma conexão periódica com um banco de dados externo são as seguintes:

1. Clique no link **[!UICONTROL Add data...]** e selecione as **[!UICONTROL External data]** opções.
1. Selecione a **[!UICONTROL Locally defining the data source]** opção.

   ![](assets/wf_add_data_local_external_data.png)

1. Selecione o mecanismo de banco de dados do Target na lista suspensa. Digite o nome do servidor e forneça os parâmetros de autenticação.

   Especifique também o nome do banco de dados externo.

   ![](assets/wf_add_data_local_external_data_param.png)

   Clique no botão **[!UICONTROL Next]**.

1. Selecione a tabela onde os dados estão armazenados.

   Você pode inserir o nome da tabela diretamente no campo correspondente ou clicar no ícone edição para acessar a lista das tabelas do banco de dados.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Click the **[!UICONTROL Add]** button to define one or several reconciliation fields between the external database data and the data in the Adobe Campaign database. Os **[!UICONTROL Edit expression]** ícones do **[!UICONTROL Remote field]** e **[!UICONTROL Local field]** fornecem acesso à lista de campos de cada uma das tabelas.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Se necessário, especifique uma condição de filtragem e o modo de classificação de dados.
1. Selecione os dados adicionais a serem coletados no banco de dados externo. To do this, double click on the fields(s) that you want to add to display them in the **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   Clique **[!UICONTROL Finish]** para confirmar esta configuração.

### Conexão segura {#secure-connection}

Você pode proteger o acesso a um banco de dados externo ao configurar uma conta FDA externa.

Para fazer isso, adicione &quot;**:ssl**&quot; após o endereço e o endereço do servidor da porta usada. Por exemplo: **192.168.0.52:4501:ssl**.

Os dados serão enviados por meio do protocolo SSL seguro.

### Configurações adicionais {#additional-configurations}

Se necessário, você pode criar o schema para processamento de dados em um banco de dados externo. Da mesma forma, o Adobe Campaign permite definir o mapeamento nos dados em uma tabela externa. Essas configurações são gerais e não se aplicam exclusivamente aos workflows.

>[!NOTE]
>
>Para obter mais informações sobre como criar schemas no Adobe Campaign e definir um novo mapeamento de dados, consulte [esta página](../../configuration/using/about-schema-edition.md).

## Criação do schema de dados {#creating-the-data-schema}

To create a schema on an external database, click the **[!UICONTROL New]** button above the list of data schemas and choose **[!UICONTROL Access external data]**.

![](assets/wf_new_schema_fda.png)

Insira um nome e uma descrição para o schema e selecione a conta externa que habilitará a conexão com o banco de dados. Isso permite o acesso à lista de tabelas disponíveis na base externa. Escolha a tabela que contém os dados a serem coletados.

![](assets/wf_new_schema_select_table_fda.png)

Click **[!UICONTROL OK]** to confirm. O Adobe Campaign detecta automaticamente a estrutura da tabela selecionada e gera o schema lógico.

>[!NOTE]
>
>O Adobe Campaign não gera links.

Click **[!UICONTROL Save]** to confirm creation.

![](assets/wf_new_schema_generate_fda.png)

Os índices são criados automaticamente ao mapear uma tabela (mapeamento padrão ou FDA).

## Definição do mapeamento de dados {#defining-data-mapping}

O Adobe Campaign permite definir o mapeamento nos dados em uma tabela externa.

Para fazer isso, após a criação do schema da tabela externa, é possível criar um novo mapeamento de delivery para usar os dados nessa tabela como um Delivery Target.

Para fazer isso, siga as etapas abaixo:

1. Crie um novo mapeamento de delivery e escolha o targeting dimension, como o schema que você acabou de criar, por exemplo.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indique os campos onde as informações de delivery são armazenadas (sobrenome, nome, e-mail, endereço, etc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Especifique os parâmetros para armazenamento de informações, incluindo o sufixo dos schemas de extensão para que sejam facilmente identificáveis.

   ![](assets/wf_new_mapping_define_names.png)

   Você pode escolher se deseja armazenar exclusões (**excludelog**), com mensagens (**broadlog**) ou em uma tabela separada.

   Você também pode escolher se deseja gerenciar o rastreamento para esse mapeamento de delivery (**trackinglog**).

1. Em seguida, selecione as extensões a serem consideradas. O tipo de extensão depende dos parâmetros e opções da sua plataforma (visualizar seu contrato de licença).

   ![](assets/wf_new_mapping_define_extensions.png)

   Click the **[!UICONTROL Save]** button to launch delivery mapping creation: all linked tables are created automatically based on the selected parameters.

## Opções adicionais {#additional-options}

### Retransmissão HTTP em uma instância remota {#http-relay-to-a-remote-instance}

É possível acessar bancos de dados externos configurados em instâncias remotas usando o protocolo HTTP.

>[!NOTE]
>
>Nem todos os tipos de dados SQL são suportados por esse recurso. Os tipos de dados Blob não são suportados. É possível que outros tipos de dados não funcionem dependendo do banco de dados de target (Carimbo de data/hora no Microsoft SQL Server, por exemplo). Entre em contato com o suporte da Adobe para obter mais informações.

Isso simplifica a transferência e a sincronização de dados entre duas instâncias. Além disso, ajuda você a evitar túneis entre uma instância e um banco de dados remoto e permite a instalação das camadas de cliente para acessar esse banco de dados. A instância de destino pode ser uma instância hospedada.

>[!CAUTION]
>
>Essa opção é apenas para facilitar os fluxos de replicação de dados (ETL).
>
>Por exemplo, ela permite que uma instância hospedada na nuvem tenha acesso direto aos dados de um banco de dados hospedado &quot;localmente&quot;. No entanto, não se destina a permitir que o direcionamento seja realizado em um banco de dados hospedado &quot;no local&quot; diretamente da nuvem.

Para fazer isso, você deve configurar as contas externas das duas instâncias para que a instância local possa se comunicar com a instância remota usando o protocolo HTTP:

* Instância local: selecione o novo tipo de **[!UICONTROL HTTP relay to a remote database]** conexão.

   Em caso de transferência de dados de carregamento em massa, especifique também o tamanho do buffer. Selecione a opção de compactação se quiser reduzir o tamanho dos dados transferidos.

   A sintaxe **[!UICONTROL Data source]** deve ser definida com: &quot;nms:extAccount : `<internal_name_of_the_external_account>`&quot;

   ![](assets/fda_over_http_1.png)

   >[!NOTE]
   >
   >É recomendável usar uma conexão HTTPS.

* Remote instance: in the FDA external account of the database accessed via the HTTP relay, check the Target of an **[!UICONTROL 'HTTP relay to a remote database' account option]**.

   ![](assets/fda_over_http_2.png)

O exemplo a seguir mostra o novo modo operacional possível:

![](assets/schema_fda_over_http_2.png)

>[!CAUTION]
>
>O banco de dados padrão da instância remota também deve ser acessado por meio de uma conta externa.

Esse método operacional evita que o workflow de limpeza de cada instância exclua as tabelas de trabalho dos bancos de dados que usam a instância como retransmissão.

Assim, no exemplo anterior, o workflow de limpeza da instância remota não executará uma ação no banco de dados FDA vermelho, pois ele é usado pela instância local.

### Criação direta de schemas temporários {#directly-creating-temporary-schemas}

Se você deseja gerenciar vários acessos a um banco de dados externo do FDA, uma nova opção permite criar um schema de trabalho diretamente ao configurar uma conta externa.

>[!NOTE]
>
>Essa opção funciona somente com PostgreSQL.

![](assets/fda_work_table.png)

### Otimização da personalização de e-mail com dados externos {#optimizing-email-personalization-with-external-data}

Na compilação 8740, a opção agora **[!UICONTROL Prepare the personalization data with a workflow]** está disponível na guia **[!UICONTROL Analysis]** das propriedades de entrega.

Durante a análise de delivery, essa opção cria e executa automaticamente um workflow que armazena todos os dados vinculados ao Target em uma tabela temporária, incluindo dados de tabelas vinculadas na FDA.

Ao selecionar essa opção, é possível obter um aumento significativo no desempenho para executar a personalização.

### Cloud Messaging - sincronização FDA {#cloud-messaging---fda-synchronization}

Quando o servidor do Cloud Messaging e o servidor Marketing não foram sincronizados por um longo período, o volume de broadlogs ausentes no servidor Marketing pode ser significativo. Para otimizar a sincronização de broadlog por meio do FDA, a opção **NmsMidSourcing_LogsPeriodHour** foi adicionada. Isso permite que um período máximo (expresso em horas) seja especificado como limite para o número de broadlogs recuperados toda vez que o workflow de sincronização é executado.

The option is to be added in the console, in the **[!UICONTROL Administration > Options]** node.

>[!CAUTION]
>
>Essa opção deve ser usada **apenas** para sincronizar um volume significativo de broadlogs por meio do FDA.

>[!NOTE]
>
>A opção só será levada em conta se existir uma última data de recuperação (**NmsMidSourcing_LastBroadLog_*** ).

### Centro de mensagens - Acesso de leitura na tabela XtkFolder {#message-center---read-access-on-the-xtkfolder-table}

A partir da compilação 8141, a ação manual é necessária se o Centro de Mensagens usar o FDA como modo de arquivamento.

Você precisa conceder acesso de leitura na tabela XtKFolder ao usuário vinculado à conta FDA externa.

Para um banco de dados PostgreSQL, por exemplo, o comando é o seguinte:

```
GRANT SELECT ON XtkFolder TO DBUSER;
```

Esse usuário deve ter acesso de leitura às seguintes tabelas:

* NmsBroadLogRtEvent
* NmsBroadLogBatchEvent
* NmsTrackingLogRtEvent
* NmsTrackingLogBatchEvent
* NmsRtEvent
* NmsBatchEvent
* NmsBroadLogMsg
* NmsTrackingUrl
* NmsDelivery
* NmsWebTrackingLog

>[!NOTE]
Essa modificação exclui a mensagem de erro &quot;Permissão negada para relação xtkfolder&quot;.

Se o schema de trabalho selecionado na conta FDA externa não for a conta Neolane pronta para o uso, essa modificação nos direitos de acesso não será necessária.

## Uso de dados de um banco de dados externo em um workflow {#using-data-from-an-external-database-in-a-workflow}

Em várias atividades de workflow do Adobe Campaign, você pode usar os dados armazenados em um banco de dados externo.

### Filtragem em dados externos {#filtering-on-external-data}

A atividade query permite adicionar dados externos e usá-los nas configurações de filtro definidas.

Para obter mais informações, consulte a seção [Query](../../workflow/using/targeting-data.md#selecting-data).

### Criação de subconjuntos {#creating-sub-sets}

A atividade dividida permite criar subconjuntos. Você pode usar dados externos para definir os critérios de filtragem a serem usados.

Para obter mais informações, consulte a seção [Split](../../workflow/using/split.md).

### Carregamento de banco de dados externo {#loading-external-database}

Você pode utilizar os dados externos no carregamento de dados (RDBMS). Essa atividade é apresentada na seção [Carregamento de dados](../../workflow/using/data-loading--rdbms-.md).

### Adição de informações e links {#adding-information-and-links}

A atividade de enriquecimento permite incluir dados adicionais na mesa de trabalho do workflow, como também links para uma tabela externa. Por esse motivo, é possível explorar os dados de um banco de dados externo. Essa atividade é apresentada na seção [Enriquecimento](../../workflow/using/enrichment.md) .
