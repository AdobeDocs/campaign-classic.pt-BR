---
product: campaign
title: Senha perdida
description: Senha perdida
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---

# Senha perdida{#lost-password}

![](../../assets/v7-only.svg)

Você pode alterar ou recuperar uma senha perdida.
Há dois cenários possíveis:

* [Senha perdida por um operador do Adobe Campaign](#password-lost-by-campaign-operator)
* [Senha interna perdida](#internal-password-lost) (somente para clientes locais)

## Senha perdida por um operador do Campaign {#password-lost-by-campaign-operator}

Se um operador do Adobe Campaign perder a senha, você poderá alterá-la.
Para fazer isso, siga as etapas abaixo:

1. Conecte-se por meio de um operador com direitos de administrador.
1. Clique com o botão direito do mouse em um operador.
1. Selecione **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Defina a nova senha do operador. Recomendamos que o operador altere sua senha ao se reconectar pela primeira vez.

## Senha interna perdida {#internal-password-lost}

>[!NOTE]
>
>Esta seção se aplica somente a clientes locais.

Se a senha interna for perdida, você deverá reinicializá-la.
Para fazer isso, siga as etapas abaixo:

1. Edite o **/usr/local/neolane/nl6/conf/serverConf.xml** arquivo.

1. Vá para o **internalPassword** linha.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Exclua a sequência de caracteres entre aspas, neste caso: **myPassword**

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

1. Agora você pode usar sua nova senha para se conectar no **Interno** modo.
