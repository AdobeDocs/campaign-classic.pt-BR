---
solution: Campaign Classic
product: campaign
title: Instalação do console do cliente
description: Saiba como instalar o console do cliente
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 14%

---


# Instalar o console do cliente do Campaign{#installing-the-client-console}

O console do Campaign Client é um cliente avançado que permite a conexão com seu(s) servidor(es) de aplicativos do Campaign. 

Antes de começar, você precisa verificar a [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html) do Campaign, obter o URL do servidor do Campaign e as credenciais do usuário.

>[!CAUTION]
>
>O console do Campaign Client e o servidor de aplicativos do Campaign devem ser executados na mesma versão de produto. A Adobe também recomenda usar a mesma build de produto.

![](assets/do-not-localize/how-to-video.png) Descubra como instalar e configurar o cliente do Adobe Campaign no  [vídeo](#video)

## Baixe o console{#download-the-client-console}

Para baixar e instalar o console do cliente Adobe Campaign, siga as etapas abaixo:

1. Abra um navegador da Web e baixe o console do seguinte endereço:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Na janela de identificação, digite o login e a senha.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessário, use as credenciais da conta interna definidas durante a criação da instância.

1. Clique no link **[!UICONTROL Download]** na página de instalação.
1. Baixe e salve o arquivo de configuração do cliente.
1. Execute o arquivo baixado em um computador no Windows: A instalação é iniciada. O caminho de instalação padrão do console do cliente é **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, onde &#39;X&#39; é &#39;6&#39; ou &#39;7&#39;, de acordo com sua versão do Adobe Campaign.

>[!NOTE]
>
>Você pode propor a atualização para a versão mais recente para todos os usuários do console do cliente do Campaign copiando o arquivo executável do console em uma pasta específica do servidor do Campaign Marketing. [Saiba mais](../../installation/using/client-console-availability-for-windows.md).


## Crie a conexão{#create-the-connection}

Depois que o console do cliente estiver instalado, siga as etapas abaixo para criar a conexão com o servidor de aplicativos:

1. Inicie o console pelo menu do Windows **[!UICONTROL Start]**, no grupo de programas **Adobe Campaign**.

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique em **[!UICONTROL Add > Connection]** e insira o rótulo e o URL do servidor de aplicativos do Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos do Adobe Campaign por meio de um URL. Use um DNS ou um alias da máquina ou seu endereço IP.

   Por exemplo, você pode usar o URL tipo [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

1. Se o Adobe IMS estiver configurado para sua organização, marque a opção **[!UICONTROL Connect with an Adobe ID]**

1. Clique em **[!UICONTROL Ok]** para salvar suas configurações.

Você pode adicionar quantas conexões forem necessárias para se conectar aos ambientes de teste, estágio e produção, por exemplo.

>[!NOTE]
>
>O botão **[!UICONTROL Add]** permite criar **[!UICONTROL folders]** para organizar todas as suas conexões. Basta arrastar e soltar cada conexão em uma pasta.

## Faça logon no Adobe Campaign

Para fazer logon em uma instância existente, siga as etapas abaixo:

1. Inicie o console pelo menu do Windows **[!UICONTROL Start]**, no grupo de programas **Adobe Campaign**.

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão.

1. Selecione a instância do Campaign na qual você precisa fazer logon.

1. Clique em **[!UICONTROL Ok]**

1. Insira suas credenciais de logon de usuário e clique em **[!UICONTROL Log in]**

**Tópicos relacionados**

* [Criação de uma instância e fazer logon](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matriz de compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## Vídeo tutorial

Este vídeo mostra como instalar e configurar o cliente do Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
