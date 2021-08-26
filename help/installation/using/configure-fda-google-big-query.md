---
solution: Campaign Classic
product: campaign
title: Configuração do acesso ao Google BigQuery
description: Saiba como configurar o acesso ao Google BigQuery no FDA
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 7%

---


# Configuração do acesso ao Google BigQuery {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Use a opção Adobe Campaign Classic **Federated Data Access** (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso a [!DNL Google BigQuery].

1. Configurar [!DNL Google BigQuery] em [Windows](#google-windows) ou [Linux](#google-linux)
1. Configure a [!DNL Google BigQuery] [conta externa](#google-external) no Adobe Campaign Classic
1. Configure [!DNL Google BigQuery] o carregamento em massa do conector no [Windows](#bulk-load-windows) ou [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] O conector está disponível para implantações híbridas e locais. Para obter mais informações, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery no Windows {#google-windows}

### Driver configurado no Windows {#driver-window}

1. Instale o [driver ODBC para Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configure o driver ODBC no Windows. Para obter mais informações, consulte [esta página](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Para que o conector [!DNL Google BigQuery] funcione, o Adobe Campaign Classic exige os seguintes parâmetros para se conectar:

   * **[!UICONTROL Project]**: criar ou usar um projeto existente.

      Para obter mais informações, consulte esta [página](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: crie uma conta de serviço.

      Para obter mais informações, consulte esta [página](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: o  **[!UICONTROL Service account]** requer um  **[!UICONTROL Key File]** para uma  [!DNL Google BigQuery] conexão por meio do ODBC.

      Para obter mais informações, consulte esta [página](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**:  **[!UICONTROL Dataset]** é opcional para uma conexão ODBC. Como cada query precisa fornecer o conjunto de dados em que a tabela está localizada, especificar um **[!UICONTROL Dataset]** é obrigatório para [!DNL Google BigQuery] Conector FDA no Adobe Campaign Classic.

      Para obter mais informações, consulte esta [página](https://cloud.google.com/bigquery/docs/datasets).

1. No Adobe Campaign Classic, você pode configurar a conta externa [!DNL Google BigQuery]. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#google-external).

### Carregamento em massa configurado no Windows {#bulk-load-window}

>[!NOTE]
>
>Você precisa do Python instalado para que o SDK da Google Cloud funcione.
>
>Recomendamos usar Python3, veja esta [página](https://www.python.org/downloads/).

O utilitário Carregamento em massa permite transferência mais rápida, que é realizada por meio do SDK da Google Cloud.

1. Baixe o arquivo do Windows de 64 bits (x86_64) a partir deste [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) e extraia-o no diretório correspondente.

1. Execute o script `google-cloud-sdk\install.sh`. É necessário aceitar a configuração da variável de caminho.

1. Após a instalação, verifique se a variável de caminho `...\google-cloud-sdk\bin` está definida. Caso contrário, adicione-o manualmente.

1. No arquivo `..\google-cloud-sdk\bin\bq.cmd`, adicione a variável local `CLOUDSDK_PYTHON`, que redirecionará para o local da instalação do Python.

   Por exemplo:

   ![](assets/google-big-query_1.png)

1. Reinicie o Adobe Campaign Classic para que as alterações sejam consideradas.

## Google BigQuery no Linux {#google-linux}

### Driver configurado no Linux {#driver-linux}

1. Antes de instalar o driver ODBC, é necessário atualizar seu sistema. No Linux ou CentOS, execute o seguinte comando:

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. Em seguida, é necessário instalar o gerenciador de driver unixODBC com o seguinte comando:

   ```
   # switch to root user
   sudo su
   ```

   No Debian:

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. Baixe o driver [Magnitude Simba Linux ODBC (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). Em seguida, transfira o arquivo de tarball para uma pasta temporária em sua máquina ou use o comando wget:

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Extraia o arquivo de tarball principal da seguinte maneira, onde **TarballName** é o nome do pacote de tarball que contém o driver:

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Acesse a pasta extraída e extraia o arquivo de tarball interno correspondente à versão do driver. Instale-o em outra pasta temporária, no seguinte exemplo BigQueryDriver:

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Acesse o local temporário onde o arquivo de tarball principal foi extraído e copie os arquivos `GoogleBigQueryODBC.did` e `setup/simba.googlebigqueryodbc.ini` para a nova pasta criada na etapa anterior:

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. Crie o diretório de instalação da seguinte maneira:

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. Copie o conteúdo do diretório no novo diretório de instalação:

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. Substitua `<INSTALLDIR>` por `/opt/simba/googlebigqueryodbc` em `simba.googlebigqueryodbc.ini` no diretório de instalação:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Altere `DriverManagerEncoding` para UTF-16 e `SwapFilePath` em `simba.googlebigqueryodbc.ini`. Se necessário, também é possível alterar as configurações de registro.

   Este é um exemplo de um arquivo de configuração atualizado de todo o driver:

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. Se estiver usando um arquivo de drivers de sistema ou qualquer arquivo `odbcinst.ini` atual, configure `/etc/odbcinst.ini` para apontar para o local do driver Google BigQuery `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

   Por exemplo:

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. Localize as bibliotecas do gerenciador de driver unixODBC e adicione os caminhos de biblioteca `unixODBC` e `googlebigqueryodbc` à variável `LD_LIBRARY_PATH environment`.

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. No Adobe Campaign Classic, você pode configurar a conta externa [!DNL Google BigQuery]. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#google-external).

### Carregamento em massa configurado no Linux {#bulk-load-linux}

>[!NOTE]
>
>Você precisa do Python instalado para que o SDK da Google Cloud funcione.
>
>Recomendamos usar Python3, veja esta [página](https://www.python.org/downloads/).

O utilitário Carregamento em massa permite transferência mais rápida, que é realizada por meio do SDK da Google Cloud.

1. Baixe o arquivo Linux de 64 bits (x86_64) neste [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) e extraia no diretório correspondente.

1. Execute o script `google-cloud-sdk\install.sh`. É necessário aceitar a configuração da variável de caminho.

1. Após a instalação, verifique se a variável de caminho `...\google-cloud-sdk\bin` está definida. Caso contrário, adicione-o manualmente.

1. Se quiser evitar o uso da variável `PATH` ou se quiser mover o diretório `google-cloud-sdk` para outro local, use o valor da opção `bqpath` ao configurar o **[!UICONTROL External account]** para especificar o caminho exato para o diretório bin em seu sistema.

1. Reinicie o Adobe Campaign Classic para que as alterações sejam consideradas.

## Conta externa do Google BigQuery {#google-external}

Você precisa criar uma conta externa [!DNL Google BigQuery] para conectar a instância do Adobe Campaign Classic ao banco de dados externo [!DNL Google BigQuery].

1. Em Adobe Campaign Classic **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Para configurar a conta externa do [!DNL Google BigQuery], você deve especificar:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: E-mail da sua  **[!UICONTROL Service account]**. Para obter mais informações, consulte a [documentação do Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Nome do seu  **[!UICONTROL Project]**. Para obter mais informações, consulte a [documentação do Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: selecione  **[!UICONTROL Click here to upload]** se você optar por fazer upload da chave por meio do Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: copie/cole o caminho absoluto nesse campo se optar por usar uma chave pré-existente.
   * **[!UICONTROL Dataset]**: Nome do seu  **[!UICONTROL Dataset]**. Para obter mais informações, consulte a [documentação do Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
