---
product: campaign
title: Chamadas de serviço da Web
description: Chamadas de serviço da Web
feature: API
role: Data Engineer, Developer
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 1%

---

# Chamadas de serviço da Web{#web-service-calls}

## Informações gerais {#general-information}

Todos os métodos de API são apresentados no formato de serviços da Web. Isso permite gerenciar todas as funções do Adobe Campaign por meio de chamadas SOAP, que são o ponto de entrada nativo do servidor de aplicativos Adobe Campaign. O próprio console do Adobe Campaign usa apenas chamadas SOAP.

Os serviços da Web permitem criar muitos aplicativos a partir de um sistema de terceiros:

* Alertas síncronos, notificação e execução de modelo de entrega em tempo real a partir de um sistema de back-office ou de transações;
* Desenvolvimento de interfaces especiais com funcionalidade simplificada (interfaces Web, etc.),
* Alimentação e pesquisa de dados no banco de dados, observando as regras comerciais e permanecendo isolados do modelo físico subjacente.

## Definição de serviços Web {#definition-of-web-services}

A definição dos serviços Web implementados no servidor de aplicativos Adobe Campaign está disponível nos schemas de dados.

Um serviço Web é descrito na gramática dos esquemas de dados e está disponível no elemento **`<methods>`**.

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

Temos aqui um exemplo da definição do método chamado **GenerateForm**.

A descrição do serviço começa com o elemento `<method>`. A lista de parâmetros do método foi concluída do elemento `<parameters>`. Cada parâmetro é especificado por um nome, um tipo (Boolean, string, DOMElement, etc.) e uma descrição. O atributo &quot;inout&quot; com o valor &quot;out&quot; permite especificar que o parâmetro &quot;result&quot; está na saída da chamada SOAP.

A presença do atributo &quot;static&quot; (com o valor &quot;true&quot;) descreve esse método como estático, o que significa que todos os parâmetros do método devem ser declarados.

Um método &quot;const&quot; tem implicitamente um documento XML no formato de seu schema associado como sua entrada.

Uma descrição completa do elemento `<method>` de um esquema Adobe Campaign está disponível no capítulo &quot;Referências de esquema&quot; no [Método](../../configuration/using/schema/method.md)

Exemplo do método &quot;ExecuteQuery&quot; do tipo &quot;const&quot; do esquema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

O parâmetro de entrada desse método é um documento XML no formato do schema &quot;xtk:queryDef&quot;.

## Descrição do serviço Web: WSDL {#web-service-description--wsdl}

Um arquivo WSDL (Web Service Description Library) está disponível para cada serviço. Esse arquivo XML usa uma metalinguagem para descrever o serviço e especificar os métodos, parâmetros e o servidor disponíveis para contatar a execução do serviço.

### Geração de arquivo WSDL {#wsdl-file-generation}

Para gerar um arquivo WSDL, você deve inserir o seguinte URL de um navegador da Web:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Com:

* **`<server>`**: o servidor de aplicativos Adobe Campaign (nlserver web)
* **`<schema>`**: chave de identificação do esquema (namespace:schema_name)

### Exemplo do método &#39;ExecuteQuery&#39; do esquema &#39;xtk:queryDef&#39; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

O arquivo WSDL é gerado pelo URL:

`https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef`

Uma descrição WSDL começa definindo os tipos usados para formar mensagens, associadas em &quot;portas&quot;, conectadas a um protocolo por &quot;vinculações&quot; formando serviços da Web.

#### Tipos {#types}

As definições de tipo são baseadas em esquemas XML. Em nosso exemplo, o método &quot;ExecuteQuery&quot; usa uma cadeia de caracteres &quot;s:string&quot; e um documento XML (`<s:complextype>`) como parâmetros. O valor de retorno do método (&quot;ExecuteQueryResponse&quot;) é um documento XML ( `<s:complextype>`).

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### Mensagens {#messages}

O `<message>` descreve os nomes e tipos de um conjunto de campos a serem enviados. O método usa duas mensagens para transmitir como um parâmetro (&quot;ExecuteQueryIn&quot;) e o valor de retorno (&quot;ExecuteQueryOut&quot;).

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

