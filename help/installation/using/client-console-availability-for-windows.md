---
solution: Campaign Classic
product: campaign
title: Disponibilidade do console do cliente para Windows
description: Disponibilidade do console do cliente para Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 5%

---


# Disponibilidade do console do cliente para Windows{#client-console-availability-for-windows}

Para que os usuários do Adobe Campaign possam fazer logon na instância criada e configurada, eles precisam usar o console do cliente.

Quando o computador usado para start de um servidor de aplicativos Adobe Campaign (**nlserver web**) recebe conexões de usuário do console do cliente, você pode configurá-lo para disponibilizar o programa de configuração para o cliente Adobe Campaign rich por meio de uma interface HTML.

Para fazer isso, você deve:

1. Recupere o pacote que contém o programa de instalação do console.

   Esse arquivo é chamado `setup-client-7.X.XXXX.exe` para v7 ou `setup-client-6.X.XXXX.exe` v6.1, onde `X` é a subversão do Adobe Campaign e `XXXX` é o número da compilação.

1. Copie e cole este pacote na pasta de instalação do Adobe Campaign, em **/datakit/nl/eng/jsp**.
1. Start o servidor Adobe Campaign.

Os usuários finais podem então baixar o programa de instalação do console por meio de um navegador da Web, graças ao seguinte URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Esta página requer um logon e uma senha definidos no aplicativo.

Para baixar e instalar o console, consulte [Instalação do console](../../installation/using/installing-the-client-console.md)do cliente.

Sempre que uma nova versão do console do cliente estiver disponível, você será convidado a baixá-la.

>[!NOTE]
>
>No prompt que é exibido, o Adobe recomenda deixar a opção **[!UICONTROL No longer ask this question]** desmarcada para garantir que todos os usuários sejam alertados quando uma nova versão do console estiver disponível.\
>Se você selecionar essa opção e optar por não baixar a versão mais recente, nenhum outro usuário será informado sobre novas versões disponíveis.

Para redefinir este prompt, siga as etapas abaixo (somente os administradores de sistema que se sentem confortáveis com a edição do Registro devem fazer estas alterações):

1. Abra o Editor do Registro usando o comando **regedit** no **[!UICONTROL Start > Run]** menu.
1. Procure o nó e expanda-o.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Exclua a entrada **confAdvisedUpgrade** e feche o Editor do Registro.

