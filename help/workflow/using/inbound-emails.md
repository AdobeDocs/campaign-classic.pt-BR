---
product: campaign
title: Emails de entrada
description: Saiba mais sobre a atividade de workflow de emails de entrada
feature: Workflows, Channels Activity
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 100%

---

# Emails de entrada{#inbound-emails}

![](../../assets/v7-only.svg)

A atividade de **emails de entrada** permite baixar e processar mensagens de email de um servidor de email POP3.

![](assets/email_rec_edit_1.png)

A primeira guia da atividade de **Emails de Entrada** permite inserir os parâmetros do servidor POP3 e digitar o script a ser executado no recebimento de cada mensagem. A segunda guia permite atribuir uma agenda à atividade e a terceira guia define as condições de expiração da atividade.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      Quando essa opção é ativada, você pode selecionar uma conta POP3 externa em vez de inserir os parâmetros de conexão. O campo **[!UICONTROL External account]** especifica a conta do POP3 externa a ser usada para se conectar ao serviço de email. Este campo só estará visível se a opção &#39;Usar uma conta externa&#39; estiver habilitada.

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

   O conteúdo da mensagem é acessível a partir da variável global **[!UICONTROL mailMessage]**.

1. **[!UICONTROL Schedule]**

   Para definir uma agenda para a atividade, clique na guia **[!UICONTROL Scheduling]** e marque **[!UICONTROL Plan execution]**. Clique no botão **[!UICONTROL Change]** para configurar o cronograma.

   A configuração do cronograma é igual à atividade de agendamento. Consulte [Scheduler](scheduler.md).

1. **[!UICONTROL Expiration]**

   Você pode definir atrasos de expiração por meio da guia **[!UICONTROL Expiration]**.

   ![](assets/email_rec_edit_3.png)

   A configuração é igual à atividade de agendamento. Consulte [Expirações](defining-approvals.md).
