---
title: APIs orientadas para empresas
seo-title: APIs orientadas para empresas
description: APIs orientadas para empresas
seo-description: null
page-status-flag: never-activated
uuid: ddb6e5cf-dfe0-4dc9-ac5b-fab21827b874
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: e7b3ffca-c85f-498d-89b4-23fcff59de49
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# APIs orientadas para empresas{#business-oriented-apis}

API comercial são específicas para cada tipo de objeto. Têm um efeito sobre:

* Entregas:

   * Criando uma ação de entrega, consulte [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * enviar uma campanha (iniciar, pausar, parar, enviar prova),
   * recuperando registros de entrega.

* Fluxos de trabalho:

   * iniciar um fluxo de trabalho,
   * verificação dos processos, etc.

      Consulte os métodos [SOAP no JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestão de conteúdo
* Gerenciamento de assinaturas, consulte [Assinar (nms:assinatura)](#subscribe--nms-subscription-) e [Cancelar inscrição (nms:assinatura)](#unsubscribe--nms-subscription-).
* Processos de dados: importações, exportações.

Esta seção detalha o uso dos serviços &quot;Assinar&quot;, &quot;Cancelar inscrição&quot; e &quot;SubmeterEntrega&quot;.

>[!IMPORTANT]
>
>[A documentação](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html) JSAPI da campanha contém informações adicionais sobre chamadas SOAP e uso do Javascript no Adobe Campaign, bem como uma referência completa a todos os métodos e funções usados no aplicativo.

## Assinar (nms:assinatura) {#subscribe--nms-subscription-}

Esse serviço permite que você assine um destinatário a um serviço de informações e atualize o perfil do destinatário.

Os seguintes parâmetros são necessários para chamar o serviço:

* autenticação,
* nome interno do serviço de assinatura,
* um documento XML contendo as informações do destinatário (do esquema &quot;nms:receipt&quot;),
* um booliano para a criação do destinatário, se ainda não houver.

Descrição do método &quot;subscribe&quot; no esquema &quot;nms:subscription&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

A definição da chave de reconciliação deve ser inserida pelo atributo _**key** no `<recipient>` elemento do documento XML. O conteúdo desse atributo é uma lista XPath separada por vírgulas.

Esta chamada não retorna nenhum dado, exceto erros.

### Exemplos {#examples}

Assinatura com chave de reconciliação do destinatário no endereço de email: o documento XML de entrada deve mencionar o endereço de email e a definição da chave neste campo.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Atualização do destinatário e da assinatura.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Exemplo de mensagens SOAP {#example-of-soap-messages}

* Consulta:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <sessiontoken xsi:type='xsd:string'/>
         <service xsi:type='xsd:string'>SVC1</service>
         <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient _key="@email" email= "john.doe@adobe.com/>
         </content>
         <create xsi:type='xsd:boolean'>true</create>
       </m:Subscribe>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Resposta:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## Cancelar assinatura (nms:assinatura) {#unsubscribe--nms-subscription-}

Este serviço permite cancelar a assinatura de um destinatário de um serviço de informações e atualizar o perfil do destinatário.

Os seguintes parâmetros são necessários para chamar o serviço:

* autenticação,
* Nome interno do serviço para cancelar a inscrição,
* um documento XML contendo as informações do destinatário (do esquema &quot;nms:receipt&quot;),

Descrição do método &quot;Cancelar inscrição&quot; no esquema &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

A definição da chave de reconciliação deve ser inserida por meio do atributo _key no `<recipient>` elemento do documento XML. O conteúdo desse atributo é uma lista XPath separada por vírgulas.

Se o destinatário não estiver presente no banco de dados ou não estiver inscrito no serviço de informações em questão, o serviço não executará nenhuma ação e não gerará um erro.

>[!NOTE]
>
>Se o nome do serviço não for especificado como um parâmetro, o destinatário será automaticamente incluído na lista negra (@blackList=&quot;1&quot;).

Esta chamada não retorna nenhum dado, exceto erros.

### Exemplo de mensagens SOAP {#example-of-soap-messages-1}

Consulta:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

Resposta:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery (nms:delivery) {#submitdelivery--nms-delivery-}

Esse serviço permite que você crie e envie uma ação de entrega.

Os seguintes parâmetros são necessários para chamar o serviço:

* autenticação,
* nome interno do modelo de entrega,
* um documento XML opcional contendo dados de entrega adicionais.

Essa API não deve ser chamada em volume, pois pode haver problemas de desempenho.

Descrição do método em seu esquema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Um modelo de entrega deve ser criado a partir do console do cliente Adobe Campaign. Contém os parâmetros comuns a todas as entregas (endereço do remetente ou duração de validade da mensagem).

O documento XML de entrada é um fragmento de modelo de entrega que obedece à estrutura do esquema &quot;nms:delivery&quot;. Ele conterá todos os dados adicionais que não puderam ser definidos estaticamente no modelo de entrega (por exemplo, lista de destinatários a serem direcionados).

Esta chamada não retorna nenhum dado, exceto erros.

### Exemplo de documento XML {#xml-document-example}

Este exemplo é baseado em um modelo de entrega personalizado de uma fonte de dados externa (um arquivo nesse caso). A configuração está totalmente descrita no modelo de entrega, portanto, tudo o que ainda precisa ser enviado quando a chamada ocorrer é o conteúdo do arquivo do `<externalsource>` elemento.

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

Se você não tiver um modelo de entrega, poderá usar a seguinte amostra:

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```

