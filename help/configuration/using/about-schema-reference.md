---
product: campaign
title: Introdução a esquemas no Adobe Campaign
description: Saiba como trabalhar com esquemas e estender o modelo de dados conceituais do banco de dados do Adobe Campaign
feature: Schema Extension
role: Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
TQID: https://experienceleague.adobe.com/ikQVjdkvhTM-361S7mcpRYsuhpqjHxX-Y-9wdRCYldg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 372
ht-degree: 2%

---

# Introdução a esquemas {#about-schema-reference}

## O que é um esquema {#what-is-a-schema}

Este capítulo descreve como configurar esquemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign.

Para entender melhor as tabelas integradas do Campaign e suas interações, consulte o [modelo de dados do Campaign Classic](about-data-model.md).

No Adobe Campaign, a estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Um **esquema** é um documento XML associado a uma tabela de banco de dados. Ele define a estrutura de dados e descreve a definição SQL da tabela:

* O nome da tabela
* Campos
* Índices
* Links com outras tabelas

Também descreve a estrutura XML usada para armazenar dados:

* Elementos e atributos
* Hierarquia de elementos
* Tipos de elemento e atributo
* Valores padrão
* Rótulos, descrições e outras propriedades.

Os esquemas permitem definir uma entidade no banco de dados. Há um esquema para cada entidade.

A ilustração a seguir mostra a localização dos esquemas no sistema de dados do Adobe Campaign:

![](assets/reference_schema_intro.png)

## Sintaxe de schemas {#syntax-of-schemas}

O elemento raiz do esquema é **`<srcschema>`**. Ele contém os subelementos **`<element>`** e **`<attribute>`**.

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
>O elemento raiz da entidade tem o mesmo nome que o schema.

![](assets/s_ncs_configuration_schema_and_entity.png)

As marcas **`<element>`** definem os nomes dos elementos da entidade. **`<attribute>`** marcas do esquema definem os nomes dos atributos nas **`<element>`** marcas às quais eles foram vinculados.

## Identificação de um esquema {#identification-of-a-schema}

Um schema de dados é identificado por seu nome e seu namespace.

Um namespace permite agrupar um conjunto de esquemas por área de interesse. Por exemplo, o namespace **cus** é usado para a configuração específica do cliente (**clientes**).

A chave de identificação de um esquema é uma cadeia de caracteres criada com o uso do namespace e do nome separados por dois pontos, por exemplo: **cus:recipient**.

>[!IMPORTANT]
>
>* O nome do namespace deve ser conciso e conter apenas caracteres autorizados de acordo com as regras de nomenclatura XML.
>
>* Os identificadores não devem começar com caracteres numéricos.
>
>* Os namespaces a seguir são reservados para descrições das entidades de sistema necessárias para a operação do aplicativo Adobe Campaign e não devem ser usados: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.
>
