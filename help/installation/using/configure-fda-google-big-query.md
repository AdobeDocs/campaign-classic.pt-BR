---
product: campaign
title: Configuração do acesso ao Google BigQuery
description: Saiba como configurar o acesso ao Google BigQuery no FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 6d53ba957fb567a9a921544418a73a9bde37c97b
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 7%

---

# Configuração do acesso ao Google BigQuery {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Usar o Adobe Campaign Classic **Federated Data Access** (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso ao [!DNL Google BigQuery].

1. Configurar [!DNL Google BigQuery] on [Windows](#google-windows) ou [Linux](#google-linux)
1. Configure o [!DNL Google BigQuery] [conta externa](#google-external) no Adobe Campaign Classic
1. Configurar [!DNL Google BigQuery] carga em massa do conector em [Windows](#bulk-load-windows) ou [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] O conector está disponível para implantações híbridas e locais. Para obter mais informações, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery no Windows {#google-windows}

### Driver configurado no Windows {#driver-window}

1. Instale o [driver ODBC para Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configure o driver ODBC no Windows. Para obter mais informações, consulte [esta página](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Para o [!DNL Google BigQuery] para funcionar, o Adobe Campaign Classic requer os seguintes parâmetros para se conectar:

   * **[!UICONTROL Project]**: criar ou usar um projeto existente.

      Para obter mais informações, consulte esta [página](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: crie uma conta de serviço.

      Para obter mais informações, consulte esta [página](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: o **[!UICONTROL Service account]** exige um **[!UICONTROL Key File]** para um [!DNL Google BigQuery] conexão via ODBC.

      Para obter mais informações, consulte esta [página](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** é opcional para uma conexão ODBC. Como cada query precisa fornecer o conjunto de dados onde a tabela está localizada, especificando um **[!UICONTROL Dataset]** é obrigatório para [!DNL Google BigQuery] Conector FDA no Adobe Campaign Classic.

      Para obter mais informações, consulte esta [página](https://cloud.google.com/bigquery/docs/datasets).

1. No Adobe Campaign Classic, você pode configurar [!DNL Google BigQuery] conta externa. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#google-external).

### Carregamento em massa configurado no Windows {#bulk-load-window}

>[!NOTE]
>
>Você precisa do Python instalado para que o SDK da Google Cloud funcione.
>
>Recomendamos usar Python3. Veja isso [página](https://www.python.org/downloads/).

O utilitário Carregamento em massa permite transferência mais rápida, que é realizada por meio do SDK da Google Cloud.

1. Faça o download do arquivo de 64 bits do Windows (x86_64) a partir desta [página](https://cloud.google.com/sdk/docs/downloads-versioned-archives) e extraia-a no diretório correspondente.

1. Execute o `google-cloud-sdk\install.sh` script. É necessário aceitar a configuração da variável de caminho.

1. Após a instalação, verifique se a variável de caminho `...\google-cloud-sdk\bin` está definida. Caso contrário, adicione-o manualmente.

1. No  `..\google-cloud-sdk\bin\bq.cmd` , adicione o `CLOUDSDK_PYTHON` variável local, que redirecionará para o local da instalação do Python.

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

1. Baixe o [Driver Magnitude Simba Linux ODBC (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). Em seguida, transfira o arquivo de tarball para uma pasta temporária em sua máquina ou use o comando wget:

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Extraia o arquivo de tarball principal da seguinte maneira, onde **TarballName** é o nome da embalagem de tarball que contém o condutor:

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Acesse a pasta extraída e extraia o arquivo de tarball interno correspondente à versão do driver. Instale-o em outra pasta temporária, no exemplo a seguir BigQueryDriver:

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Acesse o local temporário onde o arquivo de tarball principal foi extraído e copie a variável `GoogleBigQueryODBC.did` e `setup/simba.googlebigqueryodbc.ini` arquivos na nova pasta criada na etapa anterior:

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

1. Substituir `<INSTALLDIR>` com `/opt/simba/googlebigqueryodbc` em `simba.googlebigqueryodbc.ini` no diretório de instalação:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Altere o `DriverManagerEncoding` para UTF-16 e `SwapFilePath` em `simba.googlebigqueryodbc.ini`. Se necessário, também é possível alterar as configurações de registro.

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

1. Se você estiver usando um arquivo de drivers de sistema ou qualquer `odbcinst.ini` arquivo, configurar `/etc/odbcinst.ini` apontar para o local do driver Google BigQuery `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

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

1. Localize as bibliotecas do gerenciador de driver unixODBC e adicione o `unixODBC` e `googlebigqueryodbc` caminhos da biblioteca para o `LD_LIBRARY_PATH environment` variável.

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

1. No Adobe Campaign Classic, você pode configurar [!DNL Google BigQuery] conta externa. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#google-external).

### Carregamento em massa configurado no Linux {#bulk-load-linux}

>[!NOTE]
>
>Você precisa do Python instalado para que o SDK da Google Cloud funcione.
>
>Recomendamos usar Python3. Veja isso [página](https://www.python.org/downloads/).

O utilitário Carregamento em massa permite transferência mais rápida, que é realizada por meio do SDK da Google Cloud.

1. Faça o download do arquivo Linux de 64 bits (x86_64) neste [página](https://cloud.google.com/sdk/docs/downloads-versioned-archives) e extrair no diretório correspondente.

1. Execute o `google-cloud-sdk\install.sh` script. É necessário aceitar a configuração da variável de caminho.

1. Após a instalação, verifique se a variável de caminho `...\google-cloud-sdk\bin` está definida. Caso contrário, adicione-o manualmente.

1. Caso deseje evitar o uso da variável `PATH` ou se desejar mover a variável `google-cloud-sdk` para outro local, use o `bqpath` ao configurar o valor da opção **[!UICONTROL External account]** para especificar o caminho exato para o diretório bin em seu sistema.

1. Reinicie o Adobe Campaign Classic para que as alterações sejam consideradas.

## Conta externa do Google BigQuery {#google-external}

Você precisa criar um [!DNL Google BigQuery] conta externa para conectar sua instância do Adobe Campaign Classic à sua [!DNL Google BigQuery] banco de dados externo.

1. Do Adobe Campaign Classic **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Para configurar a conta externa do [!DNL Google BigQuery], você deve especificar:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: Email do seu **[!UICONTROL Service account]**. Para obter mais informações, consulte [Documentação da Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Nome da sua **[!UICONTROL Project]**. Para obter mais informações, consulte [Documentação da Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: select **[!UICONTROL Click here to upload]** se você optar por fazer upload da chave por meio do Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: copie/cole o caminho absoluto nesse campo se optar por usar uma chave pré-existente.
   * **[!UICONTROL Dataset]**: Nome da sua **[!UICONTROL Dataset]**. Para obter mais informações, consulte [Documentação da Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
