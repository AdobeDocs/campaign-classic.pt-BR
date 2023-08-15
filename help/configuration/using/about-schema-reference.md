---
product: campaign
title: Sobre a referência do esquema no Adobe Campaign Classic
description: Saiba como configurar esquemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Schema Extension
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 12%

---

# Sobre referência do esquema{#about-schema-reference}

Este capítulo descreve como configurar esquemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign.

Para obter uma melhor compreensão das tabelas integradas do Campaign e sua interação, consulte o [modelo de dados Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/data-model/about-data-model.html?lang=pt-BR).

A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de **schema**.

Um esquema é um documento XML associado a uma tabela de banco de dados. Ele define a estrutura de dados e descreve a definição SQL da tabela:

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

O elemento raiz do esquema é **`<srcschema>`**. Contém a **`<element>`** e **`<attribute>`** subelementos.

O primeiro **`<element>`** o subelemento coincide com a raiz da entidade.

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

A variável **`<element>`** as tags definem os nomes dos elementos da entidade. **`<attribute>`** As tags do esquema definem os nomes dos atributos na variável **`<element>`** tags às quais elas foram vinculadas.

## Identificação de um esquema {#identification-of-a-schema}

Um schema de dados é identificado por seu nome e seu namespace.

Um namespace permite agrupar um conjunto de esquemas por área de interesse. Por exemplo, a variável **cus** O namespace é usado para configuração específica do cliente (**clientes**).

A chave de identificação de um esquema é uma cadeia de caracteres criada usando o namespace e o nome separados por dois pontos, por exemplo: **cus:recipient**.

>[!IMPORTANT]
>
>O nome do namespace deve ser conciso e conter apenas caracteres autorizados de acordo com as regras de nomenclatura XML.
>
>Os identificadores não devem começar com caracteres numéricos.
>
>Os namespaces a seguir são reservados para descrições das entidades do sistema necessárias para a operação do aplicativo Adobe Campaign e não devem ser usados: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.

