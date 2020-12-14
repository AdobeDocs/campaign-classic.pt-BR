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
source-wordcount: '2012'
ht-degree: 0%

---


# elemento {#element--element}

## Modelo de conteúdo {#content-model-4}

element:==(attribute | sequência de caracteres de computação | dbindex | incumprimento | elemento | ajuda | aderir | chave | sysFilter | traduzidoPadrão)

## Atributos {#attributes-4}

_operation (string), avançada (booleana), agregação (string), applyIf (string), autopk (booleano), pertenceTo (string), convencDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAs Field (booleano), doesNotSupportDiff (booleano), edit (string), emptyKeyValue (string), enum (string), enumImage (string), spanSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (string), folderModel (string), folderProcess (string), fullLoad (booleano), hierárquico (booleano), hierárquicalPath (string), img (string), inout (string), integridade (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), no Db Index (booleano), noKey (booleano), order (booleano), overflow (booleano), pkSequence (string), pkgStatus (string), ref (string), required (booleano), revAdvanced (booleano), revCardinality (string), revDesc (string), revExternalJoin (booleano), revIntegrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), público alvo (MNTOKEN), template (string), limitedTable booleano), traduzdefault (string), traduzxpr (string), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (booleano), xmlChildren (booleano)

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

* Raiz `<element>` : define o nome da tabela SQL que corresponde ao schema.
* Estrutura `<element>` : define um grupo de `<element>`   ou   `<attribute>`    elementos.
* Link `<element>` : define um link. Esses elementos devem incluir o atributo &quot;@type=link&quot;.
* XML `<element>` : define um campo &quot;mData&quot; do tipo de texto. Esse elemento deve incluir o atributo &quot;@type=xml&quot;.

## Descrição do atributo {#attribute-description-4}

* **_operation (cadeia de caracteres)**: define o tipo de gravação no banco de dados.

   Este atributo é usado principalmente ao estender schemas prontos para uso.

   Os valores acessíveis são:

   * &quot;nenhum&quot;: apenas reconciliação. Isso significa que a Adobe Campaign recuperará o elemento sem atualizá-lo ou gerar um erro se ele não existir.
   * &quot;insertOrUpdate&quot;: atualizar com inserção. Isso significa que a Adobe Campaign atualizará o elemento ou o criará se ele não existir.
   * &quot;Inserir&quot;: inserção. Isso significa que a Adobe Campaign inserirá o elemento sem verificar se ele existe.
   * &quot;update&quot;: atualizar. Isso significa que a Adobe Campaign atualizará o elemento ou gerará um erro se ele não existir.
   * &quot;delete&quot;: exclusão. Isso significa que a Adobe Campaign recuperará e excluirá elementos.

* **avançado (booleano)**: quando essa opção é ativada (@advanced=&quot;true&quot;), ela permite ocultar o atributo na lista de campos disponíveis acessíveis para configurar uma lista em um formulário.
* **agregação (string)**: permite copiar a definição de um  `<element>`  por meio de outro schema. Este atributo recebe uma declaração de schema na forma de &quot;namespace:nome&quot;.
* **applyIf (string)**: para aplicar o índice. Este atributo recebe uma expressão XTK.
* **autopk (booleano)**: se essa opção estiver ativada (autopk=&quot;true&quot;), uma chave exclusiva será definida automaticamente. Essa opção só pode ser usada no elemento principal do schema. Aviso, a Adobe Campaign garante apenas que a chave gerada seja exclusiva. Não é garantido que os valores principais sejam consecutivos e incrementais.
* **dataPolicy (string)**: permite especificar restrições de aprovação em valores permitidos no campo SQL. Os valores para este atributo são:

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
* **padrão (string)**: permite definir o comportamento do elemento (chamada para uma função, valor padrão). Este atributo recebe uma expressão XTK.
* **desc (string)**: permite inserir uma descrição do elemento. Essa descrição é exibida na barra de status da interface.
* **displayAsField (booleano)**: se esse atributo estiver ativado, um tipo de &quot;link&quot;  `<element>`  será exibido como um campo na visualização em árvore dos schemas (&quot;guia Estrutura&quot;). Dessa forma, é possível exibir um link como um campo local e alterar seu comportamento durante um query. Quando o elemento for encontrado na SELEÇÃO de um query, o valor do público alvo do link será usado. Quando o elemento for encontrado em WHERE de um query, a chave subjacente do link será usada.
* **edit (string)**: esse atributo especifica o tipo de entrada que será usado no formulário vinculado ao schema.
* **enum (string)**: recebe o nome da lista discriminada vinculada ao campo. A lista discriminada pode ser inserida no mesmo schema ou em um schema remoto.
* **expr (string)**: esse atributo define um campo calculado para o qual nenhuma definição é armazenada na tabela. Ele recebe uma expressão Xpath ou XTK (string).
* **externalJoin (booleano)**: participação externa em um elemento do tipo &quot;link&quot;.
* **recurso (string)**: define um campo de características: Esses campos são usados para estender os dados em uma tabela existente, mas com armazenamento em uma tabela em anexo. Os valores aceitos são:

   * &quot;compartilhado&quot;: o conteúdo é armazenado em uma tabela compartilhada por tipo de dados
   * &quot;dedicado&quot;: o conteúdo é armazenado em uma tabela dedicada

   As tabelas de características SQL são criadas automaticamente com base no tipo de característica:

   * dedicado: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Há dois tipos de campos de características: campos simples nos quais um único valor é autorizado sobre a característica e campos de múltipla escolha, nos quais a característica está ligada a um elemento de coleção que pode conter vários valores.

   Quando uma característica é definida em um schema, esse schema deve ter uma chave principal baseada em um único campo (chaves compostas não são autorizadas).

