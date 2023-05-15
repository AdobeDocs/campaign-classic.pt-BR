---
product: campaign
title: Integração via SOAP (lado do servidor)
description: Integração via SOAP (lado do servidor)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 100%

---

# Integração via SOAP (lado do servidor){#integration-via-soap-server-side}



Os serviços da Web SOAP fornecidos para o gerenciamento de ofertas são diferentes daqueles normalmente usados no Adobe Campaign. Eles podem ser acessados por meio da URL de interação descrita na seção anterior e permitem apresentar ou atualizar ofertas para um determinado contato.

## Apresentação da oferta {#offer-proposition}

Para uma apresentação de oferta via SOAP, adicione o comando **nms:proposta#Propose** seguido pelos seguintes parâmetros:

* **targetId**: chave primária do recipient (pode ser uma chave composta).
* **maxCount**: especifica o número de apresentações de oferta para o contato.
* **contexto**: permite adicionar informações de contexto no schema de espaço. Se o schema usado for **nms:interaction**, **`<empty>`** deverá ser adicionado.
* **categories**: especifica a(s) categoria(s) que as ofertas devem pertencer.
* **themes**: especifica o(s) tema(s) aos quais a(s) oferta(s) deve pertencer.
* **uuid**: valor do cookie permanente do Adobe Campaign (&quot;uuid230&quot;).
* **nli**: valor do cookie da sessão do Adobe Campaign (&quot;nlid&quot;).
* **noProp**: use o valor &quot;true&quot; para desativar a inserção de proposta.

>[!NOTE]
>
>As configurações **targetId** e **maxCount** são obrigatórias. As outras são opcionais.

Em resposta à query, o serviço SOAP retorna os seguintes parâmetros:

* **interactionId**: ID da interação.
* **propositions**: o elemento XML contém a lista de propostas, cada uma com sua própria identificação e representação HTML.

## Atualização da oferta {#offer-update}

Adicione o comando **nms:interação#UpdateStatus** à URL, seguido desses parâmetros:

* **proposition**: string de caracteres, contém o ID de proposta fornecida como uma saída durante uma apresentação de oferta. Consulte [Apresentação da oferta](#offer-proposition).
* **status**: tipo string, ele especifica o novo status da oferta. Os valores possíveis são listados na enumeração **propositionStatus** , no schema **nms:common.** Por exemplo, inicialmente, o número 3 corresponde ao status **Accepted**.
* **context**: o elemento XML permite adicionar informações de contexto no schema de espaço. Se o schema usado for **nms:interaction**, **`<empty>`** deverá ser adicionado.

## Exemplo usando uma chamada SOAP {#example-using-a-soap-call}

Veja um exemplo de código para uma chamada SOAP:

```
<%
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.mdSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
