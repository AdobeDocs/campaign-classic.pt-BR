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
source-wordcount: '454'
ht-degree: 1%

---


# elemento srcschema {#srcschema--element}

## Modelo de conteúdo {#content-model-14}

srcSchema:==(atributo) | createdBy | dados | elemento | lista discriminada | ajuda | interface | Métodos | modifiedBy)

## Atributos {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), ExtendedSchema (string), img (string), implementações (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (booleano), visualização (booleano), xtkschema (string)

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

O `<srcschema>` é o elemento raiz de um schema. É o ponto de entrada para a definição do schema.

## Uso e contexto de uso {#use-and-context-of-use-9}

A apresentação do schema está disponível em [Sobre a referência do schema](../../../configuration/using/about-schema-reference.md) e [estrutura do Schema](../../../configuration/using/schema-structure.md).

## Descrição do atributo {#attribute-description-14}

* **criado (datetime)**: este atributo fornece informações sobre a data e a hora da criação do schema. Ele tem um formulário &quot;Data e hora&quot;. Os valores exibidos são obtidos do servidor. A hora é exibida no formato UTC.
* **createdBy-id (long)**: é o identificador do operador que criou o schema.
* **desc (string)**: descrição do schema
* **entitySchema (string)**: schema básico no qual a sintaxe e a aprovação se baseiam (por padrão para o Adobe Campaign: xtk:srcSchema). Quando você salvar o schema atual, a Adobe Campaign aprovará sua gramática com o schema declarado no atributo @xtkschema.
* **ExtendedSchema (string)**: recebe o nome do schema predefinido no qual a extensão do schema atual se baseia. O formulário é &quot;namespace:nome&quot;.
* **img (string)**: ícone vinculado ao schema (pode ser definido no assistente de criação do schema).
* **label (string)**: Rótulo do schema.
* **labelSingular (string)**: label (singular) para exibição na interface.
* **lastModified (datetime)**: este atributo fornece informações sobre a data e a hora da última modificação. Ele tem um formulário &quot;Data e hora&quot;. Os valores exibidos são obtidos do servidor. A hora é exibida no formato UTC.
* **biblioteca (booleana)**: uso do schema como uma biblioteca e não como uma entidade. Este schema pode, portanto, ser referenciado por outros schemas graças aos atributos &quot;@ref&quot; e &quot;@template&quot;.
* **mappingType (string)**:

   * &quot;sql&quot;: mapeamento de banco de dados
   * &quot;textFile&quot;: mapeamento de arquivos de texto
   * &quot;xmlFile&quot;: Mapeamento do arquivo de texto do formato XML
   * &quot;binaryFile&quot;: mapeamento de arquivos binários

* **modifiedBy-id (long)**: corresponde ao identificador do operador que alterou o schema.
* **name (string)**: nome exclusivo do schema.
* **namespace (string)**: namespace do schema (padrão: nms, xtk, nl). Ao criar um novo schema para um projeto, recomendamos que você use uma namespace dedicada.
* **useRecycleBin (booleano)**: ativa o recurso de lixeira no aplicativo. Os registros excluídos serão colocados no lixo antes da exclusão final. Esta função só está disponível no modo &quot;Delivery&quot;.
* **visualização (booleana)**: se estiver ativado (@visualização=&quot;true&quot;), o schema será usado como uma visualização. O assistente de atualização da estrutura do banco de dados não levará o schema em conta. Esta opção é principalmente utilizada para fazer referência a tabelas externas.
* **xtkschema (string)**: nome do schema que define a gramática do schema (xtk:srcSchema por padrão).

## Exemplos {#examples-11}

`<srcschema>` elemento do schema &quot;nms:delivery&quot; pronto

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
