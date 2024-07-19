---
product: campaign
title: Elementos e atributos de esquema - elemento element
description: elemento
feature: Schema Extension
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '2016'
ht-degree: 0%

---

# elemento {#element--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-4}

element:==(attribute | string de cálculo | dbindex | padrão | element | ajuda | ingressar | key | sysFilter | translateDefault)

## Atributos {#attributes-4}

_operation (string), advanced (booleano), aggregate (string), applicableIf (string), autopk (booleano), belongingTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (booleano), default (string), desc (string), displayAsField (booleano), doesNotSupportDiff (booleano), edit (string), emptyKeyValue (string), enum string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (booleano), feature (string), featureDate (booleano), filterPath (string), folderLink (string), folderModel (string), folderProcess (string), fullLoad (booleano), hierarchical (booleano), hierarchicalPath (string), img (string), inout (string), integridade (string), rótulo (string), labelSingular (string), comprimento (string) , localizable (booleano), name (MNTOKEN), noDbIndex (booleano), noKey (booleano), ordered (booleano), overflowtable (booleano), pkSequence (cadeia de caracteres), pkgStatus (cadeia de caracteres), ref (cadeia de caracteres), required (booleano), revAdvanced (booleano), revCardinality (cadeia de caracteres), revDesc (cadeia de caracteres), revExternalJoin (booleano), revIntegrity (cadeia de caracteres), rev vLabel (cadeia de caracteres), revLink (cadeia de caracteres), revTarget (cadeia de caracteres), revVisibleIf (cadeia de caracteres), sql (booleano), sqlname (cadeia de caracteres), sqltable (cadeia de caracteres), tableSpace (cadeia de caracteres), tableSpaceIndex (cadeia de caracteres), target (MNTOKEN), template (cadeia de caracteres), temporaryTable (booleano), convertedDefault (cadeia de caracteres), translateExpr (cadeia de caracteres), type (MNTOKEN), unbound (boolean), userEnuser, user um (string), visibleIf (string), xml (booleano), xmlChildren (booleano)

## Pais {#parents-4}

`<srcschema>`

`<element>`

## Filhos {#children-4}

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

## Descrição {#description-4}

Há quatro tipos de elementos `<element>` no Adobe Campaign:

* Raiz `<element>` : define o nome da tabela SQL que corresponde ao esquema.
* Estrutura `<element>` : define um grupo de `<element>`   ou   `<attribute>`    elementos.
* O link `<element>` : define um link. Esses elementos devem incluir o atributo &quot;@type=link&quot;.
* XML `<element>` : define um campo de tipo de texto &quot;mData&quot;. Esse elemento deve incluir o atributo &quot;@type=xml&quot;.

## Descrição do atributo {#attribute-description-4}

* **_operation (string)**: define o tipo de gravação no banco de dados.

  Esse atributo é usado principalmente ao estender schemas prontos para uso.

  Os valores acessíveis são:

   * &quot;none&quot;: apenas reconciliação. Isso significa que o Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualização com inserção. Isso significa que o Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;insert&quot;: inserção. Isso significa que o Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualização. Isso significa que o Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que o Adobe Campaign recuperará e excluirá elementos.

* **advanced (booleano)**: quando esta opção é ativada (@advanced=&quot;true&quot;), ela permite ocultar o atributo na lista de campos disponíveis acessíveis para configurar uma lista em um formulário.
* **agregação (cadeia de caracteres)**: permite copiar a definição de um `<element>` por meio de outro esquema. Este atributo recebe uma declaração de schema no formato de &quot;namespace:name&quot;.
* **applicableIf (string)**: condição para aplicar o índice. Este atributo recebe uma expressão XTK.
* **autopk (booleano)**: se esta opção estiver ativada (autopk=&quot;true&quot;), uma chave exclusiva será definida automaticamente. Essa opção só pode ser usada no elemento principal do esquema. Aviso: o Adobe Campaign garante apenas que a chave gerada seja exclusiva. Não há garantia de que os valores principais sejam consecutivos e incrementais.
* **dataPolicy (cadeia de caracteres)**: permite especificar restrições de aprovação em valores permitidos no campo SQL. Os valores para este atributo são:

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
* **padrão (cadeia de caracteres)**: permite definir o comportamento do elemento (chamada para uma função, valor padrão). Este atributo recebe uma expressão XTK.
* **desc (string)**: permite inserir uma descrição do elemento. Essa descrição é exibida na barra de status da interface.
* **displayAsField (booleano)**: se este atributo for ativado, um tipo de &quot;link&quot; `<element>` será exibido como um campo na exibição em árvore dos esquemas (guia &quot;Estrutura&quot;). Dessa forma, é possível exibir um link como um campo local e alterar seu comportamento durante um query. Quando o elemento é encontrado em SELECT de um query, o valor do target do link será usado. Quando o elemento for encontrado no WHERE de um query, a chave subjacente do link será usada.
* **editar (cadeia de caracteres)**: este atributo especifica o tipo de entrada que será usado no formulário vinculado ao esquema.
* **enum (cadeia de caracteres)**: recebe o nome da enumeração vinculada ao campo. A enumeração pode ser inserida no mesmo schema ou em um schema remoto.
* **expr (cadeia de caracteres)**: este atributo define um campo calculado para o qual nenhuma definição está armazenada na tabela. Ele recebe um Xpath ou uma expressão XTK (string).
* **externalJoin (booleano)**: junção externa em um elemento de tipo &quot;link&quot;.
* **recurso (cadeia de caracteres)**: define um campo de características: esses campos são usados para estender os dados em uma tabela existente, mas com armazenamento em uma tabela de anexos. Os valores aceitos são:

   * &quot;shared&quot;: o conteúdo é armazenado em uma tabela compartilhada por tipo de dados
   * &quot;dedicated&quot;: o conteúdo é armazenado em uma tabela dedicada

  As tabelas de características SQL são criadas automaticamente com base no tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * compartilhado: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Há dois tipos de campos de características: campos simples, onde um único valor é autorizado na característica, e campos de múltipla escolha, onde a característica está vinculada a um elemento de coleção que pode conter vários valores.

  Quando uma característica é definida em um esquema, esse esquema deve ter uma chave principal baseada em um único campo (chaves compostas não são autorizadas).

* **featureDate (booleano)**: atributo vinculado ao campo de características &quot;@feature&quot;. Se o valor for &quot;true&quot;, ele permitirá descobrir quando o valor foi atualizado pela última vez.
* **filterPath (cadeia de caracteres)**: este atributo recebe um Xpath e permite a definição de um filtro em um campo.
* **folderLink (string)**: esse atributo recebe o nome do link que permite recuperar os arquivos que contêm entidades.
* **folderModel (string)**: define o tipo de pasta que habilita o armazenamento de entidade. Esse atributo só será definido se &quot;@folderLink&quot; estiver presente.
* **folderProcess (cadeia de caracteres)**: define o link onde as instâncias do modelo de entidade são armazenadas. Esse atributo só será definido se &quot;@folderLink&quot; estiver presente.
* **fullLoad (booleano)**: esse atributo força a exibição de todos os registros em uma tabela durante a seleção de campo em um formulário.
* **img (string)**: recebe o caminho de uma imagem vinculada a um elemento. O valor desse atributo é do tipo &quot;namespace:image name&quot;. Por exemplo: img=&quot;cus:myImage.jpg&quot;. Fisicamente, a imagem deve ser importada para o servidor de aplicativos.
* **integridade (cadeia de caracteres)**: integridade referencial da ocorrência da tabela de origem em direção à tabela de destino.

  Os valores acessíveis são:

   * &quot;define&quot;: a Adobe Campaign não exclui a entidade se ela for referenciada por meio do link
   * &quot;normal&quot;: excluir a ocorrência de origem inicializa as chaves do link na ocorrência de destino (modo padrão), esse tipo de integridade inicializa todas as chaves estrangeiras
   * &quot;own&quot;: excluir a ocorrência de origem aciona a exclusão da ocorrência de destino
   * &quot;owncopy&quot;: semelhante a &quot;own&quot; (no caso de exclusão) ou duplica ocorrências (no caso de duplicação)
   * &quot;neutral&quot;: não faz nada

* **rótulo (cadeia de caracteres)**: rótulo do elemento.
* **labelSingular (cadeia de caracteres)**: rótulo (forma singular) do elemento usado em algumas partes da interface.
* **comprimento (cadeia de caracteres)**: máx. número de caracteres autorizados para um valor do campo SQL tipo &quot;string&quot;.
* **localizável (booleano)**: se estiver ativado, este atributo informará à ferramenta de coleção para recuperar o valor do atributo &quot;@label&quot; para tradução (uso interno).
* **name (MNTOKEN)**: nome interno do elemento que corresponde ao nome da tabela. O valor do atributo &quot;@name&quot; deve ser curto, de preferência em inglês, e estar em conformidade com as restrições de nomenclatura vinculadas ao XML.

  Quando o esquema é gravado no banco de dados, os prefixos são adicionados automaticamente ao nome do campo pelo Adobe Campaign.

   * &quot;i&quot;: prefixo para o tipo &quot;inteiro&quot;.
   * &quot;d&quot;: prefixo do tipo &quot;double&quot;.
   * &quot;s&quot;: prefixo do tipo de sequência de caracteres.
   * &quot;ts&quot;: prefixo do tipo &quot;date&quot;.

  Para definir o nome da tabela de forma autônoma, é necessário usar o atributo &quot;@sqltable&quot; na definição do elemento principal do schema.

