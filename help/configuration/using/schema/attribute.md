---
product: campaign
title: Elementos e atributos - elemento de atributo
description: Elementos e atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 1%

---

# elemento attribute {#attribute--element}


## Modelo de conteúdo {#content-model}

attribute:==help

## Atributos {#attributes}

_operation (string), advanced (booleano), applicableIf (string), autoIncrement (booleano), belongingTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (booleano), default (string), desc (string), edit (string), enum (string), expr (string), feature (string), featureDate (booleano), img (string), inout (string), label (string), length (string), localizable (booleano), nome (MNTOKEN), notNull (booleano), pkgStatus (cadeia de caracteres), ref (cadeia de caracteres), obrigatório (booleano), sql (booleano), sqlDefault (cadeia de caracteres), sqlname (cadeia de caracteres), sqltable (cadeia de caracteres), target (MNTOKEN), modelo (cadeia de caracteres), translateDefault (cadeia de caracteres), translateExpr (cadeia de caracteres), tipo (MNTOKEN), usuário (booleano), userEnum (cadeia de caracteres), visibleIf (cadeia de caracteres), (booleano)

## Pais {#parents}

`<element>`

## Derivados {#children}

`<help>`

## Descrição {#description}

`<attribute>` elementos permitem definir um campo no banco de dados.

## Uso e contexto de uso {#use-and-context-of-use}

`<attribute>` elementos devem ser declarados em um elemento `<element>`.

A sequência em que `<attribute>` elementos são definidos em um `<srcschema>` não afeta a sequência de criação do campo no banco de dados. A sequência de criação será alfabética.

## Descrição do atributo {#attribute-description}

* **_operation (string)**: define o tipo de gravação no banco de dados.

  Esse atributo é usado principalmente ao estender schemas prontos para uso.

  Os valores acessíveis são:

   * &quot;none&quot;: apenas reconciliação. Isso significa que o Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualização com inserção. Isso significa que o Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;insert&quot;: inserção. Isso significa que o Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualização. Isso significa que o Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que o Adobe Campaign recuperará e excluirá elementos.

* **advanced (booleano)**: quando esta opção é ativada (@advanced=&quot;true&quot;), ela permite ocultar o atributo na lista de campos disponíveis acessíveis para configurar uma lista em um formulário.
* **applicableIf (string)**: este atributo permite que você torne os campos opcionais. O elemento `<attribute>` será considerado ao atualizar o banco de dados quando a restrição for atendida. &quot;applicableIf&quot; recebe uma expressão XTK.
* **autoIncrement (booleano)**: se esta opção estiver ativada, o campo se torna um contador. Isso permite incrementar um valor (principalmente IDs). (uso externo)
* **belongingTo (string)**: pega o nome e o namespace da tabela que compartilha o campo e preenche o esquema no qual o atributo é declarado. (usado somente em um `<schema>`).
* **dataPolicy (cadeia de caracteres)**: permite que você especifique restrições de aprovação em valores permitidos no campo SQL ou XML. Os valores para este atributo são:

   * &quot;none&quot;: sem valor
   * &quot;smartCase&quot;: primeiras letras maiúsculas
   * &quot;lowerCase&quot;: todas em minúsculas
   * &quot;upperCase&quot;: todas maiúsculas
   * &quot;email&quot;: endereço de email
   * &quot;phone&quot;: número de telefone
   * &quot;identifier&quot;: nome do identificador
   * &quot;resIdentifier&quot;: nome de arquivo

* **dbEnum (cadeia de caracteres)**: recebe o nome interno de uma enumeração &quot;fechada&quot;. Os valores de enumeração devem ser definidos em `<srcschema>`.
* **defOnDuplicate (booleano)**: se este atributo for ativado, quando um registro for duplicado o valor padrão (definido em @default) será automaticamente reaplicado ao registro.
* **default (string)**: permite definir o valor do campo padrão (chamada para uma função, valor padrão). Este atributo recebe uma expressão XTK.
* **desc (cadeia de caracteres)**: permite inserir uma descrição do atributo. Essa descrição é usada para entender o que é o elemento e para que ele está sendo usado. Você pode exibi-lo no formulário.
* **editar (cadeia de caracteres)**: este atributo especifica o tipo de entrada que será usado no formulário vinculado ao esquema.
* **enum (cadeia de caracteres)**: recebe o nome da enumeração vinculada ao campo. A enumeração pode ser inserida no mesmo schema ou em um schema remoto.
* **expr (cadeia de caracteres)**: define uma expressão de pré-cálculo de campo. Este atributo recebe um Xpath ou uma expressão XTK.
* **recurso (cadeia de caracteres)**: define um campo de características: esses campos são usados para estender os dados em uma tabela existente, mas com armazenamento em uma tabela de anexos. Os valores aceitos são:

   * &quot;shared&quot;: o conteúdo é armazenado em uma tabela compartilhada por tipo de dados
   * &quot;dedicated&quot;: o conteúdo é armazenado em uma tabela dedicada

  As tabelas de características SQL são criadas automaticamente com base no tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * compartilhado: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Há dois tipos de campos de características: campos oà<sup>1</sup> simples, onde um único valor é autorizado na característica, e campos oà<sup>1</sup> de múltipla escolha, onde a característica é vinculada a um elemento de coleção que pode conter vários valores.

  Quando uma característica é definida em um esquema, esse esquema deve ter uma chave principal baseada em um único campo (chaves compostas não são autorizadas).

* **featureDate (booleano)**: atributo vinculado ao campo de características &quot;@feature&quot;. Se o valor for &quot;true&quot;, ele permitirá descobrir quando o valor foi atualizado pela última vez.
* **img (string)**: permite definir um caminho para uma imagem vinculada a um campo (namespace + nome da imagem)(exemplo: img=&quot;cus:mypicture.jpg&quot;). Fisicamente, a imagem deve ser importada para o servidor de aplicativos.
* **rótulo (sequência)**: rótulo vinculado ao campo, destinado principalmente ao usuário na interface. Ela permite evitar restrições de nomenclatura.
* **comprimento (cadeia de caracteres)**: máx. número de caracteres para um valor do campo SQL tipo &quot;string&quot;. Se o atributo &quot;@length&quot; não for especificado, o Adobe Campaign criará automaticamente um campo com 255 caracteres.
* **localizável (booleano)**: se estiver ativado, este atributo informará à ferramenta de coleção para recuperar o valor do atributo &quot;@label&quot; para tradução (uso interno).
* **nome (MNTOKEN)**: nome do atributo que corresponderá ao nome do campo na tabela. O valor do atributo &quot;@name&quot; deve ser curto, de preferência em inglês, e estar em conformidade com as restrições de nomenclatura XML.

  Quando o esquema é gravado no banco de dados, os prefixos são adicionados automaticamente ao nome do campo pelo Adobe Campaign:

   * &quot;i&quot;: prefixo para o tipo &quot;inteiro&quot;.
   * &quot;d&quot;: prefixo do tipo &quot;double&quot;.
   * &quot;s&quot;: prefixo do tipo de sequência de caracteres.
   * &quot;ts&quot;: prefixo do tipo &quot;date&quot;.

  Para definir totalmente o nome do campo na tabela, use a opção &quot;@sqlname&quot; ao definir um atributo.

* **notNull (booleano)**: permite redefinir o comportamento do Adobe Campaign em relação ao gerenciamento de registros NULL no banco de dados. Por padrão, os campos numéricos não são nulos e os campos de tipo de string e data podem ser nulos.
* **pkgStatus (string)**: durante as exportações de pacote, os valores são considerados, dependendo do valor de &quot;@pkgStatus&quot;:

   * &quot;always&quot;: sempre presente
   * &quot;never&quot;: nunca presente
   * &quot;default (or Nothing)&quot;: o valor é exportado, exceto se for o valor padrão ou se não for um campo interno que não seria compatível com outras instâncias.

