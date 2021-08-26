---
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 0%

---

# elemento {#element--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-4}

element:==(attribute | cadeia de caracteres de computação | dbindex | padrão | elemento | ajuda | adesão | chave | sysFilter | traduzidoPadrão)

## Atributos {#attributes-4}

_operation (cadeia de caracteres), avançado (booleano), agregado (cadeia de caracteres), applicableIf (cadeia de caracteres), autopk (booleano), pertenceTo (cadeia de caracteres), confDate (cadeia de caracteres), dataPolicy (cadeia de caracteres), dataSource (cadeia de caracteres), dbEnum (cadeia de caracteres), defOnDuplicate (booleano), padrão (cadeia de caracteres), desc (cadeia de caracteres), displayAs Field (booleano), doesNotSupportDiff (booleano), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink string), folderModel (string), folderProcess (string), fullLoad (booleano), hierárquico (booleano), hiericalPath (string), img (string), inout (string), integridade (string), rótulo (string), labelSingular (string), comprimento (string), localizável (booleano), name (MNTOKEN), noDb Index (booleano), noKey (booleano), ordered (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean), Integrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (booleano), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), target (MNTOKEN), template (string ole), TemporaryTable (boboboan), translationDefault (string), translationExpr (string), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (booleano), xmlChildren (booleano)

## Pais {#parents-4}

`<srcschema>`

`<element>`

## Crianças {#children-4}

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

* Raiz `<element>` : define o nome da tabela SQL que corresponde ao schema.
* Estrutura `<element>` : define um grupo de `<element>`   ou   `<attribute>`    elementos.
* Link `<element>` : define um link. Esses elementos devem incluir o atributo &quot;@type=link&quot;.
* XML `<element>` : define um campo &quot;mData&quot; do tipo de texto. Esse elemento deve incluir o atributo &quot;@type=xml&quot;.

## Descrição do atributo {#attribute-description-4}

* **_operation (cadeia de caracteres)**: define o tipo de gravação no banco de dados.

   Esse atributo é usado principalmente na extensão de schemas prontos para uso.

   Os valores acessíveis são:

   * &quot;nenhum&quot;: apenas a reconciliação. Isso significa que o Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualizar com inserção. Isso significa que o Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;inserir&quot;: inserção. Isso significa que o Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualizar. Isso significa que o Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que o Adobe Campaign recuperará e excluirá elementos.

* **avançado (booleano)**: quando essa opção é ativada (@advanced=&quot;true&quot;), ela permite ocultar o atributo na lista de campos disponíveis acessíveis para configurar uma lista em um formulário.
* **agregado (string)**: permite copiar a definição de um  `<element>`  por meio de outro schema. Esse atributo recebe uma declaração de schema no formato de &quot;namespace:name&quot;.
* **applicableIf (cadeia de caracteres)**: condição para aplicar o índice. Esse atributo recebe uma expressão XTK.
* **autopk (booleano)**: se essa opção estiver ativada (autopk=&quot;true&quot;), uma chave exclusiva será definida automaticamente. Essa opção só pode ser usada no elemento principal do schema. Aviso, o Adobe Campaign garante apenas que a chave gerada seja exclusiva. Não é garantido que os valores principais sejam consecutivos e incrementais.
* **dataPolicy (string)**: permite especificar restrições de aprovação em valores permitidos no campo SQL. Os valores para este atributo são:

   * &quot;nenhum&quot;: sem valor
   * &quot;smartCase&quot;: maiúsculas das primeiras letras
   * &quot;lowerCase&quot;: todas as minúsculas
   * &quot;upperCase&quot;: todas as maiúsculas
   * &quot;email&quot;: endereço de email
   * &quot;Telefone&quot;: número de telefone
   * &quot;identificador&quot;: nome do identificador
   * &quot;resIdentifier&quot;: nome do arquivo

* **dbEnum (cadeia de caracteres)**: recebe o nome interno de uma enumeração &quot;fechada&quot;. Os valores de enumeração devem ser definidos no `<srcschema>`.
* **defOnDuplicate (booleano)**: se esse atributo estiver ativado, quando um registro for duplicado, o valor padrão (definido em @default) será automaticamente reaplicado ao registro.
* **padrão (string)**: permite definir o comportamento do elemento (chamada para uma função, valor padrão). Esse atributo recebe uma expressão XTK.
* **desc (string)**: permite inserir uma descrição do elemento. Essa descrição é exibida na barra de status da interface.
* **displayAsField (booleano)**: se esse atributo estiver ativado, um tipo &quot;link&quot;  `<element>`  será exibido como um campo na visualização em árvore dos schemas (guia &quot;Estrutura&quot;). Dessa forma, é possível exibir um link como um campo local e alterar seu comportamento durante um query. Quando o elemento é encontrado na opção SELECT of a query, o valor do público alvo do link será usado. Quando o elemento é encontrado no WHERE de um query, a chave subjacente do link é usada.
* **editar (sequência de caracteres)**: esse atributo especifica o tipo de entrada que será usado no formulário vinculado ao schema.
* **enum (string)**: recebe o nome da enumeração vinculada ao campo . A enumeração pode ser inserida no mesmo schema ou em um schema remoto.
* **expr (string)**: esse atributo define um campo calculado para o qual nenhuma definição é armazenada na tabela. Ele recebe uma expressão Xpath ou XTK (sequência de caracteres).
* **externalJoin (booleano)**: associação externa em um elemento de tipo &quot;link&quot;.
* **recurso (string)**: define um campo de características: Esses campos são usados para estender os dados em uma tabela existente, mas com armazenamento em uma tabela em anexo. Os valores aceitos são:

   * &quot;shared&quot;: o conteúdo é armazenado em uma tabela compartilhada por tipo de dados
   * &quot;dedicado&quot;: o conteúdo é armazenado em uma tabela dedicada

   As tabelas de características SQL são criadas automaticamente com base no tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Existem dois tipos de campos de características: campos simples em que um único valor é autorizado nos campos característicos e de escolha múltipla, em que a característica está vinculada a um elemento de coleção que pode conter vários valores.

   Quando uma característica é definida em um schema, esse schema deve ter uma chave principal com base em um único campo (chaves compostas não são autorizadas).

