---
title: Sobre referência de esquema no Adobe Campaign Classic
description: Saiba como configurar esquemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign Classic.
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
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Sobre a referência do esquema{#about-schema-reference}

Este capítulo descreve como configurar esquemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign.

Para obter uma melhor compreensão das tabelas integradas do Campaign e de suas interações, consulte o modelo [de dados do](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)Campaign Classic.

A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ele obedece a uma gramática específica do Adobe Campaign, chamada de **esquema**.

Um esquema é um documento XML associado a uma tabela de banco de dados. Define a estrutura de dados e descreve a definição SQL da tabela:

* O nome da tabela
* Campos
* Índices
* Links com outras tabelas

Também descreve a estrutura XML usada para armazenar dados:

* Elementos e atributos
* Hierarquia de elementos
* Tipos de elementos e atributos
* Default values
* Rótulos, descrições e outras propriedades.

Os esquemas permitem que você defina uma entidade no banco de dados. Existe um esquema para cada entidade.

A ilustração a seguir mostra a localização dos esquemas no sistema de dados do Adobe Campaign:

![](assets/reference_schema_intro.png)

## Sintaxe dos esquemas {#syntax-of-schemas}

O elemento raiz do esquema é **`<srcschema>`**. Contém os ** **`<element>`** e **`<attribute>`** subelementos.

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
>O elemento raiz da entidade tem o mesmo nome que o esquema.

![](assets/s_ncs_configuration_schema_and_entity.png)

As **`<element>`** tags definem os nomes dos elementos da entidade. **`<attribute>`** as tags do esquema definem os nomes dos atributos nas **`<element>`** tags às quais foram vinculados.

## Identificação de um esquema {#identification-of-a-schema}

Um esquema de dados é identificado pelo nome e pelo namespace.

Um namespace permite agrupar um conjunto de esquemas por área de interesse. Por exemplo, o namespace **cus** é usado para configuração específica do cliente (**clientes**).

>[!IMPORTANT]
>
>Como padrão, o nome do namespace deve ser conciso e conter somente caracteres autorizados de acordo com as regras de nomenclatura XML.
>
>Os identificadores não devem começar com caracteres numéricos.

Determinados namespaces são reservados para descrições das entidades do sistema necessárias para a operação do aplicativo Adobe Campaign:

* **xtk**: no que diz respeito aos dados do sistema da plataforma,
* **nl**: relativa à utilização global do pedido,
* **nms**: relativamente à entrega (destinatário, entrega, acompanhamento, etc.),
* **ncm**: em matéria de gestão de conteúdos,
* **temp**: reservado para esquemas temporários.

The identification key of a schema is a string built using the namespace and the name separated by a colon; for example: **cus:recipient**.
