---
product: campaign
title: Esquema de uma tabela existente
description: Esquema de uma tabela existente
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 12%

---

# Esquema de uma tabela existente{#schema-of-an-existing-table}

![](../../assets/v7-only.svg)

## Visão geral {#overview}

Quando o aplicativo precisar acessar os dados de uma tabela, uma visualização SQL ou dados de um banco de dados remoto, crie seu schema no Adobe Campaign com os seguintes dados:

* Nome da tabela: insira o nome da tabela (com seu alias quando um dblink é usado) com o atributo &quot;sqltable&quot;,
* chave do schema: referência ao(s) campo(s) de reconciliação,
* índices: usado para gerar queries,
* Os campos e sua localização na estrutura XML: preencher apenas os campos usados no aplicativo,
* links: se houver associações com as outras tabelas da base.

## Implementação {#implementation}

Para criar o schema correspondente, aplique os seguintes estágios:

1. Edite o nó **[!UICONTROL Administration>Configuration>Data schemas]** da árvore do Adobe Campaign e clique em **[!UICONTROL New]** .
1. Selecione a opção **[!UICONTROL Access data from an existing table or an SQL view]** e clique em **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Escolha a tabela ou a exibição existente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adapte o conteúdo do esquema de acordo com suas necessidades.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   O schema deve ser preenchido com o atributo view=&quot;true&quot; no elemento raiz `<srcSchema>` para não gerar um script SQL de criação de tabela.

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

A opção **Federated Data Access - FDA** dá acesso aos dados armazenados em um banco de dados externo.

A configuração a ser executada nos schemas para acessar dados em um banco de dados externo é detalhada em [this page](../../installation/using/creating-data-schema.md).
