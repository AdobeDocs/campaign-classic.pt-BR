---
product: campaign
title: Métodos SOAP em JavaScript
feature: Configuration, Instance Settings
description: Métodos SOAP em JavaScript
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 13%

---

# Métodos SOAP em JavaScript{#soap-methods-in-javascript}

Esse é o JavaScript executado no servidor do Adobe Campaign.

## Métodos estáticos {#static-methods}

Os métodos SOAP estáticos são acessados chamando um método no objeto que representa o esquema. Os esquemas são propriedades de objetos &#39;namespace&#39;. Esses namespaces são variáveis globais, portanto, por exemplo, as variáveis xtk ou nms representam os namespaces correspondentes

O exemplo a seguir invoca o método PostEvent estático do schema xtk:workflow:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Métodos não estáticos {#non-static-methods}

Para usar métodos SOAP não estáticos, é necessário primeiro recuperar uma entidade usando os métodos &quot;get&quot; ou &quot;create&quot; nos schemas correspondentes.

O exemplo a seguir invoca o método ExecuteQuery do schema &quot;xtk:queryDef&quot;:

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

* Consulte a tabela de recipients com uma operação &quot;select&quot;:

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

* Gravando dados na tabela de destinatários:

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```
