---
product: campaign
title: Elementos e atributos - elemento do atributo
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 1%

---

# elemento do atributo {#attribute--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model}

atributo:==help

## Atributos {#attributes}

_operation (cadeia de caracteres), advanced (boolean), applicableIf (cadeia de caracteres), autoIncrement (booleano), pertenceTo (cadeia de caracteres), dataPolicy (cadeia de caracteres), dbEnum (cadeia de caracteres), defOnDuplicate (booleano), padrão (cadeia de caracteres), edit (cadeia de caracteres), expr (cadeia de caracteres), recurso (cadeia de caracteres), featureDate (booleano), img (string), inout (string), rótulo (string), comprimento (string), localizável (booleano), name (MNTOKEN), notNull (booleano), pkgStatus (string), ref (string), obrigatório (booleano), sql (booleano), sqlDefault (string), sqll name (string), sqltable (string), target (MNTOKEN), template (string), translationDefault (string), translationExpr (string), type (MNTOKEN), user (booleano), userEnum (string), visibleIf (string), xml (booleano)

## Pais {#parents}

`<element>`

## Filhos {#children}

`<help>`

## Descrição {#description}

`<attribute>` permitem definir um campo no banco de dados.

## Uso e contexto de uso {#use-and-context-of-use}

`<attribute>` devem ser declarados em um `<element>` elemento.

A sequência em que `<attribute>` são definidos em um `<srcschema>` não afeta a sequência de criação de campos no banco de dados. A sequência de criação será alfabética.

## Descrição do atributo {#attribute-description}

* **_operation (cadeia de caracteres)**: define o tipo de gravação no banco de dados.

   Esse atributo é usado principalmente na extensão de schemas prontos para uso.

   Os valores acessíveis são:

   * &quot;nenhum&quot;: apenas a reconciliação. Isso significa que o Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualizar com inserção. Isso significa que o Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;inserir&quot;: inserção. Isso significa que o Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualizar. Isso significa que o Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que o Adobe Campaign recuperará e excluirá elementos.

* **avançado (booleano)**: quando essa opção é ativada (@advanced=&quot;true&quot;), ela permite ocultar o atributo na lista de campos disponíveis acessíveis para configurar uma lista em um formulário.
* **applicableIf (cadeia de caracteres)**: esse atributo permite tornar os campos opcionais. O `<attribute>` será considerado ao atualizar o banco de dados quando a restrição for cumprida. &quot;applicableIf&quot; recebe uma expressão XTK.
* **autoIncrement (booleano)**: se essa opção estiver ativada, o campo se tornará um contador. Isso permite incrementar um valor (em sua maioria, IDs). (uso externo)
* **insertTo (cadeia de caracteres)**: pega o nome e o namespace da tabela que compartilha o campo e preenche o schema em que o atributo é declarado. (usado somente em um `<schema>`).
* **dataPolicy (cadeia de caracteres)**: permite especificar restrições de aprovação em valores permitidos no campo SQL ou XML. Os valores para este atributo são:

   * &quot;nenhum&quot;: sem valor
   * &quot;smartCase&quot;: maiúsculas das primeiras letras
   * &quot;lowerCase&quot;: todas as minúsculas
   * &quot;upperCase&quot;: todas as maiúsculas
   * &quot;email&quot;: endereço de email
   * &quot;Telefone&quot;: número de telefone
   * &quot;identificador&quot;: nome do identificador
   * &quot;resIdentifier&quot;: nome do arquivo

