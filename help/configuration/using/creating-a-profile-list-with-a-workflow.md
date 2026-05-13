---
product: campaign
title: Criação de uma lista de perfis com base em um fluxo de trabalho
description: Saiba como criar uma lista de perfis em um workflow
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
TQID: https://experienceleague.adobe.com/km2D2qnUAdgDCauLUYcWSC-J567twPEyvaZBsLDAOKA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 18%

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
