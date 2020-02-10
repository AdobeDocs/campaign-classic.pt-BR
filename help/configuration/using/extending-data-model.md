---
title: Uso da tabela Destinatário do Adobe Campaign Classic
description: Saiba como usar a tabela de destinatários pronta para uso no Adobe Campaign Classic ao projetar seu modelo de dados.
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
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Extensão do modelo de dados{#extending-data-model}

Ao iniciar com o Adobe Campaign, é necessário avaliar o modelo de dados padrão para verificar qual tabela é a mais adequada para armazenar seus dados de marketing.

Se relevante, você pode usar a tabela Destinatário padrão com os campos predefinidos, como descrito nesta [seção](../../configuration/using/default-recipient-table.md).

Se necessário, você pode estendê-lo com dois mecanismos:

* Estende uma tabela existente com novos campos. Por exemplo, você pode adicionar um novo campo &quot;Fidelidade&quot; à tabela Destinatário.
* Crie uma nova tabela, por exemplo, uma tabela &quot;Compra&quot; que lista todas as compras feitas por cada perfil do banco de dados e a vincula à tabela Destinatário.

Para obter mais informações sobre como configurar esquemas de extensão para estender o modelo de dados conceituais, consulte [Sobre a edição](../../configuration/using/about-schema-edition.md)do esquema.

>[!IMPORTANT]
>
>A extensão do modelo de dados está reservada para usuários avançados.
