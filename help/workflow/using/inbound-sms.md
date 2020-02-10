---
title: SMS de entrada
seo-title: SMS de entrada
description: SMS de entrada
seo-description: null
page-status-flag: never-activated
uuid: 895e54df-e795-48ac-ac94-96dab454c550
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: fa9ae600-91fc-4aea-ae02-8ab9064947ac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# SMS de entrada{#inbound-sms}

A atividade de **SMS de Entrada** permite baixar e processar mensagens de texto de uma conta externa.

## Propriedades {#properties}

![](assets/sms_rec_edit.png)

A primeira guia da atividade de **SMS de Entrada** permite inserir os parâmetros de roteamento para mensagens SMS e inserir o script a ser executado no recebimento de cada mensagem. A segunda guia permite atribuir um cronograma à atividade e a terceira guia define as condições de expiração da atividade.

1. **[!UICONTROL SMS routing]**: Selecione a conta externa a ser usada para recuperação do SMS. External accounts are configured via the **[!UICONTROL Administration > Platform > External accounts]** node of the tree.
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

As guias **[!UICONTROL Script]**, **[!UICONTROL Schedule]** e **[!UICONTROL Expiry]** são detalhadas em Emails de [entrada](../../workflow/using/inbound-emails.md).
