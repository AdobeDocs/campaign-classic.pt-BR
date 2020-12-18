---
solution: Campaign Classic
product: campaign
title: Instalação do console do cliente
description: Saiba como instalar o console do cliente
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: cea4a26935312b1cb119a3fa671af7bf00788fe9
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 13%

---


# Instalando o console do cliente Campaign{#installing-the-client-console}

O console do Campaign Client é um cliente avançado que permite a conexão com seu(s) servidor(es) de aplicativos do Campaign. 

Antes de iniciar, você precisa verificar a Campanha [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html), obter o URL do servidor de Campanha e as credenciais do usuário.

>[!CAUTION]
>
>O console do Campaign Client e o servidor de aplicativos Campanhas devem ser executados na mesma versão do produto. O Adobe também recomenda usar a mesma compilação de produto.

![](assets/do-not-localize/how-to-video.png) Descubra como instalar e configurar o Adobe Campaign Client em  [vídeo](#video)

## Baixe o console{#download-the-client-console}

Para baixar e instalar o console do cliente Adobe Campaign, siga as etapas abaixo:

1. Abra um navegador da Web e baixe o console do seguinte endereço:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Na janela de identificação, digite seu login e sua senha.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessário, use as credenciais da conta interna definida durante a criação da instância.

1. Clique no link **[!UICONTROL Download]** na página de instalação.
1. Baixe e salve o arquivo de configuração do cliente.
1. Execute o arquivo baixado em um computador no Windows: A instalação é start. O caminho de instalação padrão do console do cliente é **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, onde &#39;X&#39; é &#39;6&#39; ou &#39;7&#39;, de acordo com sua versão do Adobe Campaign.

>[!NOTE]
>
>No Windows, você pode iniciar o arquivo **nlclient.exe** diretamente do diretório `[INSTALL]/bin` em um servidor Windows, onde `[INSTALL]` é o caminho de acesso para a pasta de instalação do Adobe Campaign.

## Criar a conexão{#create-the-connection}

Depois que o console do cliente estiver instalado, siga as etapas abaixo para criar a conexão com o servidor de aplicativos:

1. Start o console do menu Windows **[!UICONTROL Start]**, no grupo de programas **Adobe Campaign**.

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique em **[!UICONTROL Add > Connection]** e insira o rótulo e o URL do servidor de aplicativos Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos Adobe Campaign por meio de um URL. Use um DNS ou um alias da máquina ou seu endereço IP.

   Por exemplo, você pode usar o URL do tipo [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

1. Se o Adobe IMS estiver configurado para sua organização, marque a opção **[!UICONTROL Connect with an Adobe ID]**

1. Clique em **[!UICONTROL Ok]** para salvar suas configurações.

Você pode adicionar quantas conexões forem necessárias para se conectar aos ambientes de teste, estágio e produção, por exemplo.

>[!NOTE]
>
>O botão **[!UICONTROL Add]** permite que você crie **[!UICONTROL folders]** para organizar todas as conexões. Basta arrastar e soltar cada conexão em uma pasta.

## Fazer logon no Adobe Campaign

Para fazer logon em uma instância existente, siga as etapas abaixo:

1. Start o console do menu Windows **[!UICONTROL Start]**, no grupo de programas **Adobe Campaign**.

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão.

1. Selecione a instância de Campanha na qual você precisa fazer logon.

1. Clique em **[!UICONTROL Ok]**

1. Digite suas credenciais de logon de usuário e clique em **[!UICONTROL Log in]**

**Tópicos relacionados**

* [Criação de uma instância e fazer logon](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matriz de compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## Vídeo tutorial

Este vídeo mostra como instalar e configurar o Adobe Campaign Client.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
