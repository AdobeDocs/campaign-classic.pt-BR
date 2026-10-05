---
product: campaign
title: Criação de uma lista de perfis com base em um fluxo de trabalho
description: Saiba como criar uma lista de perfis em um workflow
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
TQID: 'https://experienceleague.adobe.com/km2D2qnUAdgDCauLUYcWSC-J567twPEyvaZBsLDAOKA'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 14%
---
# Criação de uma lista de perfis com base em um fluxo de trabalho{#creating-a-profile-list-with-a-workflow}


Para criar uma lista do tipo **[!UICONTROL List]** com base na nova tabela de destinatários, é necessário criar um fluxo de trabalho de direcionamento que gerará a lista.

Para obter mais informações sobre listas no Campaign, consulte [esta seção](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Conheça este recurso no vídeo](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Para criar um workflow de direcionamento e atualizar recipients em uma tabela de recipients personalizada, siga as etapas abaixo:

1. Vá para o nó **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** do explorador.
1. Criação de um novo fluxo de trabalho de segmentação
1. Coloque uma atividade **Query** seguida por uma atividade **List update**.

   ![](assets/mapping_create_list_workflow01.png)

1. Clique duas vezes na atividade **Query** e clique em **[!UICONTROL Edit the query]** para escolher um targeting dimension com base no esquema da nova tabela de recipients (em nosso exemplo: **Individual**). Clique em **[!UICONTROL Finish]** para confirmar.

   ![](assets/mapping_create_list_workflow03.png)

1. Clique duas vezes na atividade **List update** e selecione o botão de opção **[!UICONTROL Create the list if necessary (Computed name)]**.

   ![](assets/mapping_create_list_workflow02.png)

1. Selecione a pasta de criação para a nova lista.
1. Execute o workflow para criar a lista.
1. Exiba o resultado no nó da árvore que você selecionou durante a atividade **[!UICONTROL List update]**.

   O painel especifica o esquema no qual a lista se baseia, conforme mostrado abaixo:

   ![](assets/mapping_list_view.png)
