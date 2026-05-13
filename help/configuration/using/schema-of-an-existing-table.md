---
product: campaign
title: Esquema de uma tabela existente
description: Esquema de uma tabela existente
feature: Custom Resources
role: Developer
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
TQID: https://experienceleague.adobe.com/Vi1DhgY8tGIhq1TtMOGKeGMrqFgGecfJQHrKyFXTSgg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 216
ht-degree: 9%

---

# Esquema de uma tabela existente{#schema-of-an-existing-table}

## Visão geral {#overview}

Quando o aplicativo precisar acessar os dados de uma tabela existente, uma visualização SQL ou dados de um banco de dados remoto, crie seu esquema no Adobe Campaign com os seguintes dados:

* Name of table: digite o nome da tabela (com seu alias quando um dblink é usado) com o atributo &quot;sqltable&quot;,
* schema key: referencie os campos de reconciliação,
* índices: usados para gerar consultas,
* Os campos e seu local na estrutura XML: preencha apenas os campos usados no aplicativo,
* links: se houver associações com outras tabelas da base.

## Implementação {#implementation}

Para criar o schema correspondente, aplique os seguintes estágios:

1. Edite o nó **[!UICONTROL Administration>Configuration>Data schemas]** da árvore do Adobe Campaign e clique em **[!UICONTROL New]**.
1. Selecione a opção **[!UICONTROL Access data from an existing table or an SQL view]** e clique em **[!UICONTROL Next]**.

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Escolha a tabela ou a exibição existente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adapte o conteúdo do esquema às suas necessidades.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   O esquema deve ser preenchido com o atributo view=&quot;true&quot; no elemento raiz `<srcSchema>` para não gerar um script SQL de criação de tabela.

**Exemplo**:

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## Acesso a um banco de dados externo {#accessing-an-external-database}

A opção **Federated Data Access - FDA** fornece acesso aos dados armazenados em um banco de dados externo.

A configuração a ser executada nos esquemas para acessar dados em um banco de dados externo está detalhada em [esta página](../../installation/using/creating-data-schema.md).
