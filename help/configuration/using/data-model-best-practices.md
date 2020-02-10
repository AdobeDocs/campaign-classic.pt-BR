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
source-git-commit: 620724e283215df1fb3f10bd0211652b36284b57

---


# Práticas recomendadas do modelo de dados{#data-model-best-practices}

Abaixo estão algumas práticas recomendadas que devem ser seguidas ao projetar seu modelo de dados usando tabelas grandes e junções complexas.

* Ao usar tabelas de destinatários personalizadas adicionais, verifique se você tem uma tabela de log dedicada para cada mapeamento de entrega.
* Reduza o número de colunas, principalmente identificando as que não são usadas.
* Otimize as relações do modelo de dados evitando junções complexas, como junções em várias condições e/ou em várias colunas.
* Para teclas de junção, sempre use dados numéricos em vez de sequências de caracteres.
* Reduza o máximo possível a profundidade da retenção de registros. Se precisar de um histórico mais profundo, você pode agregar computação e/ou manipular tabelas de log personalizadas para armazenar um histórico maior.

Para obter práticas recomendadas mais detalhadas sobre como otimizar o design do banco de dados para volumes maiores, consulte Práticas recomendadas [do modelo de dados do](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html)Campaign Classic.
