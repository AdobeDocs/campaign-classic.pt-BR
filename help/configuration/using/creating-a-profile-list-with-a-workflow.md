---
product: campaign
title: Criação de uma lista de perfis com base em um fluxo de trabalho
description: Saiba como criar uma lista de perfis em um workflow
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 14%

---

# Criação de uma lista de perfis com base em um fluxo de trabalho{#creating-a-profile-list-with-a-workflow}

![](../../assets/v7-only.svg)

Para criar um **[!UICONTROL List]** digite list com base na nova tabela de recipients, é necessário criar um workflow para construção do target que gerará a lista.

Para obter mais informações sobre listas no Campaign, consulte [esta seção](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Para criar um workflow para construção do target e atualizar recipients em uma tabela de recipients personalizada, siga as etapas abaixo:

1. Vá para o **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** nó do explorador.
1. Criação de um novo workflow para construção do target
1. Coloque um **Query** atividade seguida de uma **Atualizar lista** atividade .

   ![](assets/mapping_create_list_workflow01.png)

1. Clique duas vezes no botão **Query** e clique em **[!UICONTROL Edit the query]** para escolher um targeting dimension com base no schema da nova tabela de recipients (em nosso exemplo: **Individual**). Clique em **[!UICONTROL Finish]** para confirmar.

   ![](assets/mapping_create_list_workflow03.png)

1. Clique duas vezes no botão **Atualizar lista** e, em seguida, selecione a **[!UICONTROL Create the list if necessary (Computed name)]** botão de opção.

   ![](assets/mapping_create_list_workflow02.png)

1. Selecione a pasta de criação da nova lista.
1. Execute o workflow para criar a lista.
1. Visualize o resultado no nó da árvore que você selecionou durante a **[!UICONTROL List update]** atividade .

   O painel especifica o schema no qual a lista se baseia, conforme mostrado abaixo:

   ![](assets/mapping_list_view.png)
