---
product: campaign
title: Carregamento de dados (RDBMS)
description: Saiba mais sobre a atividade do workflow de carregamento de dados (RDBMS)
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 100%

---

# Carregamento de dados (RDBMS){#data-loading-rdbms}

![](../../assets/common.svg)

A atividade **[!UICONTROL Data loading (RDBMS)]** permite acessar esse banco de dados externo diretamente e coletar apenas os dados necessários para o direcionamento.

Para melhorar o desempenho, recomendamos o uso da atividade de query (onde os dados de um banco de dados externo podem ser usados). Para obter mais informações, consulte [Acesso a um banco de dados externo (FDA)](accessing-an-external-database--fda-.md).

A operação é como descrita a seguir:

1. Selecione a fonte de dados da lista e digite o nome da tabela com os dados a serem extraídos.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   O nome da tabela inserido no campo correspondente é usado como um template para coletar dados no banco de dados externo. O nome da tabela processada pelo workflow pode ser calculado ou transmitido pela transição de entrada da atividade de carregamento de dados. Para selecionar a tabela a ser usada, clique no link **[!UICONTROL Advanced..]**. e selecione a opção **[!UICONTROL Specified in the transition]** ou **[!UICONTROL Explicit]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Clique no link **[!UICONTROL Select the columns to extract...]** para escolher os dados que serão coletados no banco de dados.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Você pode definir um filtro nesses dados. Para fazer isso, clique em **[!UICONTROL Edit query....]**.

   Os dados coletados desta forma podem ser usados durante o ciclo de vida do workflow.