* **featureDate (booleano)**: atributo vinculado ao campo de características &quot;@feature&quot;. Se o valor for &quot;true&quot;, ele permitirá descobrir quando o valor foi atualizado pela última vez.
* **filterPath (string)**: esse atributo recebe um Xpath e permite definir um filtro em um campo.
* **folderLink (cadeia de caracteres)**: esse atributo recebe o nome do link que permite recuperar os arquivos que contêm entidades.
* **folderModel (cadeia de caracteres)**: define o tipo de pasta que permite o armazenamento de entidade. Este atributo só será definido se &quot;@folderLink&quot; estiver presente.
* **folderProcess (cadeia de caracteres)**: define o link onde as instâncias do modelo de entidade são armazenadas. Este atributo só será definido se &quot;@folderLink&quot; estiver presente.
* **fullLoad (booleano)**: esse atributo força a exibição de todos os registros em uma tabela durante a seleção de campo em um formulário.
* **img (string)**: O recebe o caminho de uma imagem vinculada a um elemento. O valor desse atributo é do tipo &quot;namespace:image name&quot;. Por exemplo: img=&quot;cus:myImage.jpg&quot;. Fisicamente, a imagem deve ser importada para o servidor de aplicativos.
* **integridade (string)**: integridade referencial da ocorrência da tabela de origem para a tabela de destino.

   Os valores acessíveis são:

   * &quot;definir&quot;: A Adobe Campaign não exclui a entidade se ela for referenciada por meio do link
   * &quot;normal&quot;: a exclusão da ocorrência de origem inicializa as chaves do link na ocorrência de destino (modo padrão), esse tipo de integridade inicializa todas as chaves estrangeiras
   * &quot;own&quot;: excluir a ocorrência de origem aciona a exclusão da ocorrência de destino
   * &quot;owncopy&quot;: semelhante a &quot;own&quot; (no caso de exclusão) ou duplicata ocorrências (no caso de duplicação)
   * &quot;Neutro&quot;: não faz nada

* **label (string)**: rótulo do elemento.
* **labelSingular (cadeia de caracteres)**: rótulo (forma singular) do elemento usado em algumas partes da interface.
* **length (string)**: máx. número de caracteres autorizados para um valor do campo SQL tipo &quot;string&quot;.
* **localizável (booleano)**: se estiver ativado, esse atributo informará a ferramenta de coleta para recuperar o valor do atributo &quot;@label&quot; para tradução (uso interno).
* **nome (MNTOKEN)**: nome interno do elemento que corresponde ao nome da tabela. O valor do atributo &quot;@name&quot; deve ser curto, preferencialmente em inglês, e estar em conformidade com as restrições de nomenclatura vinculadas ao XML.

   Quando o schema é gravado no banco de dados, os prefixos são adicionados automaticamente ao nome do campo pelo Adobe Campaign.

   * &quot;i&quot;: prefixo para o tipo &quot;inteiro&quot;.
   * &quot;d&quot;: prefixo para o tipo &quot;duplo&quot;.
   * &quot;s&quot;: prefixo para o tipo de cadeia de caracteres.
   * &quot;ts&quot;: prefixo do tipo &quot;data&quot;.

   Para definir o nome da tabela de forma autônoma, você precisa usar o atributo &quot;@sqltable&quot; na definição do elemento de schema principal.

* **noDbIndex (booleano)**: permite especificar que o elemento não será indexado.
* **ordenado (booleano)**: se o atributo estiver ativado (ordered=&quot;true&quot;), o Adobe Campaign manterá a sequência de declaração do elemento em um elemento de coleção XML.
* **pkSequence (cadeia de caracteres)**: recebe o nome da sequência a ser usada para calcular uma chave de incremento automático. Esse atributo só poderá ser usado se uma chave incremental automaticamente for definida no elemento raiz do schema.
* **pkgStatus (cadeia de caracteres)**: durante exportações de pacote, os valores serão considerados como uma função do valor desse atributo:

   * &quot;always&quot;: o elemento sempre estará presente
   * &quot;never&quot;: o elemento nunca estará presente
   * &quot;padrão (ou nada)&quot;: o elemento é exportado, a menos que seja o elemento padrão ou se não for um campo interno e não será compatível com outras instâncias

