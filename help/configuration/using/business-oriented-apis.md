---
title: APIs direcionadas para empresas
seo-title: APIs direcionadas para empresas
description: APIs direcionadas para empresas
seo-description: null
page-status-flag: never-activated
uuid: ddb6e5cf-dfe0-4dc9-ac5b-fab21827b874
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: e7b3ffca-c85f-498d-89b4-23fcff59de49
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 4%

---


# APIs direcionadas para empresas{#business-oriented-apis}

API comercial são específicas para cada tipo de objeto. Têm um efeito sobre:

* Deliveries:

   * Criando uma ação de delivery, consulte [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * enviar uma campanha (start, pausa, parar, enviar prova),
   * recuperação de logs do delivery.

* Fluxos de trabalho:

   * iniciar um fluxo de trabalho,
   * verificação dos processos, etc.

      Consulte os métodos [SOAP no JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestão de conteúdo
* Gerenciamento de subscrições, consulte [Assinar (nms:subscrição)](#subscribe--nms-subscription-) e [Cancelar inscrição (nms:subscrição)](#unsubscribe--nms-subscription-).
* Processos de dados: importações, exportações.

Esta seção detalha o uso dos serviços &quot;Assinar&quot;, &quot;Cancelar inscrição&quot; e &quot;SubmeterEntrega&quot;.

>[!IMPORTANT]
>
>[A documentação](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) JSAPI da campanha contém informações adicionais sobre chamadas SOAP e uso do Javascript no Adobe Campaign, bem como uma referência completa a todos os métodos e funções usados no aplicativo.

## Assinar (nms:subscrição) {#subscribe--nms-subscription-}

Esse serviço permite que você assine um recipient a um serviço de informação e atualize o perfil do recipient.

Os seguintes parâmetros são necessários para chamar o serviço:

* autenticação,
* nome interno da subscrição no serviço,
* um documento XML contendo as informações do recipient (do schema &quot;nms:recipient&quot;),
* um booliano para criação de recipient, se ainda não houver.

Descrição do método &quot;subscribe&quot; no schema &quot;nms:subscrição&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

A definição da chave de reconciliação deve ser inserida por meio do atributo _**key** no `<recipient>` elemento do documento XML. O conteúdo desse atributo é uma lista XPath separada por vírgulas.

Esta chamada não retorna nenhum dado, exceto erros.

### Exemplos {#examples}

Subscrição com chave de reconciliação do recipient no endereço de email: o documento XML de entrada deve fazer referência ao endereço de email e à definição da chave neste campo.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Atualização do recipient e da subscrição.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Exemplo de mensagens SOAP {#example-of-soap-messages}

* Query:

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

## Cancelar inscrição (nms:subscrição) {#unsubscribe--nms-subscription-}

Este serviço permite cancelar a inscrição de um recipient de um serviço de informação e atualizar o perfil do recipient.

Os seguintes parâmetros são necessários para chamar o serviço:

* autenticação,
* Nome interno do serviço para cancelar a inscrição,
* um documento XML contendo as informações do recipient (do schema &quot;nms:recipient&quot;),

Descrição do método &quot;Cancelar inscrição&quot; no schema &quot;nms:subscrição&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

A definição da chave de reconciliação deve ser inserida por meio do atributo _key no `<recipient>` elemento do documento XML. O conteúdo desse atributo é uma lista XPath separada por vírgulas.

Se o recipient não estiver presente no banco de dados ou não estiver inscrito no serviço de informação em questão, o serviço não executará nenhuma ação e não gerará um erro.

>[!NOTE]
>
>Se o nome do serviço não for especificado como um parâmetro, o recipient será então automaticamente colocado na lista de bloqueios (@lista de bloqueios=&quot;1&quot;).

Esta chamada não retorna nenhum dado, exceto erros.

### Exemplo de mensagens SOAP {#example-of-soap-messages-1}

Query:

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

Esse serviço permite criar e enviar uma ação de delivery.

Os seguintes parâmetros são necessários para chamar o serviço:

* autenticação,
* nome interno do template do delivery,
* um documento XML opcional que contém dados de delivery adicionais.

Essa API não deve ser chamada em volume, pois pode haver problemas de desempenho.

Descrição do método no seu schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Um template do delivery deve ser criado a partir do console do cliente Adobe Campaign. Contém os parâmetros comuns a todos os delivery (endereço do remetente ou duração de validade da mensagem).

O documento XML de entrada é um fragmento de template do delivery que obedece à estrutura do schema &quot;nms:delivery&quot;. Ele conterá todos os dados adicionais que não puderam ser definidos estaticamente no template do delivery (por exemplo, lista de recipient para público alvo).

Esta chamada não retorna nenhum dado, exceto erros.

### Exemplo de documento XML {#xml-document-example}

Este exemplo é baseado em um template do delivery personalizado de uma fonte externa de dados (um arquivo nesse caso). A configuração é totalmente descrita no template do delivery, de modo que tudo o que ainda precisa ser enviado quando a chamada ocorrer é o conteúdo do arquivo do `<externalsource>` elemento.

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

Se você não tiver um template do delivery, poderá usar a seguinte amostra:

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