* **featureDate (booleano)**: vinculado ao campo de características &quot;@feature&quot;. Se o valor for &quot;true&quot;, ele permitirá que você descubra quando o valor foi atualizado pela última vez.
* **filterPath (string)**: esse atributo recebe um Xpath e permite definir um filtro em um campo.
* **folderLink (string)**: esse atributo recebe o nome do link que permite recuperar os arquivos que contêm entidades.
* **folderModel (string)**: define o tipo de pasta que ativa o armazenamento da entidade. Este atributo só é definido se &quot;@folderLink&quot; estiver presente.
* **folderProcess (string)**: define o link no qual as instâncias do modelo de entidade são armazenadas. Este atributo só é definido se &quot;@folderLink&quot; estiver presente.
* **fullLoad (booleano)**: esse atributo força a exibição de todos os registros em uma tabela durante a seleção de campo em um formulário.
* **img (string)**: recebe o caminho de uma imagem vinculada a um elemento. O valor desse atributo é do tipo &quot;namespace:nome da imagem&quot;. Por exemplo: img=&quot;cus:myImage.jpg&quot;. Fisicamente, a imagem deve ser importada para o servidor de aplicativos.
* **integridade (string)**: integridade referencial da ocorrência da tabela de origem em direção à tabela do público alvo.

   Os valores acessíveis são:

   * &quot;definir&quot;: A Adobe Campaign não exclui a entidade se ela for referenciada pelo link
   * &quot;normal&quot;: a exclusão da ocorrência de origem inicializa as chaves do link na ocorrência do público alvo (modo padrão), esse tipo de integridade inicializa todas as chaves estrangeiras
   * &quot;own&quot;: a exclusão da ocorrência de origem aciona a exclusão da ocorrência do público alvo
   * &quot;cópia&quot;: semelhante a ocorrências &quot;próprias&quot; (em caso de exclusão) ou de duplicados (em caso de duplicação)
   * &quot;neutro&quot;: não faz nada

* **label (string)**: rótulo do elemento.
* **labelSingular (string)**: label (forma singular) do elemento usado em algumas partes da interface.
* **length (string)**: máx. número de caracteres autorizados para um valor do campo SQL tipo &quot;string&quot;.
* **localizável (booleano)**: se estiver ativado, esse atributo informará a ferramenta de coleta para recuperar o valor do atributo &quot;@label&quot; para conversão (uso interno).
* **name (MNTOKEN)**: nome interno do elemento que corresponde ao nome da tabela. O valor do atributo &quot;@name&quot; deve ser curto, de preferência em inglês, e estar em conformidade com as restrições de nomenclatura vinculadas ao XML.

   Quando o schema é gravado no banco de dados, os prefixos são adicionados automaticamente ao nome do campo pela Adobe Campaign.

   * &quot;i&quot;: prefixo para o tipo &#39;integer&#39;.
   * &quot;d&quot;: prefixo para o tipo &quot;duplo&quot;.
   * &quot;s&quot;: prefixo para o tipo de string de caractere.
   * &quot;ts&quot;: prefixo para o tipo &#39;date&#39;.

   Para definir o nome da tabela de forma autônoma, é necessário usar o atributo &quot;@sqltable&quot; na definição do elemento do schema principal.

* **noDbIndex (booleano)**: permite especificar que o elemento não será indexado.
* **pedido (booleano)**: se o atributo estiver ativado (order=&quot;true&quot;), a Adobe Campaign manterá a sequência de declaração do elemento em um elemento de coleção XML.
* **pkSequence (string)**: recebe o nome da sequência a ser usada para calcular uma chave incremental automática. Este atributo só pode ser usado se uma chave incremental automática for definida no elemento raiz do schema.
* **pkgStatus (string)**: durante as exportações de pacotes, os valores serão considerados como uma função do valor deste atributo:

   * &quot;always&quot;: o elemento sempre estará presente
   * &quot;nunca&quot;: o elemento nunca estará presente
   * &quot;padrão (ou nada)&quot;: o elemento é exportado a menos que seja o elemento padrão ou que não seja um campo interno e não seja compatível com outras instâncias

