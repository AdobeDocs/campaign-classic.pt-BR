---
product: campaign
title: Configuração do acesso ao Sybase IQ
description: Saiba como configurar o acesso ao Sybase IQ na FDA
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 73%

---

# Configuração do acesso ao Sybase IQ {#configure-access-to-sybase-iq}



Usar a campanha **Federated Data Access** (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso ao Sybase IQ.

1. Configurar [banco de dados do Sybase IQ](#configuring-sybase)
1. Configurar o Sybase IQ [conta externa](#sybase-external) no Campaign

## Configuração de sybase IQ {#configuring-sybase}

A conexão com um banco de dados externo Sybase IQ no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign.

>[!NOTE]
>
>Antes de iniciar, verifique se **unixodbc** o pacote está no servidor.

1. Instale o **iq_odbc**. Um erro pode ocorrer no final da instalação. Esse erro pode ser ignorado.

1. Instale o **iq_client_common**. Um erro Java pode ocorrer no final da instalação. Esse erro pode ser ignorado.

1. Configure o driver ODBC. A configuração pode ser realizada nos arquivos padrão: /etc/odbc.ini para parâmetros gerais e /etc/odbcinst.ini para declaração de drivers:

   * **/etc/odbc.ini** (substitua os valores como caracteres `<server_alias>`pelos seus próprios):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Adicione o caminho para a nova biblioteca libodbc16.so na variável LD_LIBRARY_PATH. Para fazer isso:

   * Se você estiver usando um arquivo customer.sh para declarar seu caminho: adicione o caminho /opt/sybase/IQ-16_0/lib64 para a variável LD_LIBRARY_PATH.
   * Caso contrário, use um comando Unix.

## Conta externa de sybase IQ {#sybase-external}

A conta externa Sybase IQ permite conectar a instância do Campaign ao banco de dados externo do Sybase IQ.

1. Do Campaign **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Sybase IQ]**, você deve especificar:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Corresponde à conexão ODBC (`<server_alias>`) definida na etapa 5. Não é necessariamente o nome do próprio servidor.

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados

>[!NOTE]
>
>Para o Windows, você deve instalar o cliente Sybase IQ no servidor do Adobe Campaign e criar uma conexão ODBC. Crie uma fonte de dados do sistema quando o servidor do Adobe Campaign (nlserver) está em execução como um serviço no Windows.
