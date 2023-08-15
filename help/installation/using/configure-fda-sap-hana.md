---
product: campaign
title: Configuração do acesso ao SAP HANA
description: Saiba como configurar o acesso ao SAP HANA no FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 72%

---

# Configuração do acesso ao SAP HANA {#configure-access-to-sap-hana}



Usar a campanha [Federated Data Access](../../installation/using/about-fda.md) (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso ao SAP HANA.

1. Configurar [banco de dados SAP HANA](#sap-config)
1. Configurar o SAP HANA [conta externa](#sap-external) no Campaign

## drivers SAP HANA {#sap-config}

A conexão com um banco de dados externo SAP HANA no FDA exige determinadas configurações adicionais no servidor do Adobe Campaign:

1. Instale os drivers ODBC para SAP HANA, de acordo com o sistema operacional que você usa:

   * **hdb_client_linux.tgz para Linux.** Após descompactado, inicie o comando hdbinst e siga as instruções para finalizar a instalação dos drivers.
   * **hdb_client_windows.zip para Windows.** Descompacte o arquivo e inicie o executável: **hdbinst.exe**. Siga as instruções do assistente para concluir a instalação dos drivers.

1. Configure o driver ODBC. A configuração pode ser realizada nos arquivos padrão: /etc/odbc.ini para parâmetros gerais e /etc/odbcinst.ini para declaração de drivers.

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     
     [HDB]
     Driver=HDBODBC
     servernode=localhost:39013 (this value depend of your server)
     User:SYSTEM
     ```

     &quot;InstallDir&quot; corresponde ao local do arquivo **odbcinst.ini**.

   * **/etc/odbcinst.ini**

     ```
     [HDBODBC]
     Description = "SmartCloudPT HANA"
     Driver = /usr/sap/hdbclient/libodbcHDB.so
     ```

1. Especifique as variáveis de ambiente do servidor do Adobe Campaign:

   * **LD_LIBRARY_PATH**: deve incluir o link para o cliente SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) por padrão.
   * **ODBCINI**: local do arquivo odbc.ini (por exemplo /etc/odbc.ini).

## conta externa SAP HANA{#sap-external}

A conta externa SAP HANA permite conectar a instância do Campaign ao banco de dados externo SAP HANA.

1. Do Campaign **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL SAP Hana]**, você deve especificar:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL do servidor SAP Hana

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário
