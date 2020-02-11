---
title: Elementos e atributos
seo-title: Elementos e atributos
description: Elementos e atributos
seo-description: null
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f9b3508fee3b441752648258b1bc9d5d2b919791

---


# Elementos e atributos {#elements-and-attributes}

Ao editar um esquema, um sistema de aprovação com base no esquema de origem (xtk:srcSchema) está disponível. Alguns erros também podem ser detectados ao atualizar o banco de dados usando a &quot;Atualização da estrutura do banco de dados...&quot; assistente.

Por padrão, nos esquemas do Adobe Campaign, todos os atributos de tipo booleano são &quot;false&quot;. Para ativá-los, é necessário especificar o atributo no esquema e definir seu valor como &quot;true&quot;.

## `<attribute>` elemento {#attribute--element}

### Modelo de conteúdo {#content-model}

atributo:==help

### Atributos {#attributes}

_operation (string), advanced (boolean), applyIf (string), autoIncrement (booleano), pertenceTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (booleano), default (string), desc (string), edit (string), enum (string), expr (string), feature (string) featureDate (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string) name (string), sqltable (string), target (MNTOKEN), template (string), traduzdefault (string), traduzidaExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (booleano)

### Pais {#parents}

`<element>`

### Crianças {#children}

`<help>`

### Descrição {#description}

`<attribute>` permitem definir um campo no banco de dados.

### Utilização e contexto de utilização {#use-and-context-of-use}

`<attribute>` os elementos devem ser declarados em um `<element>` elemento.

A sequência na qual `<attribute>` os elementos são definidos em um `<srcschema>` não afeta a sequência de criação de campos no banco de dados. A sequência de criação será alfabética.

### Descrição do atributo {#attribute-description}

* **_operation (cadeia)**: define o tipo de gravação no banco de dados.

   Este atributo é utilizado principalmente para estender esquemas predefinidos.

   Os valores acessíveis são:

   * &quot;nenhum&quot;: apenas reconciliação. Isso significa que o Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualizar com inserção. Isso significa que o Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;Inserir&quot;: inserção. Isso significa que o Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualizar. Isso significa que o Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que o Adobe Campaign recuperará e excluirá elementos.

* **avançado (booleano)**: quando essa opção é ativada (@advanced=&quot;true&quot;), ela permite ocultar o atributo na lista de campos disponíveis acessíveis para configurar uma lista em um formulário.
* **applyIf (string)**: esse atributo permite tornar os campos opcionais. O `<attribute>` elemento será considerado ao atualizar o banco de dados quando a restrição for cumprida. &quot;applyIf&quot; recebe uma expressão XTK.
* **autoIncrement (booleano)**: se essa opção estiver ativada, o campo se tornará um contador. Isso permite incrementar um valor (na maioria das IDs). (uso externo)
* **pertenceTo (string)**: pega o nome e o namespace da tabela que compartilha o campo e preenche o esquema onde o atributo é declarado. (usado somente em uma `<schema>`).
* **dataPolicy (string)**: permite especificar restrições de aprovação em valores permitidos no campo SQL ou XML. Os valores para este atributo são:

   * &quot;nenhum&quot;: sem valor
   * &quot;smartCase&quot;: letras maiúsculas e minúsculas
   * &quot;lowerCase&quot;: todas as minúsculas
   * &quot;upperCase&quot;: todas as maiúsculas
   * &quot;email&quot;: endereço de email
   * &quot;phone&quot;: número de telefone
   * &quot;identificador&quot;: nome do identificador
   * &quot;resIdentifier&quot;: nome do arquivo

* **dbEnum (string)**: recebe o nome interno de uma enumeração &quot;fechada&quot;. Os valores de enumeração devem ser definidos no `<srcschema>`.
* **defOnDuplicate (booleano)**: se esse atributo estiver ativado, quando um registro for duplicado, o valor padrão (definido em @default) será automaticamente reaplicado ao registro.
* **padrão (string)**: permite definir o valor do campo padrão (chamada para uma função, valor padrão). Este atributo recebe uma expressão XTK.
* **desc (string)**: permite inserir uma descrição do atributo. Essa descrição é exibida na barra de status da interface.
* **edit (string)**: esse atributo especifica o tipo de entrada que será usado no formulário vinculado ao esquema.
* **enum (string)**: recebe o nome da enumeração vinculada ao campo. A enumeração pode ser inserida no mesmo esquema ou em um esquema remoto.
* **expr (string)**: define uma expressão de pré-cálculo de campo. Esse atributo recebe uma expressão Xpath ou XTK.
* **recurso (string)**: define um campo de características: Esses campos são usados para estender os dados em uma tabela existente, mas com armazenamento em uma tabela em anexo. Os valores aceitos são:

   * &quot;compartilhado&quot;: o conteúdo é armazenado em uma tabela compartilhada por tipo de dados
   * &quot;dedicado&quot;: o conteúdo é armazenado em uma tabela dedicada
   As tabelas de características SQL são criadas automaticamente com base no tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   Há dois tipos de campos de características: campos oà¹ simples onde um único valor é autorizado sobre a característica e oà¹ campos de múltipla escolha, onde a característica está vinculada a um elemento de coleção que pode conter vários valores.

   Quando uma característica é definida em um esquema, esse esquema deve ter uma chave principal com base em um único campo (as chaves compostas não são autorizadas).

* **featureDate (booleano)**: vinculado ao campo de características &quot;@feature&quot;. Se o valor for &quot;true&quot;, ele permitirá que você descubra quando o valor foi atualizado pela última vez.
* **img (string)**: permite definir um caminho para uma imagem vinculada a um campo (namespace + nome da imagem) (por exemplo: img=&quot;cus:mypicture.jpg&quot;). Fisicamente, a imagem deve ser importada para o servidor de aplicativos.
* **label (string)**: rótulo vinculado ao campo, destinado principalmente ao usuário na interface. Isso permite evitar restrições de nomenclatura.
* **length (string)**: máx. número de caracteres para um valor da &quot;string&quot;, digite campo SQL. Se o atributo &quot;@length&quot; não for especificado, o Adobe Campaign criará automaticamente um campo para 255 caracteres.
* **localizável (booleano)**: se estiver ativado, esse atributo informará a ferramenta de coleta para recuperar o valor do atributo &quot;@label&quot; para conversão (uso interno).
* **name (MNTOKEN)**: nome do atributo que corresponderá ao nome do campo na tabela. O valor do atributo &quot;@name&quot; deve ser curto, de preferência em inglês, e estar em conformidade com as restrições de nomenclatura XML.

   Quando o esquema é gravado no banco de dados, os prefixos são adicionados automaticamente ao nome do campo pelo Adobe Campaign:

   * &quot;i&quot;: prefixo para o tipo &#39;integer&#39;.
   * &quot;d&quot;: prefixo para o tipo &#39;double&#39;.
   * &quot;s&quot;: para o tipo de string de caractere.
   * &quot;ts&quot;: prefixo para o tipo &#39;date&#39;.
   Para definir completamente o nome do campo na tabela, use a opção &quot;@sqlname&quot; ao definir um atributo.

* **notNull (booleano)**: permite redefinir o comportamento do Adobe Campaign em relação ao gerenciamento de registros NULOS no banco de dados. Por padrão, os campos numéricos não são nulos e os campos de cadeia de caracteres e de tipo de data podem ser nulos.
* **pkgStatus (string)**: durante as exportações do pacote, os valores são considerados dependendo do valor de &quot;@pkgStatus&quot;:

   * &quot;always&quot;: está sempre presente
   * &quot;nunca&quot;: nunca presente
   * &quot;padrão (ou nada)&quot;: o valor é exportado, exceto se for o valor padrão ou se não for um campo interno que não seja compatível com outras instâncias.

* **ref (string)**: este atributo define uma referência a um `<attribute>` elemento compartilhado por vários esquemas (fator de definição). A definição não é copiada no esquema atual.
* **obrigatório (booleano)**: se este atributo estiver ativado (@required=&quot;true&quot;), o campo será realçado na interface. O rótulo do campo será vermelho nos formulários.
* **sql (booleano)**: se esse atributo estiver ativado (@sql=&quot;true&quot;), ele forçará o armazenamento do atributo SQL, mesmo quando o elemento que contém o atributo tiver a propriedade xml=&quot;true&quot;.
* **sqlDefault (string)**: esse atributo permite que você defina o valor padrão considerado para atualizar o banco de dados se o atributo @notNull estiver ativado. Se esse atributo for adicionado após a criação do atributo, o comportamento do esquema não será alterado mesmo para os novos registros. Para alterar o esquema e atualizar o valor de novos registros, é necessário excluir e criar novamente o atributo.
* **sqlname (string)**: do campo durante a criação da tabela. Se @sqlname não for especificado, o valor do atributo &quot;@name&quot; será usado por padrão. Quando o esquema é gravado no banco de dados, os prefixos são adicionados automaticamente dependendo do tipo de campo.
* **template (string)**: este atributo define uma referência a um `<attribute>` elemento compartilhado por vários esquemas. A definição é copiada automaticamente no esquema atual.
* **transactionDefault (string)**: se um atributo &quot;@default&quot; for encontrado, o &quot;@traduzdefault&quot; permitirá que você redefina uma expressão para corresponder à definida em @default, a ser coletada pela ferramenta de conversão (uso interno).
* **transactionExpr (string)**: se um atributo &quot;@expr&quot; estiver presente, o atributo &quot;@tradutorExpr&quot; permite redefinir uma expressão para corresponder à definida em @expr, a ser coletada pela ferramenta de tradução (uso interno).
* **tipo (MNTOKEN)**: tipo de campo.

   Os tipos de campo são genéricos. Dependendo do tipo de banco de dados instalado, o Adobe Campaign altera o tipo definido em um valor específico para o banco de dados instalado durante a atualização da estrutura.

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
   * double
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
   * time
   * tempo
   * uuid
   Se o atributo &quot;@type&quot; for deixado em branco, o Adobe Campaign vinculará uma string de caracteres (STRING) com um comprimento de 100 ao campo por padrão.

   Se o campo for do tipo STRING e o nome do campo não for especificado pela presença do atributo &quot;@sqlname&quot;, o nome do campo no banco de dados será automaticamente precedido por um &quot;s&quot;. Esse modo operacional será semelhante aos campos do tipo INTEGER (i), DOUBLE (d) e DATES (ts).

* **userEnum (string)**: recebe o nome interno de uma enumeração &quot;aberta&quot;. Os valores da enumeração podem ser definidos pelo usuário na interface.
* **visibleIf (string)**: define uma condição na forma de uma expressão XTK para mostrar ou ocultar o atributo.

   >[!CAUTION]
   >
   >O atributo está oculto, mas seus dados ainda podem ser acessados.

* **xml (booleano)**: se essa opção estiver ativada, os valores do campo não terão um campo SQL vinculado. O Adobe Campaign cria um campo &quot;mData&quot; do tipo de texto para armazenamento de registros. Isso significa que não há filtragem ou classificação nesses campos.

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

## `<compute-string>` elemento {#compute-string--element}

### Modelo de conteúdo {#content-model-1}

cadeia de caracteres de computação:==EMPTY

### Atributos {#attributes-1}

@expr

### Pais {#parents-1}

`<element>`

### Crianças {#children-1}

 Nenhum

### Descrição {#description-1}

O `<compute-string>` elemento permite gerar uma string com base em uma expressão XTK para exibir um rótulo &quot;criado&quot; na interface com base em vários valores.