* **ref (string)**: esse atributo define uma referência a um elemento >element> compartilhado por vários schemas (fator de definição). A definição não é copiada para o schema atual.
* **obrigatório (booleano)**: se este atributo estiver ativado (@required=&quot;true&quot;), o campo será realçado na interface. O rótulo do campo será vermelho nos formulários.
* **revAdvanced (booleano)**: quando ativado, esse atributo especifica que o link oposto é um link &quot;avançado&quot;.
* **revCardinalidade (string)**: este atributo define a cardinalidade de um link entre duas tabelas. É usado em um tipo &quot;link&quot; `<element>`.

   Os valores possíveis são:

   * &quot;single&quot; : Link simples do tipo 1-1
   * &quot;unbound&quot;: Link de coleção do tipo 1-N

   Por padrão, se o atributo não for especificado durante a criação do link, a cardinalidade será 1-N.

* **revDesc (string)**: este atributo recebe uma descrição vinculada ao link oposto.
* **revExternalJoin (booleano)**: quando ativado, esse atributo permite forçar a junção externa no link oposto.
* **revIntegrity (string)**: esse atributo define a integridade do schema do público alvo. Os mesmos valores que o atributo &quot;@Integrity&quot; estão autorizados. Por padrão, a Adobe Campaign atribui o valor &quot;normal&quot; a esse atributo.
* **revLabel (string)**: rótulo do link oposto.
* **revLink (string)**: nome do link oposto. Se o valor for &quot;_NONE_&quot;, nenhum link oposto será criado no schema de destino.
* **revTarget (sequência)**: público alvo do link oposto.
* **sql (booleano)**: se esse atributo estiver ativado (@sql=&quot;true&quot;), ele forçará o armazenamento do elemento SQL, mesmo se o elemento tiver a propriedade xml=&quot;true&quot;.
* **sqlname (string)**: nome do campo durante a criação da tabela. Se &quot;@sqlname&quot; não for especificado, o valor do atributo &quot;@name&quot; será usado por padrão. Ao gravar o schema na tabela, os prefixos são adicionados automaticamente dependendo do tipo de campo.
* **sqltable (string)**: para o elemento principal do schema, esse atributo sobrecarrega o nome da tabela SQL gerada por padrão. Se &quot;@sqltable&quot; não for especificado, o nome padrão será estruturado desta forma: namespace (primeira letra maiúscula) seguida do valor de SrcSchema &quot;@name&quot;.
* **tableSpace (string)**: esse atributo permite que você especifique um novo tablespace de armazenamento de dados para uma tabela (válido na raiz  `<element>`).
* **tableSpaceIndex (string)**: esse atributo permite que você especifique um novo tablespace de armazenamento de índice para uma tabela (válido na raiz  `<element>`).
* **público alvo (MNTOKEN)**: recebe o nome do schema do público alvo ao criar um link entre tabelas. Este atributo está ativo apenas para elementos do tipo &quot;link&quot;.
* **template (string)**: esse atributo define uma referência a um  `<element>` elemento compartilhado por vários schemas. A definição é copiada automaticamente para o schema atual.
* **transactionDefault (string)**: se um atributo &quot;@default&quot; for encontrado, o &quot;@traduzdefault&quot; permitirá que você redefina uma expressão para corresponder àquela definida em @default, a ser coletada pela ferramenta de conversão (uso interno).
* **transactionExpr (string)**: se um atributo &quot;@expr&quot; for encontrado, o atributo &quot;@traduçõesExpr&quot; permite redefinir uma expressão que corresponde à definida em &quot;@expr&quot; e que será coletada pela ferramenta de tradução (uso interno).
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

* **unbound (booleano)**: se o atributo estiver ativado (unbound=&quot;true&quot;), o link será declarado como um elemento de coleção para uma cardinalidade 1-N.
* **userEnum (string)**: recebe o nome interno de uma lista discriminada &quot;aberta&quot;. Os valores de lista discriminada podem ser definidos pelo usuário na interface.
* **xml (booleano)**: se essa opção estiver ativada, todos os valores definidos no elemento serão armazenados em XML em um campo &quot;mData&quot; do tipo TEXT. Isso significa que não haverá filtragem ou classificação nesses campos.
* **xmlChildren (booleano)**: força o armazenamento de cada criança (  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
