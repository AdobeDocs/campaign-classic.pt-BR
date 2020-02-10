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


# Uso da tabela Destinatário padrão{#default-recipient-table}

A tabela Destinatário predefinida no Adobe Campaign fornece um bom ponto de partida para a criação do modelo de dados. Ele tem vários campos predefinidos e links de tabela que podem ser facilmente estendidos. Isso é particularmente útil quando você está direcionando principalmente os destinatários, pois se encaixa em um modelo de dados simples centrado no destinatário.

Os benefícios do uso da tabela Destinatário padrão são os seguintes:

* Trabalhar prontamente com funcionalidades como assinaturas, listas de sementes, pesquisas, sociais e assim por diante.
* Fornecer um banco de dados de marketing com um modelo de dados centrado no destinatário.
* Implementação mais rápida.
* Manutenção fácil por meio de suporte e parceiros.

No entanto, é possível estender a tabela Destinatário, mas não para reduzir o número de campos ou links na tabela.

>[!IMPORTANT]
>
>É recomendável não excluir campos (mesmo que não sejam úteis) na tabela do destinatário, pois isso pode levar a erros nos módulos incorporados.

Além disso, como a tabela Destinatário é parte do produto, tanto a tabela quanto o formulário associado evoluem conforme o produto muda. Portanto, é necessária uma manutenção extra para verificar se as extensões ainda são válidas na atualização.
