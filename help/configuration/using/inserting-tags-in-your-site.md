---
solution: Campaign Classic
product: campaign
title: Inserir tags no site
description: Inserir tags no site
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 5%

---


# Inserir tags no site{#inserting-tags-in-your-site}

## Método simples {#simple-method}

Este método consiste em enviar uma chamada HTTP para o servidor de redirecionamento inserindo uma tag **`<img>`** HTML no código-fonte HTML da página da Web que você deseja rastrear.

>[!IMPORTANT]
>
>Este método usa os cookies enviados pelo navegador da Web para identificar o recipient e não é 100% confiável.

**Exemplo**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

A tag inserida entra em contato com o servidor de redirecionamento.

![](assets/d_ncs_integration_webtracking_structure2.png)

Ao definir uma página a ser rastreada no console, você pode gerar uma tag de rastreamento da Web de amostra para copiar e colar no código-fonte da sua página da Web.

No entanto, ao usar tags do tipo TRANSAÇÃO, é necessário modificar a tag de amostra usando o JavaScript para inserir as informações da transação (quantidade, número de itens) e quaisquer informações definidas por um schema de extensão.

### Inserção estática de tags {#static-insertion-of-tags}

Para executar inserção de tags estáticas, basta copiar e colar as tags geradas pelo console ou construídas manualmente na origem da sua página da Web.

**Exemplo**: inserção de um tag de rastreamento da Web em uma página que exibe um formulário.

```
<html>
  <...>
  <body>
  <script>
      document.write("<img height='0' width='0' alt='' src='https://localhost/r/" + Math.random().toString() + "?tagid=home'>");
    </script>
    <noscript>
     <img height='0' width='0' alt='' src='https://localhost/r/?tagid=home'>
    </noscript>
    <h1>My site</h1>
    <form action="http://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

Inserção de um tag de rastreamento do tipo TRANSACTION na página de confirmação (&quot;amount.md&quot;).

```
<html>
  <body>
    <script>
      function getURLparam(name) 
      {
        var m = location.search.match new RegExp("[?&]" + name + "=([^&]+)"));
        return m ? unescape(m[1]) : "";
      }
 
       var params = "https://localhost/r/" + Math.random().toString() + "?tagid=amount&amount="
                      +getURLparam("amount")+"&article="+getURLparam("quantity");
       document.write("<img height='0' width='0' src='"+params+"'/>");
    </script>

    <h1>Approval confirmation</h1>
  </body>
</html>
```

### Geração dinâmica de tag de rastreamento da Web {#dynamic-generation-of-web-tracking-tags}

Quando suas páginas da Web são geradas dinamicamente, você pode adicionar o tag de rastreamento da Web no momento da geração da página.

**Exemplo**: Rastreamento web adicionado aos JSPs.

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <img height='0' width='0' alt='' src='https://localhost/r/<%=new Random().nextInt()%>?tagid=home'>
    <h1>My site</h1>
    <form action="https://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <%  
      String strParams = new Random().nextInt() + "?tagid=amount";
      strParams += "&amount="+request.getParameter("amount");
      strParams += "&article="+request.getParameter("quantity");
    %>
    <img height='0' width='0' alt=''
     src='http://localhost/r/<%=strParams%>'>
    <h1>Approval confirmation</h1>
    </body>
</html>
```

## Método ideal {#optimum-method-}

Se você quiser controlar as informações enviadas para o servidor de redirecionamento, a maneira mais confiável é executar o query HTTP de forma sincronizada usando um idioma de geração de página.

O URL que você constrói deve obedecer às regras de sintaxe definidas no [Tag de rastreamento web: definição](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>O redirecionamento e o rastreamento da Web usam cookies, e é importante que o servidor da Web que executa a chamada HTTP síncrona esteja no mesmo domínio que o servidor de redirecionamento. As várias trocas HTTP devem transmitir os cookies &#39;id&#39;, &#39;uuid&#39; e &#39;uid230&#39;.

**Exemplo**: Geração dinâmica em Java, com autenticação de recipient usando seu número de conta.

```
[...]
  // Recipient account, amount and articles
  String strAccount = request.getParameter("account");
  String strAmount = request.getParameter("amount");
  String strArticle = request.getParameter("article");

  StringBuffer strCookies = new StringBuffer();
  String strSetCookie = null;

  // Get cookies from client request
  Cookie[] cookies = request.getCookies();
  for(int i=0; i< cookies.length; i++ )
  {
    Cookie c = cookies[i];
    String strName = c.getName();
    if( strName.equals("id") || strName.equals("uuid") || strName.equals("uuid230") )
      // Helper function to add cookies in string
      AddCookie(strCookies, c);
  }
  // Now perform a synchronous HTTP request to inform redirection server
  // Add a tagid in auto-discover mode, and a default jobId to use (in hexa)
  StringBuffer strURL = new StringBuffer("https://www.adobe.com/r/a?tagid=cmd_page%7Ct&jobid=27EE");
  if( strAccount != null )
    AddParameter(strURL, "rcpid", "saccount="+strAccount);
  if( strAmount != null )
    AddParameter(strURL, "amount", strAmount);
  if( strArticle != null )
    AddParameter(strURL, "article", strArticle);
  
  URL url = new URL(strURL.toString());
  HttpURLConnection connection = (HttpURLConnection)url.openConnection();
  // Add the client cookies
  if( strCookies.length() > 0 )
    connection.setRequestProperty("Cookie", strCookies.toString());

  int errcode = connection.getResponseCode();

  // Now add the Adobe Campaign cookies if the server returned one :
  if( errcode == 200 )
  {
    strSetCookie = connection.getHeaderField("Set-Cookie");
    if( strSetCookie != null && strSetCookie.length() > 0 )
      response.addHeader("Set-Cookie", strSetCookie);
  }
  [...]
```

