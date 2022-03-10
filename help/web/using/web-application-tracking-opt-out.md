---
product: campaign
title: Opt out de rastreamento da aplicação web
description: Opt out de rastreamento da aplicação web
feature: Web Apps
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: ht
source-wordcount: '670'
ht-degree: 100%

---

# Opt out de rastreamento da aplicação web{#web-application-tracking-opt-out}

![](../../assets/common.svg)

O Adobe Campaign permite que você interrompa o rastreamento de comportamentos da Web de usuários finais que usam o opt out do rastreamento comportamental por meio de cookies ou web beacons. O recurso inclui a habilidade de exibir um banner para apresentar ao usuário final essa opção; você pode adicionar esses banners em aplicações web ou landing pages.

Se um usuário final usar o opt out de rastreamento comportamental por meio de cookies ou Web beacons, essas informações serão transmitidas ao servidor de rastreamento do Adobe Campaign com APIs JavaScript. Observe que algumas jurisdições podem exigir que o Cliente apresente aos usuários finais um opt in antes que um opt out possa ser oferecido (ou ter outros requisitos legais) e é responsabilidade do cliente estar em conformidade com as leis aplicáveis.

>[!NOTE]
>
>Quando os scripts sempre seguem as diretrizes descritas na [lista de verificação segurança e privacidade](https://helpx.adobe.com/br/campaign/kb/acc-security.html#dev).

## Configuração do banner {#configuring-the-banner-}

Para ser exibido em aplicações web ou Landing pages, o banner precisa ser configurado.

O Adobe Campaign é fornecido com um banner de exemplo que você deve adaptar às suas necessidades. Essa versão do banner aparece como um bloco de personalização localizado na pasta do modelo de conteúdo. Consulte [esta página](../../delivery/using/personalization-blocks.md).

>[!IMPORTANT]
>
>Para criar seu próprio banner, você deve personalizar o banner pronto para uso.

Para ativar o banner, você precisa configurar as propriedades da aplicação web. Consulte a seção [Criação de um aplicativo web](designing-a-web-application.md).

Se o rastreamento web estiver ativado, você pode ter:

* Nenhum banner.
* Configure o banner manualmente em cada página: marque essa opção e selecione o banner em cada página nas propriedades da página.

   ![](assets/pageproperties.png)

* Adicione automaticamente o banner a todas as páginas: selecione o banner diretamente nas propriedades da aplicação web.

   ![](assets/optoutconfig.png)

>[!NOTE]
>
>Um modo de compatibilidade está disponível para a aplicação web v5 com o mesmo comportamento.

O banner padrão tem a seguinte estrutura:

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

Você deve substituir a mensagem **Inserir sua mensagem aqui** com o bloco contendo suas informações de rastreamento. Essa substituição deve ser executada em seu novo bloco de personalização relacionado ao banner Opt out.

O banner é fornecido com um CSS específico. No entanto, você pode substituir os estilos ao criar e configurar uma página da Web. Consulte [esta página](content-editor-interface.md).

## Definição do cookie de recusa usando a API {#setting-the-opt-out-cookie-using-api}

O Adobe Campaign é fornecido com APIs que permitem gerenciar o valor do cookie e recuperar preferências do usuário.

O nome do cookie é **acoptout**. Os valores comuns são:

* 0: o usuário permitiu o rastreamento web (valor padrão)
* 1: o usuário proibiu o rastreamento web
* null: o usuário não escolheu, mas o rastreamento web é permitido, pois é o valor padrão

As APIs disponíveis no lado do cliente para personalizar o banner são:

* **NL.ClientWebTracking.allow()**: define o valor do cookie de opt out para permitir o rastreamento web. O rastreamento web é permitido por padrão.
* **NL.ClientWebTracking.forbid()**: define o valor do cookie de opt out para proibir o rastreamento web. O rastreamento web precisa de uma entrada de usuário para ser proibido.
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**: fecha o banner de cookie de opt out após o usuário clicar no botão Aceitar ou Recusar. (durante a fase de propagação de eventos de clique)

   bannerDomElt {DOMElement} o elemento DOM raiz do banner de cookie que precisa ser removido

* **NL.ClientWebTracking.hasUserPrefs()**: retorna verdadeiro se o usuário tiver escolhido suas preferências para o rastreamento web.
* **NL.ClientWebTracking.getUserPrefs()**: retorna o valor de cookie de opt out que define as preferências do usuário.

Se você precisar gravar uma JSSP, as APIs do lado do servidor estarão disponíveis:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**: gera a marcação para o banner de opt out a ser inserido na página JSSP

   **escapeJs {Boolean}**: verdadeiro quando a marcação gerada precisa de escape para ser usada dentro do JavaScript.

   Retorna o HTML da marcação de banner de opt out que precisa ser impressa na página.

* **NL.ServerWebTracking._displayOptOutBanner()**

   Retorna &quot;true&quot; se o banner de recusa for exibido após a seleção de um banner de recusa pelo administrador

   Esse código é chamado quando o administrador já optou por usar o banner de opt out de rastreamento web.

   O banner deve ser exibido se o usuário ainda não tiver escolhido ser rastreado ou não.

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

   Renderiza a marcação para o banner de opt out inserindo-o na página JSSP. Ele é chamado como no Jssp entre &lt;% %>

   **escapeJs {Boolean}**: verdadeiro quando a marcação gerada precisa de escape para ser usada dentro do JavaScript

Exemplo de JSSP:

```
<%@ page import="/nl/core/shared/nl.js" %>
<!doctype html>
<%
NL.require('/nl/core/shared/webTracking.js');
NL.client.require('/nl/core/shared/webTracking.js');
%>
<html>
<head>
<%==NL.client.deps()%>
</head>

<body>

<!-- TEST USING SERVER API IN JSSP -->
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
webTracking.renderOptOutBanner();
%>

<!-- TEST USING SERVER API IN A SCRIPT -->
<!--
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
%>
<script>var el = document.createElement('div'); el.innerHTML =  "<% webTracking.renderOptOutBanner(true); %>";document.body.appendChild(el);</script>
-->

<!-- TEST OF THE CLIENT API -->
<!--
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
-->
</body>
</html>
```
