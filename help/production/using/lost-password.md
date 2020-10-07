---
title: Senha perdida
seo-title: Senha perdida
description: Senha perdida
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 12%

---


# Senha perdida{#lost-password}

Você pode alterar ou recuperar uma senha perdida.

Há dois cenários possíveis:

* Senha perdida por um operador Adobe Campaign.

   Nesse caso, você pode alterar a senha do operador em questão. Para fazer isso, conecte-se por um operador com direitos de administrador, clique com o botão direito do mouse em um operador, selecione **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** e defina a nova senha do operador. Recomendamos que os operadores alterem sua senha ao se reconectarem pela primeira vez.

   ![](assets/operator-passwd.png)

* **Perda de senha interna** (somente clientes locais).

   Se a senha **interna** for perdida, você deverá reinicializá-la. Para isso, execute o seguinte procedimento:

   1. Edite o arquivo **/usr/local/neolane/nl6/conf/serverConf.xml** .
   1. Vá para a linha **internaPassword** .

      ```
      <!-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword="myPassword"/>
      ```

   1. Exclua a string entre aspas, neste caso: **myPassword**

      Assim, você obtém a seguinte linha:

      ```
      !-- XTK authentication mode internalPassword : Password of internal account -->
      <xtk internalPassword=""/
      ```

   1. Salve as alterações e feche o arquivo.
   1. Configure a nova senha. Para fazer isso, insira os seguintes comandos:

      ```
      nlserver config -internalpassword
      HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
      Enter current password.
      Password: (empty)
      Enter the new password.
      Password: 
      Confirmation 
      ```

   1. Agora você pode usar sua nova senha para se conectar no modo **Interno** .