* **ref (string)**: esse atributo define uma referência a um elemento > compartilhado por vários schemas (fator de definição). A definição não é copiada para o schema atual.
* **obrigatório (booleano)**: se este atributo for ativado (@required=&quot;true&quot;), o campo será realçado na interface. O rótulo do campo será vermelho nos formulários.
* **revAdvanced (booleano)**: quando ativado, este atributo especifica que o link oposto é um link &quot;avançado&quot;.
* **revCardinalidade (string)**: esse atributo define a cardinalidade de um vínculo entre duas tabelas. Ele é usado em um tipo &quot;link&quot; `<element>`.

   Os valores possíveis são:

   * &quot;único&quot; : Link do tipo 1-1 simples
   * &quot;unbound&quot;: Link de coleção do tipo 1-N

   Por padrão, se o atributo não for especificado durante a criação do link, a cardinalidade será 1-N.

* **revDesc (sequência de caracteres)**: esse atributo recebe uma descrição vinculada ao link oposto.
* **revExternalJoin (booleano)**: quando ativado, esse atributo permite forçar a associação externa no link oposto.
* **revIntegrity (cadeia de caracteres)**: esse atributo define a integridade no schema do target. Os mesmos valores que o atributo &quot;@integridade&quot; são autorizados. Por padrão, o Adobe Campaign fornece o valor &quot;normal&quot; para esse atributo.
* **revLabel (cadeia de caracteres)**: rótulo do link oposto.
* **revLink (sequência de caracteres)**: nome do link oposto. Se o valor for &quot;_NONE_&quot;, nenhum link oposto será criado no schema de destino.
* **revTarget (sequência de caracteres)**: target do link oposto.
* **sql (booleano)**: se este atributo for ativado (@sql=&quot;true&quot;), ele forçará o armazenamento do elemento SQL, mesmo se o elemento tiver a propriedade xml=&quot;true&quot;.
* **sqlname (sequência de caracteres)**: nome do campo durante a criação da tabela. Se &quot;@sqlname&quot; não for especificado, o valor do atributo &quot;@name&quot; será usado por padrão. Ao gravar o schema na tabela, os prefixos são adicionados automaticamente dependendo do tipo de campo.
* **sqltable (sequência)**: para o elemento principal do schema, esse atributo sobrecarrega o nome da tabela SQL gerada por padrão. Se &quot;@sqltable&quot; não for especificado, o nome padrão será estruturado desta forma: namespace (primeira letra maiúscula) seguido pelo valor de SrcSchema &quot;@name&quot;.
* **tableSpace (cadeia de caracteres)**: esse atributo permite especificar um novo tablespace de armazenamento de dados para uma tabela (válido na raiz  `<element>`).
* **tableSpaceIndex (cadeia de caracteres)**: esse atributo permite especificar um novo tablespace de armazenamento de índice para uma tabela (válido na raiz  `<element>`).
* **target (MNTOKEN)**: recebe o nome do schema target ao criar um link entre tabelas. Este atributo está ativo apenas para elementos do tipo &quot;link&quot;.
* **template (string)**: esse atributo define uma referência a um  `<element>` elemento compartilhado por vários schemas. A definição é copiada automaticamente para o schema atual.
* **translationDefault (cadeia de caracteres)**: se um atributo &quot;@default&quot; for encontrado, &quot;@translationDefault&quot; permitirá redefinir uma expressão para corresponder à definida em @default, a ser coletada pela ferramenta de tradução (uso interno).
* **translationExpr (cadeia de caracteres)**: se um atributo &quot;@expr&quot; for encontrado, o atributo &quot;@translationExpr&quot; permitirá redefinir uma expressão correspondente à definida em &quot;@expr&quot; e que será coletada pela ferramenta de tradução (uso interno).
* **tipo (MNTOKEN)**: define o tipo de dados armazenados no elemento .

   Lista de tipos disponíveis:

   * ANY
   * compartimento
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * data
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memorando
   * MNTOKEN
   * percent
   * chave primária
   * short
   * string
   * tempo
   * timespan
   * uuid

* **unbound (booleano)**: se o atributo for ativado (unbound=&quot;true&quot;), o link será declarado como um elemento de coleção para uma cardinalidade 1-N.
* **userEnum (sequência de caracteres)**: recebe o nome interno de uma enumeração &quot;open&quot;. Os valores de enumeração podem ser definidos pelo usuário na interface.
* **xml (booleano)**: se essa opção estiver ativada, todos os valores definidos no elemento serão armazenados em XML em um campo &quot;mData&quot; do tipo TEXT. Isso significa que não haverá filtragem ou classificação nesses campos.
* **xmlChildren (booleano)**: força o armazenamento para cada criança (  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
