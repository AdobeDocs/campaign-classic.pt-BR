---
solution: Campaign Classic
product: campaign
title: Instruções de pré-processamento para URLs rastreados
description: Saiba mais sobre as instruções de pré-processamento a serem usadas para criar o script do URL de um email e ainda rastrear esse URL.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 86%

---


# Instruções de pré-processamento {#pre-processing-instructions}

Você pode usar uma sintaxe específica no conteúdo do delivery para adicionar instruções e criar scripts para o URL do email rastreado. As instruções &lt;%@ não são JavaScript: essa sintaxe é específica para o Adobe Campaign.

Elas só são aplicáveis no contexto do conteúdo do delivery. É a única maneira de criar o script do URL de um email e ainda rastreá-lo (além de parâmetros de URL). Elas podem ser vistas como uma cópia/colagem automática aplicada durante a análise do delivery antes de detectar os links a serem rastreados.

Há três tipos de instruções:

* &quot;**include**&quot;: principalmente para fatorar alguns códigos em opções, blocos de personalização, arquivos externos ou páginas
* &quot;**value**&quot;: para dar acesso aos campos do delivery, às variáveis do delivery e aos objetos personalizados carregados no delivery
* &quot;**foreach**&quot;: para executar um loop em uma matriz carregada como um objeto personalizado.

Elas podem ser testadas diretamente no assistente do delivery. Elas são aplicáveis na pré-visualização de conteúdo e quando você clica no botão de rastreamento para ver a lista dos URLs.

## [!DNL include] {#include}

Os seguintes exemplos estão entre os mais usados:

* Incluindo o link de mirror page: `<%@ include view="MirrorPage" %>`
* URL de mirror page: &quot;Exibir como `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* URL de unsubscription pronto para uso: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Outros exemplos:
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Use o botão de personalização no assistente do delivery para obter a sintaxe correta.

## [!DNL value] {#value}

Essa instrução dá acesso aos parâmetros do delivery que são constantes para todos os recipients.

Sintaxe:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Em que:

* **[!DNL object]**: nome do objeto (por exemplo: delivery, provedor e assim por diante).
O objeto pode ser:
   * &quot;delivery&quot;: para o delivery atual (consulte os detalhes e as restrições na subseção abaixo).
   * &quot;provider&quot;: para o provedor/roteamento atual do delivery (nms:externalAccount).
   * Um objeto de script extra: se um objeto for carregado no contexto por meio de: **Propriedades** > **Personalização** > **Adicionar objetos no contexto de execução**.
   * Item do loop foreach: consulte a seção [Foreach](#foreach) abaixo.
* **[!DNL xpath]**: xpath do campo.
* **[!DNL index]** (opcional): se  **[!DNL object]** for uma matriz (para objetos de script extras), o índice de item na matriz (Inicia em 0).

### [!DNL delivery] objeto {#delivery-object}

Para personalização por email, o objeto de delivery pode ser acessado de duas formas:

* No JavaScript. Por exemplo: `<%= delivery.myField %>`.

   No delivery de objetos JavaScript, não há suporte para campos personalizados. Eles funcionam na pré-visualização, mas não no MTA, porque o MTA só pode acessar o esquema de delivery pronto para uso.

* Por meio do `<%@ value object="delivery"` pré-processamento.

Para a instrução `<%@ value object="delivery" xpath="@myCustomField" %>`, há outra limitação para deliveries enviados via mid-sourcing. O campo personalizado @myCustomField deve ser adicionado ao esquema nms:delivery nas plataformas de marketing e mid-sourcing.

>[!NOTE]
>
>Para parâmetros/variáveis de delivery, use a seguinte sintaxe (usando o objeto de delivery):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### [!DNL value] em uma seção Javascript  {#value-in-javascript}

Para permitir o uso do valor &lt;%@ em seções Javascript, dois objetos especiais são substituídos por &lt;% e %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Por exemplo:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

Essa instrução permite a iteração em uma matriz de objetos carregada no delivery para rastrear links individuais relacionados aos objetos.

Sintaxe:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Em que:

* &quot;object&quot;: nome do objeto do qual iniciar; geralmente, é um objeto de script extra, mas pode ser um delivery.
* &quot;xpath&quot; (opcional): xpath da coleção na qual executar um loop. O padrão é &quot;.&quot;, o que significa que o objeto é a matriz na qual executar um loop.
* &quot;índice&quot; (opcional): se xpath não for &quot;.&quot; e o objeto é uma matriz em si, índice de item do objeto (começa em 0).
* &quot;Item&quot; (opcional): nome de um novo objeto acessível com o valor &lt;%@ dentro do loop foreach. Padrão com o nome do link no esquema.

Exemplo:

Nas propriedades/personalização do delivery, carregue uma matriz de artigos e uma tabela de relação entre o recipient e os artigos.

A exibição de links para esses artigos pode ser feita apenas com JavaScript, da seguinte forma:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Com essa solução, os links de todos os artigos são rastreados sem distinção. Você pode saber que um recipient clicou em um link de artigo, mas não pode saber em qual artigo.

A solução é:

1. Pré-carregar todos os artigos possíveis em uma matriz de script extra do delivery, articleList[], o que significa que deve haver um número finito de artigos possíveis.
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

