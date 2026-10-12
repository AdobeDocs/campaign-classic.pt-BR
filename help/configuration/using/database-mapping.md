---
product: campaign
title: Mapeamento de banco de dados
description: Mapeamento de banco de dados
feature: Configuration, Instance Settings
role: Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
TQID: 'https://experienceleague.adobe.com/d3oQ8zJVsjVdj9PZ30rQ8hEuern1l3ZlMAWrbymhnvs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 19%
---
# Mapeamento de banco de dados{#database-mapping}

Esta página descreve como declarar índices nos campos de um esquema.

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8. Para saber mais sobre o mapeamento SQL de esquemas, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}

## Campos indexados {#indexed-fields}

Os índices permitem otimizar o desempenho das consultas SQL usadas na aplicação.

Um índice é declarado pelo elemento principal do schema de dados.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Os índices obedecem às seguintes regras:

* Um índice pode fazer referência a um ou mais campos na tabela
* Um índice pode ser exclusivo (para evitar duplicatas) em todos os campos se o atributo **unique** contiver o valor &quot;true&quot;
* O nome SQL do índice é determinado pelo nome SQL da tabela e pelo nome do índice

>[!NOTE]
>
>* Como padrão, os índices são os primeiros elementos declarados do elemento principal do esquema.
>
>* Os índices são criados automaticamente durante o mapeamento de tabela (padrão ou FDA).

**Exemplo**:

* Adicionar um índice ao endereço de email e à cidade:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Adicionar um índice exclusivo ao campo de nome &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## Saiba mais

Navegue pelos links a seguir para saber mais:

* [Introdução a esquemas](about-schema-reference.md)
* [Estrutura de esquema](schema-structure.md)
* [Gerenciamento de chaves](database-keys.md)
* [Gerenciamento de links](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (documentação do Campaign v8)