* **dbEnum (cadeia de caracteres)**: recebe o nome interno de uma enumeração &quot;fechada&quot;. Os valores de enumeração devem ser definidos na variável `<srcschema>`.
* **defOnDuplicate (booleano)**: se esse atributo estiver ativado, quando um registro for duplicado, o valor padrão (definido em @default) será automaticamente reaplicado ao registro.
* **padrão (string)**: permite definir o valor do campo padrão (chamada para uma função, valor padrão). Esse atributo recebe uma expressão XTK.
* **desc (cadeia de caracteres)**: permite inserir uma descrição do atributo. Essa descrição é exibida na barra de status da interface.
* **edit (string)**: esse atributo especifica o tipo de entrada que será usado no formulário vinculado ao schema.
* **enum (string)**: recebe o nome da enumeração vinculada ao campo . A enumeração pode ser inserida no mesmo schema ou em um schema remoto.
* **expr (string)**: define uma expressão de pré-cálculo de campo. Esse atributo recebe um Xpath ou uma expressão XTK.
* **recurso (string)**: define um campo de características: Esses campos são usados para estender os dados em uma tabela existente, mas com armazenamento em uma tabela em anexo. Os valores aceitos são:

   * &quot;shared&quot;: o conteúdo é armazenado em uma tabela compartilhada por tipo de dados
   * &quot;dedicado&quot;: o conteúdo é armazenado em uma tabela dedicada

   As tabelas de características SQL são criadas automaticamente com base no tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Existem dois tipos de campos de características: campos oà¹ simples em que um único valor é autorizado nos campos característicos e oà¹ múltipla escolha, em que a característica é vinculada a um elemento de coleção que pode conter vários valores.

   Quando uma característica é definida em um schema, esse schema deve ter uma chave principal com base em um único campo (chaves compostas não são autorizadas).

* **featureDate (booleano)**: atributo vinculado ao campo de características &quot;@feature&quot;. Se o valor for &quot;true&quot;, ele permitirá descobrir quando o valor foi atualizado pela última vez.
* **img (string)**: permite definir um caminho para uma imagem vinculada a um campo (namespace + nome da imagem)(exemplo: img=&quot;cus:mypicture.jpg&quot;). Fisicamente, a imagem deve ser importada para o servidor de aplicativos.
* **label (string)**: rótulo vinculado ao campo, destinado principalmente ao usuário na interface. Isso permite evitar restrições de nomenclatura.
* **length (string)**: máx. número de caracteres para um valor do campo SQL tipo &quot;string&quot;. Se o atributo &quot;@length&quot; não for especificado, o Adobe Campaign criará automaticamente um campo para 255 caracteres.
* **localizável (booleano)**: se estiver ativado, esse atributo informará a ferramenta de coleta para recuperar o valor do atributo &quot;@label&quot; para tradução (uso interno).
* **name (MNTOKEN)**: nome do atributo que corresponderá ao nome do campo na tabela. O valor do atributo &quot;@name&quot; deve ser curto, preferencialmente em inglês, e estar em conformidade com as restrições de nomenclatura XML.

   Quando o schema é gravado no banco de dados, os prefixos são adicionados automaticamente ao nome do campo pelo Adobe Campaign:

   * &quot;i&quot;: prefixo para o tipo &quot;inteiro&quot;.
   * &quot;d&quot;: prefixo para o tipo &quot;duplo&quot;.
   * &quot;s&quot;: prefixo para o tipo de cadeia de caracteres.
   * &quot;ts&quot;: prefixo do tipo &quot;data&quot;.

   Para definir totalmente o nome do campo na tabela, use a opção &quot;@sqlname&quot; ao definir um atributo.

* **notNull (booleano)**: permite redefinir o comportamento do Adobe Campaign em relação ao gerenciamento de registros NULL no banco de dados. Por padrão, os campos numéricos não são nulos, e os campos do tipo string e date podem ser nulos.
* **pkgStatus (cadeia de caracteres)**: durante exportações de pacote, os valores são considerados, dependendo do valor de &quot;@pkgStatus&quot;:

   * &quot;always&quot;: sempre presente
   * &quot;never&quot;: nunca presente
   * &quot;padrão (ou nada)&quot;: o valor é exportado, exceto se for o valor padrão ou se não for um campo interno que não seria compatível com outras instâncias.

