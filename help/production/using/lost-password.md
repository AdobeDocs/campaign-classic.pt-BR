---
solution: Campaign Classic
product: campaign
title: Senha perdida
description: Senha perdida
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: b7f44f4c18bef4cc412af878846b2c4305a17787
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 9%

---


# Senha perdida{#lost-password}

Você pode alterar ou recuperar uma senha perdida.
Há dois cenários possíveis:

* **Senha perdida por um operador Adobe Campaign**

Nesse caso, você pode alterar a senha do operador em questão.
Para fazer isso, siga as etapas abaixo:

1. Conecte-se por meio de um operador com direitos de administrador.
1. Clique com o botão direito do mouse em um operador.
1. Selecione **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Defina a nova senha do operador. Recomendamos que os operadores alterem sua senha quando reconectarem pela primeira vez.

* **Perda de senha interna (somente clientes locais)**

Se a senha interna for perdida, você deverá reinicializá-la.
Para isso, execute o seguinte procedimento:

1. Edite o arquivo **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Vá para a linha **internalPassword**.

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

1. Agora você pode usar sua nova senha para se conectar no modo **Interno**.
