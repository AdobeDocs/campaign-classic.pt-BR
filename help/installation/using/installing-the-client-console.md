---
title: Instalação do console do cliente
seo-title: Instalação do console do cliente
description: Instalação do console do cliente
seo-description: null
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Instalação do console do cliente{#installing-the-client-console}

O procedimento de instalação do console do Adobe Campaign está detalhado abaixo.

Antes de instalar o console do Adobe Campaign, verifique os pré-requisitos listados na matriz [de compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Para instalar o console do Adobe Campaign, aplique as seguintes etapas:

1. Abra um navegador da Web e baixe o console do seguinte endereço:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. Na janela de identificação, digite seu login e sua senha.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessário, use as credenciais da conta interna definida durante a criação da instância.

1. Clique no **[!UICONTROL Download]** link na página de instalação.
1. Baixe e salve o arquivo de configuração do cliente.
1. Execute o arquivo baixado em um computador no Windows: A instalação é iniciada. O caminho de instalação padrão do console do cliente é **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, onde &#39;X&#39; é &#39;6&#39; ou &#39;7&#39;, de acordo com sua versão do Adobe Campaign.
1. Depois que o programa de instalação terminar, inicie o console no menu do Windows **[!UICONTROL Start]** (no grupo de programas do **Adobe Campaign** ).

>[!NOTE]
>
>No Windows, você pode iniciar o arquivo **nlclient.exe** diretamente do `[INSTALL]/bin` diretório em um servidor Windows, onde `[INSTALL]` é o caminho de acesso para a pasta de instalação do Adobe Campaign.\
>Para criar uma nova conexão, consulte [Criação de uma instância e logon](../../installation/using/creating-an-instance-and-logging-on.md).

