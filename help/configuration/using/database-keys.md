---
product: campaign
title: Gerenciamento de chaves em esquemas de dados
description: Entender o gerenciamento de chaves em esquemas de dados
feature: Configuration, Instance Settings
role: Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 6%

---

# Gerenciamento de chaves em esquemas {#management-of-keys}

Cada tabela associada a um schema de dados deve ter pelo menos uma chave para identificar um registro em uma tabela.

Uma chave é declarada pelo elemento principal do schema de dados.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Uma chave é conhecida como &quot;chave primária&quot; quando é a primeira no esquema a ser preenchida, ou se contém o atributo `internal` definido como &quot;true&quot;.

As seguintes regras se aplicam às chaves:

* Uma chave pode fazer referência a um ou mais campos na tabela
* Um índice exclusivo é declarado implicitamente para cada definição de chave. É possível impedir a criação de um índice na chave definindo o atributo `noDbIndex` como &quot;true&quot;.

>[!NOTE]
>
>* Como padrão, as chaves são os elementos declarados do elemento principal do esquema após a definição dos índices.
>
>* As chaves são criadas durante o mapeamento de tabela (padrão ou FDA), o Adobe Campaign encontra índices exclusivos.

**Exemplo**:

* Adicionar uma chave ao endereço de email e à cidade:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  O schema gerado:

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
     <dbindex name="email" unique="true">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
     </dbindex>    
  
     <key name="email">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="location/@city"/>    
     </key>    
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* Adicionar uma chave primária ou interna no campo de nome &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  O schema gerado:

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
      <key name="email">      
        <keyfield xpath="@email"/>    
      </key>    
  
      <dbindex name="id" unique="true">      
        <keyfield xpath="@id"/>    
      </dbindex>    
  
      <key internal="true" name="id">      
       <keyfield xpath="@id"/>    
      </key>    
  
      <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

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
* [Gerenciamento de link](database-links.md)
* [Modelo de dados do Campaign](about-data-model.md)
