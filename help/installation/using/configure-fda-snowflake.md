---
product: campaign
title: Configuração do acesso ao Snowflake
description: Saiba como configurar o acesso ao Snowflake no FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 32%

---

# Configuração do acesso ao Snowflake {#configure-access-to-snowflake}

Use a opção Campaign **Federated Data Access** (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso ao [!DNL Snowflake].

1. Configurar [!DNL Snowflake] no [Linux](#snowflake-linux).
1. Configurar a [!DNL Snowflake] [conta externa](#snowflake-external) no Campaign

>[!NOTE]
>
>[!DNL Snowflake]O conector de está disponível para implantações locais e hospedadas. Para obter mais informações, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake no Linux {#snowflake-linux}

Para configurar o [!DNL Snowflake] no Linux, siga as etapas abaixo:

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

1. Antes de executar o script, você pode ter acesso a mais informações com a opção `--help`:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. Acesse o diretório onde o script está localizado e execute o script a seguir como um usuário root:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./snowflake_odbc-setup.sh
   ```

1. Após instalar os drivers ODBC, é necessário reiniciar o Campaign Classic. Para fazer isso, execute o seguinte comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. No Campaign, você pode configurar a conta externa do [!DNL Snowflake]. Para obter mais informações sobre como configurar sua conta externa, consulte [esta seção](#snowflake-external).

## conta externa Snowflake {#snowflake-external}

É necessário criar uma conta externa [!DNL Snowflake] para conectar a instância do Campaign ao banco de dados externo [!DNL Snowflake].

1. Na Campanha **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Em **[!UICONTROL Configuration]**, selecione [!DNL Snowflake] no menu suspenso **[!UICONTROL Type]**.

   ![](assets/snowflake_5.png)

1. Adicione a URL **[!UICONTROL Server]** e **[!UICONTROL Database]**.

1. Configurar a autenticação da conta externa do **[!UICONTROL Snowflake]**:

   * Para autenticação de conta/senha, você deve especificar:

      * **[!UICONTROL Account]**: Nome do usuário

      * **[!UICONTROL Password]**: Senha da conta de usuário.

     ![](assets/snowflake.png)

   * Para autenticação de Par de Chaves, clique na guia **[!UICONTROL Keypair Auth]** para usar seu **[!UICONTROL Private key]** para autenticar e copiar e colar seu **[!UICONTROL Private key]**.

     ![](assets/snowflake_4.png)

1. Clique na guia **[!UICONTROL Parameters]** e depois no botão **[!UICONTROL Deploy functions]** para criar as funções.

   >[!NOTE]
   >
   >Para que todas as funções estejam disponíveis, você precisa criar as funções Adobe Campaign SQL no banco de dados remoto. Para obter mais informações, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. Clique em **[!UICONTROL Save]** quando a configuração for concluída.

O conector é compatível com as seguintes opções:

| Opção | Descrição |
|---|---|
| schema de trabalho | schema de banco de dados que deve ser usado para tabelas de trabalho |
| depósito | Nome do depósito padrão que deve ser usado. Ele substituirá o padrão do usuário. |
| TimeZoneName | É vazio por padrão, o que significa que o fuso horário do sistema do servidor de aplicativos Campaign Classic é usado. A opção pode ser usada para forçar o parâmetro da sessão TIMEZONE. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parâmetro de sessão WEEK_START. Por padrão, defina como 0. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.com/br/sql-reference/parameters.html#week-start). |
| UseCachedResult | Parâmetro de sessão USE_CACHED_RESULTS. Por padrão, defina como TRUE. Esta opção pode ser usada para desativar os resultados em cache de Snowflake. <br>[Para obter mais informações, consulte esta página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
| bulkThreads | Número de threads a serem usados para o carregador em massa Snowflake; mais threads significam melhor desempenho para cargas em massa maiores. Por padrão, defina como 1. O número pode ser ajustado, dependendo da contagem de threads do computador. |
| tamanhoParte | Determina o tamanho do arquivo do bloco do carregador em massa. Por padrão, defina como 128 MB. Pode ser modificado para obter um desempenho melhor, quando usado com bulkThreads. Mais threads ativos simultâneos significam melhor desempenho. <br>Para obter mais informações, consulte a [documentação sobre o Snowflake](https://docs.snowflake.net/manuals/sql-reference/sql/put.html). |
| NomeEstágio | Nome do estágio interno pré-provisionado. Ele será usado no carregamento em massa em vez de criar um novo estágio temporário. |
