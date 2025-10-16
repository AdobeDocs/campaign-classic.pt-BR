---
product: campaign
title: Diretrizes de script e codificação
description: Saiba mais sobre as diretrizes a serem seguidas ao desenvolver no Adobe Campaign (workflows, Javascript, JSSP etc.)
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 1f96c3df-0ef2-4f5f-9c36-988cbcc0769f
source-git-commit: 0507e0372a81351adc145dafdd3cbe5d5422dc00
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 30%

---

# Diretrizes de script e codificação {#scripting-coding-guidelines}



## Script

Para obter mais detalhes, consulte a [documentação do Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=pt-BR).

Se você criar scripts usando fluxo de trabalho, aplicações web, jssp, siga estas práticas recomendadas:

* Tente evitar usar instruções SQL o máximo possível.

* Se necessário, use funções parametrizadas (instrução prepare) em vez de concatenação de strings.

  Prática incorreta:

  ```
  sqlGetInt( "select iRecipientId from NmsRecipient where sEmail ='" + request.getParameter('email') +  "'  limit 1" )
  ```

  Prática recomendada:

  ```
  sqlGetInt( "select iRecipientId from NmsRecipient where sEmail = $(sz) limit 1", request.getParameter('email'));
  ```

  >[!IMPORTANT]
  >
  >O sqlSelect não oferece suporte a esse recurso, portanto, é necessário usar a função de consulta da classe DBEngine:

  ```
  var cnx = application.getConnection()
  var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
  for each(var row in stmt) logInfo(row[0] + " : " + row[1])
  cnx.dispose()
  ```

Para evitar injeções de SQL, as funções SQL devem ser adicionadas ao arquivo de inclui na lista de permissões a ser usado no Adobe Campaign. Depois de adicionadas ao incluo na lista de permissões µ, elas se tornam visíveis para os operadores no editor de expressão. Consulte [esta página](../../configuration/using/adding-additional-sql-functions.md).

>[!IMPORTANT]
>
>Se você estiver usando uma compilação anterior a 8140, a opção **XtkPassUnknownSQLFunctionsToRDBMS** poderá ser definida como &#39;1&#39;. Se quiser proteger seu banco de dados, exclua esta opção (ou defina-a como &#39;0&#39;).

Se você estiver usando a entrada do usuário para criar filtros em consultas ou instruções SQL, sempre será necessário escapá-los (consulte a [documentação do Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=pt-BR) - Proteção de dados: funções de escape). Essas funções são:

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## Proteção de seu novo modelo de dados

### Base da pasta

Consulte estas páginas:

