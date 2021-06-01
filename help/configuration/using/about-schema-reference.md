---
product: campaign
title: Sobre referência de schema no Adobe Campaign Classic
description: Saiba como configurar schemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign Classic.
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 7%

---

# Sobre referência do esquema{#about-schema-reference}

Este capítulo descreve como configurar schemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign.

Para obter uma melhor compreensão das tabelas integradas do Campaign e sua interação, consulte o [Campaign Classic data model](https://helpx.adobe.com/br/campaign/kb/acc-datamodel.html).

A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de **schema**.

Um schema é um documento XML associado a uma tabela de banco de dados. Ele define a estrutura de dados e descreve a definição SQL da tabela:

* O nome da tabela
* Campos
* Índices
* Links com outras tabelas

Ele também descreve a estrutura XML usada para armazenar dados:

* Elementos e atributos
* Hierarquia de elementos
* Tipos de elemento e atributo
* Valores padrão
* Rótulos, descrições e outras propriedades.

Os esquemas permitem definir uma entidade no banco de dados. Existe um schema para cada entidade.

A ilustração a seguir mostra a localização dos schemas no sistema de dados do Adobe Campaign:

![](assets/reference_schema_intro.png)

## Sintaxe de schemas {#syntax-of-schemas}

O elemento raiz do schema é **`<srcschema>`**. Ele contém os subelementos **`<element>`** e **`<attribute>`**.

O primeiro subelemento **`<element>`** coincide com a raiz da entidade.

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

As tags **`<element>`** definem os nomes dos elementos da entidade. **`<attribute>`** as tags do schema definem os nomes dos atributos nas  **`<element>`** tags às quais foram vinculadas.

## Identificação de um schema {#identification-of-a-schema}

Um schema de dados é identificado por seu nome e namespace.

Um namespace permite agrupar um conjunto de schemas por área de interesse. Por exemplo, o namespace **cus** é usado para configuração específica do cliente (**customers**).

>[!IMPORTANT]
>
>Como padrão, o nome do namespace deve ser conciso e deve conter somente caracteres autorizados de acordo com as regras de nomenclatura XML.
>
>Os identificadores não devem começar com caracteres numéricos.

Determinados namespaces são reservados para descrições das entidades do sistema necessárias para a operação do aplicativo Adobe Campaign:

* **xtk**: no que diz respeito aos dados do sistema da plataforma,
* **nl**: sobre a utilização global do pedido,
* **nms**: relativo ao delivery (recipient, delivery, rastreamento etc.),
* **ncm**: em matéria de gestão de conteúdos,
* **temp**: reservado para schemas temporários.

A chave de identificação de um schema é uma cadeia de caracteres criada usando o namespace e o nome separados por dois pontos; por exemplo: **cus:recipient**.
