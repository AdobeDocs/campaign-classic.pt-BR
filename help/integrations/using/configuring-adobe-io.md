---
solution: Campaign Classic
product: campaign
title: Configuração de E/S de Adobe para acionadores Adobe Experience Cloud
description: Saiba como configurar a E/S do Adobe para acionadores Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 33%

---


# Configuring Adobe I/O for Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Se você estiver usando uma versão mais antiga da integração de Acionadores por meio da autenticação do oAuth, **será necessário mover para a E/S do Adobe, conforme descrito abaixo**. O modo de autenticação do oAuth herdado será desativado em 30 de abril de 2021. [Saiba mais](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Pré-requisitos {#adobe-io-prerequisites}

Essa integração só se aplica a partir do **Campaign Classic versão** 20.3.

Antes de iniciar esta implementação, verifique se você tem:

* uma IMSOrgID válida: o identificador de organização do Sistema Identity Management (IMS) é o identificador exclusivo no Adobe Experience Cloud, usado, por exemplo, para o serviço VisitorID e o IMS Single-Sign On (SSO),
* um acesso de desenvolvedor à Organização IMS.

>[!NOTE]
>
>If you need to request the System Administrator privileges of the IMS Org, follow the procedure detailed [in this page](https://helpx.adobe.com/br/enterprise/admin-guide.html/br/enterprise/using/manage-developers.ug.html) to provide this access for the all Product Profiles.


## Etapa 1: Criar/atualizar projeto de E/S de Adobe {#creating-adobe-io-project}

1. Acesse a E/S do Adobe e faça logon com o Administrador do sistema, diretamente para a IMSorg.

   >[!NOTE]
   >
   > Verifique se você está conectado ao portal IMSorg correto.

1. Extraia a ID do cliente de integração existente a partir do arquivo de configuração da instância ims/authIMSTAClientId. Atributo não existente ou vazio indica que a ID do cliente não está configurada.

   >[!NOTE]
   >
   >If your Client ID is empty, you can directly **[!UICONTROL Create a New project]** in Adobe I/O.

1. Identifique o projeto existente usando a ID do cliente extraída. Procure projetos existentes com a mesma ID de cliente que a extraída na etapa anterior.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Selecione **[!UICONTROL + Add to Project]** e escolha **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Na janela **[!UICONTROL Add an API]**, selecione **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Escolha **[!UICONTROL Service Account (JWT)]** como o tipo de autenticação.

   ![](assets/do-not-localize/adobe_io_3.png)

1. If your Client ID was empty, select **[!UICONTROL Generate a key pair]** to create a Public and Private keypair.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Carregue sua chave pública e clique em **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Escolha o perfil de produto chamado **Analytics-&lt; Org Name >** e clique em **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Em seu projeto, selecione **[!UICONTROL Service Account (JWT)]** e copie as seguintes informações:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

## Etapa 2: adicionar as credenciais do projeto no Adobe Campaign {#add-credentials-campaign}

To add the project credentials in Adobe Campaign, run the following command as &#39;neolane&#39; user on all the containers of the Adobe Campaign instance to insert the **[!UICONTROL Technical Account]** credentials in the instance configuration file.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Você deve codificar a chave privada no formato base64 UTF-8. Lembre-se de remover a nova linha da chave antes de codificá-la, exceto para a chave privada. A chave privada precisa ser a mesma usada para criar a integração.

## Etapa 3: atualizar tag de pipeline {#update-pipelined-tag}

To update [!DNL pipelined] tag, you need to update the authentication type to Adobe I/O project in the configuration file **config-&lt; instance-name >.xml** as follows:

```
<pipelined ... authType="imsJwtToken"  ... />
```
