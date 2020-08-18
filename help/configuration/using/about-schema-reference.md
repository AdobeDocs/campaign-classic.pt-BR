---
title: Sobre referência de schema no Adobe Campaign Classic
description: Saiba como configurar schemas de extensão para estender o modelo de dados conceituais do banco de dados Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d4ebaaf90d88cbec9a4d24d79eaf7c46890d933a
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 7%

---


# Sobre a referência do schema{#about-schema-reference}

Este capítulo descreve como configurar schemas de extensão para estender o modelo de dados conceituais do banco de dados Adobe Campaign.

Para obter uma melhor compreensão das tabelas integradas de Campanha e de suas interações, consulte o modelo [de dados de](https://helpx.adobe.com/br/campaign/kb/acc-datamodel.html)Campaign Classic.

A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. It obeys a grammar specific to Adobe Campaign, called a **schema**.

Um schema é um documento XML associado a uma tabela de banco de dados. Define a estrutura de dados e descreve a definição SQL da tabela:

* O nome da tabela
* Campos
* Índices
* Links com outras tabelas

Também descreve a estrutura XML usada para armazenar dados:

* Elementos e atributos
* Hierarquia de elementos
* Tipos de elementos e atributos
* Valores padrão
* Rótulos, descrições e outras propriedades.

Schemas permitem que você defina uma entidade no banco de dados. Há um schema para cada entidade.

A ilustração a seguir mostra a localização dos schemas no sistema de dados Adobe Campaign:

![](assets/reference_schema_intro.png)

## Sintaxe de schemas {#syntax-of-schemas}

O elemento raiz do schema é **`<srcschema>`**. Contém os subelementos **`<element>`** e **`<attribute>`** .

O primeiro **`<element>`** subelemento coincide com a raiz da entidade.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>O elemento raiz da entidade tem o mesmo nome do schema.

![](assets/s_ncs_configuration_schema_and_entity.png)

As **`<element>`** tags definem os nomes dos elementos da entidade. **`<attribute>`** as tags do schema definem os nomes dos atributos nas **`<element>`** tags às quais foram vinculados.

## Identificação de um schema {#identification-of-a-schema}

Um schema de dados é identificado pelo nome e pela namespace.

Uma namespace permite agrupar um conjunto de schemas por área de interesse. Por exemplo, a namespace **cus** é usada para configuração específica do cliente (**clientes**).

>[!IMPORTANT]
>
>Como padrão, o nome da namespace deve ser conciso e conter somente caracteres autorizados de acordo com as regras de nomenclatura XML.
>
>Os identificadores não devem começar com caracteres numéricos.

Determinadas namespaces são reservadas para descrições das entidades do sistema necessárias para a operação do aplicativo Adobe Campaign:

* **xtk**: no que diz respeito aos dados do sistema da plataforma,
* **nl**: relativa à utilização global do pedido,
* **nms**: relativamente ao delivery (recipient, delivery, localização, etc.),
* **ncm**: relativamente à gestão de conteúdo,
* **temp**: reservado para schemas temporários.

The identification key of a schema is a string built using the namespace and the name separated by a colon; for example: **cus:recipient**.
