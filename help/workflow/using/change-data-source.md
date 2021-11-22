---
title: Alterar fonte de dados
description: Saiba mais sobre a atividade de Alteração da fonte de dados
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: 31483bdd2e0a2dd0676ef391c5484e4b778317c1
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 100%

---

# Alterar fonte de dados {#change-data-source}

>[!NOTE]
>
> A atividade **[!UICONTROL Change data source]** só está disponível com o pacote **[!UICONTROL Access to external data (Federated Data Access)]**. Para mais informações sobre pacotes incorporados do Adobe Campaign Classic, consulte esta [página](../../installation/using/installing-campaign-standard-packages.md).

A atividade **[!UICONTROL Change data source]** permite alterar a fonte de dados de um workflow **[!UICONTROL Working table]**. Isso oferece mais flexibilidade para gerenciar dados em diferentes fontes de dados, como FDA, FFDA e o banco de dados local.

O **[!UICONTROL Working table]** permite que o workflow do Adobe Campaign Classic manipule dados e compartilhe dados com as atividades do workflow.
Por padrão, a **[!UICONTROL Working table]** é criada no mesmo banco de dados da fonte de dados que consultamos.

Por exemplo, ao consultar a tabela **[!UICONTROL Profiles]**, armazenada no banco de dados em nuvem, você criará um **[!UICONTROL Working table]** no mesmo banco de dados em nuvem.
Para alterar isso, você pode adicionar a atividade **[!UICONTROL Change Data Source]** e escolher uma fonte de dados diferente para sua **[!UICONTROL Working table]**.

Observe que, ao usar a atividade **[!UICONTROL Change Data Source]**, será necessário alternar de volta para o banco de dados em nuvem para continuar a execução do workflow.

Para usar a atividade **[!UICONTROL Change Data Source]**:

1. Criar um workflow.

1. Consulte seus recipients alvos com uma atividade de **[!UICONTROL Query]**.

   Para mais informações sobre a atividade **[!UICONTROL Query]**, consulte esta [página](../../workflow/using/query.md#creating-a-query).

1. Na guia **[!UICONTROL Targeting]** , adicione uma atividade **[!UICONTROL Change data source]** .

   ![](assets/change-data-source.png)

1. Clique duas vezes na atividade **[!UICONTROL Change data source]** para selecionar **[!UICONTROL Default data source]**.

   A tabela de trabalho, que contém o resultado do query, é então movida para o banco de dados PostgreSQL padrão.

   ![](assets/change-data-source_2.png)

1. Na guia **[!UICONTROL Actions]**, arraste e solte uma atividade **[!UICONTROL JavaScript code]** para executar operações unitárias na tabela de trabalho.

   Para mais informações sobre a atividade **[!UICONTROL JavaScript code]**, consulte a página [Código JavaScript e código JavaScript avançado](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

1. Adicione outra atividade **[!UICONTROL Change data source]** para alternar de volta para o banco de dados em nuvem.

1. Clique duas vezes na atividade e selecione **[!UICONTROL Active FDA external account]**. Em seguida, selecione a conta externa **[!UICONTROL External database]** correspondente.

   ![](assets/change-data-source_3.png)

1. Agora, você pode iniciar o seu workflow.
