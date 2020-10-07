---
title: Instalação do servidor
seo-title: Instalação do servidor
description: Instalação do servidor
seo-description: null
page-status-flag: never-activated
uuid: 02534211-c267-490d-b9c1-78f56f1284e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1510fd9-995b-46c6-8d57-e1fe3999235e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 2%

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
   * **[!UICONTROL Minimal installation (Network)]** : Instalação do computador cliente da rede. Apenas um número limitado de DLLs será instalado no computador, se necessário, e todos os outros componentes serão usados de uma unidade de rede.
   * **[!UICONTROL Installation of a client]** : Instalação dos componentes necessários para o cliente Adobe Campaign.
   * **[!UICONTROL Custom installation]** : O usuário escolhe os elementos a serem instalados.

   Selecione **Instalação de um servidor** de aplicativos e siga as diferentes etapas, conforme mostrado abaixo:

   ![](assets/s_ncs_install_installer_02.png)

1. Selecione o diretório de instalação:

   ![](assets/s_ncs_install_installer_03.png)

1. Clique **[!UICONTROL Finish]** para start da instalação:

   ![](assets/s_ncs_install_installer_04.png)

   A barra de progresso mostra até que ponto a instalação está:

   ![](assets/s_ncs_install_installer_05.png)

   Quando a instalação estiver concluída, será exibida uma mensagem informando:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >Quando a instalação do servidor estiver concluída, uma reinicialização do servidor será necessária para evitar possíveis problemas de rede.

   Quando a instalação estiver concluída, start a Adobe Campaign para criar os arquivos de configuração. Consulte [Primeiro start do servidor](#first-start-up-of-the-server).

## Teste de instalação de resumo {#summary-installation-testing}

Você pode testar a instalação inicial usando o seguinte comando:

```
nlserver pdump
```

Se o Adobe Campaign não for iniciado, a resposta será:

```
No task
```

## Primeiro start do servidor {#first-start-up-of-the-server}

Quando o teste de instalação estiver concluído, abra um prompt de comando pelo **[!UICONTROL Start > Programs > Adobe Campaign]** menu e digite o seguinte comando:

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

Os arquivos no diretório de instalação são usados para configurar os módulos do servidor Adobe Campaign.

As seguintes informações são exibidas:

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

Pressione **Ctrl+C** para parar o processo e, em seguida, digite o seguinte comando:

```
nlserver start web
```

As seguintes informações são exibidas:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Para pará-lo, digite:

```
nlserver stop web
```

As seguintes informações são exibidas:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Senha do identificador interno {#password-for-the-internal-identifier}

O servidor Adobe Campaign define um logon técnico chamado **interno** que tem todos os direitos em todas as instâncias. Logo após a instalação, o logon não tem uma senha. É obrigatório definir um.

Consulte o identificador [interno](../../installation/using/campaign-server-configuration.md#internal-identifier)da seção.

## Starting Adobe Campaign services {#starting-adobe-campaign-services}

Para start dos serviços da Adobe Campaign, você pode usar o gerenciador de serviços ou inserir o seguinte na linha de comando (com os direitos apropriados):

```
net start nlserver6
```

Se você precisar parar os processos do Adobe Campaign mais tarde, use o comando:

```
net stop nlserver6
```

## Instalação do LibreOffice {#installing-libreoffice}

Baixe o LibreOffice, por exemplo, em [https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/) , e siga as etapas normais de instalação.

Adicione a seguinte variável de ambiente:

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```

