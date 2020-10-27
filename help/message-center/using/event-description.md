---
title: Descrição do Evento
seo-title: Descrição do Evento
description: Descrição do Evento
seo-description: null
page-status-flag: never-activated
uuid: 7b174ffd-28b2-4147-b992-e17b0b2cf733
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 3c8388d8-1a91-4d16-a8ac-016f643c6009
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 100%

---


# Descrição do Evento{#event-description}

## Sobre o template de dados de mensagens transacionais {#about-transactional-messaging-datamodel}

As mensagens transacionais dependem do template de dados do Adobe Campaign e usam duas tabelas separadas adicionais. Essas [tabelas](../../configuration/using/data-model-description.md#message-center-module), **NmsRtEvent** e **NmsBatchEvent**, contêm os mesmos campos e permitem gerenciar eventos em tempo real, por um lado, e eventos em lote, por outro.

## Métodos SOAP {#soap-methods}

Esta seção detalha os métodos SOAP associados aos schemas do módulo de mensagens transacionais.

Dois métodos SOAP **PushEvent** ou **PushEvents** estão vinculados aos dois dataschemas **nms:rtEvent** e **nms:BatchEvent.** É o sistema de informações que determina se um evento é do tipo &quot;batch&quot; ou &quot;em tempo real&quot;.

* O **PushEvent** permite inserir um único evento na mensagem,
* O **PushEvents** permite inserir uma série de eventos na mensagem.

O caminho WSDL para acessar ambos os métodos é:

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** para acessar o schema do tipo em tempo real.
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** para acessar o schema do tipo batch.

Ambos os métodos contêm um elemento **`<urn:sessiontoken>`** para fazer logon no módulo de mensagens transacionais. Recomendamos usar um método de identificação por meio de endereços IP confiáveis. Para recuperar o token de sessão, execute uma chamada SOAP de logon e depois um token GET seguido de um logoff. Use o mesmo token para várias chamadas RT. Os exemplos incluídos nesta seção estão usando o método de token de sessão que é o recomendado.

Caso você esteja usando um servidor loadbalanced, use a autenticação Usuário/Senha (no nível da mensagem RT). Exemplo:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

O método **PushEvent** é composto de um parâmetro **`<urn:domevent>`** que contém o evento.

O método **PushEvents** é composto de um parâmetro **`<urn:domeventcollection>`** que contém os eventos.

Exemplo usando PushEvent:

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>No caso de uma chamada ao método **PushEvents**, precisamos adicionar um elemento primário XML para estar em conformidade com o XML padrão. Esse elemento XML enquadrará os vários elementos **`<rtevent>`** contidos no evento.

Exemplo usando PushEvents:

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

Os elementos **`<rtevent>`** e **`<batchevent>`** têm um conjunto de atributos, bem como um elemento filho obrigatório: **`<ctx>`** para integração de dados de mensagem.

>[!NOTE]
>
>O elemento **`<batchevent>`** permite adicionar o evento à fila &quot;batch&quot;. O **`<rtevent>`** adiciona o evento à fila em &quot;tempo real&quot;.

Os atributos obrigatórios dos elementos **`<rtevent>`** e **`<batchevent>`** são @type and @email. O valor de @type deve ser igual ao valor da lista discriminada definido ao configurar a instância de execução. Esse valor permite definir o template a ser vinculado ao conteúdo do evento durante o delivery.

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

Neste exemplo, dois canais são fornecidos: o endereço de email e o número do celular. O **wishedChannel** permite selecionar o canal que deseja usar ao transformar o evento em uma mensagem. O valor &quot;0&quot; corresponde ao canal de email, o valor &quot;1&quot; ao canal móvel e etc.

Se quiser adiar um delivery de evento, adicione o campo **[!UICONTROL scheduled]** seguido da data preferida. O evento será transformado em uma mensagem nessa data.

É recomendável preencher os atributos @wishedChannel e @emailFormat com valores numéricos. A tabela de função que vincula valores numéricos e rótulos é encontrada na descrição do schema de dados.

>[!NOTE]
>
>Uma descrição detalhada de todos os atributos autorizados, bem como seus valores estão disponíveis na descrição do schema de dados **nms:rtEvent** e **nms:BatchEvent**.

O elemento **`<ctx>`** contém os dados da mensagem. Seu conteúdo XML está aberto, o que significa que ele pode ser configurado dependendo do conteúdo a ser entregue.

>[!NOTE]
>
>É importante otimizar o número e o tamanho dos nós XML contidos na mensagem para evitar sobrecarga dos servidores durante o delivery.

Exemplo de dados:

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
   
```

## Informações retornadas pela chamada SOAP {#information-returned-by-the-soap-call}

Ao receber um evento, o Adobe Campaign gera uma ID de retorno exclusiva. Essa é a ID da versão arquivada do evento.

>[!IMPORTANT]
>
>Ao receber chamadas SOAP, o Adobe Campaign verifica o formato de endereço de email. Se um endereço de email estiver com a formatação incorreta, um erro será retornado.

* Exemplo de um identificador retornado pelo método quando o processamento do evento é bem-sucedido:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">72057594037935966</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

Se o valor do identificador de retorno for estritamente maior que zero, isso significa que o evento foi arquivado com êxito no Adobe Campaign.

No entanto, se houver falha no processo do evento, o método retornará uma mensagem de erro ou um valor igual a zero.

* Exemplo de processamento de um evento que falhou quando o query não contém um login ou o operador especificado não tem os direitos necessários:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
            <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Exemplo de evento que falhou devido a um erro no query (a classificação XML não cumpriu com):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
            <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
   Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
      <soapenv:Header/>
      <soapenv:Body>
         <urn:PushEvent>
            <urn:sessiontoken>mc/</urn:sessiontoken>
            <urn:domEvent>
   <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
         externalId="1596" language="english" country="EN" emailFormat="2"
         mobilePhone="+447700123123">
     <ctx>
      <website name="eCommerce" url="http://www.eCo']]></detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Exemplo de evento que falhou e retornou um identificador zero (nome de método errado):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

