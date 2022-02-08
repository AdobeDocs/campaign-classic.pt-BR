---
product: campaign
title: Sobre referência de schema no Adobe Campaign Classic
description: Saiba como configurar schemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign Classic
feature: Schema Extension
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 8%

---

# Sobre referência do esquema{#about-schema-reference}

![](../../assets/v7-only.svg)

Este capítulo descreve como configurar schemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign.

Para obter uma melhor compreensão das tabelas integradas do Campaign e sua interação, consulte [Modelo de dados Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/data-model/about-data-model.html?lang=pt-BR).

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

O elemento raiz do schema é **`<srcschema>`**. Ele contém a variável **`<element>`** e **`<attribute>`** subelementos.

O primeiro **`<element>`** O subelemento coincide com a raiz da entidade.

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

O **`<element>`** as tags definem os nomes dos elementos da entidade. **`<attribute>`** as tags do schema definem os nomes dos atributos no **`<element>`** tags às quais foram vinculadas.

## Identificação de um schema {#identification-of-a-schema}

Um schema de dados é identificado por seu nome e namespace.

Um namespace permite agrupar um conjunto de schemas por área de interesse. Por exemplo, a variável **cus** o namespace é usado para configuração específica do cliente (**clientes**).

A chave de identificação de um schema é uma cadeia de caracteres criada usando o namespace e o nome separados por dois pontos; por exemplo: **cus:recipient**.

>[!IMPORTANT]
>
>O nome do namespace deve ser conciso e deve conter somente caracteres autorizados de acordo com as regras de nomenclatura XML.
>
>Os identificadores não devem começar com caracteres numéricos.
>
>Os seguintes namespaces são reservados para descrições das entidades do sistema necessárias para a operação do aplicativo Adobe Campaign e não devem ser usados: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.

