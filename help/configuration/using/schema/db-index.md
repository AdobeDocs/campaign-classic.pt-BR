---
product: campaign
title: Elementos e atributos - elemento dbindex
description: elemento dbindex
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---

# elemento dbindex {#dbindex--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-3}

dbindex:==keyfield

## Atributos {#attributes-3}

* @_operation (string)
* @applicableIf (string)
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

É possível definir vários índices. Um índice pode fazer referência a um ou mais campos da tabela. A declaração de índice geralmente segue a definição do elemento de esquema principal.

A ordem das `<keyfield>` elementos definidos em uma `<dbindex>` é muito importante. O primeiro `<keyfield>` deve ser o critério de indexação no qual as consultas se baseiam principalmente.

O nome do índice no banco de dados é calculado pela concatenação do nome da tabela e do nome do índice. Por exemplo: Nome de tabela &quot;Sample&quot;, Namespace &quot;Cus&quot;, nome de índice &quot;MyIndex&quot;-> nome do campo de índice durante a criação do índice consultando: &quot;CusSample_myIndex&quot;.

## Descrição do atributo {#attribute-description-3}

* **_operation (string)**: define o tipo de gravação no banco de dados.

   Esse atributo é usado principalmente ao estender schemas prontos para uso.

   Os valores acessíveis são:

   * &quot;none&quot;: apenas reconciliação. Isso significa que o Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualização com inserção. Isso significa que o Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;insert&quot;: inserção. Isso significa que o Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualização. Isso significa que o Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que o Adobe Campaign recuperará e excluirá elementos.

* **applicableIf (string)**: condição para considerar o índice - recebe uma expressão XTK.
* **rótulo (string)**: rótulo do índice.
* **nome (MNTOKEN)**: nome de índice exclusivo.
* **único (booleano)**: se essa opção estiver ativada (@unique=&quot;true&quot;), o atributo garantirá a exclusividade do índice em todos os campos.

## Exemplos {#examples-3}

Criação de um índice no campo &quot;id&quot;. (o atributo &quot;@unique&quot; na variável `<dbindex>` O elemento aciona a adição da palavra-chave &quot;UNIQUE&quot; SQL quando o índice é criado no banco de dados (query).

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
