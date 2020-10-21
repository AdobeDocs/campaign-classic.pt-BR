---
title: ' Criação de uma lista de perfis com base em um workflow '
description: Saiba como criar uma lista de perfil em um fluxo de trabalho
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
translation-type: tm+mt
source-git-commit: c2c0609619e0cc81444d089850add6dec5de93fd
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 14%

---


#  Criação de uma lista de perfis com base em um workflow {#creating-a-profile-list-with-a-workflow}

Para criar uma lista de **[!UICONTROL List]** tipo com base na nova tabela de recipient, é necessário criar um fluxo de trabalho de definição de metas que gere a lista.

Para obter mais informações sobre listas na Campanha, consulte [esta seção](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Para criar um fluxo de trabalho de definição de metas e atualizar recipient em uma tabela de recipient personalizada, siga as etapas abaixo:

1. Vá para o **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** nó do explorador.
1. Criação de um novo workflow para construção do target
1. Coloque uma atividade de **Query** seguida de uma atividade de atualização **de** Lista.

   ![](assets/mapping_create_list_workflow01.png)

1. Clique na atividade do **Query** e, em seguida, clique **[!UICONTROL Edit the query]** para escolher um targeting dimension baseado no schema da nova tabela do recipient (em nosso exemplo: **Individual**). Clique em **[!UICONTROL Finish]** para confirmar.

   ![](assets/mapping_create_list_workflow03.png)

1. Clique com o duplo do mouse na atividade de atualização **da** Lista e selecione o botão de opção **[!UICONTROL Create the list if necessary (Computed name)]** .

   ![](assets/mapping_create_list_workflow02.png)

1. Selecione a pasta de criação para a nova lista.
1. Execute o fluxo de trabalho para criar a lista.
1. Visualização o resultado no nó da árvore que você selecionou durante a **[!UICONTROL List update]** atividade.

   O painel especifica o schema no qual a lista se baseia, como mostrado abaixo:

   ![](assets/mapping_list_view.png)


