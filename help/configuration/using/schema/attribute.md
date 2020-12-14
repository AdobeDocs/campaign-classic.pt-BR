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
source-wordcount: '1553'
ht-degree: 0%

---


# elemento de atributo {#attribute--element}

## Modelo de conteúdo {#content-model}

atributo:==help

## Atributos {#attributes}

_operation (string), advanced (boolean), applyIf (string), autoIncrement (booleano), pertenceTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (booleano), default (string), desc (string), edit (string), enum (string), expr (string), feature (string) featureDate (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string) name (string), sqltable (string), público alvo (MNTOKEN), template (string), traduzdefault (string), traduzidaExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (booleano)

## Pais {#parents}

`<element>`

## Filhos {#children}

`<help>`

## Descrição {#description}

`<attribute>` permitem definir um campo no banco de dados.

## Uso e contexto de uso {#use-and-context-of-use}

`<attribute>` os elementos devem ser declarados em um  `<element>` elemento.

A sequência na qual os elementos `<attribute>` são definidos em `<srcschema>` não afeta a sequência de criação de campos no banco de dados. A sequência de criação será alfabética.

## Descrição do atributo {#attribute-description}

* **_operation (cadeia de caracteres)**: define o tipo de gravação no banco de dados.

   Este atributo é usado principalmente ao estender schemas prontos para uso.

   Os valores acessíveis são:

   * &quot;nenhum&quot;: apenas reconciliação. Isso significa que a Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualizar com inserção. Isso significa que a Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;Inserir&quot;: inserção. Isso significa que a Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualizar. Isso significa que a Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que a Adobe Campaign recuperará e excluirá elementos.

* **avançado (booleano)**: quando essa opção é ativada (@advanced=&quot;true&quot;), ela permite ocultar o atributo na lista de campos disponíveis acessíveis para configurar uma lista em um formulário.
* **applyIf (string)**: esse atributo permite tornar os campos opcionais. O elemento `<attribute>` será considerado ao atualizar o banco de dados quando a restrição for cumprida. &quot;applyIf&quot; recebe uma expressão XTK.
* **autoIncrement (booleano)**: se essa opção estiver ativada, o campo se tornará um contador. Isso permite incrementar um valor (na maioria das IDs). (uso externo)
* **pertenceTo (string)**: pega o nome e a namespace da tabela que compartilha o campo e preenche o schema onde o atributo é declarado. (usado somente em `<schema>`).
* **dataPolicy (string)**: permite especificar restrições de aprovação em valores permitidos no campo SQL ou XML. Os valores para este atributo são:

   * &quot;nenhum&quot;: sem valor
   * &quot;smartCase&quot;: letras maiúsculas e minúsculas
   * &quot;lowerCase&quot;: todas as minúsculas
   * &quot;upperCase&quot;: todas as maiúsculas
   * &quot;email&quot;: endereço de email
   * &quot;phone&quot;: número de telefone
   * &quot;identificador&quot;: nome do identificador
   * &quot;resIdentifier&quot;: nome do arquivo

* **dbEnum (string)**: recebe o nome interno de uma lista discriminada &quot;fechada&quot;. Os valores de lista discriminada devem ser definidos em `<srcschema>`.
* **defOnDuplicate (booleano)**: se esse atributo estiver ativado, quando um registro for duplicado, o valor padrão (definido em @default) será automaticamente reaplicado ao registro.
* **padrão (string)**: permite definir o valor do campo padrão (chamada para uma função, valor padrão). Este atributo recebe uma expressão XTK.
* **desc (string)**: permite inserir uma descrição do atributo. Essa descrição é exibida na barra de status da interface.
* **edit (string)**: esse atributo especifica o tipo de entrada que será usado no formulário vinculado ao schema.
* **enum (string)**: recebe o nome da lista discriminada vinculada ao campo. A lista discriminada pode ser inserida no mesmo schema ou em um schema remoto.
* **expr (string)**: define uma expressão de pré-cálculo de campo. Este atributo recebe uma expressão Xpath ou XTK.
* **recurso (string)**: define um campo de características: Esses campos são usados para estender os dados em uma tabela existente, mas com armazenamento em uma tabela em anexo. Os valores aceitos são:

   * &quot;compartilhado&quot;: o conteúdo é armazenado em uma tabela compartilhada por tipo de dados
   * &quot;dedicado&quot;: o conteúdo é armazenado em uma tabela dedicada

   As tabelas de características SQL são criadas automaticamente com base no tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Há dois tipos de campos de características: campos oà¹ simples onde um único valor é autorizado sobre a característica e oà¹ campos de múltipla escolha, onde a característica está vinculada a um elemento de coleção que pode conter vários valores.

   Quando uma característica é definida em um schema, esse schema deve ter uma chave principal baseada em um único campo (chaves compostas não são autorizadas).

