---
solution: Campaign Classic
product: campaign
title: Schema de uma tabela existente
description: Schema de uma tabela existente
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 12%

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
