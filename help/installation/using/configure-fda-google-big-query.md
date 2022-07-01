---
product: campaign
title: Configuração do acesso ao Google BigQuery
description: Saiba como configurar o acesso ao Google BigQuery no FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 9%

---

# Configuração do acesso ao Google BigQuery {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Usar o Adobe Campaign Classic **Federated Data Access** (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso ao [!DNL Google BigQuery].

1. Configurar [!DNL Google BigQuery] on [Windows](#google-windows) ou [Linux](#google-linux)
1. Configure o [!DNL Google BigQuery] [conta externa](#google-external) no Adobe Campaign Classic
1. Configurar [!DNL Google BigQuery] carga em massa do conector em [Windows](#bulk-load-windows) ou [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] O conector está disponível para implantações locais, híbridas e hospedadas. Para obter mais informações, consulte [esta página](../../installation/using/capability-matrix.md).

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

Antes de configurar o driver, observe que o script e os comandos devem ser executados pelo usuário raiz. Também é recomendável usar o Google DNS 8.8.8.8 ao executar o script.

Para configurar [!DNL Google BigQuery] no Linux, siga as etapas abaixo:

1. Antes de instalar o ODBC, verifique se os seguintes pacotes estão instalados em sua distribuição Linux:

   * Para Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
      ```

   * Para Debian:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
      ```

1. Atualizar sistema antes da instalação:

   * Para Red Hat/CentOS:

      ```
      # install unixODBC driver manager
      yum install -y unixODBC
      ```

   * Para Debian:

      ```
      # install unixODBC driver manager
      apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
      ```

1. Acesse o diretório onde o script está localizado e execute o seguinte script:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Carregamento em massa configurado no Linux {#bulk-load-linux}

>[!NOTE]
>
>Você precisa do Python instalado para que o SDK da Google Cloud funcione.
>
>Recomendamos usar Python3. Veja isso [página](https://www.python.org/downloads/).

O utilitário Carregamento em massa permite transferência mais rápida, que é realizada por meio do SDK da Google Cloud.

1. Antes de instalar o ODBC, verifique se os seguintes pacotes estão instalados em sua distribuição Linux:

   * Para Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y python3
      ```

   * Para Debian:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y python3
      ```

1. Acesse o diretório onde o script está localizado e execute o seguinte script:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

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

O conector é compatível com as seguintes opções:

| Opção | Descrição |
|:-:|:-:|
| ProxyType | Tipo de proxy usado para se conectar ao BigQuery por meio de conectores ODBC e SDK. </br>HTTP (padrão), http_no_túnel, socks4 e socks5 são suportados atualmente. |
| ProxyHost | Nome do host ou endereço IP onde o proxy pode ser atingido. |
| ProxyPort | Número da porta em que o proxy está sendo executado, por exemplo, 8080 |
| ProxyUid | Nome de usuário usado para o proxy autenticado |
| ProxyPwd | Senha ProxyUid |
| bqpath | Observe que isso se aplica somente à ferramenta de carregamento em massa (Cloud SDK). </br> Para evitar o uso da variável PATH ou se o diretório google-cloud-sdk tiver que ser movido para outro local, você pode especificar com essa opção o caminho exato para o diretório do compartimento do sdk da nuvem no servidor. |