### Utilização e contexto de utilização {#use-and-context-of-use-1}

Quando nenhum `<compute-string>` é definido, um `<compute-string>` elemento é inserido por padrão com os valores da chave primária no esquema.

### Descrição do atributo {#attribute-description-1}

* **expr (string)**: Expressão XTK e/ou Xpath

### Exemplos {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultado da string calculada em um destinatário: &quot;João da Silva (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` elemento {#condition--element}

### Modelo de conteúdo {#content-model-2}

condição:==VAZIA

### Atributos {#attributes-2}

* @boolOperador (string)
* @enabledIf (string)
* @expr (string)

### Pais {#parents-2}

`<sysfilter>`

### Crianças {#children-2}

 Nenhum

### Descrição {#description-2}

Esse elemento permite definir uma condição de filtragem.

### Utilização e contexto de utilização {#use-and-context-of-use-2}

Um `<sysfiler>` elemento pode conter várias condições de filtragem.

### Descrição do atributo {#attribute-description-2}

* **boolOperador (string)**: se vários `<conditions>` forem definidos dentro do mesmo `<sysfilter>` elemento, esse atributo permitirá que você os combine. Por padrão, o link lógico é entre `<condition>` elementos: &quot;AND&quot;. O atributo &quot;@boolOperador&quot; permite combinar links de tipo &quot;OU&quot; e &quot;E&quot;.
* **enabledIf (string)**: teste de ativação de condição.
* **expr (string)**: uma expressão XTK.

### Exemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` elemento {#dbindex--element}

### Modelo de conteúdo {#content-model-3}

dbindex:==keyfield

### Atributos {#attributes-3}

* @_operation (string)
* @applyIf (string)
* @label (string)
* @name (MNTOKEN)
* @unique (booleano)

### Pais {#parents-3}

`<element>`

### Crianças {#children-3}

`<keyfield>`

### Descrição {#description-3}

Esse elemento permite definir um índice vinculado a uma tabela.

### Utilização e contexto de utilização {#use-and-context-of-use-3}

É possível definir vários índices. Um índice pode fazer referência a um ou mais campos da tabela. A declaração de índice geralmente segue a definição do elemento de esquema principal.

A ordem dos `<keyfield>` elementos definidos em um `<dbindex>` é muito importante. O primeiro `<keyfield>` deve ser o critério de indexação em que as consultas se baseiam principalmente.

O nome do índice no banco de dados é calculado concatenando o nome da tabela e o nome do índice. Por exemplo: Nome de tabela &quot;Amostra&quot;, Namespace &quot;Cus&quot;, nome de índice &quot;MyIndex&quot;-> nome do campo de índice durante a consulta de criação de índice: &quot;CusSample_myIndex&quot;.

### Descrição do atributo {#attribute-description-3}

* **_operation (cadeia)**: define o tipo de gravação no banco de dados.

   Este atributo é utilizado principalmente para estender esquemas predefinidos.

   Os valores acessíveis são:

   * &quot;nenhum&quot;: apenas reconciliação. Isso significa que o Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualizar com inserção. Isso significa que o Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;Inserir&quot;: inserção. Isso significa que o Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualizar. Isso significa que o Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que o Adobe Campaign recuperará e excluirá elementos.

* **applyIf (string)**: condição para levar em conta o índice - recebe uma expressão XTK.
* **label (string)**: rótulo do índice.
* **name (MNTOKEN)**: nome de índice exclusivo.
* **único (booleano)**: se essa opção estiver ativada (@unique=&quot;true&quot;), o atributo garante a exclusividade do índice em todos os campos.

### Exemplos {#examples-3}

Criação de um índice no campo &quot;id&quot;. (o atributo &quot;@exclusivo&quot; no `<dbindex>` elemento aciona a adição da palavra-chave SQL &quot;ÚNICO&quot; quando o índice é criado no banco de dados (consulta)).

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

## `<element>` elemento {#element--element}

### Modelo de conteúdo {#content-model-4}

element:==(attribute| sequência de caracteres| dbindex| incumprimento| elemento| ajuda| aderir| chave| sysFilter| traduzidoPadrão)

### Atributos {#attributes-4}

_operation (string), avançada (booleana), agregada (string), applyIf (string), autopk (booleano), pertenceTo (string), convencDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAs Field (booleano), doesNotSupportDiff (booleano), edit (string), emptyKeyValue (string), enum (string), enumImage (string), spanSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink string), folderModel (string), folderProcess (string), fullLoad (booleano), hierárquico (booleano), hierárquicalPath (string), img (string), inout (string), integridade (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDb Index (booleano), noKey (booleano), order (booleano), overflow (booleano), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (booleano), revCardinality (string), revDesc (string), revExternalJoin (boolean), Integrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), target (MNTOKEN), template (string), limitedTable (booleano) an), traduzidaDefault (string), traduzidaExpr (string), tipo (MNTOKEN), unbound (booleano), usuário (booleano), userEnum (string), visibleIf (string), xml (booleano), xmlChildren (booleano)

### Pais {#parents-4}

`<srcschema>`

`<element>`

### Crianças {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

### Descrição {#description-4}

Há quatro tipos de `<element>` elementos no Adobe Campaign:

* Raiz `<element>` : define o nome da tabela SQL que corresponde ao esquema.
* Estrutura `<element>` : define um grupo de `<element>` elementos ou `<attribute>` .
* Link `<element>` : define um link. Esses elementos devem incluir o atributo &quot;@type=link&quot;.
* XML `<element>` : define um campo &quot;mData&quot; do tipo de texto. Esse elemento deve incluir o atributo &quot;@type=xml&quot;.

### Descrição do atributo {#attribute-description-4}

