---
product: campaign
title: Instalação do servidor
description: Instalação do servidor
feature: Installation, Instance Settings
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 3%

---

# Instalação do servidor{#installing-the-server}

## Execução do programa de instalação {#executing-the-installation-program}

Para uma plataforma Windows de 32 bits, instale o Adobe Campaign de 32 bits. Para uma plataforma Windows de 64 bits, instale o Adobe Campaign de 64 bits.

As etapas de instalação do servidor Adobe Campaign são as seguintes:

1. Execute o arquivo **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. Selecione o tipo de instalação.

   ![](assets/s_ncs_install_installer_01a.png)

   Vários tipos de instalação estão disponíveis:

   * **[!UICONTROL Installation of an application server]** : Instale o servidor de aplicativos Adobe Campaign e o console do cliente.
   * **[!UICONTROL Minimal installation (Network)]** : Instalação do computador cliente a partir da rede. Somente um número limitado de DLLs será instalado no computador, se necessário, e todos os outros componentes serão usados de uma unidade de rede.
   * **[!UICONTROL Installation of a client]** : Instalação dos componentes necessários para o cliente do Adobe Campaign.
   * **[!UICONTROL Custom installation]** : o usuário escolhe os elementos a serem instalados.

   Selecione **Instalação de um servidor de aplicativos** e passe pelas diferentes etapas, conforme mostrado abaixo:

   ![](assets/s_ncs_install_installer_02.png)

1. Selecione o diretório de instalação:

   ![](assets/s_ncs_install_installer_03.png)

1. Clique em **[!UICONTROL Finish]** para iniciar a instalação:

   ![](assets/s_ncs_install_installer_04.png)

   A barra de progresso mostra a distância da instalação:

   ![](assets/s_ncs_install_installer_05.png)

   Quando a instalação estiver concluída, uma mensagem será exibida para avisá-lo:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >Quando a instalação do servidor estiver concluída, será necessário reinicializar o servidor para evitar possíveis problemas de rede.

   Quando a instalação estiver concluída, inicie o Adobe Campaign para criar os arquivos de configuração. Consulte [Primeira inicialização do servidor](#first-start-up-of-the-server).

## Teste de instalação de resumo {#summary-installation-testing}

Você pode testar a instalação inicial usando o seguinte comando:

```sql
nlserver pdump
```

Se o Adobe Campaign não for iniciado, a resposta será:

```sql
No task
```

## Primeira inicialização do servidor {#first-start-up-of-the-server}

Quando o teste de instalação estiver concluído, abra um prompt de comando através do menu **[!UICONTROL Start > Programs > Adobe Campaign]** e digite o seguinte comando:

```sql
nlserver web
```

Os arquivos no diretório de instalação são usados para configurar os módulos do servidor do Adobe Campaign.

As seguintes informações são exibidas:

```sql
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

Pressione **Ctrl+C** para parar o processo e digite o seguinte comando:

```sql
nlserver start web
```

As seguintes informações são exibidas:

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Para interrompê-lo, digite:

```sql
nlserver stop web
```

As seguintes informações são exibidas:

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Senha do identificador interno {#password-for-the-internal-identifier}

O servidor do Adobe Campaign define um logon técnico chamado **interno** que tem todos os direitos em todas as instâncias. Logo após a instalação, o login não terá uma senha. É obrigatório definir um.

Saiba mais [nesta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

## Iniciando serviços do Adobe Campaign {#starting-adobe-campaign-services}

Para iniciar os serviços da Adobe Campaign, você pode usar o gerenciador de serviços ou inserir o seguinte na linha de comando (com os direitos apropriados):

```sql
net start nlserver6
```

Se precisar interromper os processos do Adobe Campaign posteriormente, use o comando:

```sql
net stop nlserver6
```

## Instalação do LibreOffice {#installing-libreoffice}

Baixe o LibreOffice e siga as etapas regulares de instalação.

Adicione a seguinte variável de ambiente:

```sql
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
