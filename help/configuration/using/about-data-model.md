---
title: Sobre o modelo de dados do Adobe Campaign Classic
description: Este documento descreve as noções básicas do modelo de dados do Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b7fa53a0463c5752a5fe4d11262dbf7b8ad77144

---


# Sobre o modelo de dados do Campaign Classic{#about-data-model}

Esta seção descreve as noções básicas do modelo de dados do Adobe Campaign Classic, para obter uma melhor compreensão das tabelas incorporadas do Campaign e de suas interações.

O modelo de dados conceituais do banco de dados do Adobe Campaign consiste em um conjunto de tabelas incorporadas e sua interação.

Para acessar a descrição de cada tabela, vá para **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso da lista e clique na **[!UICONTROL Documentation]** guia.

![](assets/data-model_documentation-tab.png)

Para obter mais informações sobre a descrição padrão do modelo de dados do Campaign Classic, consulte este [documento](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ele obedece a uma gramática específica do Adobe Campaign, chamada de esquema. Para obter mais informações sobre os esquemas do Adobe Campaign, leia esta [seção](../../configuration/using/about-schema-reference.md).

## Visão geral {#data-model-overview}

O Adobe Campaign depende de um banco de dados relacional que contém tabelas vinculadas.

A estrutura básica do modelo de dados do Adobe Campaign pode ser descrita da seguinte maneira.

## Tabela do destinatário {#recipient-table}

O modelo de dados depende de uma tabela principal que é, por padrão, a tabela Destinatário (**NmsRecipient**). Esta tabela permite armazenar todos os perfis de marketing.

Para obter mais informações sobre a tabela Destinatário, consulte esta [seção](../../configuration/using/default-recipient-table.md).

## Tabela de entrega {#delivery-table}

O modelo de dados também inclui uma peça dedicada a armazenar todas as atividades de marketing. Geralmente, é a tabela Entrega (**NmsDelivery**). Cada registro nesta tabela representa uma ação de entrega ou um modelo de entrega. Ele contém todos os parâmetros necessários para executar entregas, como destino, conteúdo etc.

## Tabelas de registros {#log-tables}

Outra parte do modelo de dados permite armazenar temporariamente todos os registros associados à execução das campanhas.

Todos os registros de entrega são mensagens enviadas para destinatários ou dispositivos em todos os canais. A tabela principal de registros de entrega (**NmsBroadLog**) contém os registros de entrega para todos os destinatários.
A tabela de registros de rastreamento principal (**NmsTrackingLog**) armazena os logs de rastreamento para todos os destinatários. Os registros de rastreamento se referem a reações de destinatários, como aberturas de email e cliques. Cada reação corresponde a um registro de acompanhamento.
Os registros de entrega e de rastreamento são excluídos após um determinado período, que é especificado no Adobe Campaign e pode ser modificado. Portanto, é altamente recomendável exportar os registros regularmente.

## Quadros técnicos {#technical-tables}

Por fim, parte do modelo de dados consiste em dados técnicos usados para o processo de aplicação, incluindo operadores e direitos de usuário (**NmsGroup**), pastas (**XtkFolder**).