---
product: campaign
title: Configuração do acesso ao Hadoop
description: Saiba como configurar o acesso ao Hadoop no FDA
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: e3a97e55-dd8b-41e1-b48c-816d973f62a8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 79%

---

# Configuração do acesso ao Hadoop {#configure-access-to-hadoop}



Usar a campanha **Federated Data Access** (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso ao Hadoop.

1. Configurar [banco de dados Hadoop](#configuring-hadoop)
1. Configurar o Hadoop [conta externa](#hadoop-external) no Campaign

## Configuração do Hadoop 3.0 {#configuring-hadoop}

A conexão com um banco de dados externo do Hadoop no FDA exige as seguintes configurações no servidor do Adobe Campaign. Observe que essa configuração está disponível para Windows e Linux.

1. Baixe os drivers ODBC para Hadoop de acordo com a versão do sistema operacional. Os drivers podem ser encontrados [nesta página](https://www.cloudera.com/br/downloads.html).

1. Em seguida, é necessário instalar os drivers ODBC e criar um DSN para a conexão Hive. As instruções podem ser encontradas [nesta página](https://docs.cloudera.com/br/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Após baixar e instalar os drivers ODBC, é necessário reiniciar o Campaign Classic. Para fazer isso, execute o seguinte comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. No Campaign Classic, você pode configurar a conta externa do [!DNL Hadoop]. Para obter mais informações sobre como configurar a conta externa, consulte [nesta seção](#hadoop-external).

## Conta externa do Hadoop {#hadoop-external}

A conta externa do [!DNL Hadoop] permite conectar a instância do Campaign ao banco de dados externo do Hadoop.

1. No Campaign Classic, configure a conta externa do [!DNL Hadoop]. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Hadoop]**, você deve especificar:

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


## Configuração do Hadoop 2.1 {#configure-access-hadoop-2}

Se precisar se conectar ao Hadoop 2.1, siga as etapas descritas abaixo para [Windows](#for-windows) ou [Linux](#for-linux).

### Hadoop 2.1 para Windows {#for-windows}

1. Instale os drivers ODBC e [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) para Windows.
1. Crie o DSN (Data Source Name) executando a ferramenta ODBC DataSource Administrator. Um exemplo de DSN de Sistema para Hive é fornecido para você modificar.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Crie a conta externa do Hadoop, conforme detalhado em [nesta seção](#hadoop-external).

### Hadoop 2.1 para Linux {#for-linux}

1. Instale o unixodbc para Linux.

   ```
   apt-get install unixodbc
   ```

1. Baixe e instale os drivers ODBC para Apache Hive a partir do HortonWorks: [https://www.cloudera.com/downloads.html](https://www.cloudera.com/br/downloads.html).

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

1. Crie a conta externa do Hadoop, conforme detalhado em [nesta seção](#hadoop-external).
