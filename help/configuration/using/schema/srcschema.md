---
product: campaign
title: Elementos e atributos - elemento srcschema
description: Elementos e atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# elemento srcschema {#srcschema--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-14}

srcSchema:==(attribute | createdBy | dados | element | enumeração | ajuda | interface | Métodos | modifiedBy)

## Atributos {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (booleano), mappingType (string), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (booleano), view (booleano), xtkschema (string)

## Pais {#parents-14}

nenhuma

## Filhos {#children-14}

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

O `<srcschema>` é o elemento raiz de um esquema. É o ponto de entrada para a definição do schema.

## Uso e contexto de uso {#use-and-context-of-use-9}

A apresentação do esquema está disponível em [Sobre a referência do esquema](../../../configuration/using/about-schema-reference.md) e a [Estrutura do esquema](../../../configuration/using/schema-structure.md).

## Descrição do atributo {#attribute-description-14}

* **created (datetime)**: este atributo fornece informações sobre a data e a hora da criação do esquema. Ele tem um formulário de &quot;Data e hora&quot;. Os valores exibidos são retirados do servidor. A hora é mostrada no formato UTC.
* **createdBy-id (long)**: é o identificador do operador que criou o esquema.
* **desc (cadeia de caracteres)**: descrição do esquema
* **entitySchema (string)**: esquema básico no qual a sintaxe e a aprovação são baseadas (por padrão para Adobe Campaign: xtk:srcSchema). Ao salvar o esquema atual, o Adobe Campaign aprovará sua gramática com o esquema declarado no atributo @xtkschema.
* **extendedSchema (cadeia de caracteres)**: recebe o nome do esquema predefinido no qual a extensão de esquema atual se baseia. O formulário é &quot;namespace:name&quot;.
* **img (cadeia de caracteres)**: ícone vinculado ao esquema (pode ser definido no assistente de criação de esquemas).
* **rótulo (cadeia de caracteres)**: rótulo de esquema.
* **labelSingular (string)**: rótulo (singular) para exibição na interface.
* **lastModified (datetime)**: este atributo fornece informações sobre a data e a hora da última modificação. Ele tem um formulário de &quot;Data e hora&quot;. Os valores exibidos são retirados do servidor. A hora é mostrada no formato UTC.
* **biblioteca (booleano)**: uso do esquema como uma biblioteca e não como uma entidade. Portanto, esse schema pode ser referenciado por outros schemas graças aos atributos &quot;@ref&quot; e &quot;@template&quot;.
* **mappingType (cadeia de caracteres)**:

   * &quot;sql&quot;: mapeamento de banco de dados
   * &quot;textFile&quot;: mapeamento de arquivo de texto
   * &quot;xmlFile&quot;: mapeamento de arquivo de texto em formato XML
   * &quot;binaryFile&quot;: mapeamento de arquivo binário

* **modifiedBy-id (long)**: corresponde ao identificador do operador que alterou o esquema.
* **nome (cadeia de caracteres)**: nome de esquema exclusivo.
* **namespace (cadeia de caracteres)**: namespace do esquema (padrão: nms, xtk, nl). Ao criar um novo schema para um projeto, recomendamos que você use um namespace dedicado.
* **useRecycleBin (booleano)**: ativa o recurso de lixeira no aplicativo. Os registros excluídos serão colocados no lixo antes da exclusão final. Essa função só está disponível no modo &quot;Delivery&quot;.
* **exibição (booleano)**: se estiver ativado (@view=&quot;true&quot;), o esquema será usado como exibição. O assistente de atualização da estrutura do banco de dados não levará o esquema em consideração. Essa opção é usada principalmente para fazer referência a tabelas externas.
* **xtkschema (string)**: nome do esquema que define a gramática do esquema (xtk:srcSchema por padrão).

## Exemplos {#examples-11}

`<srcschema>` elemento do &quot;nms:delivery&quot; esquema predefinido

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
