---
product: campaign
title: Configuração do acesso ao Netezza
description: Saiba como configurar o acesso ao Netezza no FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 81%

---

# Configuração do acesso ao Netezza {#configure-access-to-netezza}



Usar a campanha [Federated Data Access](../../installation/using/about-fda.md) (FDA) para processar informações armazenadas em um banco de dados externo. Siga as etapas abaixo para configurar o acesso ao Netezza.

1. Instalar e configurar [Drivers de netezza](#netezza-config)
1. Configurar o Netezza [conta externa](#netezza-external) no Campaign

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

1. Do Campaign **[!UICONTROL Explorer]**, clique em **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clique em **[!UICONTROL New]** e selecione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar a conta externa do **[!UICONTROL Netezza]**, você deve especificar:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: o URL do servidor Netezza

   * **[!UICONTROL Account]**: Nome do usuário

   * **[!UICONTROL Password]**: Senha da conta do usuário

   * **[!UICONTROL Database]**: Nome do banco de dados

>[!NOTE]
>
>As operações em schemas que contêm chaves primárias geradas automaticamente não são consideradas.
>
>A tabela utilizará a cláusula **Organizar em** no primeiro índice definido no schema. Como esta cláusula é limitada de 1 até 4 colunas com Netezza, este índice não pode conter mais de 4 colunas.
