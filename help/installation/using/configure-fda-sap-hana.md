---
title: Configuração do acesso ao SAP HANA
description: Saiba como configurar o acesso ao SAP HANA no FDA
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 71%

---


# Configuração do acesso ao SAP HANA {#configure-access-to-sap-hana}

Use a opção Campanha [Federated Data Acces](../../installation/using/about-fda.md) (FDA) para processar informações armazenadas em bancos de dados externos. Siga as etapas abaixo para configurar o acesso ao SAP HANA.

1. Configurar banco de dados [SAP HANA](#sap-config)
1. Configure a [conta externa](#sap-external) SAP HANA na Campanha

## Drivers SAP HANA {#sap-config}

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

## CONTA EXTERNA SAP HANA{#sap-external}

A conta externa SAP HANA permite que você conecte a instância da Campanha ao banco de dados externo da SAP HANA.

1. Na Campanha **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL SAP Hana]**, você deve especificar:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL do servidor SAP Hana

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário
