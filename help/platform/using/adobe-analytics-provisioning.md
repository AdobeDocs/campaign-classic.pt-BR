---
solution: Campaign Classic
product: campaign
title: Adobe Analytics Connector
description: Saiba mais sobre o Adobe Analytics Connector provisionamento
feature: Overview
role: User, Admin
level: Beginner
source-git-commit: 24cd84d37c48613aa035769514a43b6dd7aa3869
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 8%

---

# Provisionamento do conector Adobe Analytics {#adobe-analytics-connector-provisioning}

![](../../assets/common.svg)

>[!IMPORTANT]
>
> Essas etapas só devem ser executadas por implementações híbridas e no local.
>
>Para implementações hospedadas, entre em contato com a equipe de [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

A integração entre a autenticação Adobe Campaign Classic e Adobe Analytics é compatível com o Adobe Identity Management Service (IMS). Você deve implementar o Adobe IMS e se conectar ao Campaign [por meio de um Adobe ID](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/connect-to-campaign/connecting-via-an-adobe-id/about-adobe-id.html?lang=en), antes de iniciar a implementação do Analytics Connector.

Para que essa integração funcione, é necessário criar um perfil de produto do Adobe Analytics que será usado exclusivamente para o conector do Analytics. Em seguida, será necessário criar um projeto do Adobe I/O.

## Criar um perfil de produto do Adobe Analytics {#analytics-product-profile}

O Perfil do produto determina o nível de acesso que um usuário tem em seus diferentes Componentes do Analytics.

Se você já tiver um Perfil de produto do Analytics, ainda deverá criar um novo perfil de produto do Adobe Analytics usado exclusivamente para o conector do Analytics. Isso garantirá que o perfil de produto seja definido com as permissões corretas para essa integração.

Para obter mais informações sobre perfis de produto, consulte a [documentação do Admin Console](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. No [Admin Console](https://adminconsole.adobe.com/), selecione seu Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. Clique em **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Adicione um **[!UICONTROL Product profile name]**, sugerimos usar a seguinte sintaxe: `reserved_campaign_classic_<Company Name>`. Em seguida, clique em **[!UICONTROL Next]**.

   Esse **[!UICONTROL Product profile]** deve ser usado exclusivamente para o Analytics Connector a fim de evitar erros de configuração.

1. Abra o **[!UICONTROL Product profile]** recém-criado e selecione a guia **[!UICONTROL Permissions]** .

   ![](assets/do-not-localize/triggers_3.png)

1. Configure os diferentes recursos clicando em **[!UICONTROL Edit]** e selecione as permissões a serem atribuídas a seu **[!UICONTROL Product profile]** clicando no ícone de adição (+).

   Para obter mais informações sobre como gerenciar permissões, consulte a [documentação do Admin Console](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. Para o recurso **[!UICONTROL Report Suites]**, adicione o **[!UICONTROL Report Suites]** que será necessário usar posteriormente.

   Se você não tiver conjuntos de relatórios, poderá criá-los seguindo [essas etapas](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. Para o recurso **[!UICONTROL Metrics]**, adicione o **[!UICONTROL Metrics]** que será necessário configurar posteriormente.

   Se necessário, você pode ativar a opção Incluir automaticamente , que adicionará cada item de permissões na lista incluída e adicionará automaticamente novos itens de permissão.

   ![](assets/do-not-localize/triggers_13.png)

1. Para o recurso **[!UICONTROL Dimensions]**, adicione o **[!UICONTROL Dimensions]** que será necessário configurar posteriormente.

1. Para o recurso **[!UICONTROL Report Suite Tools]** , adicione as seguintes permissões:

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. Para o recurso **[!UICONTROL Analytics Tools]** , adicione as seguintes permissões:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

O perfil de produto está configurado. Em seguida, é necessário criar o Adobe I/O project.

## Criar projeto do Adobe I/O {#create-adobe-io}

1. Acesse o Adobe I/O e faça logon como **Administrador do sistema** da Organização IMS.

   Para obter mais informações sobre funções de Administrador, consulte esta [página](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Clique em **[!UICONTROL Create a new project]**.

   ![](assets/do-not-localize/triggers_5.png)

1. Clique em **[!UICONTROL Add to Project]** e selecione **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. Selecione [!DNL Adobe Analytics] e clique em **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_7.png)

1. Escolha **[!UICONTROL Service Account (JWT)]** como tipo de autenticação e clique em **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_8.png)

1. Selecione a opção **[!UICONTROL Option 1: Generate a Key-Pair]** e clique em **[!UICONTROL Generate a Key-Pair]**.

   O arquivo config.zip será baixado automaticamente.

   ![](assets/do-not-localize/triggers_9.png)

1. Clique em **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_10.png)

1. Selecione o **[!UICONTROL Product profile]** criado nas etapas anteriores detalhadas nesta [seção](#analytics-product-profile).

1. Em seguida, clique em **[!UICONTROL Save Configured API]**.

   ![](assets/do-not-localize/triggers_11.png)

1. Em seu projeto, selecione [!DNL Adobe Analytics] e copie as seguintes informações em **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/triggers_12.png)

1. Cole essas credenciais da Conta de Serviço no nlserver usando o seguinte comando:

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

Agora é possível começar a usar o conector do Analytics e rastrear os comportamentos do cliente.
