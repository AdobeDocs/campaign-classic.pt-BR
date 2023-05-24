---
product: campaign
title: Sobre a edição de esquema
description: Introdução à edição de esquema
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 10%

---

# Sobre a edição de esquema{#about-schema-edition}

A Adobe Campaign emprega esquemas de dados para:

* Definir como os objetos de dados no aplicativo estão vinculados às tabelas de banco de dados subjacentes.
* Definir links entre os diferentes objetos de dados no aplicativo Campaign.
* Definir e descrever os campos individuais incluídos em cada objeto.

Para obter uma melhor compreensão das tabelas integradas do Campaign e sua interação, consulte [nesta seção](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/data-model/about-data-model.html?lang=pt-BR).

## Extensão ou criação de esquemas {#extending-or-creating-schemas}

Para adicionar um campo, índice ou outro elemento a um dos esquemas de dados principais no Campaign, como a tabela de recipients (nms:recipient), é necessário estender esse esquema. Para obter mais informações, consulte [Extensão de um schema](../../configuration/using/extending-a-schema.md) seção.

Para adicionar um tipo de dados totalmente novo que não existe pronto para uso no Adobe Campaign (uma tabela de contratos, por exemplo), você pode criar um esquema personalizado diretamente. Para obter mais informações, consulte [Esquemas de dados](../../configuration/using/data-schemas.md) seção.

![](assets/schemaextension_getting_started_1.png)

Depois de estender ou criar um esquema para trabalhar, a prática recomendada é definir seus elementos de conteúdo XML na mesma ordem em que aparecem abaixo.

## Enumerações {#enumerations}

As enumerações são definidas primeiro, antes do elemento principal do esquema. Eles permitem exibir valores em uma lista para restringir as opções que o usuário tem para um determinado campo.

Exemplo:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

Ao definir campos, é possível usar essa enumeração da seguinte maneira:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>Você também pode empregar enumerações gerenciadas pelo usuário (geralmente em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ) para especificar os valores de um determinado campo. Elas são enumerações globais efetivamente e uma opção melhor se sua enumeração puder ser usada fora do esquema específico em que você está trabalhando.

Para saber mais sobre enumerações, consulte o [Enumerações](../../configuration/using/schema-structure.md#enumerations) e [`<enumeration>` element](../../configuration/using/schema/enumeration.md) seções.

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

A variável **xpath** O atributo aponta para o campo no esquema que você deseja indexar.

>[!IMPORTANT]
>
>É importante lembrar que os ganhos de desempenho de leitura de consulta SQL fornecidos por índices também vêm com uma ocorrência de desempenho na gravação de registros. Portanto, os índices devem ser usados com precaução.

Para obter mais informações sobre índices, consulte [Campos indexados](../../configuration/using/database-mapping.md#indexed-fields) seção.

## Chaves {#keys}

Cada tabela deve ter pelo menos uma chave e, com frequência, é estabelecida automaticamente no elemento principal do esquema usando o **@autopk=true** atributo definido como &quot;true&quot;.

A chave primária também pode ser definida usando o **interno** atributo.

Exemplo:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

Neste exemplo, em vez de permitir que **@autopk** atributo criar uma chave primária padrão chamada &quot;id&quot; estamos especificando nossa própria chave primária &quot;householdId&quot;.

>[!IMPORTANT]
>
>Ao criar um novo schema ou durante uma extensão de schema, você precisa manter o mesmo valor de sequência da chave primária (@pkSequence) para todo o schema.

Para saber mais sobre as teclas, consulte o [Gerenciamento de chaves](../../configuration/using/database-mapping.md#management-of-keys) seção.

## Atributos (Campos) {#attributes--fields-}

Os atributos permitem definir os campos que compõem seu objeto de dados. Você pode usar o **[!UICONTROL Insert]** botão na barra de ferramentas da edição do esquema para soltar modelos de atributos vazios no XML onde o cursor está. Para obter mais informações, consulte [Esquemas de dados](../../configuration/using/data-schemas.md) seção.

![](assets/schemaextension_getting_started_2.png)

A lista completa de atributos está disponível no [`<attribute>` element](../../configuration/using/schema/attribute.md) seção. Estes são alguns dos atributos usados com mais frequência:

* **@advanced**
* **@dataPolicy**
* **@padrão**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@required**
* **@ref**
* **@xml**
* **@tipo**

   Para exibir uma tabela listando os mapeamentos para os tipos de dados gerados pelo Adobe Campaign para os diferentes sistemas de gerenciamento de banco de dados, consulte [Mapeamento dos tipos de dados do Adobe Campaign/DBMS](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) seção.

Para obter mais informações sobre cada atributo, consulte a [Descrição do atributo](../../configuration/using/schema/attribute.md) seção.

### Exemplos {#examples}

Exemplo de definição de um valor padrão:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Exemplo de uso de um atributo comum como modelo para um campo também marcado como obrigatório:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Exemplo de um campo calculado que está oculto usando o **@advanced** atributo:

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

Exemplo de um campo XML também armazenado em um campo SQL e que tem um **@dataPolicy** atributo.

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Embora a maioria dos atributos seja vinculada de acordo com uma cardinalidade 1-1 a um campo físico do banco de dados, esse não é o caso para os campos XML ou os campos calculados.\
>Um campo XML é armazenado em um campo de memorando (&quot;mData&quot;) da tabela.\
>No entanto, um campo calculado é criado dinamicamente sempre que uma consulta é iniciada, portanto, ele só existe na camada do aplicativo.

## Links {#links}

Os links são alguns dos últimos elementos no elemento principal do esquema. Elas definem como todos os diferentes esquemas na sua instância se relacionam entre si.

Os links são declarados no esquema que contém a variável **chave estrangeira** da tabela à qual está vinculado.

Há três tipos de cardinalidade: 1-1, 1-N e N-N. É o tipo 1-N usado por padrão.

### Exemplos {#examples-1}

Um exemplo de um link 1-N entre a tabela do recipient (schema pronto para uso) e uma tabela de transações personalizadas:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Um exemplo de um link 1-1 entre um schema personalizado &quot;Car&quot; (no namespace &quot;cus&quot;) e a tabela de recipients:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Exemplo de uma associação externa entre a tabela de recipients e uma tabela de endereços com base no endereço de email e não em uma chave primária:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Aqui, &quot;xpath-dst&quot; corresponde à chave primária no esquema de destino e &quot;xpath-src&quot; corresponde à chave externa no esquema de origem.

## Trilha de auditoria {#audit-trail}

Um elemento útil que você pode querer incluir na parte inferior do esquema é um elemento de rastreamento (Trilha de auditoria).

Use o exemplo abaixo para incluir campos relacionados à data de criação, ao usuário que criou os dados, à data e ao autor da última modificação para todos os dados na tabela:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Atualização da estrutura do banco de dados {#updating-the-database-structure}

Depois que as alterações forem concluídas e salvas, qualquer alteração que possa afetar a estrutura SQL precisará ser aplicada ao banco de dados. Para fazer isso, use o assistente de atualização de banco de dados.

![](assets/schemaextension_getting_started_3.png)

Para obter mais informações, consulte a seção [Atualização da estrutura do banco de dados](../../configuration/using/updating-the-database-structure.md).

>[!NOTE]
>
>Quando as modificações não afetam a estrutura do banco de dados, você só precisa gerar novamente os esquemas. Para fazer isso, selecione os esquemas a serem atualizados, clique com o botão direito do mouse e escolha **[!UICONTROL Actions > Regenerate selected schemas...]** . Para obter mais informações, consulte [Regeneração de schemas](../../configuration/using/regenerating-schemas.md) seção.
