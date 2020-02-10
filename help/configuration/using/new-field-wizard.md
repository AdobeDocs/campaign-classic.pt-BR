---
title: Assistente para novos campos
seo-title: Assistente para novos campos
description: Assistente para novos campos
seo-description: null
page-status-flag: never-activated
uuid: 2c8d35db-042a-47cf-a7a6-3bb63bf40d94
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6da65fb5-18a1-41a0-96d8-588e383f944b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Assistente para novos campos{#new-field-wizard}

Um assistente acessível por meio **[!UICONTROL Tools > Advanced > Add new fields]** permite adicionar um ou mais campos a uma tabela no banco de dados.

A validação do assistente atualiza o esquema de extensão da tabela a ser estendida e inicia o script SQL para modificar a estrutura física do banco de dados.

Esse assistente tem a vantagem de adicionar rapidamente um campo sem precisar conhecer a estrutura de um esquema de dados.

A principal desvantagem é a limitação dos dados e as propriedades a serem ampliadas.

As telas do assistente contêm as seguintes etapas:

1. A primeira página permite que você insira o nome do esquema a ser estendido e o namespace do esquema de extensão no qual as modificações serão salvas:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. A próxima página permite que você insira as propriedades do campo a ser adicionado.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Para confirmar as alterações, clique no **[!UICONTROL Finish]** botão.

Um arquivo de extensão, chamado &quot;cus:customer&quot; em nosso exemplo, é criado automaticamente e o script SQL correspondente é executado:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Por padrão, os campos adicionados são declarados com o **usuário** da propriedade (com o valor &quot;true&quot;). Isso permite exibir e editar o campo no formulário de entrada do esquema estendido usando um controle do tipo &quot;treeEdit&quot; (consulte Formulário de entrada).

