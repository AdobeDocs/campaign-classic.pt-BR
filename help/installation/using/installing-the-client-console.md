---
product: campaign
title: Instalação do console do cliente
description: Saiba como instalar o console do cliente
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 5%

---

# Instalar e atualizar o console do cliente do Campaign{#installing-the-client-console}

![](../../assets/v7-only.svg)

O Console do Cliente do Campaign é um cliente avançado que permite a conexão com o(s) servidor(es) de aplicativos do Campaign.

Before starting to install the Client Console, you need to:

* Verifique a compatibilidade do sistema e das ferramentas com o Adobe Campaign no [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Obter o URL do servidor do Campaign
* Obter suas credenciais de usuário

O processo para instalar ou atualizar o console do cliente varia dependendo da implementação do Adobe Campaign Classic.
Revise os detalhes abaixo para entender o que é necessário para sua implementação.

![](assets/do-not-localize/how-to-video.png) Saiba como instalar e configurar o Adobe Campaign Client no [vídeo](#video)

>[!CAUTION]
>
>O console do Campaign Client e o servidor de aplicativos do Campaign devem ser executados **na mesma versão do produto**. O Adobe também recomenda usar o **mesma build de produto**. Saiba como verificar as versões do cliente e do servidor do Campaign em [esta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Implementações Adobe hospedadas {#hosted-customers}

Além de um cliente hospedado, você tem duas opções para instalar ou atualizar seu(s) console(s) do cliente:

1. O Adobe pode implantar diretamente. Quando o console for atualizado, os usuários serão solicitados a baixar a versão mais recente do console do cliente em uma janela pop-up.

1. Você pode baixar para seus console(s) do cliente em [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)

   **Os usuários precisarão de acesso de Administrador para concluir a atualização. If the users do not have admin rights, a system administrator will need to deploy to all client consoles**

## Implementações híbridas e no local {#hybrid-onprem-customers}

Para que os usuários do Adobe Campaign possam fazer logon na instância criada e configurada, eles precisam usar o console do cliente.

### Disponibilizar o console para os usuários {#make-console-available}

Quando o computador usado para iniciar um servidor de aplicativos do Adobe Campaign (nlserver web) recebe conexões de usuário do console do cliente, você pode configurá-lo para disponibilizar o programa de configuração do cliente rico do Adobe Campaign por meio de uma interface HTML. Whenever a new version of the client console is available, users are invited to download it when launching their client console.

Para fazer isso, você deve:

1. Selecione o pacote que contém o programa de instalação do console.

   This file is called setup-client-7.X.XXXX.exe for v7 or setup-client-6.X.XXXX.exe for v6.1, where X is the sub-version of Adobe Campaign and XXXX is the build   number.

1. Copie e cole este pacote na pasta de instalação do Adobe Campaign (no servidor de marketing para instalações híbridas), em /datakit/nl/eng/jsp.

1. Inicie o servidor Adobe Campaign.


### Não perguntar mais esta opção de pergunta

O Adobe recomenda deixar a opção **[!UICONTROL No longer ask this question]** não selecionado para garantir que todos os usuários sejam alertados quando uma nova versão do console estiver disponível.  Se essa opção for selecionada, o usuário não será informado sobre novas versões disponíveis.

If **[!UICONTROL No longer ask this question]**  tiver sido selecionado, você poderá redefinir este prompt. Somente administradores de sistema familiarizados com a edição do Registro do Windows devem fazer estas alterações:

1. Abra o Editor do Registro usando o **regedit** do **[!UICONTROL Start > Run]** menu.

1. Procure o nó e expanda-o.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Exclua o **confAdvisedUpgrade** entre e feche o Editor do Registro.

>[!NOTE]
>
>Se você estiver aplicando um console atualizado a uma implementação existente, os usuários receberão automaticamente um prompt para atualizar seu console do cliente. Se você estiver implementando o Campaign pela primeira vez, os usuários precisarão baixar o console. Consulte abaixo para obter detalhes sobre ambas as opções

### Atualizar o console para a implementação existente{#update-the-client-console}

Once the console is available in the Campaign server folder, users will be prompted to download the latest client console version in a pop-up window.

**Os usuários precisarão de acesso de administrador para concluir a atualização. Se os usuários não tiverem direitos de administrador, um administrador do sistema precisará implantar em todos os consoles do cliente**


### Baixe o console para nova implementação{#download-the-client-console}

Os usuários agora devem baixar e instalar o console seguindo as etapas abaixo:

1. Open a web browser and download the console from the following address:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Na janela de identificação, digite o login e a senha.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessário, use as credenciais da conta interna definidas durante a criação da instância.

1. Clique no botão **[!UICONTROL Download]** na página de instalação.
1. Baixe e salve o arquivo de configuração do cliente.
1. Execute o arquivo baixado em um computador no Windows: A instalação é iniciada. O caminho de instalação padrão do console do cliente é **$PROGRAFILES$/Adobe/Adobe Campaign Classic vX Client**, onde &#39;X&#39; é &#39;6&#39; ou &#39;7&#39;, de acordo com sua versão do Adobe Campaign.

### Criar a conexão - somente usuários pela primeira vez{#create-the-connection}

Depois que o console do cliente estiver instalado, siga as etapas abaixo para criar a conexão com o servidor de aplicativos:

1. Inicie o console a partir do Windows **[!UICONTROL Start]** no menu **Adobe Campaign** grupo de programas.

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique em **[!UICONTROL Add > Connection]** e insira o rótulo e o URL do servidor de aplicativos do Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos do Adobe Campaign por meio de um URL. Use um DNS ou um alias da máquina ou seu endereço IP.

   For example, you can use the [`https://<machine>.<domain>.com`](https://myserver.adobe.com) type URL.

1. Se o Adobe IMS estiver configurado para sua organização, marque a opção . **[!UICONTROL Connect with an Adobe ID]**

1. Click **[!UICONTROL Ok]** to save your settings.

Você pode adicionar quantas conexões forem necessárias para se conectar aos ambientes de teste, estágio e produção, por exemplo.

>[!NOTE]
>
>The **[!UICONTROL Add]** button lets you create **[!UICONTROL folders]** to organize all your connections. Basta arrastar e soltar cada conexão em uma pasta.

### Log on to Adobe Campaign

Para fazer logon em uma instância existente, siga as etapas abaixo:

1. Inicie o console a partir do Windows **[!UICONTROL Start]** no menu **Adobe Campaign** grupo de programas.

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração da conexão.

1. Selecione a instância do Campaign na qual você precisa fazer logon.

1. Clique em **[!UICONTROL Ok]**

1. Insira suas credenciais de logon de usuário e clique em **[!UICONTROL Log in]**


**Tópicos relacionados**

* [Criação de uma instância e fazer logon](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

## Tutorial em vídeo

Este vídeo mostra como instalar e configurar o Adobe Campaign Client.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Vídeos extras com instruções do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
