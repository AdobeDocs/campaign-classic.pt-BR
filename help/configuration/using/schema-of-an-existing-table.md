---
title: Esquema de uma tabela existente
seo-title: Esquema de uma tabela existente
description: Esquema de uma tabela existente
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Esquema de uma tabela existente{#schema-of-an-existing-table}

## Visão geral {#overview}

Quando o aplicativo precisar acessar os dados de uma tabela, uma exibição SQL ou dados de um banco de dados remoto, crie seu esquema no Adobe Campaign com os seguintes dados:

* Nome da tabela: digite o nome da tabela (com seu alias quando um dblink é usado) com o atributo &quot;sqltable&quot;,
* chave do esquema: referência aos campos de reconciliação,
* índices: usado para gerar consultas,
* Os campos e sua localização na estrutura XML: preencher apenas os campos usados no aplicativo,
* links: se houver junções com as outras tabelas da base.

## Implementação {#implementation}

Para criar o esquema correspondente, aplique as seguintes etapas:

1. Edite o **[!UICONTROL Administration>Configuration>Data schemas]** nó da árvore do Adobe Campaign e clique em **[!UICONTROL New]** .
1. Selecione a **[!UICONTROL Access data from an existing table or an SQL view]** opção e clique em **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Escolha a tabela ou a exibição existente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adapte o conteúdo do esquema para atender às suas necessidades.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   O esquema deve ser preenchido com o atributo view=&quot;true&quot; no elemento `<srcSchema>` raiz para não gerar um script SQL de criação de tabela.

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

A opção **Federated Data Access - FDA** fornece acesso aos dados armazenados em um banco de dados externo.

A configuração a ser realizada nos esquemas para acessar dados em um banco de dados externo é detalhada [nesta página](../../platform/using/creating-data-schema.md).
