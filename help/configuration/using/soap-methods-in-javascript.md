---
solution: Campaign Classic
product: campaign
title: Métodos SOAP em JavaScript
description: Métodos SOAP em JavaScript
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---


# Métodos SOAP em JavaScript{#soap-methods-in-javascript}

Este é o JavaScript executado no servidor Adobe Campaign.

## Métodos estáticos {#static-methods}

Métodos SOAP estáticos são acessados chamando um método no objeto que representa o schema. Schemas são propriedades de objetos &#39;namespace&#39;. Essas namespaces são variáveis globais, portanto, por exemplo, as variáveis xtk ou nms representam as namespaces correspondentes

O exemplo a seguir chama o método PostEvent estático do schema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Métodos não estáticos {#non-static-methods}

Para usar métodos SOAP não estáticos, é necessário primeiro recuperar uma entidade usando os métodos &quot;get&quot; ou &quot;create&quot; nos schemas correspondentes.

O exemplo a seguir chama o método ExecuteQuery do schema &quot;xtk:queryDef&quot;:

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## Exemplos {#examples}

* Query na tabela recipient com uma operação &quot;get&quot;:

   ```
   var query = xtk.queryDef.create(  
     <queryDef schema="nms:recipient" operation="get">    
       <select>      
         <node expr="@firstName"/>      
         <node expr="@lastName"/>      
         <node expr="@email"/>    
       </select>    
       <where>      
         <condition expr="@email = 'peter.martinez@adobe.com'"/>    
       </where>  
     </queryDef>)
   
   var recipient = query.ExecuteQuery()
   
   logInfo(recipient.@firstName)
   logInfo(recipient.@lastName)
   ```

* Query na tabela recipient com uma operação &quot;select&quot;:

   ```
   var query = xtk.queryDef.create(  
     <queryDef schema="nms:recipient" operation="select">    
       <select>      
         <node expr="@email"/>      
         <node expr="@lastName"/>      
         <node expr="@firstName"/>    
       </select>    
       <where>      
         <condition expr="@age > 25"/>    
       </where>    
     </queryDef>)
   
   var res = query.ExecuteQuery()
   
   for each (var recipient in res.recipient) 
   {  
     logInfo(recipient.@email)  
     logInfo(recipient.@firstName)  
     logInfo(recipient.@lastName)
   }
   ```

* Gravando dados na tabela do recipient:

   ```
   xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
   ```

