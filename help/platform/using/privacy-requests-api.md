---
product: campaign
title: Processo automático de solicitação de privacidade
description: Saiba como configurar um processo automático de solicitação de privacidade
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: a93bac61-f615-4178-bc12-0f056e48687d
source-git-commit: 42b420d7dae7d38e9f4df442146d3b484c25e831
workflow-type: ht
source-wordcount: '652'
ht-degree: 100%

---

# Processo automático de solicitação de privacidade {#automatic-privacy-request-api}

![](../../assets/v7-only.svg)

O Adobe Campaign fornece uma **API** que permite configurar um processo automático de solicitação de acesso a dados pessoais.

Com a API, o processo de privacidade geral é o mesmo que o [utilizado com a interface](privacy-requests-ui.md). A única diferença é a criação da solicitação de acesso a dados pessoais. Em vez de criar a solicitação no Adobe Campaign, um POST contendo as informações da solicitação é enviado para o Campaign. Para cada solicitação, uma nova entrada é adicionada na tela **[!UICONTROL Privacy Requests]**. Os workflows técnicos de privacidade processam a solicitação, da mesma forma que uma solicitação adicionada usando a interface.

Se você estiver usando a API para enviar solicitação de acesso a dados pessoais, recomendamos que ative o **processo de duas etapas** durante as primeiras solicitações de exclusão para testar os dados retornados. Após a conclusão dos testes, o processo de duas etapas pode ser desativado para que o processo de solicitação de exclusão possa ser executado automaticamente.

A API JS **[!UICONTROL CreateRequestByName]** é definida da seguinte maneira.

>[!NOTE]
>
>Se você estava usando a API **gdprRequest**, ainda é possível usá-la, mas é recomendável usar a nova API **privacyRequest** .

>[!IMPORTANT]
>
>O direito nomeado **[!UICONTROL Privacy Data Right]** é necessário para usar a API.

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>O campo &quot;Regulation&quot; só estará disponível no Campaign Classic 20.2 (build 9178+).
>
>Se você estiver migrando para a versão 20.2 e já estiver usando a API, precisará adicionar o campo &quot;regulation&quot;, como mostrado acima. Se você estiver usando uma build anterior, poderá continuar a usar a API sem o campo &quot;regulation&quot;.

## Chamada de API externamente   {#invoking-api-externally}

Este é um exemplo de como chamar a API externamente (autenticação por meio da API e detalhes específicos sobre a API de privacidade). Para obter mais informações sobre a API de privacidade, consulte a [documentação da API](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=pt-BR). Você também pode consultar a [documentação de chamadas de serviço da web](../../configuration/using/web-service-calls.md).

Primeiro, é necessário executar a autenticação por meio da API:

1. Baixe o **xtk:session** WSDL por meio deste url: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:sessão**.

1. Use o método &quot;Logon&quot; e forneça um nome de usuário e senha como parâmetros na solicitação. Você receberá uma resposta contendo um token de sessão. Veja um exemplo de utilização de SoapUI.

   ![](assets/do-not-localize/privacy-api.png)

1. Use o token de sessão retornado como autenticação para todas as chamadas de API subsequentes. Ela expira após 24 horas.

Em seguida, chame a API de privacidade:

1. Baixe o WSDL com este URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Use **[!UICONTROL CreateRequestByName]** para criar uma solicitação específica de acesso a dados pessoais.

   Veja um exemplo de uso de **[!UICONTROL CreateRequestByName]**. Observe como usamos o token de sessão fornecido acima como autenticação. A resposta é a ID da solicitação criada.

   ![](assets/do-not-localize/privacy-api-2.png)

   Para ajudar você a executar as etapas acima, considere o seguinte:

   * Você pode usar uma **queryDef** no esquema **nms:gdprRequest** para verificar o status da solicitação de acesso.
   * Você pode usar uma **queryDef** no esquema **nms:gdprRequestData** para obter o resultado da solicitação de acesso.
   * Para baixar o arquivo XML a partir de **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**, é preciso estar conectado e acessá-lo a partir de um IP incluso na lista de permissões. Para fazer isso, crie um aplicativo web que permita acessar o arquivo gerado pelo JSSP.

## Chamar a API a partir de um JS {#invoking-api-from-js}

Este é um exemplo de como você pode chamar a API a partir de um JS dentro do Campaign Classic.

>[!NOTE]
>
>O campo “Regulation” só estará disponível no Campaign Classic 20.2 (build 9178+).
>
>Se você estiver migrando para a versão 20.2 e já estiver usando a API, precisará adicionar o campo “regulation”. Se você estiver usando uma build anterior, poderá continuar a usar a API sem o campo “regulation”.

* Se você estiver **usando uma build anterior (com o pacote GDPR)** é possível continuar a usar a API sem o campo “regulation”, como mostrado abaixo:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 4 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // GDPR_REQUEST_TYPE_ACCESS = 1;
   // GDPR_REQUEST_TYPE_DELETE = 2;
   var requestType = GDPR_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Se você estiver **migrando para a versão 20.2** e já estiver usando a API, será preciso adicionar o campo “regulation”, como mostrado abaixo:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Se você estiver **usando o Campaign Classic 20.2 (build 9178+) ou superior**, o campo “regulation” é opcional, como mostrado abaixo:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values 
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is optional parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```
