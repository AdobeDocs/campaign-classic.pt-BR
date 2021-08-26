---
product: campaign
title: Configuração do acesso ao Snowflake
description: Saiba como configurar o acesso ao Snowflake no FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 72%

---

# Configuração do acesso ao Snowflake {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

Use a opção Campaign **Federated Data Access** (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso a [!DNL Snowflake].

1. Configurar [!DNL Snowflake] em [CentOS](#snowflake-centos), [Windows](#snowflake-windows) ou [Debian](#snowflake-debian)
1. Configure a [!DNL Snowflake] [conta externa](#snowflake-external) no Campaign


>[!NOTE]
>
>[!DNL Snowflake]O conector de está disponível para implantações locais e hospedadas. Para obter mais informações, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake no CentOS {#snowflake-centos}

Para configurar [!DNL Snowflake] no CentOS, siga as etapas abaixo:

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

1. No Campaign, você pode configurar a conta externa [!DNL Snowflake]. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#snowflake-external).

## Snowflake no Windows {#snowflake-windows}

1. Instale o [driver ODBC para Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Observe que é necessário ter os privilégios de nível de administrador para instalar o driver. Para obter mais informações, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configure o driver ODBC. Para obter mais informações, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. No Campaign, você pode configurar a conta externa [!DNL Snowflake]. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#snowflake-external).

## Snowflake no Debian {#snowflake-debian}

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

1. No Campaign, você pode configurar a conta externa [!DNL Snowflake]. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#snowflake-external).

## Conta externa do Snowflake {#snowflake-external}

Você precisa criar uma conta externa [!DNL Snowflake] para conectar a instância do Campaign ao banco de dados externo [!DNL Snowflake].

1. Em Campanha **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Snowflake]**, você deve especificar:

   * **[!UICONTROL Type]**: [!DNL Snowflake]

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
| TimeZoneName | É vazio por padrão, o que significa que o fuso horário do sistema do servidor de aplicativos Campaign Classic é usado. A opção pode ser usada para forçar o parâmetro da sessão TIMEZONE. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parâmetro de sessão WEEK_START. Por padrão, defina como 0. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.com/br/sql-reference/parameters.html#week-start). |
| UseCachedResult | Parâmetro de sessão USE_CACHED_RESULTS. Por padrão, defina como TRUE. Esta opção pode ser usada para desativar os resultados em cache do Snowflake. <br>Para obter mais informações, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
