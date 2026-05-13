---
product: campaign
title: Carregamento de dados (RDBMS)
description: Saiba mais sobre a atividade do fluxo de trabalho de carregamento de dados (RDBMS)
feature: Workflows, Data Management Activity
hide: true
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
TQID: https://experienceleague.adobe.com/w7MFQZpUw-a0SIp634sptKz2VKm2MTZisjmN3VLDt2g
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a658c786-869b-4194-a780-2594d663adda
topic_v2: id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 187
ht-degree: 100%

---

# Carregamento de dados (RDBMS){#data-loading-rdbms}



A atividade **[!UICONTROL Data loading (RDBMS)]** permite acessar esse banco de dados externo diretamente e coletar apenas os dados necessários para o direcionamento.

Para melhorar o desempenho, recomendamos o uso da atividade de consulta (onde os dados de um banco de dados externo podem ser usados). Para obter mais informações, consulte [Acesso a um banco de dados externo (FDA)](accessing-an-external-database-fda.md).

A operação é como descrita a seguir:

1. Selecione a fonte de dados da lista e digite o nome da tabela com os dados a serem extraídos.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   O nome da tabela inserido no campo correspondente é usado como um modelo para coletar dados no banco de dados externo. O nome da tabela processada pelo fluxo de trabalho pode ser calculado ou transmitido pela transição de entrada da atividade de carregamento de dados. Para selecionar a tabela a ser usada, clique no link **[!UICONTROL Advanced..]**. e selecione a opção **[!UICONTROL Specified in the transition]** ou **[!UICONTROL Explicit]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Clique no link **[!UICONTROL Select the columns to extract...]** para escolher os dados que serão coletados no banco de dados.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Você pode definir um filtro nesses dados. Para fazer isso, clique em **[!UICONTROL Edit query....]**.

   Os dados coletados desta forma podem ser usados durante o ciclo de vida do fluxo de trabalho.
