---
product: campaign
title: Elementos e atributos - elemento srcschema
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# elemento srcschema {#srcschema--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-14}

srcSchema:=(attribute | criadoBy | dados | elemento | enumeração | ajuda | interface | métodos | modifiedBy)

## Atributos {#attributes-14}

criado (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implementações (string), rótulo (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), nome (string), espace (string), useRecycleBin (booleano), view (booleano), xtkschema (string)

## Pais {#parents-14}

nenhuma

## Crianças {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## Descrição {#description-14}

O `<srcschema>` é o elemento raiz de um schema. É o ponto de entrada para a definição do schema.

## Uso e contexto de uso {#use-and-context-of-use-9}

A apresentação do schema está disponível em [Sobre a referência do schema](../../../configuration/using/about-schema-reference.md) e [Estrutura do schema](../../../configuration/using/schema-structure.md).

## Descrição do atributo {#attribute-description-14}

* **criado (datetime)**: esse atributo fornece informações sobre a data e a hora da criação do schema. Ele tem um formulário de &quot;Data e hora&quot;. Os valores exibidos são obtidos do servidor. A hora é mostrada no formato UTC.
* **createdBy-id (long)**: é o identificador do operador que criou o schema.
* **desc (cadeia de caracteres)**: descrição do schema
* **entitySchema (cadeia de caracteres)**: esquema básico no qual a sintaxe e a aprovação são baseadas (por padrão para o Adobe Campaign: xtk:srcSchema). Ao salvar o schema atual, o Adobe Campaign aprovará sua gramática com o schema declarado no atributo @xtkschema.
* **extendedSchema (cadeia de caracteres)**: O recebe o nome do schema pronto para uso no qual a extensão do schema atual se baseia. O formulário é &quot;namespace:name&quot;.
* **img (string)**: ícone vinculado ao schema (pode ser definido no assistente de criação de schema).
* **label (string)**: rótulo do esquema.
* **labelSingular (cadeia de caracteres)**: rótulo (singular) para exibição na interface.
* **lastModified (datetime)**: este atributo fornece informações sobre a data e a hora da última modificação. Ele tem um formulário de &quot;Data e hora&quot;. Os valores exibidos são obtidos do servidor. A hora é mostrada no formato UTC.
* **biblioteca (booleano)**: usar o schema como uma biblioteca e não como uma entidade. Esse schema pode, portanto, ser referenciado por outros schemas graças aos atributos &quot;@ref&quot; e &quot;@template&quot;.
* **mappingType (cadeia de caracteres)**:

   * &quot;sql&quot;: mapeamento de banco de dados
   * &quot;textFile&quot;: mapeamento de arquivo de texto
   * &quot;xmlFile&quot;: Mapeamento de arquivo de texto do formato XML
   * &quot;binaryFile&quot;: mapeamento de arquivo binário

* **modifiedBy-id (long)**: corresponde ao identificador do operador que alterou o esquema.
* **name (string)**: nome exclusivo do esquema.
* **namespace (cadeia de caracteres)**: namespace do schema (padrão: nms, xtk, nl). Ao criar um novo schema para um projeto, recomendamos que você use um namespace dedicado.
* **useRecycleBin (booleano)**: ativa o recurso de lixeira no aplicativo. Os registros excluídos serão colocados na lixeira antes da exclusão final. Essa função só está disponível no modo &quot;Delivery&quot;.
* **view (booleano)**: se estiver ativado (@view=&quot;true&quot;), o schema será usado como uma visualização. O assistente de atualização da estrutura do banco de dados não levará o schema em consideração. Essa opção é usada principalmente para fazer referência a tabelas externas.
* **xtkschema (cadeia de caracteres)**: nome do schema que define a gramática do schema (xtk:srcSchema por padrão).

## Exemplos {#examples-11}

`<srcschema>` elemento do schema pronto para uso &quot;nms:delivery&quot;

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