* **noDbIndex (booleano)**: permite especificar que o elemento não será indexado.
* **ordered (boolean)**: se o atributo estiver ativado (ordered=&quot;true&quot;), o Adobe Campaign mantém a sequência de declaração do elemento em um elemento de coleção XML.
* **pkSequence (string)**: recebe o nome da sequência a ser usada para calcular uma chave incremental automática. Esse atributo só pode ser usado se uma chave incremental automática for definida no elemento raiz do esquema.
* **pkgStatus (string)**: durante as exportações de pacote, os valores serão considerados como uma função do valor deste atributo:

   * &quot;always&quot;: o elemento sempre estará presente
   * &quot;never&quot;: o elemento nunca estará presente
   * &quot;default (or anything)&quot;: o elemento é exportado, a menos que seja o elemento padrão ou se não for um campo interno e não for compatível com outras instâncias

* **ref (string)**: este atributo define uma referência a um elemento >element> compartilhado por vários esquemas (fatoração de definição). A definição não é copiada para o esquema atual.
* **obrigatório (booleano)**: se este atributo estiver ativado (@required=&quot;true&quot;), o campo será realçado na interface. O rótulo do campo será vermelho nos formulários.
* **revAdvanced (booleano)**: quando ativado, este atributo especifica que o link oposto é um link &quot;avançado&quot;.
* **revCardinality (string)**: este atributo define a cardinalidade de um vínculo entre duas tabelas. Ele é usado em um tipo de &quot;link&quot; `<element>`.

  Os valores possíveis são:

   * &quot;single&quot; : link de tipo simples 1-1
   * &quot;unbound&quot;: link de coleção do tipo 1-N

  Por padrão, se o atributo não for especificado durante a criação do link, a cardinalidade será 1-N.

* **revDesc (cadeia de caracteres)**: este atributo recebe uma descrição vinculada ao link oposto.
* **revExternalJoin (booleano)**: quando ativado, esse atributo permite forçar a associação externa no link oposto.
* **revIntegrity (cadeia de caracteres)**: este atributo define a integridade no esquema de destino. Os mesmos valores que o atributo &quot;@integrity&quot; são autorizados. Por padrão, o Adobe Campaign fornece o valor &quot;normal&quot; para esse atributo.
* **revLabel (cadeia de caracteres)**: rótulo do link oposto.
* **revLink (cadeia de caracteres)**: nome do link oposto. Se o valor for &quot;_NONE_&quot;, nenhum link oposto será criado no esquema de destino.
* **revTarget (cadeia de caracteres)**: destino do link oposto.
* **sql (booleano)**: se este atributo for ativado (@sql=&quot;true&quot;), ele forçará o armazenamento do elemento SQL, mesmo que o elemento tenha a propriedade xml=&quot;true&quot;.
* **sqlname (cadeia de caracteres)**: nome do campo durante a criação da tabela. Se &quot;@sqlname&quot; não for especificado, o valor do atributo &quot;@name&quot; será usado por padrão. Ao gravar o schema na tabela, os prefixos são adicionados automaticamente, dependendo do tipo de campo.
* **sqltable (string)**: para o elemento principal do esquema, esse atributo sobrecarrega o nome da tabela SQL gerada por padrão. Se &quot;@sqltable&quot; não for especificado, o nome padrão será estruturado desta forma: namespace (primeira letra maiúscula) seguido pelo valor de SrcSchema &quot;@name&quot;.
* **tableSpace (string)**: este atributo permite especificar um novo tablespace de armazenamento de dados para uma tabela (válido na raiz `<element>`).
* **tableSpaceIndex (string)**: este atributo permite especificar um novo tablespace de armazenamento de índice para uma tabela (válido na raiz `<element>`).
* **target (MNTOKEN)**: recebe o nome do esquema de destino ao criar um vínculo entre tabelas. Esse atributo só está ativo para elementos do tipo &quot;link&quot;.
* **modelo (cadeia de caracteres)**: este atributo define uma referência a um elemento `<element>` compartilhado por vários esquemas. A definição é copiada automaticamente para o esquema atual.
* **TranslationDefault (cadeia de caracteres)**: se um atributo &quot;@default&quot; for encontrado, o &quot;@translatedDefault&quot; permitirá que você redefina uma expressão para corresponder à definida em @default, a ser coletada pela ferramenta de tradução (uso interno).
* **translateExpr (cadeia de caracteres)**: se um atributo &quot;@expr&quot; for encontrado, o atributo &quot;@translatedExpr&quot; permitirá redefinir uma expressão correspondente à definida em &quot;@expr&quot; e que será coletada pela ferramenta de tradução (uso interno).
* **type (MNTOKEN)**: define o tipo de dados armazenados no elemento.

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

* **desvinculado (booleano)**: se o atributo for ativado (unbound=&quot;true&quot;), o link será declarado como um elemento de coleção para uma cardinalidade 1-N.
* **userEnum (cadeia de caracteres)**: recebe o nome interno de uma enumeração &quot;aberta&quot;. Valores de enumeração podem ser definidos pelo usuário na interface.
* **xml (booleano)**: se esta opção estiver ativada, todos os valores definidos no elemento serão armazenados em XML em um campo &quot;mData&quot; do tipo TEXT. Isso significa que não haverá filtragem ou classificação nesses campos.
* **xmlChildren (booleano)**: força o armazenamento para cada filho ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
