---
product: campaign
title: Configuração do acesso ao Oracle
description: Saiba como configurar o acesso ao Oracle no FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 71%

---

# Configuração do acesso ao Oracle {#configure-access-to-oracle}



Use a opção Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) para processar informações armazenadas em bancos de dados externos. Siga as etapas abaixo para configurar o acesso ao Oracle.

1. Configurar o Oracle no [Linux](#oracle-linux) ou [Windows](#azure-windows)
1. Configurar o Oracle [conta externa](#oracle-external) no Campaign

## Oracle no Linux {#oracle-linux}

A conexão com um banco de dados externo Oracle no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign:

1. Instale o cliente completo do Oracle correspondente à sua versão do Oracle.
1. Adicione suas definições de TNS à instalação. Para fazer isso, especifique em um arquivo **tnsnames.ora** no repositório /etc/oracle. Crie o repositório, caso ele não exista.

   Em seguida, crie uma nova variável de ambiente TNS_ADMIN: exporte TNS_ADMIN=/etc/oracle e reinicie a máquina.

1. Integre o Oracle ao seu servidor do Adobe Campaign (nlserver). Para fazer isso, verifique se o arquivo **customer.sh** está na pasta &quot;nl6&quot; da estrutura da árvore do servidor do Adobe Campaign e se inclui os links para as bibliotecas Oracle.

   Por exemplo, para um cliente em 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Esses valores (particularmente ORACLE_HOME) dependem dos repositórios de instalação. Verifique sua estrutura de árvore antes de fazer referência a esses valores.

1. Instale as bibliotecas necessárias para Oracle:

   * **libclntsh.so**

     ```
     cd /usr/lib/oracle/<version>/client<architecture>/lib
     ln -s libclntsh.so.<version> libclntsh.so
     ```

   * **libaio1**

     ```
     apt install libaio1
     or
     yum install libaio1
     ```

1. No Campaign Classic, você pode configurar a conta externa do [!DNL Oracle]. Para obter mais informações sobre como configurar sua conta externa, consulte [esta seção](#oracle-external).

## Oracle no Windows {#oracle-windows}

A conexão com um banco de dados externo Oracle no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign:

1. Instale o software cliente Oracle.

1. Na pasta C:\Oracle, crie um arquivo **tnsnames.ora** contendo sua definição TNS.

1. Adicione uma variável de ambiente TNS_ADMIN com C:\Oracle como valor e reinicie o computador.

1. No Campaign Classic, você pode configurar a conta externa do [!DNL Oracle]. Para obter mais informações sobre como configurar sua conta externa, consulte [esta seção](#oracle-external).

## Conta externa do Oracle {#oracle-external}

A conta externa [!DNL Oracle] permite conectar a instância do Campaign ao banco de dados externo do Oracle.

1. Na Campanha **[!UICONTROL Explorer]**, selecione **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Escolha **[!UICONTROL New]**.

1. Selecione **[!UICONTROL External database]** como sua conta externa **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Oracle]**, você deve especificar:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Nome do DNS

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Time zone]**: Fuso horário do servidor

   ![](assets/oracle_config.png)
