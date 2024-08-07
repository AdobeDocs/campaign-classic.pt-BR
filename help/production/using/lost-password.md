---
product: campaign
title: Senha perdida
description: Senha perdida
feature: Monitoring, Access Management
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 13%

---

# Senha perdida{#lost-password}

>[!NOTE]
>
>Esta página se aplica somente a operadores conectados ao Campaign com autenticação nativa.

Você pode alterar ou recuperar uma senha perdida.
Há dois cenários possíveis:

* [Senha perdida por um operador do Adobe Campaign](#password-lost-by-campaign-operator)
* [Senha interna perdida](#internal-password-lost) (somente clientes locais)

## Senha perdida por um operador do Campaign {#password-lost-by-campaign-operator}

Se um operador do Adobe Campaign perder a senha, você poderá alterá-la.

>[!NOTE]
>
>Esse procedimento só se aplica aos operadores conectados ao Campaign com autenticação nativa. Para a autenticação do Adobe IMS, consulte [esta documentação](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}.

Para redefinir uma senha do Campaign, siga as etapas abaixo:

1. Conecte-se por meio de um operador com direitos de administrador.
1. Clique com o botão direito do mouse em um operador.
1. Selecione **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Defina a nova senha do operador. Recomendamos que o operador altere a senha quando se reconectar pela primeira vez.

## Senha interna perdida {#internal-password-lost}

>[!NOTE]
>
>Esta seção se aplica somente a clientes no local.

Se a senha interna for perdida, você deverá reinicializá-la.

Para fazer isso, siga o procedimento abaixo:

1. Edite o arquivo **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Vá para a linha **internalPassword**.

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Exclua a cadeia de caracteres entre aspas, neste caso: `myPassword`. Você obtém a seguinte linha:

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/>
   ```

1. Salvar as alterações e fechar o arquivo.

1. Pare o processo `nlserver`.

1. Configure a nova senha. Para fazer isso, insira os seguintes comandos:

   ```javascript
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. Inicie o processo `nlserver`.

1. Agora você pode usar sua nova senha para se conectar no modo **Interno**.
