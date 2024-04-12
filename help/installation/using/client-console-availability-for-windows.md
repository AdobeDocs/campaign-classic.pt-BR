---
product: campaign
title: Disponibilidade do console do cliente para Windows
description: Disponibilidade do console do cliente para Windows
feature: Installation, Upgrade
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 6%

---

# Disponibilidade do console do cliente para Windows{#client-console-availability-for-windows}



Para que os usuários do Adobe Campaign possam fazer logon na instância criada e configurada, eles precisam usar o console do cliente.

## Disponibilizar o console do cliente

Quando o computador iniciava um servidor de aplicativos Adobe Campaign (**nlserver web**) receber conexões de usuário do console do cliente, você poderá configurá-lo para disponibilizar o programa de configuração do cliente avançado Adobe Campaign por meio de uma interface HTML. Sempre que uma nova versão do console do cliente estiver disponível, os usuários serão convidados a baixá-la ao iniciar o console do cliente.

Para fazer isso, você deve:

1. Selecione o pacote que contém o programa de instalação do console.

   Esse arquivo é chamado de `setup-client-7.X.XXXX.exe`, onde `X` é a subversão do Adobe Campaign e `XXXX` é o número da build.

1. Copie e cole este pacote na pasta de instalação do Adobe Campaign (no servidor de marketing para instalações híbridas), em **/datakit/nl/eng/jsp**.
1. Inicie o servidor do Adobe Campaign.

Os usuários do Campaign podem baixar o programa de instalação do console por meio de um navegador da Web graças ao seguinte URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Esta página requer um logon e senha definidos no aplicativo.

Saiba como instalar o console [nesta seção](../../installation/using/installing-the-client-console.md).

## Proponha que os usuários finais atualizem seu console do cliente

Quando o console estiver disponível na pasta do servidor do Campaign, os usuários serão convidados a baixar a versão mais recente do console do cliente em uma janela dedicada ao prompt. O Adobe recomenda deixar a opção **[!UICONTROL No longer ask this question]** desmarcada para garantir que todos os usuários sejam alertados quando uma nova versão do console estiver disponível.

Se você selecionar essa opção e optar por não baixar a versão mais recente, nenhum outro usuário será informado sobre novas versões disponíveis.

Caso a opção tenha sido selecionada, é possível redefinir esse prompt. Somente administradores de sistema familiarizados com a edição do Registro do Windows devem fazer estas alterações:

1. Abra o Editor do Registro usando o **regedit** comando do **[!UICONTROL Start > Run]** menu.
1. Procure o nó e expanda-o.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Exclua o **confAdvisedUpgrade** entrada e feche o Editor do Registro.
