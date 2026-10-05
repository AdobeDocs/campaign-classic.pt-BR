---
product: campaign
title: Configuração do acesso ao SAP HANA
description: Saiba como configurar o acesso ao SAP HANA no FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
TQID: 'https://experienceleague.adobe.com/m2ibPllvRz-0vRS80bsktgY2qKdxL-fH9UEmHDgokT8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 67%
---
# Configuração do acesso ao SAP HANA {#configure-access-to-sap-hana}



Use a opção Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) para processar informações armazenadas em bancos de dados externos. Siga as etapas abaixo para configurar o acesso ao SAP HANA.

1. Configurar o [banco de dados SAP HANA](#sap-config)
1. Configurar a [conta externa](#sap-external) do SAP HANA no Campaign

## Drivers para SAP HANA {#sap-config}

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

## Conta externa do SAP HANA{#sap-external}

A conta externa do SAP HANA permite conectar a instância do Campaign ao banco de dados externo do SAP HANA.

1. Na Campanha **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL SAP Hana]**, você deve especificar:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL do servidor SAP Hana

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário
