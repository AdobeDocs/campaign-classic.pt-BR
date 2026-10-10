---
product: campaign
title: Enviar alertas personalizados aos operadores
description: Saiba como enviar alertas personalizados aos operadores
feature: Workflows
hide: true
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
TQID: 'https://experienceleague.adobe.com/AhEp-fucKo-UN8M9kzPxqpbHU2ichyv1LHa-qeN9qRc'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 100%
---
# Enviar alertas personalizados aos operadores{#sending-personalized-alerts-to-operators}



Neste exemplo, queremos enviar um alerta para um operador que conterá os nomes dos perfis que abriram um boletim informativo, mas não clicaram no link que ele continha.

Os campos de nome e sobrenome dos perfis são vinculados à dimensão de direcionamento **[!UICONTROL Recipients]**, enquanto a atividade **[!UICONTROL Alert]** é vinculada à dimensão de direcionamento **[!UICONTROL Operator]**. Como resultado, não há nenhum campo disponível entre as duas dimensões de direcionamento para executar uma reconciliação e recuperar os campos de nome e sobrenome e exibi-los na atividade Alert.

O processo é criar um fluxo de trabalho como abaixo:

1. Use uma atividade **[!UICONTROL Query]** para direcionar dados.
1. Adicione uma atividade **[!UICONTROL JavaScript code]** no fluxo de trabalho para salvar o formulário de preenchimento da consulta à variável de instância.
1. Utilize uma atividade **[!UICONTROL Test]** para verificar a contagem de população.
1. Use uma atividade **[!UICONTROL Alert]** para enviar um alerta para um operador, dependendo do resultado da atividade **[!UICONTROL Test]**.

![](assets/uc_operator_1.png)

## Salvar a população na variável de instância {#saving-the-population-to-the-instance-variable}

Adicione o código abaixo na atividade **[!UICONTROL JavaScript code]**.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Verifique se o código Javascript corresponde às suas informações de fluxo de trabalho:

* A tag **[!UICONTROL queryDef schema]** deve corresponder ao nome da dimensão de direcionamento usada na atividade de consulta.
* A tag **[!UICONTROL node expr]** deve corresponder ao nome dos campos que você deseja recuperar.

![](assets/uc_operator_3.png)

Para recuperar essas informações, siga as etapas abaixo:

1. Clique com o botão direito do mouse na transição de saída da atividade de **[!UICONTROL Query]** e selecione **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Clique com o botão direito do mouse na lista e depois selecione **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. A dimensão de direcionamento e os nomes de campos da consulta são exibidos na lista.

   ![](assets/uc_operator_6.png)

## Teste da contagem de população {#testing-the-population-count}

Adicione o código abaixo na atividade **[!UICONTROL Test]** para verificar se a população direcionada contém pelo menos 1 perfil.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Configuração de um alerta {#setting-up-the-alert}

Agora que a população foi adicionada na variável da instância com os campos desejados, é possível adicionar essas informações na atividade **[!UICONTROL Alert]**.

Para fazer isso, adicione o código abaixo na guia **[!UICONTROL Source]**:

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>O comando **[!UICONTROL <%= item.target.recipient.@fieldName %>]** permite adicionar um dos campos que foram salvos na variável da instância por meio da atividade **[!UICONTROL JavaScript code]**.\
>É possível adicionar quantos campos desejar, desde que tenham sido inseridos no código JavaScript.

![](assets/uc_operator_8.png)
