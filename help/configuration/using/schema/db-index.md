---
solution: Campaign Classic
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---


# dbindex element {#dbindex--element}

## Modelo de conteúdo {#content-model-3}

dbindex:==keyfield

## Atributos {#attributes-3}

* @_operation (string)
* @applyIf (string)
* @label (string)
* @name (MNTOKEN)
* @unique (booleano)

## Pais {#parents-3}

`<element>`

## Filhos {#children-3}

`<keyfield>`

## Descrição {#description-3}

Esse elemento permite definir um índice vinculado a uma tabela.

## Uso e contexto de uso {#use-and-context-of-use-3}

É possível definir vários índices. Um índice pode fazer referência a um ou mais campos da tabela. A declaração de índice segue normalmente a definição do elemento principal do schema.

A ordem dos elementos `<keyfield>` definidos em `<dbindex>` é muito importante. O primeiro `<keyfield>` deve ser o critério de indexação no qual os query se baseiam principalmente.

O nome do índice no banco de dados é calculado concatenando o nome da tabela e o nome do índice. Por exemplo: Nome da tabela &quot;Amostra&quot;, Namespace &quot;Cus&quot;, nome do índice &quot;MyIndex&quot;-> nome do campo de índice durante a consulta da criação do índice: &quot;CusSample_myIndex&quot;.

## Descrição do atributo {#attribute-description-3}

* **_operation (cadeia de caracteres)**: define o tipo de gravação no banco de dados.

   Este atributo é usado principalmente ao estender schemas prontos para uso.

   Os valores acessíveis são:

   * &quot;nenhum&quot;: apenas reconciliação. Isso significa que a Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualizar com inserção. Isso significa que a Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;Inserir&quot;: inserção. Isso significa que a Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualizar. Isso significa que a Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que a Adobe Campaign recuperará e excluirá elementos.

* **applyIf (string)**: condição para levar em conta o índice - recebe uma expressão XTK.
* **label (string)**: rótulo do índice.
* **name (MNTOKEN)**: nome de índice exclusivo.
* **único (booleano)**: se essa opção estiver ativada (@unique=&quot;true&quot;), o atributo garante a exclusividade do índice em todos os campos.

## Exemplos {#examples-3}

Criação de um índice no campo &quot;id&quot;. (o atributo &quot;@unique&quot; no elemento `<dbindex>` aciona a adição da palavra-chave SQL &quot;UNIQUE&quot; quando o índice é criado no banco de dados (query)).

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
