---
product: campaign
title: Novo assistente de campo
description: Novo assistente de campo
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: ec774cc10a69a694b3c2bf5a6f662afd12a1435a
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Novo assistente de campo{#new-field-wizard}


Um assistente acessível via **[!UICONTROL Tools > Advanced > Add new fields]** permite adicionar um ou mais campos a uma tabela no banco de dados.

A validação do assistente atualiza o esquema de extensão da tabela a ser estendida e inicia o script SQL para modificar a estrutura física do banco de dados.

Esse assistente tem a vantagem de adicionar rapidamente um campo sem precisar saber a estrutura de um schema de dados.

A principal desvantagem é a limitação dos dados e as propriedades a serem estendidas.

As telas do assistente contêm as seguintes etapas:

1. A primeira página permite inserir o nome do schema a ser estendido e o namespace do schema de extensão onde as modificações serão salvas:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. A próxima página permite inserir as propriedades do campo a ser adicionado.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Para confirmar as alterações, clique no botão **[!UICONTROL Finish]**.

Um arquivo de extensão, chamado &quot;cus:recipient&quot; em nosso exemplo, é criado automaticamente e o script SQL correspondente é executado:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Por padrão, os campos adicionados são declarados com a propriedade **user** (com o valor &quot;true&quot;). Isso permite exibir e editar o campo no formulário de entrada do schema estendido usando um controle do tipo &quot;treeEdit&quot; (consulte Formulário de entrada).
