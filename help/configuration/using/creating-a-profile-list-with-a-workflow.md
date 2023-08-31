---
product: campaign
title: Criação de uma lista de perfis com base em um fluxo de trabalho
description: Saiba como criar uma lista de perfis em um workflow
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 20%

---

# Criação de uma lista de perfis com base em um fluxo de trabalho{#creating-a-profile-list-with-a-workflow}


Para criar um **[!UICONTROL List]** digite list com base na nova tabela de recipients, é necessário criar um workflow de direcionamento que gerará a lista.

Para obter mais informações sobre listas no Campaign, consulte [nesta seção](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Para criar um workflow de direcionamento e atualizar recipients em uma tabela de recipients personalizada, siga as etapas abaixo:

1. Vá para a **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** nó do explorador.
1. Criação de um novo workflow para construção do target
1. Colocar um **Query** atividade seguida de um **Atualização da lista** atividade.

   ![](assets/mapping_create_list_workflow01.png)

1. Clique duas vezes no ícone **Query** atividade e clique em **[!UICONTROL Edit the query]** para escolher um targeting dimension com base no schema da nova tabela de recipients (em nosso exemplo: **Indivíduo**). Clique em **[!UICONTROL Finish]** para confirmar.

   ![](assets/mapping_create_list_workflow03.png)

1. Clique duas vezes no ícone **Atualização da lista** e selecione a **[!UICONTROL Create the list if necessary (Computed name)]** botão de opção.

   ![](assets/mapping_create_list_workflow02.png)

1. Selecione a pasta de criação para a nova lista.
1. Execute o workflow para criar a lista.
1. Exibir o resultado no nó da árvore que você selecionou durante a **[!UICONTROL List update]** atividade.

   O painel especifica o esquema no qual a lista se baseia, conforme mostrado abaixo:

   ![](assets/mapping_list_view.png)
