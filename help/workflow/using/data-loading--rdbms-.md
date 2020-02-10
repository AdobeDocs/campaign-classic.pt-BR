---
title: Carregamento de dados (RDBMS)
seo-title: Carregamento de dados (RDBMS)
description: Carregamento de dados (RDBMS)
seo-description: null
page-status-flag: never-activated
uuid: d5ec30f2-398a-4b16-9232-924437da146a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a128caac-5740-4dac-b14d-1d2fcef3cc69
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Carregamento de dados (RDBMS){#data-loading-rdbms}

The **[!UICONTROL Data loading (RDBMS)]** activity lets you access this external database directly and to collect only the data required for targeting.

Para melhorar o desempenho, recomendamos o uso da atividade de query (onde os dados de um banco de dados externo podem ser usados). Para obter mais informações, consulte [Acesso a um banco de dados externo (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

A operação é como descrita a seguir:

1. Selecione a fonte de dados da lista e digite o nome da tabela com os dados a serem extraídos.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   O nome da tabela inserido no campo correspondente é usado como um template para coletar dados no banco de dados externo. O nome da tabela processada pelo workflow pode ser calculado ou transmitido pela transição de entrada da atividade de carregamento de dados. Para selecionar a tabela a ser usada, clique no **[!UICONTROL Advanced..]**. e selecione a opção **[!UICONTROL Specified in the transition]** ou **[!UICONTROL Explicit]** .

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Click the **[!UICONTROL Select the columns to extract...]** link to choose the data to be collected in the database.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Você pode definir um filtro nesses dados. To do this, click the **[!UICONTROL Edit query....]** link.

   Os dados coletados desta forma podem ser usados durante o ciclo de vida do workflow.

