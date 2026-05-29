---
product: campaign
title: Configuração do acesso ao Amazon Redshift
description: Saiba como configurar o acesso ao Amazon Redshift no FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ef2b98bd-441e-4e59-bb41-4e835e250663
TQID: https://experienceleague.adobe.com/j-ZDe68d2AlmSqJsNTn8TAqN8Dq5jrB--lq5Ef4xJZY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 253
ht-degree: 26%

---

# Configuração do acesso ao Amazon Redshift {#configure-access-to-redshift}

Use a opção Campaign **Federated Data Access** (FDA) para processar informações armazenadas em bancos de dados externos. Siga as etapas abaixo para configurar o acesso ao Amazon Redshift.

1. Configurar o [banco de dados do Amazon Redshift](#configuring-redshift)
1. Configurar o Amazon Redshift [conta externa](#redshift-external) no Campaign

## Amazon Redshift no Linux {#redshift-linux}

Para configurar o [!DNL Amazon Redshift] no Linux, siga as etapas abaixo:

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
   ./redshift_odbc-setup.sh --help
   ```

1. Acesse o diretório onde o script está localizado e execute o script a seguir como um usuário root:

   ```
     cd /usr/local/neolane/nl6/bin/fda-setup-scripts
     ./redshift_odbc-setup.sh
   ```

1. Após instalar os drivers ODBC, é necessário reiniciar o Campaign Classic. Para fazer isso, execute o seguinte comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. No Campaign, você pode configurar a conta externa do [!DNL Amazon Redshift]. Para obter mais informações sobre como configurar sua conta externa, consulte [esta seção](#redshift-external).

## Conta externa do Amazon Redshift {#redshift-external}

A conta externa [!DNL Amazon Redshift] permite conectar a instância do Campaign ao banco de dados externo do Amazon Redshift.

1. No Campaign Classic, configure a conta externa do [!DNL Amazon Redshift]. No **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Amazon Redshift]**, você deve especificar:

   * **[!UICONTROL Type]**: Amazon Redshift

   * **[!UICONTROL Server]**: Nome do DNS

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: nome do banco de dados, se não estiver especificado no DSN. Pode ficar em branco, se estiver especificado no DSN

   * **[!UICONTROL Working schema]**: Nome do esquema de trabalho. [Saiba mais](https://docs.aws.amazon.com/redshift/latest/dg/r_Schemas_and_tables.html)

   * **[!UICONTROL Time zone]**: Fuso horário do servidor

   ![](assets/amazon_redshift.png)

1. Clique em **[!UICONTROL Save]**.
