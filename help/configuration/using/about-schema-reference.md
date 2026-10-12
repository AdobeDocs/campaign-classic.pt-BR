---
product: campaign
title: Introdução a esquemas no Adobe Campaign
description: Saiba como trabalhar com esquemas e estender o modelo de dados conceituais do banco de dados do Adobe Campaign
feature: Schema Extension
role: Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
TQID: 'https://experienceleague.adobe.com/ikQVjdkvhTM-361S7mcpRYsuhpqjHxX-Y-9wdRCYldg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 16%
---
# Introdução a esquemas {#about-schema-reference}

## O que é um esquema {#what-is-a-schema}

Este capítulo descreve como configurar esquemas de extensão para estender o modelo de dados conceituais do banco de dados do Adobe Campaign.

Para entender melhor as tabelas integradas do Campaign e suas interações, consulte o [modelo de dados do Campaign Classic](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/datamodel){target="_blank"} (documentação do Campaign v8).

No Adobe Campaign, a estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Um **esquema** é um documento XML associado a uma tabela de banco de dados. Ele define a estrutura de dados e descreve a definição SQL da tabela:

* O nome da tabela
* Campos
* Índices
* Links com outras tabelas

Também descreve a estrutura XML usada para armazenar dados:

* Elementos e atributos
* Hierarquia de elementos
* Tipos de elemento e atributo
* Valores padrão
* Rótulos, descrições e outras propriedades.

Os esquemas permitem definir uma entidade no banco de dados. Há um esquema para cada entidade.

A ilustração a seguir mostra a localização dos esquemas no sistema de dados do Adobe Campaign:

![](assets/reference_schema_intro.png)

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8. Para saber mais sobre a sintaxe e a identificação de esquemas, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}
