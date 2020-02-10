---
title: Sobre a edição do esquema
seo-title: Sobre a edição do esquema
description: Sobre a edição do esquema
seo-description: null
page-status-flag: never-activated
uuid: edb4d47d-b507-4d86-9873-ebd5f6acefc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: d5b08e4e-060c-4185-9dac-af270918e2b9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 58b69ae83d0ff2bece26cb3ff0604cd92e3c20f4

---


# Sobre a edição do esquema{#about-schema-edition}

O Adobe Campaign emprega os Esquemas de dados para:

* Definir como os objetos de dados no aplicativo estão vinculados às tabelas de banco de dados subjacentes.
* Definir links entre os diferentes objetos de dados no aplicativo Campaign.
* Definir e descrever os campos individuais incluídos em cada objeto.

Para obter uma melhor compreensão das tabelas integradas do Campaign e de suas interações, consulte o modelo [de dados do](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)Campaign Classic.

## Extensão ou criação de esquemas {#extending-or-creating-schemas}

Para adicionar um campo, índice ou outro elemento a um dos esquemas de dados principais do Campaign, como a tabela do destinatário (nms:receipt), é necessário estender esse esquema. Para obter mais informações, consulte a seção [Extensão de um esquema](../../configuration/using/extending-a-schema.md) .

Para adicionar um tipo de dados totalmente novo que não existe prontamente no Adobe Campaign (uma tabela de contratos, por exemplo), é possível criar um esquema personalizado diretamente. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_1.png)

Depois de estender ou criar um esquema para trabalhar, a prática recomendada é definir seus elementos de conteúdo XML na mesma ordem em que aparecem abaixo.

## Enumerações {#enumerations}

As enumerações são definidas primeiro, antes do elemento principal do esquema. Eles permitem que você exiba valores em uma lista para restringir as opções que o usuário tem para um determinado campo.

Exemplo:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

Ao definir campos, você pode usar essa enumeração da seguinte maneira:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>Também é possível empregar enumerações gerenciadas pelo usuário (normalmente em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ) para especificar os valores para um determinado campo. Essas enumerações são efetivamente globais e uma escolha melhor se sua enumeração puder ser usada fora do esquema específico em que você está trabalhando.

Para saber mais sobre enumerações, consulte as seções [Enumerações](../../configuration/using/schema-structure.md#enumerations) e [`<enumeration>` elementos](../../configuration/using/elements-and-attributes.md#enumeration--element) .

## Índice {#index}

Os índices são os primeiros elementos declarados no elemento principal do esquema.

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

O atributo **xpath** aponta para o campo no esquema que você deseja indexar.

>[!CAUTION]
>
>É importante lembrar que os ganhos de desempenho de leitura da consulta SQL fornecidos por índices também vêm com uma ocorrência de desempenho nos registros de gravação. Por conseguinte, os índices devem ser utilizados com precaução.

Para obter mais informações sobre índices, consulte a seção Campos [](../../configuration/using/database-mapping.md#indexed-fields) indexados.

## Teclas {#keys}

Todas as tabelas devem ter pelo menos uma chave e muitas vezes são automaticamente estabelecidas no elemento principal do esquema usando o atributo **@autopk=true** definido como &quot;true&quot;.

A chave primária também pode ser definida usando o atributo **interno** .

Exemplo:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

Neste exemplo, em vez de permitir que o atributo **@autopk** crie uma chave primária padrão chamada &quot;id&quot;, estamos especificando nossa própria chave primária &quot;homeId&quot;.

>[!CAUTION]
>
>Ao criar um novo schema ou durante uma extensão de schema, você precisa manter o mesmo valor de sequência da chave primária (@pkSequence) para todo o schema.

Para saber mais sobre chaves, consulte a seção [Gerenciamento de chaves](../../configuration/using/database-mapping.md#management-of-keys) .

## Atributos (Campos) {#attributes--fields-}

Os atributos permitem definir os campos que compõem o objeto de dados. Você pode usar o **[!UICONTROL Insert]** botão na barra de ferramentas da edição do esquema para soltar modelos de atributos vazios no seu XML onde está o cursor. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

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

   Para exibir uma tabela que lista os mapeamentos dos tipos de dados gerados pelo Adobe Campaign para os diferentes sistemas de gerenciamento de banco de dados, consulte a seção [Mapeamento dos tipos de dados](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) do Adobe Campaign/DBMS.

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

>[!CAUTION]
>
>Embora a maioria dos atributos esteja vinculada de acordo com uma cardinalidade de 1 a 1 a um campo físico do banco de dados, esse não é o caso dos campos XML ou computados.\
>Um campo XML é armazenado em um campo de memorando (&quot;mData&quot;) da tabela.\
>Entretanto, um campo calculado é criado dinamicamente cada vez que uma consulta é iniciada, portanto, só existe na camada aplicativa.

## Links {#links}

Os links são alguns dos últimos elementos no elemento principal do esquema. Eles definem como todos os diferentes esquemas em seu caso se relacionam entre si.

Os links são declarados no esquema que contém a chave **** estrangeira da tabela à qual estão vinculados.

Há três tipos de cardinalidade: 1-1, 1-N e N-N. É o tipo 1-N usado por padrão.

### Exemplos {#examples-1}

Um exemplo de um link 1-N entre a tabela do destinatário (esquema predefinido) e uma tabela de transações personalizadas:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Um exemplo de um link 1-1 entre um esquema personalizado &quot;Carro&quot; (no namespace &quot;cus&quot;) e a tabela do destinatário:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Exemplo de uma associação externa entre a tabela do destinatário e uma tabela de endereços com base no endereço de email e não em uma chave primária:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Aqui, &quot;xpath-dst&quot; corresponde à chave primária no esquema de destino e &quot;xpath-src&quot; corresponde à chave estrangeira no esquema de origem.

## Audit trail {#audit-trail}

Um elemento útil que você pode querer incluir na parte inferior do esquema é um elemento de rastreamento (Trilha de auditoria).

Use o exemplo abaixo para incluir campos relacionados à data de criação, o usuário que criou os dados, a data e o autor da última modificação para todos os dados na tabela:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Atualização da estrutura do banco de dados {#updating-the-database-structure}

Quando as alterações forem concluídas e salvas, todas as alterações que possam afetar a estrutura SQL deverão ser aplicadas ao banco de dados. Para fazer isso, use o assistente de atualização de banco de dados.

![](assets/schemaextension_getting_started_3.png)

Para obter mais informações, consulte a seção [Atualização da estrutura](../../configuration/using/updating-the-database-structure.md) do banco de dados.

>[!NOTE]
>
>Quando as modificações não afetam a estrutura do banco de dados, você só precisa regenerar esquemas. Para fazer isso, selecione os esquemas a serem atualizados, clique com o botão direito do mouse e escolha **[!UICONTROL Actions > Regenerate selected schemas...]** . For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.