* **_operation (cadeia)**: define o tipo de gravação no banco de dados.

   Este atributo é utilizado principalmente para estender esquemas predefinidos.

   Os valores acessíveis são:

   * &quot;nenhum&quot;: apenas reconciliação. Isso significa que o Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualizar com inserção. Isso significa que o Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;Inserir&quot;: inserção. Isso significa que o Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualizar. Isso significa que o Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que o Adobe Campaign recuperará e excluirá elementos.

* **avançado (booleano)**: quando essa opção é ativada (@advanced=&quot;true&quot;), ela permite ocultar o atributo na lista de campos disponíveis acessíveis para configurar uma lista em um formulário.
* **agregado (string)**: permite copiar a definição de um `<element>` por meio de outro esquema. Este atributo recebe uma declaração de esquema na forma de um &quot;namespace:name&quot;.
* **applyIf (string)**: para aplicar o índice. Este atributo recebe uma expressão XTK.
* **autopk (booleano)**: se essa opção estiver ativada (autopk=&quot;true&quot;), uma chave exclusiva será definida automaticamente. Essa opção só pode ser usada no elemento principal do esquema. Aviso, o Adobe Campaign garante apenas que a chave gerada seja exclusiva. Não é garantido que os valores principais sejam consecutivos e incrementais.
* **dataPolicy (string)**: permite especificar restrições de aprovação em valores permitidos no campo SQL. Os valores para este atributo são:

   * &quot;nenhum&quot;: sem valor
   * &quot;smartCase&quot;: letras maiúsculas e minúsculas
   * &quot;lowerCase&quot;: todas as minúsculas
   * &quot;upperCase&quot;: todas as maiúsculas
   * &quot;email&quot;: endereço de email
   * &quot;phone&quot;: número de telefone
   * &quot;identificador&quot;: nome do identificador
   * &quot;resIdentifier&quot;: nome do arquivo

* **dbEnum (string)**: recebe o nome interno de uma enumeração &quot;fechada&quot;. Os valores de enumeração devem ser definidos no `<srcschema>`.
* **defOnDuplicate (booleano)**: se esse atributo estiver ativado, quando um registro for duplicado, o valor padrão (definido em @default) será automaticamente reaplicado ao registro.
* **padrão (string)**: permite definir o comportamento do elemento (chamada para uma função, valor padrão). Este atributo recebe uma expressão XTK.
* **desc (string)**: permite inserir uma descrição do elemento. Essa descrição é exibida na barra de status da interface.
* **displayAsField (booleano)**: se esse atributo estiver ativado, um tipo de &quot;link&quot; `<element>` será exibido como um campo na visualização em árvore dos esquemas (&quot;guia Estrutura&quot;). Dessa forma, é possível exibir um link como um campo local e alterar seu comportamento durante uma consulta. Quando o elemento for encontrado na SELECT de uma consulta, o valor do destino do link será usado. Quando o elemento for encontrado no WHERE de uma consulta, a chave subjacente do link será usada.
* **edit (string)**: esse atributo especifica o tipo de entrada que será usado no formulário vinculado ao esquema.
* **enum (string)**: recebe o nome da enumeração vinculada ao campo. A enumeração pode ser inserida no mesmo esquema ou em um esquema remoto.
* **expr (string)**: esse atributo define um campo calculado para o qual nenhuma definição é armazenada na tabela. Ele recebe uma expressão Xpath ou XTK (string).
* **externalJoin (booleano)**: participação externa em um elemento do tipo &quot;link&quot;.
* **recurso (string)**: define um campo de características: Esses campos são usados para estender os dados em uma tabela existente, mas com armazenamento em uma tabela em anexo. Os valores aceitos são:

   * &quot;compartilhado&quot;: o conteúdo é armazenado em uma tabela compartilhada por tipo de dados
   * &quot;dedicado&quot;: o conteúdo é armazenado em uma tabela dedicada
   As tabelas de características SQL são criadas automaticamente com base no tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   Há dois tipos de campos de características: campos simples nos quais um único valor é autorizado sobre a característica e campos de múltipla escolha, nos quais a característica está ligada a um elemento de coleção que pode conter vários valores.

   Quando uma característica é definida em um esquema, esse esquema deve ter uma chave principal com base em um único campo (as chaves compostas não são autorizadas).

* **featureDate (booleano)**: vinculado ao campo de características &quot;@feature&quot;. Se o valor for &quot;true&quot;, ele permitirá que você descubra quando o valor foi atualizado pela última vez.
* **filterPath (string)**: esse atributo recebe um Xpath e permite definir um filtro em um campo.
* **folderLink (string)**: esse atributo recebe o nome do link que permite recuperar os arquivos que contêm entidades.
* **folderModel (string)**: define o tipo de pasta que permite o armazenamento da entidade. Este atributo só é definido se &quot;@folderLink&quot; estiver presente.
* **folderProcess (string)**: define o link no qual as instâncias do modelo de entidade são armazenadas. Este atributo só é definido se &quot;@folderLink&quot; estiver presente.
* **fullLoad (booleano)**: esse atributo força a exibição de todos os registros em uma tabela durante a seleção de campo em um formulário.
* **img (string)**: recebe o caminho de uma imagem vinculada a um elemento. O valor desse atributo é do tipo &quot;namespace:nome da imagem&quot;. Por exemplo: img=&quot;cus:myImage.jpg&quot;. Fisicamente, a imagem deve ser importada para o servidor de aplicativos.
* **integridade (string)**: integridade referencial da ocorrência da tabela de origem para a tabela de destino.

   Os valores acessíveis são:

   * &quot;definir&quot;: O Adobe Campaign não exclui a entidade se ela for referenciada por meio do link
   * &quot;normal&quot;: a exclusão da ocorrência de origem inicializa as chaves do link na ocorrência de destino (modo padrão), esse tipo de integridade inicializa todas as chaves estrangeiras
   * &quot;own&quot;: excluir a ocorrência de origem aciona a exclusão da ocorrência de destino
   * &quot;cópia&quot;: semelhante a &quot;próprio&quot; (em caso de exclusão) ou duplicata ocorrências (em caso de duplicação)
   * &quot;neutro&quot;: não faz nada

