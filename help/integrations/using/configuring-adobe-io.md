---
title: Configuração de E/S de Adobe para acionadores Adobe Experience Cloud
description: Saiba como configurar a E/S do Adobe para acionadores Adobe Experience Cloud
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2d0d2d4eefc67312e1b9a8edc7ae88def2980ef1
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 1%

---


# Configuração de E/S de Adobe para acionadores Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Se você estiver usando uma versão mais antiga da integração de Acionadores por meio da autenticação do oAuth, **será necessário mover para a E/S do Adobe, conforme descrito abaixo**. O modo de autenticação do oAuth herdado será desativado em 30 de abril de 2021. [Saiba mais](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md)

## Pré-requisitos {#adobe-io-prerequisites}

Essa integração só se aplica a partir do **Campaign Classic versão** 20.3.

Antes de iniciar esta implementação, verifique se você tem:

* uma IMSOrgID válida: o identificador de organização do Sistema Identity Management (IMS) é o identificador exclusivo no Adobe Experience Cloud, usado, por exemplo, para o serviço VisitorID e o IMS Single-Sign On (SSO),
* um acesso de desenvolvedor à Organização IMS.

>[!NOTE]
>
>Se você precisar solicitar os privilégios de Administrador do sistema da Organização IMS, siga o procedimento detalhado [nesta página](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) para fornecer esse acesso para todos os Perfis do Produto.


## Etapa 1: Criar/atualizar projeto de E/S de Adobe {#creating-adobe-io-project}

1. Acesse a E/S do Adobe e faça logon com o Administrador do sistema, diretamente para a IMSorg.

   >[!NOTE]
   >
   > Verifique se você está conectado ao portal IMSorg correto.

1. Extraia a ID do cliente de integração existente do arquivo de configuração da instância ims/authIMSTAClientId. Atributo não existente ou vazio indica que a ID do cliente não está configurada.

   >[!NOTE]
   >
   >Se a ID do cliente estiver vazia, é possível entrar diretamente **[!UICONTROL Create a New project]** na E/S do Adobe.

1. Identifique o projeto existente usando a ID do cliente extraída. Procure projetos existentes com a mesma ID de cliente que a extraída na etapa anterior.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Selecione **[!UICONTROL + Add to Project]** e escolha **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Na janela **[!UICONTROL Add an API]**, selecione **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Escolha **[!UICONTROL Service Account (JWT)]** como o tipo de autenticação.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Se a ID do cliente estava vazia, selecione **[!UICONTROL Generate a key pair]** para criar um par de chaves Público e Privado.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Carregue sua chave pública e clique em **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Escolha o perfil de produto chamado **Analytics-&lt; Nome da organização >** e clique em **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Em seu projeto, selecione **[!UICONTROL Service Account (JWT)]** e copie as seguintes informações:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

## Etapa 2: Adicionar as credenciais do projeto no Adobe Campaign {#add-credentials-campaign}

Para adicionar as credenciais do projeto no Adobe Campaign, execute o seguinte comando como usuário &#39;neolane&#39; em todos os container da instância do Adobe Campaign para inserir as **[!UICONTROL Technical Account]** credenciais no arquivo de configuração da instância.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Você deve codificar a chave privada no formato base64 UTF-8. Lembre-se de remover a nova linha da chave antes de codificá-la, exceto para a chave privada. A chave privada precisa ser a mesma usada para criar a integração.

## Etapa 3: Atualizar tag pipelined {#update-pipelined-tag}

Para atualizar a [!DNL pipelined] tag, é necessário atualizar o tipo de autenticação para o projeto de E/S do Adobe no arquivo de configuração **config-&lt; instance-name >.xml** da seguinte maneira:

```
<pipelined ... authType="imsJwtToken"  ... />
```
