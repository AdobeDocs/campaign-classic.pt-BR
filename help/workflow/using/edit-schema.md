---
title: Editar schema
seo-title: Editar schema
description: Editar schema
seo-description: null
page-status-flag: never-activated
uuid: abd77902-98b7-4ab7-a240-dd6b3bb247bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 733576d2-505f-4598-89eb-a10e7331bf7e
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Editar schema{#edit-schema}

Os dados podem ser transformados, normalizados e, se necessário, enriquecidos no workflow utilizando a atividade **[!UICONTROL Edit schema]**. Geralmente é usado para normalizar a estrutura de dados: é possível renomear as colunas de saída ou modificar o conteúdo, calculando os valores médios de um campo ou agregado.

Essa atividade não altera os dados na tabela de trabalho, altera apenas seu schema, ou seja, o modo de exibição lógico dos dados.

![](assets/wf_manipulation_box.png)

Também é possível criar associações com outras tabelas de trabalho, por meio da guia **[!UICONTROL Links]**.

![](assets/wf_manipulation_box_link_tab.png)

A seção inferior permite configurar a lista de condições de associação, isto é, os critérios utilizados para reconciliar os dados a partir das duas tabelas.