O `<porttype>` associa as mensagens na operação &quot;ExecuteQuery&quot; disparada pela consulta (&quot;input&quot;) gerando uma resposta (&quot;output&quot;).

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Vinculação {#binding}

A parte `<binding>` especifica o protocolo de comunicação SOAP ( `<soap:binding>` ), o transporte de dados em HTTP (valor do atributo &quot;transport&quot;) e o formato dos dados para a operação &quot;ExecuteQuery&quot;. O corpo do envelope SOAP contém os segmentos de mensagem diretamente sem transformação.

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### Serviço {#service}

A parte `<service>` descreve o serviço &quot;XtkQueryDef&quot; com seu URI na URL do servidor de aplicativos do Adobe Campaign.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Conectividade {#connectivity}

O Adobe Campaign aumentou a segurança para mecanismos de autenticação ao introduzir [zonas de segurança](../../installation/using/security-zones.md) e configurações de gerenciamento de sessão.

Há dois modos de autenticação disponíveis:

* **por meio de uma chamada para o método de logon()**. Esse modo gera um token de sessão e um token de segurança. É o modo mais seguro e, portanto, o mais recomendado.

ou

* **por meio do logon do Adobe Campaign + senha** que cria um token de sessão. O token de sessão expira automaticamente após um período definido. Este modo não é recomendado e requer a redução das configurações de segurança do aplicativo para algumas configurações de zona (allowUserPassword=&quot;true&quot; e sessionTokenOnly=&quot;true&quot;).

### Características do token de sessão {#session-token-characteristics}

O token de sessão tem as seguintes características:

* um ciclo de vida de X horas (o ciclo de vida é configurável no arquivo &#39;serverConf.xml&#39;, o período padrão é de 24 horas)
* uma construção aleatória (ela não contém mais o logon e a senha do usuário)
* quando acessado pela Web:

   * o token de sessão se torna um token permanente e não é destruído depois que o navegador é fechado
   * ele é colocado em um cookie HTTP-ONLY (os cookies devem ser ativados para operadores)

### Características do token de segurança {#security-token-characteristics}

O token de segurança tem as seguintes características:

* é gerado pelo token de sessão
* ele tem um ciclo de vida de 24 horas (configurável no arquivo &quot;serverConf.xml&quot;, o período padrão é de 24 horas)
* ele é armazenado no console do Adobe Campaign
* quando acessado pela Web:

   * ele é armazenado em um documento.propriedade __securityToken
   * os URLs da página são atualizados para atualizar o token de segurança
   * os formulários também são atualizados por um campo oculto contendo o token

#### Movimento do token de segurança {#security-token-movement}

Quando acessada pelo console, é:

* transmitido na resposta de logon (no cabeçalho HTTP)
* usado em cada query (no cabeçalho HTTP)

De um POST e GET HTTP:

* o servidor conclui os links com o token
* o servidor adiciona um campo oculto a formulários

De uma chamada SOAP:

* ele é adicionado aos cabeçalhos de chamada

### Exemplos de chamada {#call-examples}

* Usando **HttpSoapConnection/SoapService**:

```
  
    var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
  var session = new SoapService(cnx, 'urn:xtk:session');
  session.addMethod("Logon", "xtk:session#Logon",
                      ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                      ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
  
  var res = session.Logon("", "admin", "pwd", <param/>);
  var sessionToken = res[0];
  var securityToken = res[2];
  
  cnx.addTokens(sessionToken, securityToken);
  var query = new SoapService(cnx, 'urn:xtk:queryDef');
  query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                      ["sessiontoken", "string", "entity", "NLElement"],
                      ["res", "NLElement"]);
  
  var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@email = 'joe.doe@aol.com'"/>
            </where>
          </queryDef>);
  logInfo(queryRes[0].toXMLString())
```

* Usando **HttpServletRequest**:

>[!NOTE]
>
>As URLs usadas nas chamadas **HttpServletRequest** a seguir precisam estar em lista de permissões na seção de permissões de URL do arquivo **serverConf.xml**. Isso também é verdadeiro para o URL do próprio servidor.

Execução() de logon:

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
    '<soapenv:Header/>' +
    '<soapenv:Body>' +
        '<urn:Logon>' +
            '<urn:sessiontoken></urn:sessiontoken>' +
            '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
            '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
            '<urn:elemParameters></urn:elemParameters>' +
        '</urn:Logon>' +
    '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
           
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

Execução da consulta:

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
             '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
                '<queryDef operation="select" schema="nms:recipient">' +
                  '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                  '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
                '</queryDef>' +
           '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```
