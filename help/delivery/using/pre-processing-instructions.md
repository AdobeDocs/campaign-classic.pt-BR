---
solution: Campaign Classic
product: campaign
title: Instruções de pré-processamento para URLs rastreados
description: Saiba mais sobre as instruções de pré-processamento a serem usadas para script do URL de um email e ainda ter esse URL rastreado.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 1%

---


# Instruções de pré-processamento {#pre-processing-instructions}

As instruções &lt;%@ não são JavaScript, essa sintaxe é específica para a Adobe Campaign.

Eles só se aplicam no contexto do conteúdo do delivery. É a única maneira de escrever o URL de um email e ainda tê-lo rastreado (além de parâmetros de URL). Eles podem ser vistos como uma cópia/colagem automática aplicada durante a análise do delivery antes de detectar os links a serem rastreados.

Existem três tipos de instruções:

* &quot;**include**&quot;: principalmente para fatorizar algumas códigos em opções, alocos de personalização, arquivos externos ou páginas
* &quot;**value**&quot;: para dar acesso aos campos do delivery, às variáveis do delivery e aos objetos personalizados carregados no delivery
* &quot;**foreach**&quot;: para executar loop em uma matriz carregada como um objeto personalizado.

Eles podem ser testados diretamente do assistente do delivery. Eles se aplicam na pré-visualização de conteúdo e quando você clica no botão de rastreamento para ver a lista dos URLs.

## &lt;>{#<%@-include}

Os exemplos a seguir estão entre os mais usados:

* Incluindo o link do mirror page: `<%@ include view="MirrorPage" %>`
* URL do mirror page: &quot;Visualização como `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* URL de unsubscription predefinido: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Outros exemplos:
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Use o botão de personalização no assistente do delivery para obter a sintaxe correta.

## &lt;%@ value {#<%@-value}

Essa instrução dá acesso aos parâmetros do delivery que são constantes para todos os recipient.

Sintaxe:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Em que:

* &quot;object&quot;: nome do objeto (por exemplo: delivery, provedor e assim por diante).
* &quot;xpath&quot;: xpath do campo.
* &quot;index&quot; (opcional): se &quot;object&quot; for uma matriz (para objetos de script extras), o índice de item na matriz (Start em 0).

O objeto pode ser:

* *&quot;delivery&quot;: para o delivery atual (consulte os detalhes e as restrições na subseção abaixo).
* &quot;fornecedor&quot;: para o provedor/roteamento atual do delivery (nms:externalAccount).
* Um objeto de script extra: se um objeto for carregado no contexto por meio de: **Propriedades** > **Personalização** > **Adicione objetos no contexto de execução**.
* Item do ciclo foreach: consulte a seção [Foreach](#<%@-foreach) abaixo.

### objeto &quot;delivery&quot; {#delivery-object}

Para personalização por email, o objeto de delivery pode ser acessado de duas formas:

* Em JavaScript. Por exemplo: `<%= delivery.myField %>`.

   No delivery de objetos JavaScript, os campos personalizados não são suportados. Eles trabalham na pré-visualização, mas não no MTA porque o MTA só pode acessar o schema de delivery pronto para uso.

* Por meio do pré-processamento `<%@ value object="delivery"`.

Para a instrução `<%@ value object="delivery" xpath="@myCustomField" %>`, há outra limitação para delivery. O campo personalizado @myCustomField deve ser adicionado ao schema nms:delivery nas plataformas de marketing e mid-sourcing.

>[!NOTE]
>
>Para parâmetros/variáveis de delivery, use a seguinte sintaxe (usando o objeto de delivery):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### &lt;>{#<%@-value-in-javascript}

Para permitir o uso do valor &lt;%@ em seções de script, dois objetos especiais são substituídos por &lt;% e %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Por exemplo:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## &lt;>{#<%@-foreach}

Essa instrução permite a iteração em uma matriz de objetos carregados no delivery para rastrear links individuais relacionados aos objetos.

Sintaxe:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Em que:

* &quot;object&quot;: nome do objeto do start, geralmente um objeto de script extra, mas pode ser um delivery.
* &quot;xpath&quot; (opcional): xpath da coleção para executar loop. O padrão é &quot;.&quot;, o que significa que o objeto é a matriz para executar loop.
* &quot;index&quot; (opcional): se xpath não for &quot;.&quot; e o objeto é uma matriz em si, índice de item do objeto (start em 0).
* &quot;Item&quot; (facultativo): nome de um novo objeto acessível com o valor &lt;%@ dentro do loop foreach. Padrão com o nome do link no schema.

Exemplo:

Nas propriedades/personalização do delivery, carregue uma matriz de artigos e uma tabela de relação entre o recipient e os artigos.

A exibição de links para esses artigos pode ser feita apenas com um Javascript, da seguinte forma:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Com essa solução, os links para todos os artigos são rastreados sem distinção. Você pode saber que um recipient clicou em um link de artigo, mas não pode saber em qual artigo.

A solução é:

1. Pré-carregue todos os artigos possíveis em uma matriz de script extra do delivery - articleList[] - o que significa que deve haver um número finito de artigos possíveis.
1. Grave uma função JavaScript no início do conteúdo.

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```
1. Exiba o artigo chamando a função.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```