* **label (string)**: rótulo do elemento.
* **labelSingular (string)**: label (forma singular) do elemento usado em algumas partes da interface.
* **length (string)**: máx. número de caracteres autorizados para um valor do campo SQL tipo &quot;string&quot;.
* **localizável (booleano)**: se estiver ativado, esse atributo informará a ferramenta de coleta para recuperar o valor do atributo &quot;@label&quot; para conversão (uso interno).
* **name (MNTOKEN)**: nome interno do elemento que corresponde ao nome da tabela. O valor do atributo &quot;@name&quot; deve ser curto, de preferência em inglês, e estar em conformidade com as restrições de nomenclatura vinculadas ao XML.

   Quando o esquema é gravado no banco de dados, os prefixos são adicionados automaticamente ao nome do campo pelo Adobe Campaign.

   * &quot;i&quot;: prefixo para o tipo &#39;integer&#39;.
   * &quot;d&quot;: prefixo para o tipo &#39;double&#39;.
   * &quot;s&quot;: para o tipo de string de caractere.
   * &quot;ts&quot;: prefixo para o tipo &#39;date&#39;.
   Para definir o nome da tabela de forma autônoma, é necessário usar o atributo &quot;@sqltable&quot; na definição do elemento do esquema principal.

* **noDbIndex (booleano)**: permite especificar que o elemento não será indexado.
* **pedido (booleano)**: se o atributo estiver ativado (order=&quot;true&quot;), o Adobe Campaign manterá a sequência de declaração do elemento em um elemento de coleção XML.
* **pkSequence (string)**: recebe o nome da sequência a ser usada para calcular uma chave incremental automática. Este atributo só pode ser usado se uma chave incremental automática for definida no elemento raiz do esquema.
* **pkgStatus (string)**: durante as exportações de pacotes, os valores serão considerados como função do valor deste atributo:

   * &quot;always&quot;: o elemento sempre estará presente
   * &quot;nunca&quot;: o elemento nunca estará presente
   * &quot;padrão (ou nada)&quot;: o elemento é exportado a menos que seja o elemento padrão ou que não seja um campo interno e não seja compatível com outras instâncias

* **ref (string)**: esse atributo define uma referência a um elemento >element> compartilhado por vários esquemas (fator de definição). A definição não é copiada no esquema atual.
* **obrigatório (booleano)**: se este atributo estiver ativado (@required=&quot;true&quot;), o campo será realçado na interface. O rótulo do campo será vermelho nos formulários.
* **revAdvanced (booleano)**: quando ativado, esse atributo especifica que o link oposto é um link &quot;avançado&quot;.
* **revCardinalidade (string)**: este atributo define a cardinalidade de um link entre duas tabelas. É usado em um tipo de &quot;link&quot; `<element>`.

   Os valores possíveis são:

   * &quot;single&quot; : Link simples do tipo 1-1
   * &quot;unbound&quot;: Link de coleção do tipo 1-N
   Por padrão, se o atributo não for especificado durante a criação do link, a cardinalidade será 1-N.

* **revDesc (string)**: este atributo recebe uma descrição vinculada ao link oposto.
* **revExternalJoin (booleano)**: quando ativado, esse atributo permite forçar a junção externa no link oposto.
* **revIntegrity (string)**: este atributo define a integridade no esquema de destino. Os mesmos valores que o atributo &quot;@Integrity&quot; estão autorizados. Por padrão, o Adobe Campaign atribui o valor &quot;normal&quot; a esse atributo.
* **revLabel (string)**: rótulo do link oposto.
* **revLink (string)**: nome do link oposto. Se o valor for &quot;_NONE_&quot;, nenhum link oposto será criado no esquema de destino.
* **revTarget (sequência)**: destino do link oposto.
* **sql (booleano)**: se esse atributo estiver ativado (@sql=&quot;true&quot;), ele forçará o armazenamento do elemento SQL, mesmo se o elemento tiver a propriedade xml=&quot;true&quot;.
* **sqlname (string)**: nome do campo durante a criação da tabela. Se &quot;@sqlname&quot; não for especificado, o valor do atributo &quot;@name&quot; será usado por padrão. Ao gravar o esquema na tabela, os prefixos são adicionados automaticamente dependendo do tipo de campo.
* **sqltable (string)**: para o elemento principal do esquema, esse atributo sobrecarrega o nome da tabela SQL gerada por padrão. Se &quot;@sqltable&quot; não for especificado, o nome padrão será estruturado desta forma: namespace (primeira letra maiúscula) seguido pelo valor de SrcSchema &quot;@name&quot;.
* **tableSpace (string)**: esse atributo permite especificar um novo tablespace de armazenamento de dados para uma tabela (válido na raiz `<element>`).
* **tableSpaceIndex (string)**: esse atributo permite que você especifique um novo tablespace de armazenamento de índice para uma tabela (válido na raiz `<element>`).
* **target (MNTOKEN)**: recebe o nome do esquema de destino ao criar um link entre tabelas. Este atributo está ativo apenas para elementos do tipo &quot;link&quot;.
* **template (string)**: este atributo define uma referência a um `<element>` elemento compartilhado por vários esquemas. A definição é copiada automaticamente no esquema atual.
* **transactionDefault (string)**: se um atributo &quot;@default&quot; for encontrado, o &quot;@traduzdefault&quot; permitirá que você redefina uma expressão para corresponder à definida em @default, a ser coletada pela ferramenta de conversão (uso interno).
* **transactionExpr (string)**: se um atributo &quot;@expr&quot; for encontrado, o atributo &quot;@traduçõesExpr&quot; permite redefinir uma expressão correspondente à definida em &quot;@expr&quot; e que será coletada pela ferramenta de tradução (uso interno).
* **tipo (MNTOKEN)**: define o tipo de dados armazenados no elemento.

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
   * double
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
   * time
   * tempo
   * uuid

