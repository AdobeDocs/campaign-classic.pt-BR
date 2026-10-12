---
product: campaign
title: Gerenciamento de chaves em esquemas de dados
description: Entender o gerenciamento de chaves em esquemas de dados
feature: Configuration, Instance Settings
role: Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
TQID: 'https://experienceleague.adobe.com/dErbfzRabMls-5x1S3eRZO94Kqcz9LRh3PaUhVD5zAU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 11%
---
# Gerenciamento de chaves em esquemas {#management-of-keys}

Cada tabela associada a um schema de dados deve ter pelo menos uma chave para identificar um registro em uma tabela. Esta página descreve a chave incremental automática usada nas tabelas do Campaign Classic v7.

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8. Para saber mais sobre o gerenciamento de chaves, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}

## Chave incremental automática {#auto-incremental-key}

A chave primária da maioria das tabelas do Adobe Campaign é um inteiro longo de 32 bits gerado automaticamente pelo mecanismo de banco de dados. O cálculo do valor da chave depende de uma sequência (por padrão, a função SQL **XtkNewId**) gerando um número exclusivo no banco de dados inteiro. O conteúdo da chave é inserido automaticamente ao inserir o registro.

A vantagem de uma chave incremental é que ela fornece uma chave técnica não modificável para as associações entre tabelas. Além disso, essa chave não ocupa muita memória porque usa um inteiro de dois bytes.

Você pode especificar no esquema de origem o nome da sequência a ser usada com o atributo **pkSequence**. Se este atributo não for fornecido no esquema de origem, a sequência padrão **XtkNewId** será usada. O aplicativo usa sequências dedicadas para os esquemas **nms:broadLog** e **nms:trackingLog** (**NmsBroadLogId** e **NmsTrackingLogId**, respectivamente) porque essas são as tabelas que contêm mais registros.

A partir do ACC 18.10, **XtkNewId** não é mais o valor padrão para a sequência nos esquemas prontos para uso. Agora é possível criar um esquema ou estender um esquema existente com uma sequência dedicada.

>[!IMPORTANT]
>
>Ao criar um novo esquema ou durante uma extensão de esquema, você precisa manter o mesmo valor de sequência da chave primária (@pkSequence) para todo o esquema.

Uma sequência referenciada em um esquema Adobe Campaign (**NmsTrackingLogId**, por exemplo) deve ser associada a uma função SQL que retorna o número de IDs nos parâmetros, separadas por vírgulas. Esta função deve ser chamada de **GetNew** XXX **Ids**, onde **XXX** é o nome da sequência (**GetNewNmsTrackingLogIds**, por exemplo). Exiba os arquivos **postgres-nms.sql**, **mssql-nms.sql** ou **oracle-nms.sql** fornecidos com o aplicativo no diretório **datakit/nms/eng/sql/** para recuperar o exemplo de criação de sequência &#39;NmsTrackingLogId&#39; para cada mecanismo de banco de dados.

Para declarar uma chave exclusiva, preencha o atributo **autopk** (com o valor &quot;true&quot;) no elemento principal do esquema de dados.

**Exemplo**:

Declaração de uma chave incremental no schema de origem:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

O schema gerado:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Além da definição da chave e de seu índice, um campo numérico chamado &quot;id&quot; foi adicionado ao esquema estendido para conter a chave primária gerada automaticamente.

>[!IMPORTANT]
>
>Um registro com uma chave primária definida como 0 é inserido automaticamente ao criar a tabela. Esse registro é usado para evitar associações externas, que não são eficazes em tabelas de volume. Por padrão, todas as chaves estrangeiras são inicializadas com o valor 0 para que um resultado sempre possa ser retornado na associação quando o item de dados não for preenchido.


## Saiba mais

Navegue pelos links a seguir para saber mais:

* [Introdução a esquemas](about-schema-reference.md)
* [Estrutura de esquema](schema-structure.md)
* [Mapeamento de banco de dados](database-mapping.md)
* [Gerenciamento de links](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (documentação do Campaign v8)
* [Modelo de dados do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/developer/datamodel){target="_blank"} (documentação do Campaign v8)
