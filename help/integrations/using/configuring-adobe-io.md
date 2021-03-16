---
solution: Campaign Classic
product: campaign
title: Configuração do Adobe I/O para acionadores da Adobe Experience Cloud
description: Saiba como configurar a Adobe I/O para acionadores da Adobe Experience Cloud
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 42166334d361ffdac13842cd9d07ca7c9859bbb2
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 75%

---


# Configuração do Adobe I/O para acionadores da Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Se você estiver usando uma versão mais antiga da integração de acionadores por meio da autenticação oAuth, **será necessário mover para o Adobe I/O conforme descrito abaixo**. O modo de autenticação oAuth herdado será desativado em **30 de abril de 2021**. [Saiba mais](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).
>
>Observe que durante essa mudança para [!DNL Adobe I/O], alguns acionadores recebidos podem ser perdidos.

## Pré-requisitos {#adobe-io-prerequisites}

Essa integração se aplica somente a partir das **versões Campaign Classic 20.3, 20.2.4, 19.1.8 e Gold Standard 11**.

Antes de iniciar esta implementação, verifique se você tem:

* um **identificador de organização** valido: o identificador de organização do Identity Management System (IMS) é o identificador exclusivo da Adobe Experience Cloud, usado por exemplo para o serviço VisitorID e o IMS Single-Sign On (SSO). [Saiba mais](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=pt-BR)
* um **Acesso de desenvolvedor** para sua organização.  Se você precisar solicitar os privilégios de Administrador do Sistema da IMS Org, siga o procedimento detalhado [nesta página](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) e forneça esse acesso a todos os perfis do produto.

## Etapa 1: Criar/atualizar projeto do Adobe I/O {#creating-adobe-io-project}

1. Acesse [!DNL Adobe I/O] e faça logon com o Administrador do sistema diretamente para a Organização IMS.

   >[!NOTE]
   >
   > Verifique se você está conectado ao portal correto do Organization.

1. Extraia o identificador do cliente de integração (ID do cliente) existente a partir do arquivo de configuração da instância ims/authIMSTAClientId. Um atributo não existente ou vazio indica que o identificador do cliente não está configurado.

   >[!NOTE]
   >
   >Se o identificador do cliente estiver vazio, será possível **[!UICONTROL Create a New project]** diretamente no Adobe I/O.

1. Identifique o projeto existente usando o identificador do cliente extraído. Procure projetos existentes com o mesmo identificador do cliente que o extraído na etapa anterior.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Selecione **[!UICONTROL + Add to Project]** e escolha **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Na janela **[!UICONTROL Add an API]**, selecione **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Escolha **[!UICONTROL Service Account (JWT)]** como o tipo de autenticação.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Se a ID do cliente estiver vazia, selecione **[!UICONTROL Generate a key pair]** para criar um par de chaves público e privado.

   As chaves serão baixadas automaticamente com uma data de expiração padrão de 365 dias. Depois de expirar, você precisará criar um novo par de chaves e atualizar a integração no arquivo de configuração. Usando a Opção 2, você pode optar por criar e carregar manualmente seu **[!UICONTROL Public key]** com uma data de expiração mais longa.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Clique em **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Escolha qualquer **[!UICONTROL Product profile]** existente ou crie um novo, se necessário. Em seguida, clique em **[!UICONTROL Save configured API]**.

   Para obter mais informações sobre [!DNL Analytics] **[!UICONTROL Product Profiles]**, consulte a [documentação do Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console).

   ![](assets/do-not-localize/adobe_io_6.png)

1. Em seu projeto, selecione **[!UICONTROL Adobe Analytics]** e copie as seguintes informações em **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>O certificado do Adobe I/O expirará após 12 meses. Você precisa gerar um novo par de chaves todo ano.

## Etapa 2: adicionar as credenciais do projeto no Adobe Campaign {#add-credentials-campaign}

Para adicionar as credenciais do projeto no Adobe Campaign, execute o seguinte comando como usuário “neolane” em todos os containers da instância do Adobe Campaign para inserir as credenciais **[!UICONTROL Technical Account]** no arquivo de configuração da instância.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

A chave privada deve ser codificada no formato base64 UTF-8. Para fazer isso:

1. Use a chave privada gerada na [Etapa 1: criar/atualizar a seção Projeto do Adobe I/O](#creating-adobe-io-project). A chave privada precisa ser a mesma usada para criar a integração.

1. Codifique a chave privada usando o seguinte comando: ```base64 ./private.key```.

   >[!NOTE]
   >
   >Às vezes, linhas adicionais podem ser adicionadas automaticamente ao copiar/colar a chave privada. Lembre-se de removê-la antes de codificar sua chave privada.

1. Use a chave privada recém-gerada codificada no formato base64 UTF-8 para executar o comando detalhado acima.

## Etapa 3: atualizar a tag de pipeline {#update-pipelined-tag}

Para atualizar a tag [!DNL pipelined], é necessário atualizar o tipo de autenticação para o projeto do Adobe I/O no arquivo de configuração **config-&lt; instance-name >.xml** da seguinte maneira:

```
<pipelined ... authType="imsJwtToken"  ... />
```
