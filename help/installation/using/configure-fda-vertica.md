---
product: campaign
title: Configuração do acesso à Vertica
description: Saiba como configurar o acesso à Vertica no FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 27%

---

# Configuração do acesso à Vertica {#configure-fda-vertica}

![](../../assets/v7-only.svg)

Usar Campanha **Federated Data Access** (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso ao [!DNL Vertica].

1. Configurar [!DNL Vertica] on [CentOS](#vertica-centos), [Windows](#vertica-windows) ou [Debian](#vertica-debian)
1. Configure o [!DNL Vertica] [conta externa](#vertica-external) no Campaign

>[!NOTE]
>
>[!DNL Vertica] O conector está disponível para implantações híbridas e locais. Para obter mais informações, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Vertica no CentOS {#vertica-centos}

Para configurar [!DNL Vertica] no CentOS, siga as etapas abaixo:

1. Baixe os drivers ODBC para o [!DNL Vertica]. [Clique aqui](https://www.vertica.com/download/vertica/client-drivers/) e faça o download do RPM Linux mais recente.

1. Em seguida, é necessário instalar o unixODBC com o seguinte comando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Se você já instalou o [!DNL Vertica] Um driver ODBC já será instalado no servidor. Nesse caso, atualize a unidade da seguinte maneira:

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

1. No Adobe Campaign, você pode configurar [!DNL Vertica] conta externa. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#vertica-external).

## Vertica no Windows {#vertica-windows}

1. Instale o [driver ODBC para Windows](https://www.vertica.com/download/vertica/client-drivers/). Para instalar o driver para Windows, você precisará habilitar o .NET Framework 3.5 ou o assistente de instalação tentará habilitá-lo e baixá-lo automaticamente.

1. Configure o driver ODBC no Windows. Para obter mais informações, consulte [esta página](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. No Adobe Campaign, você pode configurar [!DNL Vertica] conta externa. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#vertical-external).

## Vertica em Debian {#vertica-debian}

1. Baixe os drivers ODBC para o [!DNL Vertica]. [Clique aqui](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) para iniciar o download.

1. Em seguida, é necessário instalar o unixODBC com o seguinte comando:

   ```
   apt-get install unixODBC
   ```

1. Se você já instalou o [!DNL Vertica] Um driver ODBC já será instalado no servidor. Nesse caso, atualize a unidade da seguinte maneira:

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

1. No Adobe Campaign, você pode configurar [!DNL Vertica] conta externa. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#vertica-external).

## Conta externa da Vertica {#vertica-external}

Você precisa criar um [!DNL Vertica] conta externa para conectar a instância do Campaign à [!DNL Vertica] banco de dados externo.

1. Da campanha **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Vertica]**, você deve especificar:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL do servidor [!DNL Vertica]

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados

   ![](assets/vertica.png)

O conector é compatível com as seguintes opções:

| Opção | Descrição |
|---|---|
| TimeZoneName | É vazio por padrão, o que significa que o fuso horário do sistema do servidor de aplicativos Campaign Classic é usado. A opção pode ser usada para forçar o parâmetro da sessão TIMEZONE. |