* **ref (cadeia de caracteres)**: este atributo define uma referência a um elemento `<attribute>` compartilhado por vários esquemas (fatoração de definição). A definição não é copiada para o esquema atual.
* **obrigatório (booleano)**: se este atributo estiver ativado (@required=&quot;true&quot;), o campo será realçado na interface. O rótulo do campo será vermelho nos formulários.
* **sql (booleano)**: se este atributo estiver ativado (@sql=&quot;true&quot;), ele forçará o armazenamento do atributo SQL, mesmo quando o elemento que contém o atributo tiver a propriedade xml=&quot;true&quot;.
* **sqlDefault (string)**: este atributo permite definir o valor padrão considerado para atualizar o banco de dados se o atributo @notNull estiver ativado. Se esse atributo for adicionado após a criação do atributo, o comportamento do esquema não será alterado nem mesmo para os novos registros. Para alterar o schema e atualizar o valor para novos registros, você precisa excluir e criar novamente o atributo.
* **sqlname (cadeia de caracteres)**: do campo durante a criação da tabela. Se @sqlname não for especificado, o valor do atributo &quot;@name&quot; será usado por padrão. Quando o schema é gravado no banco de dados, os prefixos são adicionados automaticamente, dependendo do tipo de campo.
* **modelo (cadeia de caracteres)**: este atributo define uma referência a um elemento `<attribute>` compartilhado por vários esquemas. A definição é copiada automaticamente para o esquema atual.
* **TranslationDefault (cadeia de caracteres)**: se um atributo &quot;@default&quot; for encontrado, o &quot;@translatedDefault&quot; permitirá que você redefina uma expressão para corresponder à definida em @default, a ser coletada pela ferramenta de tradução (uso interno).
* **translateExpr (cadeia de caracteres)**: se um atributo &quot;@expr&quot; estiver presente, o atributo &quot;@translatedExpr&quot; permitirá redefinir uma expressão para corresponder à definida em @expr, a ser coletada pela ferramenta de tradução (uso interno).
* **tipo (MNTOKEN)**: tipo de campo.

  Os tipos de campo são genéricos. Dependendo do tipo de banco de dados instalado, o Adobe Campaign altera o tipo definido em um valor específico para o banco de dados instalado durante a atualização da estrutura.

  Lista de tipos disponíveis:

   * QUALQUER UMA
   * compartimento
   * blob
   * booleano
   * byte
   * CDATA
   * data e hora
   * datetimetz
   * datetimenotz
   * data
   * duplo
   * enum
   * flutuante
   * html
   * int64
   * link
   * long
   * memorando
   * MNTOKEN
   * por cento
   * primarykey
   * curto
   * sequência de caracteres
   * tempo
   * intervalo de tempo
   * uuid

  Se o atributo &quot;@type&quot; for deixado em branco, o Adobe Campaign vinculará uma string de caracteres (STRING) com um comprimento de 100 ao campo, por padrão.

  Se o campo for do tipo STRING e o nome do campo não for especificado pela presença do atributo &quot;@sqlname&quot;, o nome do campo no banco de dados será precedido automaticamente por um &#39;s&#39;. Esse modo operacional será semelhante com os campos do tipo INTEIRO (i), DUPLO (d) e DATAS (ts).

* **userEnum (cadeia de caracteres)**: recebe o nome interno de uma enumeração &quot;aberta&quot;. Os valores da enumeração podem ser definidos pelo usuário na interface.
* **visibleIf (cadeia de caracteres)**: define uma condição no formato de uma expressão XTK para mostrar ou ocultar o atributo.

  >[!IMPORTANT]
  >
  >O atributo está oculto, mas os dados ainda podem ser acessados.

* **xml (booleano)**: se esta opção estiver ativada, os valores do campo não terão um campo SQL vinculado. O Adobe Campaign cria um campo &quot;mData&quot; do tipo Text para armazenamento de registro. Isso significa que não há filtragem ou classificação nesses campos.

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

Exemplo com um &quot;@applicableIf&quot;: o atributo &quot;contains&quot; somente será criado se o número de países for maior que 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Exemplo com &quot;@feature&quot; de tipo &quot;shared&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Exemplo com &quot;@feature&quot; de tipo &quot;dedicado&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
