---
solution: Campaign Classic
product: campaign
title: Características do schema
description: Características do schema
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---


# Características do schema{#schema-characteristics}

As características de um schema que faz referência a uma tabela existente são as seguintes:

* A Adobe Campaign não deve modificar objetos SQL relativos a tabelas existentes,
* Os nomes das tabelas e colunas devem ser explicitamente especificados,
* Os índices devem ser declarados.

>[!IMPORTANT]
>
>Não exclua os campos na tabela de recipient padrão, mesmo que eles não sejam úteis. Isso pode causar erros de comportamento no banco de dados Adobe Campaign.

## O atributo visualização {#the-view-attribute}

Os schemas de origem aceitam o atributo **visualização** para o elemento raiz **srcSchema** . Ele deve ser usado quando o Adobe Campaign é manipulado em tabelas personalizadas. O atributo **visualização=&quot;true&quot;** diz ao assistente de atualização da estrutura do banco de dados para ignorar esse schema. O aplicativo é, portanto, proibido de sincronizar a tabela, suas colunas e seus índices com o schema correspondente.

Quando esse atributo é definido como **true**, o schema é usado apenas para gerar query SQL para acessar os dados desta tabela.

## Nomes das tabelas e colunas {#names-of-tables-and-columns}

Quando tabelas são criadas pelo assistente de atualização de tabela, os nomes das tabelas e colunas são gerados automaticamente com base nos nomes dos respectivos schemas e atributos. No entanto, é possível forçar os nomes SQL a serem usados inserindo os seguintes atributos:

* **sqltable** dentro do elemento principal do schema, para especificar a tabela,
* **sqlname** em cada atributo, para especificar as colunas.

**Exemplo**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

Neste exemplo, se os nomes das tabelas e colunas não tivessem sido explicitamente especificados, o aplicativo teria usado **CusIndividual** para a tabela, **lastName** e **firstName** para as colunas.

Em um schema, é possível preencher apenas parte das colunas de uma tabela existente. As colunas não preenchidas não serão acessíveis ao usuário.

## Campos indexados {#indexed-fields}

Ao classificar os registros de uma lista no console do cliente, um melhor desempenho é obtido ao classificar em campos indexados. Declarar um índice em um schema faz com que o console exiba os campos indexados com uma linha vermelha sob a seta de ordem de classificação à esquerda do rótulo da coluna, como mostrado abaixo:

![](assets/s_ncs_integration_mapping_index.png)

Em um schema, um índice é definido da seguinte forma:

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

É por isso que é importante declarar os índices existentes da tabela personalizada no schema correspondente.

Um índice é declarado implicitamente para cada declaração de chave e link do schema de origem. A declaração de índice pode ser impedida especificando o atributo **noDbIndex=&quot;true&quot;** :

**Exemplo**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

