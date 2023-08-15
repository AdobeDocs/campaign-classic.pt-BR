---
product: campaign
title: Configuração do acesso ao PostgreSQL
description: Saiba como configurar o acesso ao PostgreSQL
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 12%

---

# Configuração do acesso ao PostgreSQL {#configure-fda-postgresql}



Usar a campanha **Federated Data Access** (FDA) opção para processar informações armazenadas em um banco de dados PostgreSQL externo.

## Configuração do PostgreSQL {#postgresql-configuration}

Primeiro precisa instalar o Libpq. O Libpq permite que os programas clientes enviem consultas ao servidor de back-end PostgreSQL e recebam os resultados dessas consultas.

Siga as etapas abaixo para configurar o acesso ao [!DNL PostgreSQL]:

* Para o CentOS, execute o seguinte comando `sudo apt-get -y install libpq-dev`.

* No Linux, execute o seguinte comando `yum install postgresql-devel`.

* Para Windows, o Libpq é implementado por meio de `libpq.dll` que está incluído na instalação do Adobe Campaign.

No Adobe Campaign, você pode configurar as [!DNL PostgreSQL] conta externa. Para obter mais informações sobre como configurar a conta externa, consulte [nesta seção](#postgresql-external).

## Conta externa PostgreSQL {#postgresql-external}

>[!NOTE]
>
> O PostgreSQL está disponível no CentOS 7 e 6.

É necessário criar um [!DNL PostgreSQL] conta externa para conectar a instância do Campaign à [!DNL PostgreSQL] banco de dados externo.

1. Do Campaign **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Em **[!UICONTROL Configuration]**, selecione [!DNL PostgreSQL, Greenplum] do **[!UICONTROL Type]** menu suspenso.

   ![](assets/postgresql_1.png)

1. Configure o **[!UICONTROL PostgreSQL]** autenticação de conta externa:

   * **[!UICONTROL Server]**: O URL do [!DNL PostgreSQL] servidor.

   * **[!UICONTROL Account]**: Nome do usuário.

   * **[!UICONTROL Password]**: Senha da conta do usuário.

   * **[!UICONTROL Database]**: Nome do banco de dados (opcional).

   * **[!UICONTROL Working schema]**: Nome do esquema de trabalho. [Saiba mais](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: Fuso horário definido em [!DNL PostgreSQL]. [Saiba mais](https://www.postgresql.org/docs/7.2/timezones.html)

1. Clique na guia **[!UICONTROL Parameters]** e depois no botão **[!UICONTROL Deploy functions]** para criar as funções.

   >[!NOTE]
   >
   >Para que todas as funções estejam disponíveis, você precisa criar as funções Adobe Campaign SQL no banco de dados remoto. Para obter mais informações, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

1. Clique em **[!UICONTROL Save]** quando a configuração for concluída.

O conector é compatível com as seguintes opções:

| Opção | Descrição |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Espera máxima por conexão, em segundos. <br>Para obter mais informações, consulte [Documentação do PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Número de segundos de inatividade após o qual o TCP deve enviar uma mensagem de manutenção de atividade para o servidor. <br>Para obter mais informações, consulte [Documentação do PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Número de segundos após o qual a mensagem de manutenção de atividade TCP não confirmada pelo servidor deve ser retransmitida.  <br>Para obter mais informações, consulte [Documentação do PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Número de manutenções de atividades de TCP que podem ser perdidas antes que a conexão do cliente com o servidor seja considerada inoperante. <br>Para obter mais informações, consulte [Documentação do PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
