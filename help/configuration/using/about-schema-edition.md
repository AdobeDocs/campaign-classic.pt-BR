---
solution: Campaign Classic
product: campaign
title: Sobre a edição do schema
description: Introdução à edição do schema
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 9%

---


# Sobre a edição do schema{#about-schema-edition}

A Adobe Campaign emprega Schemas de dados para:

* Definir como os objetos de dados no aplicativo estão vinculados às tabelas de banco de dados subjacentes.
* Definir links entre os diferentes objetos de dados no aplicativo Campaign.
* Definir e descrever os campos individuais incluídos em cada objeto.

Para obter uma melhor compreensão das tabelas integradas de Campanha e de suas interações, consulte o modelo [de dados de](https://helpx.adobe.com/br/campaign/kb/acc-datamodel.html)Campaign Classic.

## Extensão ou criação de schemas {#extending-or-creating-schemas}

Para adicionar um campo, índice ou outro elemento a um dos schemas de dados principais na Campanha, como a tabela recipient (nms:recipient), é necessário estender esse schema. For more on this, refer to the [Extending a schema](../../configuration/using/extending-a-schema.md) section.

Para adicionar um tipo de dados totalmente novo que não existe predefinido no Adobe Campaign (uma tabela de contratos, por exemplo), você pode criar um schema personalizado diretamente. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_1.png)

Depois de estender ou criar um schema para trabalhar, a prática recomendada é definir seus elementos de conteúdo XML na mesma ordem em que aparecem abaixo.

## Enumerações {#enumerations}

As listas discriminadas são definidas primeiro, antes do elemento principal do schema. Eles permitem que você exiba valores em uma lista para restringir as opções que o usuário tem para um determinado campo.

Exemplo:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

Ao definir campos, você pode usar essa lista discriminada da seguinte maneira:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>Você também pode empregar listas discriminadas gerenciadas pelo usuário (normalmente em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ) para especificar os valores para um determinado campo. Essas são listas discriminadas globais de modo eficiente e uma escolha melhor se sua lista discriminada puder ser usada fora do schema específico em que você está trabalhando.

Para saber mais sobre listas discriminadas, consulte as seções [Listas discriminadas](../../configuration/using/schema-structure.md#enumerations) e [`<enumeration>` elementos](../../configuration/using/elements-and-attributes.md#enumeration--element) .

## Índice {#index}

Os índices são os primeiros elementos declarados no elemento principal do schema.

Eles podem ser exclusivos ou não e fazer referência a um ou mais campos.

Exemplos:

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

O atributo **xpath** aponta para o campo no seu schema que você deseja indexar.

>[!IMPORTANT]
>
>É importante lembrar que os ganhos de desempenho de leitura do query SQL fornecidos por índices também vêm com uma ocorrência de desempenho nos registros de gravação. Por conseguinte, os índices devem ser utilizados com precaução.

Para obter mais informações sobre índices, consulte a seção [Campos](../../configuration/using/database-mapping.md#indexed-fields) indexados.

## Teclas {#keys}

Todas as tabelas devem ter pelo menos uma chave, e muitas vezes são automaticamente estabelecidas no elemento principal do schema usando o atributo **@autopk=true** definido como &quot;true&quot;.

A chave primária também pode ser definida usando o atributo **interno** .

Exemplo:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

Neste exemplo, em vez de permitir que o atributo **@autopk** crie uma chave primária padrão chamada &quot;id&quot;, estamos especificando nossa própria chave primária &quot;homeId&quot;.

>[!IMPORTANT]
>
>Ao criar um novo schema ou durante uma extensão de schema, você precisa manter o mesmo valor de sequência da chave primária (@pkSequence) para todo o schema.

Para saber mais sobre chaves, consulte a seção [Gerenciamento de chaves](../../configuration/using/database-mapping.md#management-of-keys) .

## Atributos (Campos) {#attributes--fields-}

Os atributos permitem que você defina os campos que compõem o objeto de dados. Você pode usar o **[!UICONTROL Insert]** botão na barra de ferramentas da edição do schema para soltar modelos de atributos vazios em seu XML, onde está o cursor. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_2.png)

A lista completa de atributos está disponível na seção de [`<attribute>` elementos](../../configuration/using/elements-and-attributes.md#attribute--element) . Estes são alguns dos atributos mais usados:

* **@avançado**
* **@dataPolicy**
* **@padrão**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@obrigatório**
* **@ref**
* **@xml**
* **@type**

   Para visualização de uma tabela que lista os mapeamentos para os tipos de dados gerados pela Adobe Campaign para os diferentes sistemas de gerenciamento de banco de dados, consulte a seção [Mapeamento dos tipos de dados](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) Adobe Campaign/DBMS.

Para obter mais informações sobre cada atributo, consulte a seção Descrição [do](../../configuration/using/elements-and-attributes.md#attribute-description) atributo.

### Exemplos {#examples}

Exemplo de definição de um valor padrão:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Exemplo de uso de um atributo comum como modelo para um campo também marcado como obrigatório:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Exemplo de um campo calculado que está oculto usando o atributo **@advanced** :

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

Exemplo de um campo XML também armazenado em um campo SQL e que tem um atributo **@dataPolicy** .

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Embora a maioria dos atributos esteja vinculada de acordo com uma cardinalidade de 1 a 1 a um campo físico do banco de dados, esse não é o caso dos campos XML ou computados.\
>Um campo XML é armazenado em um campo de memorando (&quot;mData&quot;) da tabela.\
>Entretanto, um campo calculado é criado dinamicamente cada vez que um query é iniciado, portanto, ele só existe na camada aplicativa.

## Links {#links}

Os links são alguns dos últimos elementos no elemento principal do seu schema. Eles definem como todos os diferentes schemas em seu caso se relacionam entre si.

Os links são declarados no schema que contém a chave **** estrangeira da tabela à qual estão vinculados.

Há três tipos de cardinalidade: 1-1, 1-N e N-N. É o tipo 1-N usado por padrão.

### Exemplos {#examples-1}

Um exemplo de um link 1-N entre a tabela do recipient (schema predefinido) e uma tabela de transações personalizadas:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Um exemplo de um link 1-1 entre um schema personalizado &quot;Carro&quot; (na namespace &quot;cus&quot;) e a tabela do recipient:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Exemplo de uma associação externa entre a tabela do recipient e uma tabela de endereços com base no endereço de email e não em uma chave primária:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Aqui, &quot;xpath-dst&quot; corresponde à chave primária no schema do público alvo e &quot;xpath-src&quot; corresponde à chave estrangeira no schema de origem.

## Trilha de auditoria {#audit-trail}

Um elemento útil que você pode querer incluir na parte inferior do schema é um elemento de rastreamento (Trilha de auditoria).

Use o exemplo abaixo para incluir campos relacionados à data de criação, o usuário que criou os dados, a data e o autor da última modificação para todos os dados na tabela:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Atualização da estrutura do banco de dados {#updating-the-database-structure}

Quando as alterações forem concluídas e salvas, todas as alterações que possam afetar a estrutura SQL deverão ser aplicadas ao banco de dados. Para fazer isso, use o assistente de atualização de banco de dados.

![](assets/schemaextension_getting_started_3.png)

Para obter mais informações, consulte a seção [Atualização da estrutura do banco de dados](../../configuration/using/updating-the-database-structure.md).

>[!NOTE]
>
>Quando as modificações não afetam a estrutura do banco de dados, é necessário apenas gerar novamente os schemas. Para fazer isso, selecione os schemas a serem atualizados, clique com o botão direito do mouse e escolha **[!UICONTROL Actions > Regenerate selected schemas...]** . For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.

