---
product: campaign
title: Importação e exportação de públicos
description: Importação e exportação de públicos
feature: Audiences
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: ht
source-wordcount: '589'
ht-degree: 100%

---


# Importação e exportação de públicos{#importing-and-exporting-audiences}



## Importação de um público-alvo {#importing-an-audience}

É possível importar públicos-alvo e segmentos do Audience Manager para o Adobe Campaign por meio das listas de destinatários.

1. Acesse o nó **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** no explorer do Adobe Campaign.
1. Na barra de ações, selecione **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. Na janela que abre, clique em **[!UICONTROL Select a shared audience]** para abrir a lista de audiences/segmentos compartilhados disponíveis nas outras soluções da Adobe Experience Cloud.
1. Selecione um público e confirme. As informações do público são concluídas automaticamente.

   Observe que para poder importar público compartilhado, o produto **[!UICONTROL Audience library]** dever ter sido atribuído a você no console do administrador e você deve ser um administrador no Audience Manager. Para obter mais informações, consulte a [documentação do console do administrador](https://helpx.adobe.com/br/enterprise/admin-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Selecione a fonte de dados AMC no campo **[!UICONTROL AMC Data source]** para definir o tipo de dados esperado.

   ![](assets/aam_import_audience_2.png)

1. Salve o público.

O público é importado por meio de um workflow técnico. A lista importada contém elementos que podem ser reconciliados usando a fonte de dados da AMC. Os elementos que não são reconhecidos pelo Adobe Campaign não são importados.

O processo de importação leva de 24 a 36 horas para sincronizar quando os segmentos são importados diretamente do Audience Manager. Após esse período, é possível encontrar e usar seu novo público-alvo no Adobe Campaign.

>[!NOTE]
>
>Se estiver importando públicos-alvo do Adobe Analytics para o Adobe Campaign, eles precisam ser compartilhados primeiro no Audience Manager. Esse processo leva de 12 a 24 horas, e deve ser adicionado ao tempo de sincronização de 24 a 36 horas com o Campaign.
>
>Nesse caso específico, o período de compartilhamento de público pode durar até 60 horas. Para obter mais informações sobre o compartilhamento de público-alvo do Adobe Analytics no Audience Manager, consulte a [documentação do Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=pt-BR){target="_blank"}.

Os dados do público são substituídos completamente sempre quando sincronizados. Apenas segmentos podem ser importados. Dados granulares, incluindo pares chave-valor, traços e regras não são compatíveis.

## Exportação de um público-alvo {#exporting-an-audience}

É possível exportar um público-alvo do Adobe Campaign para o Audience Manager usando um fluxo de trabalho. Os processos para criar e usar um fluxo de trabalho são detalhados [neste documento](../../workflow/using/building-a-workflow.md). Os públicos-alvo exportados são salvos como segmentos:

1. Criação de um novo workflow para construção do target
1. Usando as diferentes atividades disponíveis, target de conjunto de destinatários.
1. Depois do target, arraste e solte uma atividade **[!UICONTROL Update shared audience]** e depois a abra.

   ![](assets/aam_export_example.png)

1. Defina o público que deseja exportar por meio da opção **[!UICONTROL Select a shared audience]**. Na janela que abre, você pode selecionar um público existente ou criar um novo público.

   Se você selecionar um público existente, somente os novos registros serão adicionados ao público.

   Para exportar sua lista de destinatários para um novo público, preencha o campo **[!UICONTROL Segment name]** e depois clique em **[!UICONTROL Create]** antes de selecionar o público recém-criado.

   Conclua a operação clicando no símbolo de seleção na parte superior direita da janela e, em seguida, no botão **[!UICONTROL OK]**.

1. Selecione a **[!UICONTROL AMC Data source]** para especificar o tipo de dados esperado. O schema é determinado automaticamente.

   ![](assets/aam_export_audience_activity.png)

1. Salve o público.

O público é então exportado. A atividade de público salva tem duas transições de saída. A transição principal contém os destinatários que foram exportados com êxito. A transição adicional contém os destinatários que não puderam ser mapeados com uma ID de visitante ou ID declarada.

A sincronização entre soluções leva de 24 a 36 horas. Após esse período, é possível encontrar seu novo público-alvo e reutilizá-lo em outras soluções da Adobe Experience Cloud. Para obter mais informações sobre como usar um público-alvo compartilhado do Adobe Campaign, consulte esta [documentação](https://experienceleague.adobe.com/pt-br/docs/core-services/interface/services/audiences/create){target="_blank"}.

>[!NOTE]
>
>Para serem reconciliados, os registros devem ter uma ID da Adobe Experience Cloud (&#39;ID do visitante&#39; ou &#39;ID declarada&#39;). Os registros que não têm uma ID da Adobe Experience Cloud são ignorados ao exportar e importar públicos.
