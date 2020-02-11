---
title: Criação de uma lista de perfis com um fluxo de trabalho
seo-title: Criação de uma lista de perfis com um fluxo de trabalho
description: Criação de uma lista de perfis com um fluxo de trabalho
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 681e6ec5fc9ed8c7e46af04f0ed62927b30e1b2e

---


# Criação de uma lista de perfis com um fluxo de trabalho{#creating-a-profile-list-with-a-workflow}

Para criar uma lista de **[!UICONTROL List]** tipos com base na nova tabela de destinatários, é necessário criar um fluxo de trabalho de definição de metas que gere a lista. Para obter mais informações sobre listas no Campaign, consulte [esta seção](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

1. Vá para o **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** nó do explorador.
1. Criação de um novo workflow para construção do target
1. Coloque uma atividade de **Consulta** seguida de uma atividade de atualização **** Lista.

   ![](assets/mapping_create_list_workflow01.png)

1. Clique duas vezes na atividade **Consulta** e, em seguida, clique **[!UICONTROL Edit the query]** para escolher uma dimensão de definição de metas com base no esquema da nova tabela de destinatários (em nosso exemplo: **Individual**). Click **[!UICONTROL Finish]** to confirm.

   ![](assets/mapping_create_list_workflow03.png)

1. Clique duas vezes na atividade de atualização **** Lista e selecione o botão de **[!UICONTROL Create the list if necessary (Computed name)]** opção.

   ![](assets/mapping_create_list_workflow02.png)

1. Selecione a pasta de criação para a nova lista.
1. Execute o fluxo de trabalho para criar a lista.
1. Visualize o resultado no nó da árvore selecionado durante a **[!UICONTROL List update]** atividade.

   O painel especifica o esquema no qual a lista se baseia, como mostrado abaixo:

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>Você também pode consultar o vídeo [Criação de uma lista de destinatários](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-list-of-recipients.html) .

