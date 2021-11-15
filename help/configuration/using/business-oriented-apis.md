---
product: campaign
title: APIs direcionadas por empresas
description: APIs direcionadas por empresas
audience: configuration
content-type: reference
topic-tags: api
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 5d9e2f7d7cea9e6d1243b0e3a790f3990772e603
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 2%

---

# APIs direcionadas por empresas{#business-oriented-apis}

![](../../assets/v7-only.svg)

As APIs de negócios são específicas para cada tipo de objeto. Eles têm efeito sobre:

* Entregas:

   * Criação de uma ação de delivery, consulte [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * enviar uma campanha (iniciar, pausar, parar, enviar prova),
   * recuperando logs do delivery.

* Fluxos de trabalho:

   * iniciar um workflow,
   * verificar processos, etc.

      Consulte [Métodos SOAP em JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestão de conteúdo
* Gerenciamento de subscrição, consulte [Assinar (nms:subscription)](#subscribe--nms-subscription-) e [Cancelar inscrição (nms:subscription)](#unsubscribe--nms-subscription-).
* Processos de dados: importações, exportações.

Esta seção detalha o uso dos serviços &quot;Subscribe&quot;, &quot;Unsubscribe&quot; e &quot;SubmitDelivery&quot;.

>[!IMPORTANT]
>
>[Documentação JSAPI do Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html) contém informações adicionais sobre chamadas SOAP e uso de Javascript no Adobe Campaign, bem como uma referência completa a todos os métodos e funções usados no aplicativo.

## Assinar (nms:subscription) {#subscribe--nms-subscription-}

Esse serviço permite assinar um recipient para um serviço de informações e atualizar o perfil do recipient.

Os seguintes parâmetros são necessários para chamar o serviço:

* uma autenticação,
* nome interno do serviço de assinatura,
* um documento XML contendo as informações do recipient (do schema &quot;nms:recipient&quot;),
* um booleano para criação de recipient se ainda não houver um.

Descrição do método &quot;subscribe&quot; no schema &quot;nms:subscription&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

A definição da chave de reconciliação deve ser inserida por meio do _**key** no `<recipient>` elemento do documento XML. O conteúdo desse atributo é uma lista XPath separada por vírgulas.

Essa chamada não retorna dados, exceto erros.

### Exemplos {#examples}

Assinatura com chave de reconciliação de recipient no endereço de email: o documento XML de entrada deve referenciar o endereço de email e a definição da chave nesse campo.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Atualização do recipient e da subscrição.

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

## Cancelar inscrição (nms:subscription) {#unsubscribe--nms-subscription-}

Esse serviço permite cancelar a subscrição de um recipient em um serviço de informação e atualizar o perfil do recipient.

Os seguintes parâmetros são necessários para chamar o serviço:

* uma autenticação,
* Nome interno do serviço para cancelar a subscrição,
* um documento XML contendo as informações do recipient (do schema &quot;nms:recipient&quot;),

Descrição do método &quot;Unsubscribe&quot; no schema &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

A definição da chave de reconciliação deve ser inserida por meio do atributo _key na variável `<recipient>` elemento do documento XML. O conteúdo desse atributo é uma lista XPath separada por vírgulas.

Se o recipient não estiver presente no banco de dados ou não estiver inscrito no serviço de informações relacionado, o serviço não executará nenhuma ação e não gerará um erro.

>[!NOTE]
>
>Se o nome do serviço não for especificado como um parâmetro, o recipient será automaticamente em lista de bloqueios(@blackList=&quot;1&quot;).

Essa chamada não retorna dados, exceto erros.

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

Esse serviço permite criar e enviar uma ação de delivery.

Os seguintes parâmetros são necessários para chamar o serviço:

* uma autenticação,
* nome interno do template de delivery,
* um documento XML opcional contendo dados de delivery adicionais.

Essa API não deve ser chamada em volume, pois pode haver problemas de desempenho.

Descrição do método em seu schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Um template do delivery deve ser criado a partir do console do cliente do Adobe Campaign. Ele contém os parâmetros comuns a todos os deliveries (endereço do remetente ou duração da validade da mensagem).

O documento XML de entrada é um fragmento de modelo de delivery que obedece à estrutura do schema &quot;nms:delivery&quot;. Ele conterá todos os dados adicionais que não puderam ser definidos estaticamente no template do delivery (por exemplo, lista de recipients a serem alvos).

Essa chamada não retorna dados, exceto erros.

### Exemplo de documento XML {#xml-document-example}

Este exemplo é baseado em um template de delivery personalizado de uma fonte de dados externa (um arquivo, neste caso). A configuração é totalmente descrita no template do delivery, portanto, tudo o que permanece para ser enviado quando a chamada ocorrer é o conteúdo do arquivo do `<externalsource>` elemento.

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
