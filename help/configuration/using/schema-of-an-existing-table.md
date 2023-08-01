---
product: campaign
title: Esquema de uma tabela existente
description: Esquema de uma tabela existente
feature: Custom Resources
badge-v7-only: label="v7" type="Informative" tooltip="Aplicável somente ao Campaign Classic v7"
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 12%

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

1. Edite o **[!UICONTROL Administration>Configuration>Data schemas]** da árvore do Adobe Campaign e clique em **[!UICONTROL New]** .
1. Selecione a opção **[!UICONTROL Access data from an existing table or an SQL view]** e clique em **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Escolha a tabela ou a exibição existente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adapte o conteúdo do esquema às suas necessidades.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   O esquema deve ser preenchido com o atributo view=&quot;true&quot; na variável `<srcSchema>` elemento raiz para não gerar um script SQL de criação de tabela.

**Exemplo** :

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

A variável **Federated Data Access - FDA** opção dão acesso aos dados armazenados em um banco de dados externo.

A configuração a ser executada nos schemas para acessar dados em um banco de dados externo é detalhada em [esta página](../../installation/using/creating-data-schema.md).
