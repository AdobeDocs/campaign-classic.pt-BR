---
title: Importação e exportação de públicos
seo-title: Importação e exportação de públicos
description: Importação e exportação de públicos
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Importação e exportação de públicos{#importing-and-exporting-audiences}

## Importação de um público {#importing-an-audience}

Você pode importar públicos/segmentos do Audience Manager ou do Serviço principal de pessoas para o Adobe Campaign através das listas de recipients.

1. Vá para o nó **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** no Adobe Campaign explorer.
1. Na barra de ações, selecione **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. In the window that opens, click **[!UICONTROL Select a shared audience]** to go to the list of shared audiences/segments available from the other Adobe Experience Cloud solutions.
1. Selecione um público e confirme. As informações do público são concluídas automaticamente.

   Please note that to be able to import shared audience, you should be assigned the **[!UICONTROL Audience library]** product in the admin console and be an administrator in Audience Manager. Para obter mais informações, consulte a [documentação do console do administrador](https://helpx.adobe.com/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Select the AMC Data source from the **[!UICONTROL AMC Data source]** field to define the type of data expected.

   ![](assets/aam_import_audience_2.png)

1. Salve o público.

O público é importado por meio de um workflow técnico. A lista importada contém elementos que podem ser reconciliados usando a fonte de dados da AMC. Os elementos que não são reconhecidos pelo Adobe Campaign não são importados.

O processo de importação leva de 24 a 36 horas para sincronizar, quando os segmentos são importados diretamente do Serviço principal de pessoas ou do Audience Manager. Após esse período, é possível encontrar e usar seu novo público no Adobe Campaign.

>[!NOTE]
>
>Se você estiver importando públicos do Adobe Analytics para o Adobe Campaign, esses públicos precisam ser compartilhados primeiro no Serviço Principal de Pessoas ou no Audience Manager. Esse processo leva de 12 a 24 horas, e deve ser adicionado ao tempo de sincronização de 24 a 36 horas com o Campaign.
>
>Nesse caso específico, o período de compartilhamento de público pode durar até 60 horas. Para obter mais informações sobre o compartilhamento de público do Adobe Analytics no Serviço Principal de Pessoas e no Audience Manager, consulte esta [documentação](https://marketing.adobe.com/resources/help/en_US/mcloud/t_publish_audience_segment.html).

Os dados do público são substituídos completamente sempre quando sincronizados. Apenas segmentos podem ser importados. Dados granulares, incluindo pares chave-valor, características e regras não são compatíveis.

## Exportação de um público {#exporting-an-audience}

Você pode exportar um público do Adobe Campaign para o Audience Manager ou o Serviço Principal de Pessoas usando um workflow. Os processos para criar e usar um workflow são detalhados [neste documento](../../workflow/using/building-a-workflow.md). Os públicos exportados são salvos como segmentos no Serviço principal de pessoas:

1. Criação de um novo workflow para construção do target
1. Usando as diferentes atividades disponíveis, target de conjunto de recipients.
1. After the targeting, drag and drop an **[!UICONTROL Update shared audience]** activity, then open it.

   ![](assets/aam_export_example.png)

1. Define the audience that you want to export via the **[!UICONTROL Select a shared audience]** option. Na janela que abre, você pode selecionar um público existente ou criar um novo público.

   Se você selecionar um público existente, somente os novos registros serão adicionados ao público.

   To export your recipient list in a new audience, complete the **[!UICONTROL Segment name]** field then click **[!UICONTROL Create]** before selecting the newly created audience.

   Finish the operation by clicking the check symbol at the top right of the window, then the **[!UICONTROL OK]** button.

1. Select the **[!UICONTROL AMC Data source]** to specify the expected data type. O schema é determinado automaticamente.

   ![](assets/aam_export_audience_activity.png)

1. Salve o público.

O público é então exportado. A atividade de público salva tem duas transições de saída. A transição principal contém os recipients que foram exportados com êxito. A transição adicional contém os recipients que não puderam ser mapeados com uma ID de visitante ou ID declarada.

A sincronização entre o Adobe Campaign e o Serviço principal de pessoas leva de 24 a 36 horas. Após esse período, é possível encontrar seu novo público no Serviço principal de pessoas e reutilizá-lo em outras soluções da Adobe Experience Cloud. Para obter mais informações sobre como usar um público compartilhado do Adobe Campaign no Serviço principal de pessoas da Adobe, consulte esta [documentação](https://marketing.adobe.com/resources/help/en_US/mcloud/t_audience_create.html).

>[!NOTE]
>
>Para serem reconciliados, os registros devem ter uma ID da Adobe Experience Cloud (&#39;ID do visitante&#39; ou &#39;ID declarada&#39;). Os registros que não têm uma ID da Adobe Experience Cloud são ignorados ao exportar e importar públicos.

