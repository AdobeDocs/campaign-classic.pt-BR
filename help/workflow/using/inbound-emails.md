---
title: Emails de entrada
seo-title: Emails de entrada
description: Emails de entrada
seo-description: null
page-status-flag: never-activated
uuid: 6bcc7952-f051-4e50-8833-95d49c7ed781
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 4c0530b1-0292-45bc-8730-668bc5b8550b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Emails de entrada{#inbound-emails}

A atividade de **emails de entrada** permite baixar e processar mensagens de email de um servidor de email POP3.

![](assets/email_rec_edit_1.png)

A primeira guia da atividade de **Emails de Entrada** permite inserir os parâmetros do servidor POP3 e digitar o script a ser executado no recebimento de cada mensagem. A segunda guia permite atribuir uma agenda à atividade e a terceira guia define as condições de expiração da atividade.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      Quando essa opção é ativada, você pode selecionar uma conta POP3 externa em vez de inserir os parâmetros de conexão. The **[!UICONTROL External account]** field specifies the external POP3 account to be used to connect to the email service. Este campo só estará visível se a opção &#39;Usar uma conta externa&#39; estiver habilitada.

      Se essa opção não estiver selecionada, especifique os seguintes parâmetros:

      ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

         Nome do servidor POP3.

      * **[!UICONTROL POP3 account]**

         Nome do usuário.

      * **[!UICONTROL Password]**

         Senha da conta do usuário.

      * **[!UICONTROL Port]**

         Número da porta de conexão POP3. A porta padrão é 110.
   * **[!UICONTROL Stop as soon as email is processed]**

      Essa opção permite processar emails individualmente. A atividade ativa sua transição apenas uma vez e depois conclui o processamento, deixando mensagens não processadas no servidor.


1. **[!UICONTROL Script]**

   O script permite processar a mensagem e executar várias operações que dependem do conteúdo da mensagem. O script é executado para cada mensagem e pode determinar a operação a ser executada nas mensagens (deixe ou excluir a mensagem) e a ativação da transição de saída.

   O código de retorno deve ser um dos seguintes valores:

   * 1 - Exclui a mensagem do servidor e ativa a transição de saída.
   * 2 - Deixa a mensagem no servidor e ativa a transição de saída.
   * 3 - Exclui a mensagem do servidor.
   * 4 - Deixa a mensagem no servidor.
   The content of the message is accessible from the global **[!UICONTROL mailMessage]** variable.

1. **[!UICONTROL Schedule]**

   To define a schedule for the activity, click the **[!UICONTROL Scheduling]** tab and check **[!UICONTROL Plan execution]**. Click the **[!UICONTROL Change]** button to configure the schedule.

   A configuração do cronograma é igual à atividade de agendamento. Consulte o [Agendador](../../workflow/using/scheduler.md).

1. **[!UICONTROL Expiration]**

   You can define expiration delays via the **[!UICONTROL Expiration]** tab.

   ![](assets/email_rec_edit_3.png)

   A configuração é igual à atividade de agendamento. Consulte [Expirações](../../workflow/using/executing-a-workflow.md#expirations).

