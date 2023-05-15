---
product: campaign
title: Configuração do acesso ao PostgreSQL
description: Saiba como configurar o acesso ao PostgreSQL
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 11%

---

# Configuração do acesso ao PostgreSQL {#configure-fda-postgresql}



Usar Campanha **Federated Data Access** (FDA) opção para processar informações armazenadas em um banco de dados PostgreSQL externo.

## Configuração PostgreSQL {#postgresql-configuration}

Primeiro precisa instalar o Libpq. O Libpq permite que programas clientes enviem consultas para o servidor de back-end PostgreSQL e recebam os resultados dessas consultas.

Siga as etapas abaixo para configurar o acesso ao [!DNL PostgreSQL]:

* Para CentOS, execute o seguinte comando `sudo apt-get -y install libpq-dev`.

* Para Linux, execute o seguinte comando `yum install postgresql-devel`.

* Para Windows, o Libpq é implementado por meio de `libpq.dll` que está incluído na instalação do Adobe Campaign.

No Adobe Campaign, você pode configurar [!DNL PostgreSQL] conta externa. Para obter mais informações sobre como configurar a conta externa, consulte [esta seção](#postgresql-external).

## Conta externa PostgreSQL {#postgresql-external}

>[!NOTE]
>
> O PostgreSQL está disponível no CentOS 7 e 6.

Você precisa criar um [!DNL PostgreSQL] conta externa para conectar a instância do Campaign à [!DNL PostgreSQL] banco de dados externo.

1. Da campanha **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Em **[!UICONTROL Configuration]**, selecione [!DNL PostgreSQL, Greenplum] do **[!UICONTROL Type]** lista suspensa.

   ![](assets/postgresql_1.png)

1. Configure o **[!UICONTROL PostgreSQL]** autenticação de conta externa:

   * **[!UICONTROL Server]**: URL da [!DNL PostgreSQL] servidor.

   * **[!UICONTROL Account]**: Nome do usuário.

   * **[!UICONTROL Password]**: Senha da conta do usuário.

   * **[!UICONTROL Database]**: Nome do banco de dados (opcional).

   * **[!UICONTROL Working schema]**: Nome do seu schema de trabalho. [Saiba mais](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: Fuso horário definido em [!DNL PostgreSQL]. [Saiba mais](https://www.postgresql.org/docs/7.2/timezones.html)

1. Clique na guia **[!UICONTROL Parameters]** e depois no botão **[!UICONTROL Deploy functions]** para criar as funções.

   >[!NOTE]
   >
   >Para que todas as funções estejam disponíveis, é necessário criar as funções Adobe Campaign SQL no banco de dados remoto. Para obter mais informações, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

1. Clique em **[!UICONTROL Save]** quando a configuração for concluída.

O conector é compatível com as seguintes opções:

| Opção | Descrição |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Aguardar a conexão, em segundos. <br>Para obter mais informações, consulte [Documentação PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Número de segundos de inatividade após os quais o TCP deve enviar uma mensagem keepalive ao servidor. <br>Para obter mais informações, consulte [Documentação PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Número de segundos após o qual a mensagem de manutenção de TCP não confirmada pelo servidor deve ser retransmitida.  <br>Para obter mais informações, consulte [Documentação PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Número de chaves TCP que podem ser perdidas antes que a conexão do cliente com o servidor seja considerada inativa. <br>Para obter mais informações, consulte [Documentação PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
