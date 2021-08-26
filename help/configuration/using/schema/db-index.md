---
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---

# elemento dbindex {#dbindex--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-3}

dbindex:==keyfield

## Atributos {#attributes-3}

* @_operation (cadeia de caracteres)
* @applicableIf (cadeia de caracteres)
* @label (cadeia de caracteres)
* @name (MNTOKEN)
* @unique (booleano)

## Pais {#parents-3}

`<element>`

## Crianças {#children-3}

`<keyfield>`

## Descrição {#description-3}

Esse elemento permite definir um índice vinculado a uma tabela.

## Uso e contexto de uso {#use-and-context-of-use-3}

É possível definir vários índices. Um índice pode fazer referência a um ou mais campos da tabela. A declaração Index geralmente segue a definição do elemento schema principal.

A ordem dos elementos `<keyfield>` definidos em um `<dbindex>` é muito importante. O primeiro `<keyfield>` deve ser o critério de indexação no qual as consultas se baseiam principalmente.

O nome do índice no banco de dados é calculado concatenando o nome da tabela e o nome do índice. Por exemplo: Nome da tabela &quot;Amostra&quot;, Namespace &quot;Cus&quot;, nome do índice &quot;MyIndex&quot;-> nome do campo de índice durante a consulta de criação de índice: &quot;CusSample_myIndex&quot;.

## Descrição do atributo {#attribute-description-3}

* **_operation (cadeia de caracteres)**: define o tipo de gravação no banco de dados.

   Esse atributo é usado principalmente na extensão de schemas prontos para uso.

   Os valores acessíveis são:

   * &quot;nenhum&quot;: apenas a reconciliação. Isso significa que o Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualizar com inserção. Isso significa que o Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;inserir&quot;: inserção. Isso significa que o Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualizar. Isso significa que o Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que o Adobe Campaign recuperará e excluirá elementos.

* **applicableIf (cadeia de caracteres)**: condição para considerar o índice - recebe uma expressão XTK.
* **label (string)**: rótulo do índice.
* **nome (MNTOKEN)**: nome de índice exclusivo.
* **exclusivo (booleano)**: se essa opção estiver ativada (@unique=&quot;true&quot;), o atributo garantirá a exclusividade do índice em seus campos.

## Exemplos {#examples-3}

Criação de um índice no campo &quot;id&quot;. (o atributo &quot;@unique&quot; no elemento `<dbindex>` aciona a adição da palavra-chave SQL &quot;UNIQUE&quot; quando o índice é criado no banco de dados (query).

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Criação de um índice composto nos campos &quot;@mail&quot; e &quot;@phoneNumber&quot;:

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```
