---
solution: Campaign Classic
product: campaign
title: Configuração do acesso à Vertica
description: Saiba como configurar o acesso à Vertica no FDA
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 19%

---


# Configuração do acesso à Vertica {#configure-fda-vertica}

![](../../assets/v7-only.svg)

Use a opção Campaign **Federated Data Access** (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso a [!DNL Vertica].

1. Configurar [!DNL Vertica] em [CentOS](#vertica-centos), [Windows](#vertica-windows) ou [Debian](#vertica-debian)
1. Configure a [!DNL Vertica] [conta externa](#vertica-external) no Campaign


>[!NOTE]
>
>[!DNL Vertica] O conector está disponível para implantações híbridas e locais. Para obter mais informações, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Vertica no CentOS {#vertica-centos}

Para configurar [!DNL Vertica] no CentOS, siga as etapas abaixo:

1. Baixe os drivers ODBC para o [!DNL Vertica]. [Clique ](https://www.vertica.com/download/vertica/client-drivers/) aqui e baixe o RPM Linux mais recente.

1. Em seguida, é necessário instalar o unixODBC com o seguinte comando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Se tiver instalado anteriormente o servidor [!DNL Vertica], um driver ODBC já estará instalado. Nesse caso, atualize a unidade da seguinte maneira:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. No Adobe Campaign, você pode configurar a conta externa [!DNL Vertica]. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#vertica-external).

## Vertica no Windows {#vertica-windows}

1. Instale o [driver ODBC para Windows](https://www.vertica.com/download/vertica/client-drivers/). Para instalar o driver para Windows, você precisará habilitar o .NET Framework 3.5 ou o assistente de instalação tentará habilitá-lo e baixá-lo automaticamente.

1. Configure o driver ODBC no Windows. Para obter mais informações, consulte [esta página](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. No Adobe Campaign, você pode configurar a conta externa [!DNL Vertica]. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#vertical-external).

## Vertica em Debian {#vertica-debian}

1. Baixe os drivers ODBC para o [!DNL Vertica]. [Clique aqui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) para iniciar o download.

1. Em seguida, é necessário instalar o unixODBC com o seguinte comando:

   ```
   apt-get install unixODBC
   ```

1. Se tiver instalado anteriormente o servidor [!DNL Vertica], um driver ODBC já estará instalado. Nesse caso, atualize a unidade da seguinte maneira:

   ```
   #Switch to root
   sudo su
   
   #Move or copy the downloaded file and change to /root
   mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
   cd /
   
   #Uncompress the file you downloaded
   tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Remove the tar.gz since it is not needed anymore
   rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. No Adobe Campaign, você pode configurar a conta externa [!DNL Vertica]. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#vertica-external).

## Conta externa da Vertica {#vertica-external}

Você precisa criar uma conta externa [!DNL Vertica] para conectar a instância do Campaign ao banco de dados externo [!DNL Vertica].

1. Em Campanha **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Vertica]**, você deve especificar:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL do servidor [!DNL Vertica]

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados
   ![](assets/vertica.png)
