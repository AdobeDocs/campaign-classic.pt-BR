---
product: campaign
title: Instalação do console do cliente
description: Saiba como instalar o console do cliente
feature: Installation, Upgrade
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 2%

---

# Instalar e atualizar o console do cliente do Campaign{#installing-the-client-console}

O Console do cliente do Campaign é um cliente avançado que permite a conexão com seu(s) servidor(es) de aplicativos do Campaign.

Antes de começar a instalar o Console do cliente, é necessário:

* Verifique a compatibilidade do sistema e das ferramentas com o Adobe Campaign na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Obter o URL do servidor do Campaign
* Obter suas credenciais de usuário
* Tenha o Webview2 Runtime do Microsoft Edge instalado em seu sistema (a partir da versão de build Campaign Classic 7.3). [Saiba mais](#webview)

O processo para instalar ou atualizar o console do cliente é diferente, dependendo da implementação do Adobe Campaign Classic.
Revise os detalhes abaixo para entender o que é necessário para sua implementação.

![](assets/do-not-localize/how-to-video.png) Descubra como instalar e configurar o Adobe Campaign Client no [vídeo](#video)

>[!CAUTION]
>
>* O console do Cliente do Campaign e o servidor de aplicativos do Campaign devem executar **na mesma versão de produto**. A Adobe também recomenda usar a **mesma compilação de produto**. Saiba como verificar as versões do Cliente e do Servidor do Campaign [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
>
>* O acesso à pasta de instalação em que o console está instalado deve ser limitado apenas ao usuário pretendido, garantindo que as permissões de gravação sejam restritas de maneira apropriada.



## Instalação em tempo de execução do Microsoft Edge Webview2 {#webview}

A partir da versão de build do Campaign Classic 7.3, a instalação do Webview 2 runtime do Microsoft Edge é necessária para qualquer instalação de console.

O Modo de Exibição da Web é instalado por padrão como parte do sistema operacional Windows 11. Se ele ainda não estiver presente no sistema, o Instalador do Console do Campaign Classic solicitará que você o baixe do [site do Microsoft Developer](https://www.adobe.com/go/acc-ms-webview2-runtime-download_br). Observe que o link de download não funciona no navegador Internet Explorer 11, pois o Microsoft descontinuou seu suporte. Use um navegador diferente para acessar o link.

## Implementações hospedadas no Adobe {#hosted-customers}

Como cliente hospedado, você tem duas opções para instalar ou atualizar seu(s) console(s) do cliente:

1. O Adobe pode implantar diretamente. Depois que o console for atualizado, os usuários serão solicitados a baixar a versão mais recente do console do cliente em uma janela pop-up.

1. Você pode baixar para o(s) seu(s) console(s) cliente em [Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)

   **Os usuários precisarão de acesso de Administrador para concluir a atualização. Se os usuários não tiverem direitos de administrador, um administrador do sistema precisará implantar em todos os consoles clientes**

## Implementações híbridas e no local {#hybrid-onprem-customers}

Para que os usuários do Adobe Campaign possam fazer logon na instância criada e configurada, eles precisam usar o console do cliente.

### Disponibilização do console para usuários {#make-console-available}

Quando o computador usado para iniciar um servidor de aplicativos Adobe Campaign (nlserver web) recebe conexões de usuário do console do cliente, você pode configurá-lo para disponibilizar o programa de configuração do cliente avançado Adobe Campaign por meio de uma interface HTML. Sempre que uma nova versão do console do cliente estiver disponível, os usuários serão convidados a baixá-la ao iniciar o console do cliente.

Para fazer isso, você deve:

1. Selecione o pacote que contém o programa de instalação do console.

   Esse arquivo é chamado setup-client-7.X.XXXX.exe, onde X é a subversão do Adobe Campaign e XXXX é o número da build.

1. Copie e cole este pacote na pasta de instalação do Adobe Campaign (no servidor de marketing para instalações híbridas), em /datakit/nl/eng/jsp.

1. Inicie o servidor do Adobe Campaign.


### Opção Não fazer mais esta pergunta

A Adobe recomenda deixar a opção **[!UICONTROL No longer ask this question]** desmarcada para garantir que todos os usuários sejam alertados quando uma nova versão do console estiver disponível.  Se essa opção estiver selecionada, o usuário não será informado sobre novas versões disponíveis.

Se **[!UICONTROL No longer ask this question]** foi selecionado, você pode redefinir este prompt. Somente administradores de sistema familiarizados com a edição do Registro do Windows devem fazer estas alterações:

1. Abra o Editor do Registro usando o comando **regedit** do menu **[!UICONTROL Start > Run]**.

1. Procure o nó e expanda-o.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Exclua a entrada **confAdvisedUpgrade** e feche o Editor do Registro.

>[!NOTE]
>
>Se você estiver aplicando um console atualizado a uma implementação existente, os usuários receberão automaticamente um prompt para atualizar seu console do cliente. Se você estiver implementando o Campaign pela primeira vez, os usuários precisarão baixar o console. Consulte abaixo para obter detalhes sobre ambas as opções

### Atualizar o console para implementação existente{#update-the-client-console}

Quando o console estiver disponível na pasta do servidor do Campaign, os usuários serão solicitados a baixar a versão mais recente do console do cliente em uma janela pop-up.

**Os usuários precisarão de acesso de administrador para concluir a atualização. Se os usuários não tiverem direitos de administrador, um administrador do sistema precisará implantar em todos os consoles clientes**


### Baixar o console para nova implementação{#download-the-client-console}

Agora, os usuários devem baixar e instalar o console seguindo as etapas abaixo:

1. Abra um navegador da Web e baixe o console no seguinte endereço:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. Na janela de identificação, digite seu login e senha.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessário, use as credenciais da conta interna definida durante a criação da instância.

1. Clique no link **[!UICONTROL Download]** na página de instalação.
1. Baixe e salve o arquivo de configuração do cliente.
1. Execute o arquivo baixado em um computador no Windows: a instalação é iniciada. O caminho de instalação padrão do console do cliente é **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, onde &#39;X&#39; é &#39;6&#39; ou &#39;7&#39;, de acordo com a sua versão do Adobe Campaign.

### Criar a conexão - somente usuários pela primeira vez{#create-the-connection}

Depois que o console do cliente estiver instalado, siga as etapas abaixo para criar a conexão com o servidor de aplicativos:

1. Inicie o console pelo menu **[!UICONTROL Start]** do Windows, no grupo de programas **Adobe Campaign**.

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração de conexão.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clique em **[!UICONTROL Add > Connection]** e insira o rótulo e a URL do servidor de aplicativos do Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Especifique uma conexão com o servidor de aplicativos Adobe Campaign por meio de um URL. Use um DNS ou um alias da máquina, ou seu endereço IP.

   Por exemplo, você pode usar o URL do tipo `https://<machine>.<domain>.com`.

1. Se o Adobe IMS estiver configurado para sua organização, marque a opção **[!UICONTROL Connect with an Adobe ID]**

1. Clique em **[!UICONTROL Ok]** para salvar suas configurações.

Você pode adicionar quantas conexões forem necessárias para se conectar aos ambientes de teste, preparo e produção, por exemplo.

>[!NOTE]
>
>O botão **[!UICONTROL Add]** permite criar **[!UICONTROL folders]** para organizar todas as suas conexões. Basta arrastar e soltar cada conexão em uma pasta.

### Fazer logon no Adobe Campaign

Para fazer logon em uma instância existente, siga as etapas abaixo:

1. Inicie o console pelo menu **[!UICONTROL Start]** do Windows, no grupo de programas **Adobe Campaign**.

1. Clique no link no canto superior direito dos campos de credenciais para acessar a janela de configuração de conexão.

1. Selecione a instância do Campaign para a qual você precisa fazer logon.

1. Clique em **[!UICONTROL Ok]**

1. Insira suas credenciais de logon de usuário e clique em **[!UICONTROL Log in]**

>[!NOTE]
>
>Para versões de build do campaign classic 7.3, o console do cliente Adobe Campaign pode solicitar credenciais de proxy duas vezes durante a autenticação de proxy. Isso ocorre porque o Microsoft Edge Webview2 não salva credenciais de proxy no armazenamento de cache/senha, ao contrário do Internet Explorer.

**Tópicos relacionados**

* [Criando uma instância e fazendo logon](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

## Tutorial em vídeo

Este vídeo mostra como instalar e configurar o Adobe Campaign Client.

>[!VIDEO](https://video.tv.adobe.com/v/38272?quality=12&captions=por_br)

Vídeos extras com instruções do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
