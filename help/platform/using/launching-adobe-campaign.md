---
solution: Campaign Classic
product: campaign
title: Iniciar o Adobe Campaign
description: Iniciar o Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 86%

---


# Iniciar o Adobe Campaign{#launching-adobe-campaign}

O console do Campaign Client é um cliente avançado que permite a conexão com seu(s) servidor(es) de aplicativos do Campaign. Saiba como baixar e configurar o console do cliente [nesta página](../../installation/using/installing-the-client-console.md).

## Introdução ao Adobe Campaign {#starting-adobe-campaign}

Você pode iniciar o Adobe Campaign selecionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

A janela de conexão do console do cliente permite selecionar ou configurar bancos de dados existentes e conectar-se a eles usando um nome de usuário e uma senha:

![](assets/acc-logon.png)

## Conexão com o Adobe Campaign {#connecting-to-adobe-campaign}

Você pode se conectar ao Adobe Campaign usando sua Adobe ID. Para obter mais informações, consulte [esta página](../../integrations/using/about-adobe-id.md).

Também é possível conectar-se com uma combinação exclusiva de login e senha:

1. Digite o identificador da conta do operador no campo **[!UICONTROL login]**.

   Seu identificador é fornecido pelo administrador da plataforma Adobe Campaign.

1. Digite sua senha no campo **[!UICONTROL Password]**.

   Na primeira vez que você acessar o banco de dados, sua senha será fornecida pelo administrador. Depois de conectado, você poderá alterar a senha usando o menu **[!UICONTROL Tools > Change password...]** Os detalhes sobre operadores e conexões estão disponíveis em [Gerenciamento de acesso](../../platform/using/access-management.md).

1. Clique em **[!UICONTROL LOG IN]** para confirmar.

Agora, você pode acessar a [área de trabalho do Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

## Configurar conexões {#setting-up-connections}

É possível acessar as configurações de conexão do servidor pelo link acima da zona de entrada.

![](assets/s_ncs_user_connections_management.png)

Na janela **[!UICONTROL Connections]**, clique em **[!UICONTROL Add > Connection]**.

Em seguida, defina as configurações de conexão. Para fazer isso:

1. Digite um valor em **[!UICONTROL Label]** para atribuir um nome à conexão de banco de dados.

1. Adicione o endereço do servidor de aplicativos no campo **[!UICONTROL URL]**. Se você não souber o URL de conexão, entre em contato com o administrador.

1. Marque a opção **[!UICONTROL Connect with an Adobe ID]** para que os operadores se conectem ao console usando a Adobe ID. Para obter mais informações, consulte [esta página](../../integrations/using/about-adobe-id.md).

1. Clique em **[!UICONTROL OK]** para validar.

## Operadores e permissões {#operators-and-permissions}

Os identificadores e senhas dos operadores com acesso ao software e suas respectivas permissões são definidos pelo administrador do sistema no caminho **[!UICONTROL Administration > Access management > Operators]** do Adobe Campaign.

Essa funcionalidade é detalhada na seção [Access management](../../platform/using/access-management.md).

## Desconectar-se do Adobe Campaign {#disconnecting-from-adobe-campaign}

Para desconectar-se do Adobe Campaign, use o primeiro ícone na barra de ícones.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>Você também pode fechar o aplicativo sem fazer logoff.

## Getting your Adobe Campaign version {#getting-your-campaign-version}

O menu **[!UICONTROL Help > About...]** permite acessar as seguintes informações:

* **número da versão** para o console do cliente e o servidor de aplicativos do Campaign
* **número da compilação** para o console do cliente e o servidor de aplicativos do Campaign
* um link para entrar em contato com o Atendimento ao cliente da Adobe
* links para Política de privacidade da Adobe, Termos de uso e Política de cookies

![](assets/about-acc.png)

Sempre que você entrar em contato com a equipe de Atendimento ao cliente do Adobe, precisará fornecer o número da versão e o número da compilação do console do cliente Adobe Campaign e do servidor de aplicativos.

Se estiver executando na [versão Campaign Gold Standard](../../rn/using/gold-standard.md), você também precisará compartilhar os caracteres SHA/1 exibidos na caixa **[!UICONTROL About]**. Por exemplo, para a versão **Gold Standard 10**, o número da build mostrará a **build 9032@efd8a94**, como mostrado abaixo:

![](assets/about-acc-gs.png)

Saiba mais sobre a Gold Standard [neste artigo](https://helpx.adobe.com/br/campaign/kb/gold-standard.html).

**Tópicos relacionados**:

* [Opções de Ajuda e suporte da Adobe Campaign](https://helpx.adobe.com/br/campaign/kb/ac-support.html#acc-support)
* [Distribuição de software Adobe](https://docs.adobe.com/content/help/pt-BR/experience-cloud/software-distribution/home.html)
* [Sessões de suporte e especialista da Adobe Experience Cloud](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