* [Propriedades de acesso à pasta](../../platform/using/access-management.md)
* [Pasta vinculada](../../configuration/using/configuration.md#linked-folder)

### Direitos nomeados

Além do modelo de segurança baseado em pastas, você pode usar direitos nomeados para limitar as ações do operador:

* Você pode adicionar alguns filtros de sistema (sysFilter) para impedir a leitura/gravação de seus dados (consulte [esta página](../../configuration/using/filtering-schemas.md)).

  ```
  <sysFilter name="writeAccess">    
      <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
  </sysFilter>
  ```

* Você também pode proteger algumas ações (método SOAP) definidas em esquemas. Basta definir o atributo de acesso com o direito nomeado correspondente como o valor.

  ```
  <method name="grantVIPAccess" access="myNewRole">
      <parameters>
  ...
      </parameters>
  </method>
  ```

  Para obter mais informações, consulte [esta página](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>Você pode usar direitos nomeados no nó de comando em uma árvore de navegação. Proporciona uma melhor experiência ao usuário, mas não fornece nenhuma proteção (use apenas o lado do cliente para ocultá-los/desativá-los). É necessário usar o atributo de acesso.

### Tabela de sobreposição

Se você precisar proteger dados confidenciais (parte de um esquema), dependendo do nível de acesso do operador, não os oculte na definição do formulário (condições enabledIf/visibleIf).

A entidade completa é carregada pela tela, mas você também pode exibi-las na definição da coluna. Para fazer isso, você precisa criar uma tabela de sobreposição. Consulte [esta página](../../configuration/using/examples-of-schemas-edition.md#overflow-table).

## Adicionar captchas em aplicações web

É uma boa prática adicionar um captcha em páginas de páginas/assinaturas públicas. Infelizmente, adicionar um captcha nas páginas do DCE (Digital Content Editor) não é fácil. Mostraremos como adicionar um captcha v5 ou um reCAPTCHA do Google.

A maneira geral de adicionar um captcha no DCE é criar um bloco de personalização para incluí-lo facilmente no conteúdo da página. Você terá que adicionar uma atividade **Script** e um **Test**.

### Bloco de personalização

1. Vá para **[!UICONTROL Resources]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Personalization blocks]** e crie um novo.

1. Use o tipo de conteúdo **[!UICONTROL Web application]** e verifique **[!UICONTROL Visible in the customization menus]**.

   Para obter mais informações, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html?lang=pt-BR){target="_blank"}.

   Veja um exemplo de um **captcha do Campaign**:

   ```javascript
   <%
   var captchaID = CaptchaIDGen();
   %>
   <img src="/nms/jsp/captcha.jsp?captchaID=<%=captchaID%>&width=200&height=50&minWordSize=8&maxWordSize=8"/>
   <input id="captchaValue" name="captchaValue" <%= String(ctx.vars.captchaValid) === "false" ? class="ui-state-error" : "" %>>
   <input type="hidden" name="captchaID" value="<%=captchaID%>"/>
   <%
   if( serverForm.isInputErroneous("captchaValue") ) {
   %>
   <script type="text/javascript"> 
   $("#captchaValue").addClass("ui-state-error")
   </script>
   <%
   }
   %>
   ```

   * As linhas de 1 a 6 geram todas as entradas necessárias.
   * As linhas 7 e sucessivas tratam dos erros.
   * A Linha 4 permite alterar o tamanho da caixa cinza do captcha (largura/altura) e o comprimento da palavra gerada (minWordSize/maxWordSize).
   * Antes de usar o Google reCAPTCHA, você deve se registrar no Google e criar um novo site reCAPTCHA.

     `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`

   Você deve ser capaz de desativar o botão de validação, mas como não temos nenhum botão/link padrão, é melhor fazê-lo no próprio HTML. Para aprender a fazê-lo, consulte [esta página](https://developers.google.com/recaptcha/).

### Atualização da sua aplicação web

1. Acesse as propriedades do seu aplicativo web para adicionar uma variável booleana denominada **captchaValid**.

   ![](assets/scripting-captcha.png)

1. Entre a última página e a atividade **[!UICONTROL Storage]**, adicione um **[!UICONTROL Script]** e um **[!UICONTROL Test]**.

   Conecte a ramificação **[!UICONTROL True]** a **[!UICONTROL Storage]** e a outra à página que terá o captcha.

   ![](assets/scripting-captcha2.png)

1. Edite a condição da ramificação True com `"[vars/captchaValid]"` igual a True.

   ![](assets/scripting-captcha3.png)

1. Editar a atividade **[!UICONTROL Script]**. O conteúdo dependerá do mecanismo captcha escolhido.

1. Finalmente, você pode adicionar seu bloco personalizado à página: consulte [esta página](../../web/using/editing-content.md).

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>Para a integração do reCAPTCHA, é necessário adicionar o JavaScript do lado do cliente no HTML (em `<head>...</head>`):
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### Captcha da campanha

```javascript
var captchaID = request.getParameter("captchaID");
var captchaValue = request.getParameter("captchaValue");
  
if( !CaptchaValidate(captchaID, captchaValue) ) {
  serverForm.logInputError("captchaValue",
                           "The characters you typed for the captcha must match the image ones.",
                           "captchaValue")
  ctx.vars.captchaValid = false
}
else
  ctx.vars.captchaValid = true
```

Linha 6: você pode colocar qualquer tipo de mensagem de erro.

### recaptcha do Google

Consulte a [documentação oficial](https://developers.google.com/recaptcha/docs/verify).

```javascript
ctx.vars.captchaValid = false
var gReCaptchaResponse = request.getParameter("g-recaptcha-response");
  
// Call reCaptcha API to validate it
var req = new HttpClientRequest("https://www.google.com/recaptcha/api/siteverify")
req.method = "POST"
req.header["Content-Type"] = "application/x-www-form-urlencoded"
req.body = "secret=YOUR_SECRET_HERE&response=" + encodeURIComponent(gReCaptchaResponse)
req.execute()
var response = req.response
if( response.code == 200 ) {
  captchaRes = JSON.parse(response.body.toString(response.codePage));
  ctx.vars.captchaValid = captchaRes.success
}
  
if( ctx.vars.captchaValid == false ) {
  serverForm.logInputError("reCaptcha",
                           "Please validate the captcha",
                           "reCaptcha")
  logInfo("reCaptcha not validated")
}
```

Para usar o JSON.parse, você precisa incluir &quot;shared/json2.js&quot; em seu webApp:

![](assets/scripting-captcha6.png)

Incluir na lista de permissões A partir da build 8797, para usar o URL da API de verificação, você deve adicioná-lo ao arquivo no serverConf adicionando no nó urlPermission:

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`
