---
product: campaign
title: SMS de entrada
description: Saiba mais sobre a atividade de workflow de SMS de entrada
feature: Workflows, Channels Activity
exl-id: 94a9d50b-4ead-4815-8d12-942fa78b4e8a
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 100%

---

# SMS de entrada{#inbound-sms}

![](../../assets/common.svg)

A atividade de **SMS de Entrada** permite baixar e processar mensagens de texto de uma conta externa.

## Propriedades {#properties}

![](assets/sms_rec_edit.png)

A primeira guia da atividade de **SMS de Entrada** permite inserir os parâmetros de roteamento para mensagens SMS e inserir o script a ser executado no recebimento de cada mensagem. A segunda guia permite atribuir um cronograma à atividade e a terceira guia define as condições de expiração da atividade.

1. **[!UICONTROL SMS routing]**: selecione a conta externa que será usada para recuperação do SMS. As contas externas são configuradas no nó **[!UICONTROL Administration > Platform > External accounts]** da árvore.
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

As guias **[!UICONTROL Script]**, **[!UICONTROL Schedule]** e **[!UICONTROL Expiry]** são detalhadas em [Emails de entrada](inbound-emails.md).
