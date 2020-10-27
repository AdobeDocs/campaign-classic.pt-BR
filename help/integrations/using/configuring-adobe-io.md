---
title: Configurando Adobe IO para acionadores Adobe Experience Cloud
seo-title: Configurando Adobe IO para acionadores Adobe Experience Cloud
description: Configurando Adobe IO para acionadores Adobe Experience Cloud
seo-description: null
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
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# Configurando Adobe IO para acionadores Adobe Experience Cloud {#configuring-adobe-io}

As configurações de pré-requisito são:

* Adobe Campaign Classic build ACC-19.1.9 ou ACC-20.2.1 e superior.
* um IMSOrgID válido.
* um acesso de desenvolvedor à Organização IMS. Você precisa solicitar os privilégios de Administrador do Sistema da Organização IMS para seguir o procedimento detalhado nesta [página](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) para fornecer esse acesso para todos os Perfis do Produto.

## Etapa 1: Criar/atualizar projeto de E/S de Adobe {#creating-adobe-io-project}

1. Acesse Adobe E/S e faça logon com o Administrador do sistema diretamente para o IMSorg.

   >[!NOTE]
   >
   > Verifique se você está conectado ao portal IMSorg correto.

1. Extraia a ID do cliente de integração existente do arquivo de configuração da instância ims/authIMSTAClientId. Atributo não existente ou vazio indica que a ID do cliente não está configurada.

   >[!NOTE]
   >
   >Se a ID do cliente estiver vazia, é possível entrar diretamente **[!UICONTROL Create a New project]** em Adobe IO.

1. Agora é necessário identificar o projeto existente usando a ID do cliente extraída. Procure projetos existentes com a mesma ID de cliente que a extraída na etapa anterior.

   ![](assets/adobe_io_8.png)

1. Selecione **[!UICONTROL + Add to Project]** e escolha **[!UICONTROL API]**.

   ![](assets/adobe_io_1.png)

1. In the window **[!UICONTROL Add an API]**, select **[!UICONTROL Adobe Analytics]**.

   ![](assets/adobe_io_2.png)

1. Escolha **[!UICONTROL Service Account (JWT)]** como o tipo de autenticação.

   ![](assets/adobe_io_3.png)

1. Se a ID do cliente estiver vazia, selecione **[!UICONTROL Generate a key pair]** para criar um par de chaves Público e Privado.

   ![](assets/adobe_io_4.png)

1. Carregue sua chave pública e clique em **[!UICONTROL Next]**.

   ![](assets/adobe_io_5.png)

1. Escolha o perfil de produto chamado **Analytics-&lt; Nome da organização >** e clique em **[!UICONTROL Save configured API]**.

   ![](assets/adobe_io_6.png)

1. Em seu projeto, selecione **[!UICONTROL Service Account (JWT)]** e copie as seguintes informações:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/adobe_io_7.png)

## Etapa 2: Adicionar as credenciais do projeto no Adobe Campaign {#add-credentials-campaign}

Para adicionar as credenciais do projeto no Adobe Campaign, execute o seguinte comando como usuário neolane em todos os container da instância do Adobe Campaign para inserir as **[!UICONTROL Technical Account]** credenciais no arquivo de configuração da instância.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Você deve codificar a chave privada no formato base64 UTF-8. Lembre-se de remover a nova linha da chave antes de codificá-la, exceto para a chave privada. A chave privada precisa ser a mesma usada para criar a integração.

## Etapa 3: Atualizar tag pipelined {#update-pipelined-tag}

Para atualizar a [!DNL pipelined] tag, é necessário atualizar o tipo de autenticação para o projeto Adobe IO no arquivo de configuração **config-&lt; instance-name >.xml** da seguinte maneira:

```
<pipelined ... authType="imsJwtToken"  ... />
```

>[!NOTE]
>
>Se você estiver usando a versão mais antiga da Integração de Triggers usando tokens JWT herdados, também deverá adicionar a API Adobe IO para obter detalhes na primeira etapa para migrar automaticamente para a nova Autenticação de Triggers. [!DNL Adobe Analytics]