* **featureDate (booleano)**: vinculado ao campo de características &quot;@feature&quot;. Se o valor for &quot;true&quot;, ele permitirá que você descubra quando o valor foi atualizado pela última vez.
* **img (string)**: permite definir um caminho para uma imagem vinculada a um campo (namespace + nome da imagem) (por exemplo: img=&quot;cus:mypicture.jpg&quot;). Fisicamente, a imagem deve ser importada para o servidor de aplicativos.
* **label (string)**: rótulo vinculado ao campo, destinado principalmente ao usuário na interface. Isso permite evitar restrições de nomenclatura.
* **length (string)**: máx. número de caracteres para um valor da &quot;string&quot;, digite campo SQL. Se o atributo &quot;@length&quot; não for especificado, a Adobe Campaign cria automaticamente um campo para 255 caracteres.
* **localizável (booleano)**: se estiver ativado, esse atributo informará a ferramenta de coleta para recuperar o valor do atributo &quot;@label&quot; para conversão (uso interno).
* **name (MNTOKEN)**: nome do atributo que corresponderá ao nome do campo na tabela. O valor do atributo &quot;@name&quot; deve ser curto, de preferência em inglês, e estar em conformidade com as restrições de nomenclatura XML.

   Quando o schema é gravado no banco de dados, os prefixos são adicionados automaticamente ao nome do campo pela Adobe Campaign:

   * &quot;i&quot;: prefixo para o tipo &#39;integer&#39;.
   * &quot;d&quot;: prefixo para o tipo &quot;duplo&quot;.
   * &quot;s&quot;: prefixo para o tipo de string de caractere.
   * &quot;ts&quot;: prefixo para o tipo &#39;date&#39;.

   Para definir completamente o nome do campo na tabela, use a opção &quot;@sqlname&quot; ao definir um atributo.

* **notNull (booleano)**: permite redefinir o comportamento do Adobe Campaign em relação ao gerenciamento de registros NULL no banco de dados. Por padrão, os campos numéricos não são nulos e os campos de cadeia de caracteres e de tipo de data podem ser nulos.
* **pkgStatus (string)**: durante as exportações do pacote, os valores são considerados dependendo do valor de &quot;@pkgStatus&quot;:

   * &quot;always&quot;: está sempre presente
   * &quot;nunca&quot;: nunca presente
   * &quot;padrão (ou nada)&quot;: o valor é exportado, exceto se for o valor padrão ou se não for um campo interno que não seja compatível com outras instâncias.

* **ref (string)**: esse atributo define uma referência a um  `<attribute>` elemento compartilhado por vários schemas (fator de definição). A definição não é copiada para o schema atual.
* **obrigatório (booleano)**: se este atributo estiver ativado (@required=&quot;true&quot;), o campo será realçado na interface. O rótulo do campo será vermelho nos formulários.
* **sql (booleano)**: se esse atributo estiver ativado (@sql=&quot;true&quot;), ele forçará o armazenamento do atributo SQL, mesmo quando o elemento que contém o atributo tiver a propriedade xml=&quot;true&quot;.
* **sqlDefault (string)**: esse atributo permite que você defina o valor padrão considerado para a atualização do banco de dados se o atributo @notNull estiver ativado. Se esse atributo for adicionado após a criação do atributo, o comportamento do schema não será alterado mesmo para os novos registros. Para alterar o schema e atualizar o valor de novos registros, é necessário excluir e criar novamente o atributo.
* **sqlname (string)**: do campo durante a criação da tabela. Se @sqlname não for especificado, o valor do atributo &quot;@name&quot; será usado por padrão. Quando o schema é gravado no banco de dados, os prefixos são adicionados automaticamente dependendo do tipo de campo.
* **template (string)**: esse atributo define uma referência a um  `<attribute>` elemento compartilhado por vários schemas. A definição é copiada automaticamente para o schema atual.
* **transactionDefault (string)**: se um atributo &quot;@default&quot; for encontrado, o &quot;@traduzdefault&quot; permitirá que você redefina uma expressão para corresponder àquela definida em @default, a ser coletada pela ferramenta de conversão (uso interno).
* **transactionExpr (string)**: se um atributo &quot;@expr&quot; estiver presente, o atributo &quot;@tradutorExpr&quot; permite redefinir uma expressão para corresponder à definida em @expr, a ser coletada pela ferramenta de tradução (uso interno).
* **tipo (MNTOKEN)**: tipo de campo.

   Os tipos de campo são genéricos. Dependendo do tipo de banco de dados instalado, a Adobe Campaign altera o tipo definido em um valor específico para o banco de dados instalado durante a atualização da estrutura.

   Lista de tipos disponíveis:

   * ANY
   * compartimento
   * mancha
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * duplo
   * enum
   * flutuante
   * html
   * int64
   * link
   * long
   * memorando
   * MNTOKEN
   * percent
   * primário
   * short
   * string
   * tempo
   * tempo
   * uuid

   Se o atributo &quot;@type&quot; for deixado vazio, a Adobe Campaign vinculará uma string de caracteres (STRING) com um comprimento de 100 ao campo por padrão.

   Se o campo for do tipo STRING e o nome do campo não for especificado pela presença do atributo &quot;@sqlname&quot;, o nome do campo no banco de dados será automaticamente precedido por um &quot;s&quot;. Esse modo operacional será semelhante aos campos dos tipos INTEGER (i), DUPLO (d) e DATES (ts).

* **userEnum (string)**: recebe o nome interno de uma lista discriminada &quot;aberta&quot;. Os valores da lista discriminada podem ser definidos pelo usuário na interface.
* **visibleIf (string)**: define uma condição na forma de uma expressão XTK para mostrar ou ocultar o atributo.

   >[!IMPORTANT]
   >
   >O atributo está oculto, mas seus dados ainda podem ser acessados.

* **xml (booleano)**: se essa opção estiver ativada, os valores do campo não terão um campo SQL vinculado. A Adobe Campaign cria um campo &quot;mData&quot; do tipo de texto para o armazenamento de registro. Isso significa que não há filtragem ou classificação nesses campos.

### Exemplos {#examples}

Exemplo de valores de lista discriminada cujos valores são armazenados no banco de dados:

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

Exemplo com um &quot;@applyIf&quot;: o atributo &quot;contém&quot; só será criado se o número de países for maior que 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Exemplo com &quot;@feature&quot; do tipo &quot;shared&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Exemplo com &quot;@feature&quot; do tipo &quot;dedicado&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