* **ref (string)**: esse atributo define uma referência a um `<attribute>` elemento compartilhado por vários schemas (fator de definição). A definição não é copiada para o schema atual.
* **obrigatório (booleano)**: se este atributo for ativado (@required=&quot;true&quot;), o campo será realçado na interface. O rótulo do campo será vermelho nos formulários.
* **sql (booleano)**: se este atributo for ativado (@sql=&quot;true&quot;), ele forçará o armazenamento do atributo SQL, mesmo quando o elemento que contém o atributo tiver a propriedade xml=&quot;true&quot;.
* **sqlDefault (cadeia de caracteres)**: esse atributo permite definir o valor padrão levado em conta para atualizar o banco de dados se o atributo @notNull for ativado. Se esse atributo for adicionado após a criação do atributo, o comportamento do schema não será alterado mesmo para os novos registros. Para alterar o schema e atualizar o valor de novos registros, é necessário excluir e criar novamente o atributo.
* **sqlname (cadeia de caracteres)**: do campo durante a criação da tabela. Se @sqlname não for especificado, o valor do atributo &quot;@name&quot; será usado por padrão. Quando o schema é gravado no banco de dados, os prefixos são adicionados automaticamente, dependendo do tipo de campo.
* **template (string)**: esse atributo define uma referência a um `<attribute>` elemento compartilhado por vários schemas. A definição é copiada automaticamente para o schema atual.
* **translationDefault (cadeia de caracteres)**: se um atributo &quot;@default&quot; for encontrado, &quot;@translationDefault&quot; permitirá redefinir uma expressão para corresponder à definida em @default, a ser coletada pela ferramenta de tradução (uso interno).
* **translationExpr (cadeia de caracteres)**: se um atributo &quot;@expr&quot; estiver presente, o atributo &quot;@translationExpr&quot; permitirá que você redefina uma expressão para corresponder à definida em @expr, a ser coletada pela ferramenta de tradução (uso interno).
* **tipo (MNTOKEN)**: tipo de campo.

   Os tipos de campo são genéricos. Dependendo do tipo de banco de dados instalado, o Adobe Campaign altera o tipo definido em um valor específico para o banco de dados instalado durante a atualização da estrutura.

   Lista de tipos disponíveis:

   * QUALQUER UMA
   * compartimento
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * double
   * enum
   * float
   * html
   * int64
   * Link 
   * long
   * memorando
   * MNTOKEN
   * percent
   * chave primária
   * short
   * sequência de caracteres
   * tempo
   * timespan
   * uuid

   Se o atributo &quot;@type&quot; for deixado vazio, o Adobe Campaign vinculará uma cadeia de caracteres (STRING) com um comprimento de 100 ao campo por padrão.

   Se o campo for do tipo STRING e o nome do campo não for especificado pela presença do atributo &quot;@sqlname&quot;, o nome do campo no banco de dados será automaticamente precedido por um &quot;s&quot;. Esse modo operacional será semelhante aos campos dos tipos INTEGER (i), DOUBLE (d) e DATES (ts) .

* **userEnum (cadeia de caracteres)**: recebe o nome interno de uma enumeração &quot;open&quot;. Os valores da enumeração podem ser definidos pelo usuário na interface.
* **visibleIf (cadeia de caracteres)**: define uma condição no formato de uma expressão XTK para mostrar ou ocultar o atributo.

   >[!IMPORTANT]
   >
   >O atributo está oculto, mas seus dados ainda podem ser acessados.

* **xml (booleano)**: se essa opção estiver ativada, os valores do campo não terão um campo SQL vinculado. O Adobe Campaign cria um campo &quot;mData&quot; do tipo Text para o armazenamento de registros. Isso significa que não há filtragem ou classificação nesses campos.

### Exemplos {#examples}

Exemplo de valores de enumeração cujos valores são armazenados no banco de dados:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

Declaração de um campo XML com &quot;@datapolicy&quot;:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

Exemplo com um &quot;@applicableIf&quot;: o atributo &quot;contains&quot; só será criado se o número de países for maior que 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Exemplo com &quot;@feature&quot; do tipo &quot;shared&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Exemplo com &quot;@feature&quot; do tipo &quot;dedicated&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
