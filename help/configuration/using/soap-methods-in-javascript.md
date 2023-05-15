---
product: campaign
title: Métodos SOAP em JavaScript
description: Métodos SOAP em JavaScript
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---

# Métodos SOAP em JavaScript{#soap-methods-in-javascript}

Este é o JavaScript executado no servidor do Adobe Campaign.

## Métodos estáticos {#static-methods}

Métodos SOAP estáticos são acessados chamando um método no objeto que representa o esquema. Esquemas são propriedades de objetos &#39;namespace&#39;. Esses namespaces são variáveis globais, portanto, por exemplo, as variáveis xtk ou nms representam os namespaces correspondentes

O exemplo a seguir chama o método PostEvent estático do schema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Métodos não estáticos {#non-static-methods}

Para usar métodos SOAP não estáticos, é necessário primeiro recuperar uma entidade usando os métodos &quot;get&quot; ou &quot;create&quot; nos esquemas correspondentes.

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

* Consulta na tabela de recipients com uma operação &quot;get&quot;:

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

* Consulta na tabela de recipients com uma operação &quot;select&quot;:

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

* Gravando dados na tabela de recipients:

   ```
   xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
   ```
