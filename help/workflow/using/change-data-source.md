---
title: Alterar fonte de dados
description: Saiba mais sobre a atividade Alterar fonte de dados
audience: workflow
content-type: reference
topic-tags: targeting-activities
source-git-commit: 9fc4add3f12e3f06b031c4969bd8409c67e4359e
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# Alterar fonte de dados {#change-data-source}

>[!NOTE]
>
> A atividade **[!UICONTROL Change data source]** só está disponível com o pacote **[!UICONTROL Access to external data (Federated Data Access)]**. Para obter mais informações sobre pacotes incorporados do Adobe Campaign Classic, consulte esta [página](../../installation/using/installing-campaign-standard-packages.md).

A atividade **[!UICONTROL Change data source]** permite alterar a fonte de dados de um workflow **[!UICONTROL Working table]**. Isso oferece mais flexibilidade para gerenciar dados em diferentes fontes de dados, como FDA, FDA e banco de dados local.

O **[!UICONTROL Working table]** permite que o workflow do Adobe Campaign Classic manipule dados e compartilhe dados com as atividades do workflow.
Por padrão, o **[!UICONTROL Working table]** é criado no mesmo banco de dados que a fonte de dados que consultamos.

Por exemplo, ao consultar a tabela **[!UICONTROL Profiles]** armazenada no banco de dados do Cloud, você criará um **[!UICONTROL Working table]** no mesmo banco de dados do Cloud.
Para alterar isso, você pode adicionar a atividade **[!UICONTROL Change Data Source]** para escolher uma fonte de dados diferente para seu **[!UICONTROL Working table]**.

Observe que, ao usar a atividade **[!UICONTROL Change Data Source]** , será necessário alternar de volta para o banco de dados do Cloud para continuar a execução do workflow.

Para usar a atividade **[!UICONTROL Change Data Source]**:

1. Criar um fluxo de trabalho.

1. Consulte seus recipients alvos com uma atividade **[!UICONTROL Query]** .

   Para obter mais informações sobre a atividade **[!UICONTROL Query]**, consulte esta [página](../../workflow/using/query.md#creating-a-query).

1. Na guia **[!UICONTROL Targeting]** , adicione uma atividade **[!UICONTROL Change data source]** .

   ![](assets/change-data-source.png)

1. Clique duas vezes na atividade **[!UICONTROL Change data source]** para selecionar **[!UICONTROL Default data source]**.

   A tabela de trabalho, que contém o resultado do query, é então movida para o banco de dados PostgreSQL padrão.

   ![](assets/change-data-source_2.png)

1. Na guia **[!UICONTROL Actions]** , arraste e solte uma atividade **[!UICONTROL JavaScript code]** para executar operações unitárias na tabela de trabalho.

   Para obter mais informações sobre a atividade **[!UICONTROL JavaScript code]**, consulte o [código JavaScript e a página Código JavaScript avançado](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) .

1. Adicione outra atividade **[!UICONTROL Change data source]** para alternar de volta para o banco de dados do Cloud.

1. Clique duas vezes na atividade e selecione **[!UICONTROL Active FDA external account]**, em seguida, a conta externa **[!UICONTROL External database]** correspondente.

   ![](assets/change-data-source_3.png)

1. Agora é possível iniciar o workflow.