* **unbound (booleano)**: se o atributo estiver ativado (unbound=&quot;true&quot;), o link será declarado como um elemento de coleção para uma cardinalidade 1-N.
* **userEnum (string)**: recebe o nome interno de uma enumeração &quot;aberta&quot;. Os valores de enumeração podem ser definidos pelo usuário na interface.
* **xml (booleano)**: se essa opção estiver ativada, todos os valores definidos no elemento serão armazenados em XML em um campo &quot;mData&quot; do tipo TEXT. Isso significa que não haverá filtragem ou classificação nesses campos.
* **xmlChildren (booleano)**: força o armazenamento de cada criança ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` elemento {#enumeration--element}

### Modelo de conteúdo {#content-model-5}

enumeração:==(help| value)

### Atributos {#attributes-5}

* @basetype (string)
* @default (string)
* @desc (string)
* @label (string)
* @name (string)
* @template (string)

### Pais {#parents-5}

`<srcschema>`

### Crianças {#children-5}

* `<help>`
* `<value>`

### Descrição {#description-5}

Esse elemento permite definir uma enumeração de valor. Uma enumeração pertence ao esquema no qual está definida, mas é acessível por meio de outro esquema.

### Utilização e contexto de utilização {#use-and-context-of-use-4}

As enumerações são definidas no início de um esquema (antes de o elemento principal ser definido).

### Descrição do atributo {#attribute-description-5}

* **basetype (string)**: tipo dos valores armazenados na enumeração.

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
   * DOMDocument
   * DOMElement
   * double
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
   * time
   * tempo
   * uuid

* **padrão (string)**: Valor padrão. O valor padrão também pode ser um dos valores definidos na enumeração.
* **desc (string)**: descrição da enumeração.
* **label (string)**: rótulo de enumeração.
* **name (string)**: nome interno da enumeração.
* **template (string)**: este atributo define uma referência a um `<enumeration>` elemento compartilhado por vários esquemas. A definição é copiada automaticamente no esquema atual.

### Exemplos {#examples-4}

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

Definição de uma enumeração com um valor padrão:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` elemento {#help--element}

### Modelo de conteúdo {#content-model-6}

ajuda:==VAZIO

### Atributos {#attributes-6}

 Nenhum

### Pais {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### Crianças {#children-6}

 Nenhum

### Descrição {#description-6}

Esse elemento permite que você descreva um elemento `<element>` ou `<attribute>` . Ele pode conter apenas texto e é armazenado em XML no banco de dados.

### Descrição do atributo {#attribute-description-6}

Este elemento não tem atributos.

### Exemplos {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` elemento {#join--element}

### Modelo de conteúdo {#content-model-7}

join:==EMPTY

### Atributos {#attributes-7}

* @dstFilterExpr (string)
* @xpath-dst (string)
* @xpath-src (string)

### Pais {#parents-7}

`<element>`

### Crianças {#children-7}

 Nenhum

### Descrição {#description-7}

Permite definir os campos que criam uma junção entre tabelas SQL.

### Utilização e contexto de utilização {#use-and-context-of-use-5}

Um `<join>` elemento só pode ser usado se o `<element>` elemento pai for do tipo &quot;link&quot;. Isso significa que o elemento pai deve ter o atributo &quot;@type=link&quot; declarado.

Não é necessário especificar o nome e o namespace da tabela remota no `<join>` elemento. Eles precisam ser especificados no pai `<element>`.

Por convenção, os links são definidos no final do esquema.

Se o `<join>` elemento não for especificado quando o elemento de tipo de link for definido, o link será colocado automaticamente nas chaves primárias de ambas as tabelas.

### Descrição do atributo {#attribute-description-7}

* **dstFilterExpr (string)**: esse atributo permite restringir o número de valores elegíveis na tabela remota.
* **xpath-dst (string)**: este atributo recebe um Xpath (@name atributo da tabela remota).
* **xpath-src (string)**: este atributo recebe um Xpath (@name atributo no esquema atual).

### Exemplos {#examples-6}

Link entre o campo &#39;email&#39; da tabela atual e o campo &quot;@compagny-id&quot; da tabela remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Link filtrado para a tabela &quot;cus:Country&quot; com base no conteúdo do campo &quot;@country&quot; que deve conter o valor &#39;EN&#39;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` elemento {#key--element}

### Modelo de conteúdo {#content-model-8}

key:==keyfield

### Atributos {#attributes-8}

* @allowEmptyPart (booleano)
* @applyIf (string)
* @internal (booleano)
* @label (string)
* @name (MNTOKEN)
* @noDbIndex (booleano)

### Pais {#parents-8}

`<element>`

### Crianças {#children-8}

`<keyfield>`

### Descrição {#description-8}

Esse elemento permite definir uma chave para identificar um registro na tabela.

Uma tabela deve ter pelo menos uma chave.

### Utilização e contexto de utilização {#use-and-context-of-use-6}

Como regra, as chaves são declaradas após o elemento principal do esquema e os índices.

Uma tecla é conhecida como composta se incluir vários campos (ou seja, vários `<keyfield>` filhos). Não use uma chave composta para definir uma chave primária.

Se o elemento principal do esquema contiver o atributo &quot;@autopk=true&quot;, a chave primária será exclusiva. Só podemos ter uma chave primária por esquema.

Os primeiros 1000 identificadores são reservados, portanto, se uma faixa de valores precisar ser definida para chaves, comece em 1000.

### Descrição do atributo {#attribute-description-8}

* **allowEmptyPart (booleano)**: no caso de uma chave composta, se esse atributo estiver ativado, a chave será considerada válida se pelo menos uma de suas chaves não estiver vazia. Se esse for o caso, o valor vazio da noção é &quot;0&quot; (booleano ou para todos os tipos de dados numéricos). Por padrão, todas as teclas que compõem uma chave composta precisam ser inseridas.
* **applyIf (string)**: esse atributo permite tornar a chave opcional. Define a condição de acordo com a qual a definição de chave será aplicada. Este atributo recebe uma expressão XTK.
* **interno (booleano)**: se estiver ativado, esse atributo permite que o Adobe Campaign saiba que a chave é primária.
* **label (string)**: da chave.
* **name (MNTOKEN)**: nome interno da chave.
* **noDbIndex (booleano)**: se estiver ativado (noDbIndex=&quot;true&quot;), o campo correspondente à chave não será indexado.

### Exemplos {#examples-------}

Declaração de uma chave composta que autoriza que o campo &quot;@expr&quot; ou &quot;alias&quot; esteja vazio:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaração de uma chave primária no campo &quot;Nome&quot; do tipo STRING em uma consulta SQL correspondente `<srcschema>` e:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` elemento {#keyfield--element}

### Modelo de conteúdo {#content-model-9}

campo de chaves:==VAZIO

### Atributos {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

### Pais {#parents-9}

`<key>`  ,  `<dbindex />`

### Crianças {#children-9}

 Nenhum

### Descrição {#description-9}

Esse elemento define os campos a serem integrados em um índice ou chave.

### Descrição do atributo {#attribute-description-9}

* **xlink (MNTOKEN)**: permite referenciar automaticamente chaves estrangeiras definidas na junção para uma tabela de relação (link N-N).
* **xpath (MNTOKEN)**: definição de um índice ou de uma chave em um `<attribute>` elemento. Este atributo recebe um Xpath que define o caminho para o atributo do esquema que define a chave ou o índice.

### Exemplos {#examples-}

Seleção do campo &quot;sName&quot; em um índice com um Xpath em &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```

## `<method>` elemento {#method--element}

### Modelo de conteúdo {#content-model-10}

método:==( help| parâmetros)

### Atributos {#attributes-10}

* @_operation (string)
* @access (string)
* @const (booleano)
* @hidden (booleano)
* @label (string)
* @library (string)
* @name (MNTOKEN)
* @pkonly (booleano)
* @static (booleano)

### Pais {#parents-10}

`<methods>`  ,  `<interface />`

### Crianças {#children-10}

* `<help>`
* `<parameters>`

### Descrição {#description-10}

Esse elemento permite definir um método SOAP.

### Utilização e contexto de utilização {#use-and-context-of-use-7}

Métodos SOAP habilitam processos de aplicativo.

A &quot;@library&quot; é necessária para declarar um novo método (não nativo): o namespace e o nome usados para a biblioteca são independentes do namespace e do nome do esquema em que a declaração está.

### Descrição do atributo {#attribute-description-10}

* **access (string)**: este atributo define o controle de acesso para usar o método. Se este atributo estiver faltando, a identificação é obrigatória. Os valores disponíveis são: &quot;anônimo&quot;, &quot;admin&quot; e &quot;sql&quot;.
* **const (booleano)**: se estiver ativado, este atributo significa que o método declarado alterará a entidade
* **label (string)**: rótulo do método.
* **biblioteca (string)**: esse método não é nativo do aplicativo. Esse atributo obtém o valor da biblioteca de métodos na qual a definição do método é encontrada (nms:mylibrary.js).
* **name (MNTOKEN)**: nome do método exclusivo.
* **estático (booleano)**: se esse atributo estiver ativado, o método for considerado autônomo, todos os parâmetros deverão ser especificados para o método quando ele for chamado.

### Exemplos {#examples-7}

Definição do método &quot;Assinar&quot; na caixa:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```

## `<methods>` elemento {#methods--element}

### Modelo de conteúdo {#content-model-11}

methods:==method

### Atributos {#attributes-11}

 Nenhum

### Pais {#parents-11}

`<srcschema>`

### Crianças {#children-11}

método

### Descrição {#description-11}

Esse elemento permite definir um `<method>` elemento. É obrigatório declarar um método.

### Descrição do atributo {#attribute-description-11}

Este elemento não tem atributos.

### Exemplos {#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` elemento {#param--element}

### Modelo de conteúdo {#content-model-12}

param:==help

### Atributos {#attributes-12}

* @_operation (string)
* @desc (string)
* @enum (string)
* @inout (string)
* @label (string)
* @localizable (string)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (string)

### Pais {#parents-12}

`<parameters>`

### Crianças {#children-12}

`<help>`

### Descrição {#description-12}

Esse elemento permite definir um parâmetro para chamar um método SOAP.

### Descrição do atributo {#attribute-description-12}

* **desc (string)**: descrição que diz respeito ao `<param>` elemento.
* **inout (string)**: esse atributo define se o parâmetro está ou não na entrada (in) ou saída (fora) da chamada SOAP. Se este atributo não for especificado, o parâmetro padrão será input (&quot;@inout=in&quot;).
* **label (string)**: `<param>` rótulo
* **localizável (string)**: se estiver ativado, esse atributo informará a ferramenta de coleta para recuperar o valor do atributo &quot;@label&quot; para conversão (uso interno).
* **name (MNTOKEN)**: nome interno do `<param>`
* **type (string)**: este atributo define o tipo de `<param>` elemento

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
   * DOMDocument
   * DOMElement
   * double
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
   * time
   * tempo
   * uuid

### Exemplos {#examples-9}

Definição da definição de entrada &quot;serviceName&quot; do tipo de cadeia de caracteres:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` elemento {#parameters--element}

### Modelo de conteúdo {#content-model-13}

parâmetros:==param

### Atributos {#attributes-13}

 Nenhum

### Pais {#parents-13}

`<method>`

### Crianças {#children-13}

`<param>`

### Descrição {#description-13}

Esse elemento define um grupo de `<parameter>` elementos.

### Utilização e contexto de utilização {#use-and-context-of-use-8}

Esse elemento é obrigatório, mesmo para um único elemento `<param>` filho do `<method>` elemento.

### Descrição do atributo {#attribute-description-13}

 Nenhum

### Exemplos {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` elemento {#srcschema--element}

### Modelo de conteúdo {#content-model-14}

srcSchema:==(atributo)| createdBy| dados| elemento| enumeração| ajuda| interface| Métodos| modifiedBy)

### Atributos {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), ExtendedSchema (string), img (string), implementações (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), espace (string), useRecycleBin (boolean), view (booleana), xtkschema (string)

### Pais {#parents-14}

 Nenhum

### Crianças {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### Descrição {#description-14}

O `<srcschema>` é o elemento raiz de um esquema. É o ponto de entrada para a definição do esquema.

### Utilização e contexto de utilização {#use-and-context-of-use-9}

A apresentação do esquema está disponível em [Sobre a referência](../../configuration/using/about-schema-reference.md) do esquema e a estrutura [do](../../configuration/using/schema-structure.md)Esquema.

### Descrição do atributo {#attribute-description-14}

* **criado (datetime)**: este atributo fornece informações sobre a data e a hora da criação do esquema. Ele tem um formulário &quot;Data e hora&quot;. Os valores exibidos são obtidos do servidor. A hora é exibida no formato UTC.
* **createdBy-id (long)**: é o identificador do operador que criou o esquema.
* **desc (string)**: descrição do esquema
* **entitySchema (string)**: esquema básico no qual a sintaxe e a aprovação se baseiam (por padrão para o Adobe Campaign: xtk:srcSchema). Ao salvar o esquema atual, o Adobe Campaign aprovará sua gramática com o esquema declarado no atributo @xtkschema.
* **ExtendedSchema (string)**: recebe o nome do esquema predefinido no qual a extensão do esquema atual se baseia. O formulário é &quot;namespace:name&quot;.
* **img (string)**: ícone vinculado ao esquema (pode ser definido no assistente de criação de esquema).
* **label (string)**: rótulo do esquema.
* **labelSingular (string)**: label (singular) para exibição na interface.
* **lastModified (datetime)**: este atributo fornece informações sobre a data e a hora da última modificação. Ele tem um formulário &quot;Data e hora&quot;. Os valores exibidos são obtidos do servidor. A hora é exibida no formato UTC.
* **biblioteca (booleana)**: uso do esquema como uma biblioteca e não como uma entidade. Este esquema pode, portanto, ser referenciado por outros esquemas graças aos atributos &quot;@ref&quot; e &quot;@template&quot;.
* **mappingType (string)**:

   * &quot;sql&quot;: mapeamento de banco de dados
   * &quot;textFile&quot;: mapeamento de arquivos de texto
   * &quot;xmlFile&quot;: Mapeamento do arquivo de texto do formato XML
   * &quot;binaryFile&quot;: mapeamento de arquivos binários

* **modifiedBy-id (long)**: corresponde ao identificador do operador que alterou o esquema.
* **name (string)**: nome exclusivo do esquema.
* **namespace (string)**: namespace do esquema (padrão: nms, xtk, nl). Ao criar um novo esquema para um projeto, recomendamos que você use um namespace dedicado.
* **useRecycleBin (booleano)**: ativa o recurso de lixeira no aplicativo. Os registros excluídos serão colocados no lixo antes da exclusão final. Esta função só está disponível no modo &quot;Entrega&quot;.
* **view (booleano)**: se estiver ativado (@view=&quot;true&quot;), o esquema será usado como uma exibição. O assistente de atualização da estrutura do banco de dados não levará o esquema em conta. Esta opção é principalmente utilizada para fazer referência a tabelas externas.
* **xtkschema (string)**: nome do esquema que define a gramática do esquema (xtk:srcSchema por padrão).

### Exemplos {#examples-11}

`<srcschema>` elemento do esquema &quot;nms:delivery&quot; fora da caixa

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` elemento {#sysfilter--element}

### Modelo de conteúdo {#content-model-15}

sysFilter:==condition

### Atributos {#attributes-15}

 Nenhum

### Pais {#parents-15}

`<element>`

### Crianças {#children-15}

`<condition>`

### Descrição {#description-15}

Esse elemento permite definir um filtro.

### Descrição do atributo {#attribute-description-15}

Este elemento não tem atributos.

### Exemplos {#examples-12}

Definição de um filtro com uma condição no atributo @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` elemento {#value--element}

### Modelo de conteúdo {#content-model-16}

value:==help

### Atributos {#attributes-16}

* @applyIf (string)
* @desc (string)
* @enabledIf (string)
* @img (string)
* @label (string)
* @name (string)
* @value (string)

### Pais {#parents-16}

`<enumeration>`

### Crianças {#children-16}

`<help>`

### Descrição {#description-16}

Esse elemento permite definir os valores armazenados em uma enumeração.

### Descrição do atributo {#attribute-description-16}

* **applyIf (string)**: esse atributo permite tornar um valor de enumeração opcional. Ele recebe uma expressão XTK.
* **desc (string)**: descrição do valor de enumeração.
* **enabledIf (string)**: para ativar o valor de enumeração.
* **img (string)**: imagem vinculada à enumeração no formulário &quot;namespace:image_name&quot;. A imagem deve ser importada para o servidor de aplicativos.
* **label (string)**: rótulo do valor de enumeração.
* **name (string)**: nome interno do valor de enumeração.
* **value (string)**: valor do valor de enumeração. O tipo de valor é definido com base no tipo de enumeração. Se a enumeração for do tipo de string de caractere, ela só poderá conter valores do tipo de string de caractere.

### Exemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
