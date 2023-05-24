---
product: campaign
title: Características do esquema
description: Características do esquema
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# Características do esquema{#schema-characteristics}



As características de um schema que faz referência a uma tabela existente são as seguintes:

* O Adobe Campaign não deve modificar objetos SQL em relação a tabelas existentes,
* Os nomes das tabelas e colunas devem ser especificados explicitamente,
* Os índices devem ser declarados.

>[!IMPORTANT]
>
>Não exclua campos na tabela de destinatários integrada, mesmo que eles sejam inúteis. Isso pode causar erros de comportamento no banco de dados do Adobe Campaign.

## O atributo de visualização {#the-view-attribute}

Os esquemas de origem aceitam o **exibir** atributo para o **srcSchema** elemento raiz. Ele deve ser usado quando o Adobe Campaign é manipulado em tabelas personalizadas. A variável **view=&quot;true&quot;** attribute informa ao assistente de atualização de estrutura de banco de dados para ignorar esse esquema. Portanto, o aplicativo está proibido de sincronizar a tabela, suas colunas e seus índices com o schema correspondente.

Quando este atributo é definido como **true**, o schema é usado apenas para gerar consultas SQL para acessar os dados desta tabela.

## Nomes de tabelas e colunas {#names-of-tables-and-columns}

Quando tabelas são criadas pelo assistente de atualização de tabela, os nomes de tabelas e colunas são gerados automaticamente com base nos nomes dos respectivos esquemas e atributos. No entanto, é possível forçar os nomes SQL a serem usados inserindo os seguintes atributos:

* **sqltable** no elemento principal do schema, para especificar a tabela,
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

Em um schema, é possível preencher apenas parte das colunas de uma tabela existente. Colunas não preenchidas não serão acessíveis ao usuário.

## Campos indexados {#indexed-fields}

Ao classificar os registros de uma lista no console do cliente, obtém-se melhor desempenho ao classificar em campos indexados. A declaração de um índice em um esquema faz com que o console exiba os campos indexados com uma linha vermelha sob a seta de ordem de classificação à esquerda do rótulo da coluna, conforme mostrado abaixo:

![](assets/s_ncs_integration_mapping_index.png)

Em um esquema, um índice é definido da seguinte maneira:

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

É por isso que é importante declarar índices existentes da tabela personalizada no schema correspondente.

Um índice é declarado implicitamente para cada declaração de chave e link do esquema de origem. A declaração de índice pode ser evitada especificando o **noDbIndex=&quot;true&quot;** atributo:

**Exemplo**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
