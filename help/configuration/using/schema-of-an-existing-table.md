---
title: Schema de uma tabela existente
seo-title: Schema de uma tabela existente
description: Schema de uma tabela existente
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 14%

---


# Schema de uma tabela existente{#schema-of-an-existing-table}

## Visão geral {#overview}

Quando o aplicativo precisar acessar os dados de uma tabela existente, uma visualização SQL ou dados de um banco de dados remoto, crie seu schema no Adobe Campaign com os seguintes dados:

* Nome da tabela: digite o nome da tabela (com seu alias quando um dblink é usado) com o atributo &quot;sqltable&quot;,
* Chave do schema: referência ao(s) campo(s) de reconciliação,
* índices: utilizados para gerar query,
* Os campos e sua localização na estrutura XML: preencher apenas os campos usados no aplicativo,
* links: se houver junções com as outras tabelas da base.

## Implementação {#implementation}

Para criar o schema correspondente, aplique as seguintes etapas:

1. Edite o **[!UICONTROL Administration>Configuration>Data schemas]** nó da árvore do Adobe Campaign e clique em **[!UICONTROL New]** .
1. Selecione a opção **[!UICONTROL Access data from an existing table or an SQL view]** e clique em **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Escolha a tabela ou a visualização existente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adapte o conteúdo do schema às suas necessidades.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   O schema deve ser preenchido com o atributo visualização=&quot;true&quot; no elemento `<srcSchema>` raiz para não gerar um script SQL de criação de tabela.

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

A opção **Federated Data Acces - FDA** fornece acesso aos dados armazenados em um banco de dados externo.

A configuração a ser realizada nos schemas para acessar dados em um banco de dados externo é detalhada [nesta página](../../installation/using/creating-data-schema.md).
