---
solution: Campaign Classic
product: campaign
title: Configuração do Adobe I/O para acionadores da Adobe Experience Cloud
description: Saiba como configurar a Adobe I/O para acionadores da Adobe Experience Cloud
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
ht-degree: 100%

---


# Configuração do Adobe I/O para acionadores da Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Se você estiver usando uma versão mais antiga da integração de acionadores por meio da autenticação oAuth, **será necessário mover para o Adobe I/O conforme descrito abaixo**. O modo de autenticação oAuth herdado será desativado em 30 de abril de 2021. [Saiba mais](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Pré-requisitos {#adobe-io-prerequisites}

Essa integração só se aplica a partir da **versão 20.3 do Campaign Classic**.

Antes de iniciar esta implementação, verifique se você tem:

* uma IMSOrgID válida: o identificador de organização do Identity Management System (IMS) é o identificador exclusivo da Adobe Experience Cloud, usado por exemplo para o serviço VisitorID e o IMS Single-Sign On (SSO),
* um acesso de desenvolvedor à IMS Org.

>[!NOTE]
>
>Se você precisar solicitar os privilégios de Administrador do Sistema da IMS Org, siga o procedimento detalhado [nesta página](https://helpx.adobe.com/br/enterprise/admin-guide.html/br/enterprise/using/manage-developers.ug.html) e forneça esse acesso a todos os perfis do produto.


## Etapa 1: Criar/atualizar projeto do Adobe I/O {#creating-adobe-io-project}

1. Acesse o Adobe I/O e faça logon como Administrador do sistema diretamente para o IMSorg.

   >[!NOTE]
   >
   > Verifique se você está conectado ao portal IMSorg correto.

1. Extraia a ID do cliente de integração existente a partir do arquivo de configuração da instância ims/authIMSTAClientId. Se o atributo for não existente ou estiver vazio, a ID do cliente não está configurada.

   >[!NOTE]
   >
   >Se a ID do cliente estiver vazia, é possível **[!UICONTROL Create a New project]** diretamente no Adobe I/O.

1. Identifique o projeto existente usando a ID do cliente extraída. Procure projetos existentes com a mesma ID de cliente que a extraída na etapa anterior.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Selecione **[!UICONTROL + Add to Project]** e escolha **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Na janela **[!UICONTROL Add an API]**, selecione **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Escolha **[!UICONTROL Service Account (JWT)]** como o tipo de autenticação.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Se a ID do cliente estiver vazia, selecione **[!UICONTROL Generate a key pair]** para criar um par de chaves público e privado.

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

Para adicionar as credenciais do projeto no Adobe Campaign, execute o seguinte comando como usuário “neolane” em todos os containers da instância do Adobe Campaign para inserir as credenciais **[!UICONTROL Technical Account]** no arquivo de configuração da instância.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Você deve codificar a chave privada no formato base64 UTF-8. Lembre-se de remover a nova linha da chave antes de codificá-la, exceto para a chave privada. A chave privada precisa ser a mesma usada para criar a integração.

## Etapa 3: atualizar tag de pipeline {#update-pipelined-tag}

Para atualizar a tag [!DNL pipelined], é necessário atualizar o tipo de autenticação para o projeto do Adobe I/O no arquivo de configuração **config-&lt; instance-name >.xml** da seguinte maneira:

```
<pipelined ... authType="imsJwtToken"  ... />
```
