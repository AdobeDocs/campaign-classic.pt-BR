---
solution: Campaign Classic
product: campaign
title: Editar esquema
description: Saiba mais sobre a atividade de workflow editar esquema
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '115'
ht-degree: 100%

---

# Editar esquema{#edit-schema}

Os dados podem ser transformados, normalizados e, se necessário, enriquecidos no workflow utilizando a atividade **[!UICONTROL Edit schema]**. Geralmente é usado para normalizar a estrutura de dados: é possível renomear as colunas de saída ou modificar o conteúdo, calculando os valores médios de um campo ou agregado.

Essa atividade não altera os dados na tabela de trabalho, altera apenas seu schema, ou seja, o modo de exibição lógico dos dados.

![](assets/wf_manipulation_box.png)

Também é possível criar associações com outras tabelas de trabalho, por meio da guia **[!UICONTROL Links]**.

![](assets/wf_manipulation_box_link_tab.png)

A seção inferior permite configurar a lista de condições de associação, isto é, os critérios utilizados para reconciliar os dados a partir das duas tabelas.
