---
product: campaign
title: Senha perdida
description: Senha perdida
feature: Monitoring, Access Management
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
badge-v7-prem: label="No local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 15%

---

# Senha perdida{#lost-password}



Você pode alterar ou recuperar uma senha perdida.
Há dois cenários possíveis:

* [Senha perdida por um operador do Adobe Campaign](#password-lost-by-campaign-operator)
* [Senha interna perdida](#internal-password-lost) (somente clientes locais)

## Senha perdida por um operador do Campaign {#password-lost-by-campaign-operator}

Se um operador do Adobe Campaign perder a senha, você poderá alterá-la.
Para fazer isso, siga as etapas abaixo:

1. Conecte-se por meio de um operador com direitos de administrador.
1. Clique com o botão direito do mouse em um operador.
1. Selecionar **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Defina a nova senha do operador. Recomendamos que o operador altere a senha quando se reconectar pela primeira vez.

## Senha interna perdida {#internal-password-lost}

>[!NOTE]
>
>Esta seção se aplica somente a clientes no local.

Se a senha interna for perdida, você deverá reinicializá-la.
Para fazer isso, siga o procedimento abaixo:

1. Edite o **/usr/local/neolane/nl6/conf/serverConf.xml** arquivo.

1. Vá para a **internalPassword** linha.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Exclua a string entre aspas, neste caso: **myPassword**

   Dessa forma, você obtém a seguinte linha:

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. Salvar as alterações e fechar o arquivo.

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

1. Agora você pode usar sua nova senha para se conectar ao **Interno** modo.
