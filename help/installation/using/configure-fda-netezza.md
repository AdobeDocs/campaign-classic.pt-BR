---
product: campaign
title: Configuração do acesso ao Netezza
description: Saiba como configurar o acesso ao Netezza no FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
TQID: https://experienceleague.adobe.com/HiTQ6eoYcjp8pLqNmqLhiDTNhplE4ipnYlWuRFOZvog
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 376
ht-degree: 79%

---

# Configuração do acesso ao Netezza {#configure-access-to-netezza}



Use a opção Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) para processar informações armazenadas em bancos de dados externos. Siga as etapas abaixo para configurar o acesso ao Netezza.

1. Instalar e configurar [drivers do Netezza](#netezza-config)
1. Configurar a [conta externa](#netezza-external) do Netezza no Campaign

## Configuração do Netezza {#netezza-config}

A conexão com um banco de dados externo Netezza no FDA exige as seguintes configurações adicionais no servidor do Adobe Campaign.

1. Instale os drivers ODBC do Netezza, de acordo com o sistema operacional que você utiliza:

   * **nz-linuxclient-v7.2.0.0.tar.gz para Linux.** Selecione a pasta que corresponde ao seu sistema operacional (linux ou linux64) e inicie o comando unpack. Você pode deixar a instalação ser executada no repositório sugerido por padrão: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip para Windows.** Descompacte o arquivo e inicie o script executável que corresponde ao seu sistema operacional: nzodbcsetup.exe ou nzodbcsetup64.exe. Siga as instruções do assistente para concluir a instalação dos drivers.

1. Configure o driver ODBC. A configuração pode ser realizada nos arquivos padrão: **/etc/odbc.ini** para parâmetros gerais e **/etc/odbcinst.ini** para declaração de drivers.

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     ```

     &quot;InstallDir&quot; corresponde ao local do arquivo odbcinst.ini.

   * **/etc/odbcinst.ini**

     ```
     [ODBC Drivers]
     NetezzaSQL = Installed
     
     [NetezzaSQL]
     Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
     Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
     APILevel         = 1
     ConnectFunctions = YYN
     Description      = Netezza ODBC driver
     DriverODBCVer    = 03.51
     DebugLogging     = false
     LogPath          = /tmp
     UnicodeTranslationOption = utf8
     CharacterTranslationOption = all
     PreFetch         = 256
     Socket           = 16384
     ```

1. Especifique as variáveis de ambiente do servidor do Adobe Campaign:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib e /usr/local/nz/lib64. &quot;/usr/local/nz&quot; corresponde ao repositório de instalação oferecido por padrão ao instalar os drivers. Aqui você precisa especificar o repositório selecionado para a instalação.
   * **ODBCINI**: local do arquivo odbc.ini (por exemplo /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: local do arquivo odbc.ini. Netezza também exige essa segunda variável para utilizar o arquivo odbc.ini.

## Conta externa do Netezza {#netezza-external}

A conta externa do Netezza permite conectar a instância do Campaign ao banco de dados externo do Netezza.

1. Na Campanha **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Netezza]**, você deve especificar:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: o URL do servidor Netezza

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados

>[!NOTE]
>
>As operações em esquemas que contêm chaves primárias geradas automaticamente não são consideradas.
>
>A tabela utilizará a cláusula **Organizar em** no primeiro índice definido no esquema. Como esta cláusula é limitada de 1 até 4 colunas com Netezza, este índice não pode conter mais de 4 colunas.
