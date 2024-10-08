---
product: campaign
title: Instruções de pré-processamento para URLs rastreados
description: Saiba mais sobre as instruções de pré-processamento a serem usadas para criar o script do URL de um email e ainda rastrear esse URL
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Monitoring
role: User, Data Engineer, Developer
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: ht
source-wordcount: '653'
ht-degree: 100%

---

# Instruções de pré-processamento {#pre-processing-instructions}

Você pode usar uma sintaxe específica no conteúdo da entrega para adicionar instruções e criar scripts para o URL do email rastreado. As instruções &lt;%@ não estão em JavaScript: essa sintaxe é específica do Adobe Campaign.

Elas só são aplicáveis no contexto do conteúdo da entrega. É a única maneira de criar o script do URL de um email e ainda rastreá-lo (além de parâmetros de URL). Elas podem ser vistas como uma cópia/colagem automática aplicada durante a análise da entrega antes de detectar os links a serem rastreados.

Há três tipos de instruções:

* **[!DNL include]**: principalmente para fatorizar alguns códigos em opções, blocos de personalização, arquivos externos ou páginas. [Saiba mais](#include)
* **[!DNL value]**: para dar acesso aos campos da entrega, às variáveis da entrega e aos objetos personalizados carregados na entrega. [Saiba mais](#value)
* **[!DNL foreach]**: para executar um loop em uma matriz carregada como um objeto personalizado. [Saiba mais](#foreach)

Os testes podem ser feitos diretamente no assistente de entrega. Eles são aplicados na pré-visualização de conteúdo e quando você clica no botão de rastreamento para ver a lista dos URLs.

## [!DNL include] {#include}

Os seguintes exemplos estão entre os mais usados:

* Incluindo o link de mirror page:

  ```
  <%@ include view="MirrorPage" %>  
  ```

* URL da mirror page:

  ```
  View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
  ```

* URL de unsubscription pronto para uso:

  ```
  <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
  ```

* Outros exemplos:

  ```
  <%@ include file='http://www.google.com' %>
  <%@ include file='file:///X:/france/service/test.html' %>
  <%@ include option='NmsServer_URL' %>
  ```

  Use o botão de personalização no assistente de entrega para obter a sintaxe correta.

## [!DNL value] {#value}

Essa instrução dá acesso aos parâmetros da entrega que são constantes para todos os destinatários.

Sintaxe:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

Em que:

* **[!DNL object]**: nome do objeto (por exemplo: entrega, provedor e assim por diante).
O objeto pode ser:
   * **[!DNL delivery]**: para a entrega atual (consulte os detalhes e as restrições na subseção abaixo).
   * **[!DNL provider]**: para o provedor/roteamento atual da entrega (nms:externalAccount).
   * Um objeto de script extra: se um objeto for carregado no contexto por meio de: **Propriedades** > **Personalização** > **Adicionar objetos no contexto de execução**.
   * Item do loop foreach: consulte a seção [Foreach](#foreach) abaixo.
* **[!DNL xpath]**: xpath do campo.
* **[!DNL index]** (opcional): se **[!DNL object]** é uma matriz (para objetos de script extras), índice de item na matriz (começa em 0).

### Objeto de [!DNL delivery] {#delivery-object}

Para personalização por email, o objeto de entrega pode ser acessado de duas formas:

* Utilização do JavaScript:

  ```
  <%= delivery.myField %>`.
  ```

  Na entrega de objetos JavaScript, não há suporte para campos personalizados. Eles funcionam na pré-visualização, mas não no MTA, porque o MTA só pode acessar o esquema de entrega pronto para uso.

* Utilização de um pré-processamento:

  ```
  <%@ value object="delivery"
  ```


**Cuidado**

Se você estiver usando a seguinte instrução para entregas enviadas via mid-sourcing, o campo personalizado **@myCustomField** deverá ser adicionado ao esquema nms:delivery nas plataformas de marketing e mid-sourcing:

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

Para parâmetros/variáveis de entrega, use a seguinte sintaxe (usando o objeto de entrega):

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] em uma seção JavaScript {#value-in-javascript}

Para permitir o uso do valor &lt;%@ em seções de JavaScript, dois objetos especiais são substituídos por &lt;% e %>:

```
<%@ value object='startScript' %>
<%@ value object='endScript' %>
```

Por exemplo:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

Essa instrução permite a iteração em uma matriz de objetos carregada na entrega para rastrear links individuais relacionados aos objetos.

Sintaxe:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

Em que:

* **[!DNL object]**: nome do objeto do qual iniciar; geralmente, é um objeto de script extra, mas pode ser uma entrega.
* **[!DNL xpath]** (opcional): xpath da coleção na qual executar um loop. O padrão é &quot;.&quot;, o que significa que o objeto é a matriz na qual executar um loop.
* **[!DNL index]** (opcional): se xpath não for &quot;.&quot; e o objeto é uma matriz em si, índice de item do objeto (começa em 0).
* **[!DNL item]** (opcional): nome de um novo objeto acessível com o valor &lt;%@ dentro do loop foreach. Padrão com o nome do link no esquema.

Exemplo:

Nas propriedades/personalização da entrega, carregue uma matriz de artigos e uma tabela de relação entre o destinatário e os artigos.

A exibição de links para esses artigos pode ser feita apenas com JavaScript, da seguinte forma:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Com essa solução, os links de todos os artigos são rastreados sem distinção. Você pode saber que um destinatário clicou em um link de artigo, mas não pode saber em qual artigo.

A solução é:

1. Pré-carregar todos os artigos possíveis em uma matriz de script extra da entrega, articleList[], o que significa que deve haver um número finito de artigos possíveis.
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
