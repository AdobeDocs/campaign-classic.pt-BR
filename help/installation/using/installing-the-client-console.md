---
title: Instalação do console do cliente
description: Saiba como instalar o console do cliente
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
translation-type: tm+mt
source-git-commit: 6d6f63fb6ac99c3a9e58a8670bc9bc59e6cfd420
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 11%

---


# Instalação do console do cliente Campaign{#installing-the-client-console}

O console do Campaign Client é um cliente avançado que permite a conexão com seu(s) servidor(es) de aplicativos do Campaign. 

Antes de iniciar, você precisa verificar a matriz [de](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)Compatibilidade de Campanha, obter o URL do servidor de Campanha e as credenciais do usuário.

>[!CAUTION]
>
>O console do Campaign Client e o servidor de aplicativos Campanhas devem ser executados na mesma versão do produto. O Adobe também recomenda usar a mesma compilação de produto.

## Download do console{#download-the-client-console}

Para baixar e instalar o console do cliente Adobe Campaign, siga as etapas abaixo:

1. Abra um navegador da Web e baixe o console do seguinte endereço:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Na janela de identificação, digite seu login e sua senha.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessário, use as credenciais da conta interna definida durante a criação da instância.

1. Clique no **[!UICONTROL Download]** link na página de instalação.
1. Baixe e salve o arquivo de configuração do cliente.
1. Execute o arquivo baixado em um computador no Windows: A instalação é start. O caminho de instalação padrão do console do cliente é **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, onde &#39;X&#39; é &#39;6&#39; ou &#39;7&#39;, de acordo com sua versão do Adobe Campaign.

>[!NOTE]
>
>No Windows, você pode iniciar o arquivo **nlclient.exe** diretamente do `[INSTALL]/bin` diretório em um servidor Windows, onde `[INSTALL]` é o caminho de acesso para a pasta de instalação do Adobe Campaign.

## Criar a conexão{#create-the-connection}

Depois que o console do cliente estiver instalado, siga as etapas abaixo para criar a conexão com o servidor de aplicativos:

1. Start o console do menu do Windows **[!UICONTROL Start]** , no grupo de programas **Adobe Campaign** .

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique em **[!UICONTROL Add > Connection]** e insira o rótulo e o URL do servidor de aplicativos Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos Adobe Campaign por meio de um URL. Use um DNS ou um alias da máquina ou seu endereço IP.

   Por exemplo, você pode usar o [`https://<machine>.<domain>.com`](https://myserver.adobe.com) tipo URL.

1. Se o Adobe IMS estiver configurado para sua organização, marque a opção **[!UICONTROL Connect with an Adobe ID]**

1. Click **[!UICONTROL Ok]** to save your settings.

Você pode adicionar quantas conexões forem necessárias para se conectar aos ambientes de teste, estágio e produção, por exemplo.

>[!NOTE]
>
>The **[!UICONTROL Add]** button lets you create **[!UICONTROL folders]** to organize all your connections. Basta arrastar e soltar cada conexão em uma pasta.

## Fazer logon no Adobe Campaign

Para fazer logon em uma instância existente, siga as etapas abaixo:

1. Start o console do menu do Windows **[!UICONTROL Start]** , no grupo de programas **Adobe Campaign** .

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão.

1. Selecione a instância de Campanha na qual você precisa fazer logon.

1. Clique em **[!UICONTROL Ok]**

1. Digite suas credenciais de logon de usuário e clique em **[!UICONTROL Log in]**

**Tópicos relacionados**

* [Criação de uma instância e fazer logon](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)
* [Instalar e configurar o Adobe Campaign Client](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/getting-started/install-and-setup-the-adobe-campaign-client.html) (vídeo)
