---
product: campaign
title: Configuração do acesso ao Google BigQuery
description: Saiba como configurar o acesso ao Google BigQuery no FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 6%

---

# Configuração do acesso ao Google BigQuery {#configure-fda-google-big-query}



Use a opção **Federated Data Access** (FDA) do Adobe Campaign Classic para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso ao [!DNL Google BigQuery].

1. Configurar [!DNL Google BigQuery] no [Windows](#google-windows) ou [Linux](#google-linux)
1. Configurar a [!DNL Google BigQuery] [conta externa](#google-external) no Adobe Campaign Classic
1. Configurar o carregamento em massa do conector [!DNL Google BigQuery] no [Windows](#bulk-load-windows) ou [Linux](#bulk-load-linux)

>[!NOTE]
>
> O conector [!DNL Google BigQuery] está disponível para implantações locais, híbridas e hospedadas. Para obter mais informações, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery no Windows {#google-windows}

### Driver configurado no Windows {#driver-window}

1. Baixe o driver ODBC [para Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configure o driver ODBC no Windows. Para obter mais informações, consulte [esta página](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Para que o conector [!DNL Google BigQuery] funcione, o Adobe Campaign Classic exige os seguintes parâmetros para se conectar:

   * **[!UICONTROL Project]**: criar ou usar um projeto existente.

     Para obter mais informações, consulte esta [página](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: criar uma conta de serviço.

     Para obter mais informações, consulte esta [página](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: **[!UICONTROL Service account]** requer **[!UICONTROL Key File]** para uma conexão [!DNL Google BigQuery] através de ODBC.

     Para obter mais informações, consulte esta [página](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** é opcional para uma conexão ODBC. Como cada consulta precisa fornecer o conjunto de dados onde a tabela está localizada, a especificação de um **[!UICONTROL Dataset]** é obrigatória para o Conector FDA do [!DNL Google BigQuery] no Adobe Campaign Classic.

     Para obter mais informações, consulte esta [página](https://cloud.google.com/bigquery/docs/datasets).

1. No Adobe Campaign Classic, você pode configurar a conta externa do [!DNL Google BigQuery]. Para obter mais informações sobre como configurar sua conta externa, consulte [esta seção](#google-external).

### Configuração de carregamento em massa no Windows {#bulk-load-window}

>[!NOTE]
>
>É necessário ter o Python instalado para que o SDK da Google Cloud funcione.
>
>Recomendamos o uso do Python3; consulte esta [página](https://www.python.org/downloads/).

O utilitário de Carregamento em massa permite uma transferência mais rápida, alcançada pelo SDK da Google Cloud.

1. Baixe o arquivo morto do Windows de 64 bits (x86_64) desta [página](https://cloud.google.com/sdk/docs/downloads-versioned-archives) e extraia-o no diretório correspondente.

1. Execute o script `google-cloud-sdk\install.sh`. É necessário aceitar a configuração da variável de caminho.

1. Após a instalação, verifique se a variável de caminho `...\google-cloud-sdk\bin` está definida. Caso contrário, adicione-o manualmente.

1. No arquivo `..\google-cloud-sdk\bin\bq.cmd`, adicione a variável local `CLOUDSDK_PYTHON`, que redirecionará para o local da instalação do Python.

   Por exemplo:

   ![](assets/google-big-query_1.png)

1. Reinicie o Adobe Campaign Classic para que as alterações sejam consideradas.

## Google BigQuery no Linux {#google-linux}

### Driver configurado no Linux {#driver-linux}

Antes de configurar o driver, observe que o script e os comandos devem ser executados pelo usuário raiz. Também é recomendável usar o Google DNS 8.8.8.8 ao executar o script.

Para configurar o [!DNL Google BigQuery] no Linux, siga as etapas abaixo:

1. Antes da instalação do ODBC, verifique se os seguintes pacotes estão instalados na distribuição Linux:

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

1. Atualize o sistema antes da instalação:

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

1. Antes de executar o script, você pode obter mais informações especificando o argumento —help:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. Acesse o diretório onde o script está localizado e execute o script a seguir como usuário root:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Configuração de carregamento em massa no Linux {#bulk-load-linux}

>[!NOTE]
>
>É necessário ter o Python instalado para que o SDK da Google Cloud funcione.
>
>Recomendamos o uso do Python3; consulte esta [página](https://www.python.org/downloads/).

O utilitário de Carregamento em massa permite uma transferência mais rápida, alcançada pelo SDK da Google Cloud.

1. Antes da instalação do ODBC, verifique se os seguintes pacotes estão instalados na distribuição Linux:

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

É necessário criar uma conta externa [!DNL Google BigQuery] para conectar sua instância do Adobe Campaign Classic ao banco de dados externo [!DNL Google BigQuery].

1. No Adobe Campaign Classic **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Para configurar a conta externa do [!DNL Google BigQuery], você deve especificar:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: email de **[!UICONTROL Service account]**. Para obter mais informações, consulte a [documentação da Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Nome de seu **[!UICONTROL Project]**. Para obter mais informações, consulte a [documentação da Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: selecione **[!UICONTROL Click here to upload]** se você optar por carregar a chave por meio do Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: copie/cole seu caminho absoluto neste campo se você optar por usar uma chave pré-existente.

   * **[!UICONTROL Dataset]**: Nome de seu **[!UICONTROL Dataset]**. Para obter mais informações, consulte a [documentação da Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

O conector é compatível com as seguintes opções:

| Opção | Descrição |
|:-:|:-:|
| ProxyType | Tipo de proxy usado para se conectar ao BigQuery por meio de conectores ODBC e SDK. </br>HTTP (padrão), http_no_tunnel, socks4 e socks5 são suportados no momento. |
| ProxyHost | Nome do host ou endereço IP onde o proxy pode ser acessado. |
| PortaProxy | Número da porta em que o proxy está sendo executado, por exemplo, 8080 |
| ProxyUid | Nome de usuário usado para o proxy autenticado |
| ProxyPwd | Senha do ProxyUid |
| bqpath | Observe que isso é aplicável somente para a ferramenta de carregamento em massa (SDK da nuvem). </br> Para evitar o uso da variável PATH ou se o diretório google-cloud-sdk tiver que ser movido para outro local, você poderá especificar com essa opção o caminho exato para o diretório bin do sdk da nuvem no servidor. |
| GCloudConfigName | Observe que isso é aplicável a partir da versão 7.3.4 e somente para a ferramenta de carregamento em massa (SDK da nuvem).</br> O SDK da Google Cloud usa configurações para carregar dados em tabelas do BigQuery. A configuração chamada `accfda` armazena os parâmetros para carregar os dados. No entanto, essa opção permite que os usuários especifiquem um nome diferente para a configuração. |
| GCloudDefaultConfigName | Observe que isso é aplicável a partir da versão 7.3.4 e somente para a ferramenta de carregamento em massa (SDK da nuvem).</br> A configuração ativa do SDK da Google Cloud não pode ser excluída sem antes transferir a marca ativa para uma nova configuração. Essa configuração temporária é necessária para recriar a configuração principal para carregar dados. O nome padrão para a configuração temporária é `default`, que pode ser alterado se necessário. |
| GCloudRecreateConfig | Observe que isso é aplicável a partir da versão 7.3.4 e somente para a ferramenta de carregamento em massa (SDK da nuvem).</br> Quando definido como `false`, o mecanismo de carregamento em massa não tenta recriar, excluir ou modificar as configurações do SDK da Google Cloud. Em vez disso, ele continua com o carregamento de dados usando a configuração existente na máquina. Esse recurso é importante quando outras operações dependem das configurações do SDK da Google Cloud. </br> Se o usuário habilitar esta opção de mecanismo sem uma configuração adequada, o mecanismo de carregamento em massa emitirá uma mensagem de aviso: `No active configuration found. Please either create it manually or remove the GCloudRecreateConfig option`. Para evitar mais erros, ele será revertido para o usando o mecanismo de carregamento em massa de Inserção de matriz ODBC padrão. |

