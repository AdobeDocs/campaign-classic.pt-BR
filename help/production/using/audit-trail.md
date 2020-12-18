---
solution: Campaign Classic
product: campaign
title: Trilha de auditoria
description: Trilha de auditoria
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---


# Trilha de auditoria{#audit-trail}

No Adobe Campaign, o **[!UICONTROL Audit trail]** fornece acesso ao histórico completo das alterações feitas em sua instância.

**[!UICONTROL Audit trail]** captura, em tempo real, uma lista abrangente de ações e eventos que ocorrem em sua instância do Adobe Campaign. Ele inclui uma forma de autoatendimento para acessar um histórico de dados para ajudar a responder perguntas como: o que aconteceu com seus workflows e quem os atualizou pela última vez ou o que seus usuários fizeram na instância.

>[!NOTE]
>
>A Adobe Campaign não está auditando alterações feitas em direitos de usuário, modelos, personalização ou campanhas.\
>A trilha de auditoria só pode ser gerenciada por administradores da instância.

A Trilha de auditoria é composta por três componentes:

* **Trilha** de auditoria do schema: Verifique as atividades e as últimas modificações feitas em seus schemas.

   Para obter mais informações sobre schemas, consulte esta [página](../../configuration/using/data-schemas.md).

* **Trilha** de auditoria do fluxo de trabalho: Verifique as atividades e as últimas modificações feitas nos workflows e, além disso, o estado dos workflows, como:

   * Start
   * Pause
   * Stop
   * Restart
   * Cleanup que é igual à ação Expurgar histórico
   * Simular o que é igual ao Start de ação no modo de simulação
   * Ativação igual à ação Executar tarefas pendentes agora
   * Unconditional Stop

   Para obter mais informações sobre workflows, consulte esta [página](../../workflow/using/about-workflows.md).

   Para obter mais informações sobre como monitorar workflows, consulte a seção [dedicada](../../workflow/using/monitoring-workflow-execution.md).

* **Trilha** de auditoria de opções: Verifique as atividades e as últimas modificações feitas em suas opções.

   Para obter mais informações sobre opções, consulte esta [página](../../installation/using/configuring-campaign-options.md).

## Acessar a trilha de auditoria {#accessing-audit-trail}

Para acessar o **[!UICONTROL Audit trail]** de sua instância:

1. Acesse o menu **[!UICONTROL Explorer]** da sua instância.
1. No menu **[!UICONTROL Administration]**, selecione **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. A janela **[!UICONTROL Audit trail]** é aberta com a lista de suas entidades. A Adobe Campaign verificará as ações de criação, edição e exclusão de workflows, opções e schemas.

   Selecione uma das entidades para saber mais sobre as últimas modificações.

   ![](assets/audit_trail_2.png)

1. A janela **[!UICONTROL Audit entity]** fornece informações mais detalhadas sobre a entidade escolhida, como:

   * **[!UICONTROL Type]** : Fluxo de trabalho, opções ou Schemas.
   * **[!UICONTROL Entity]** : Nome interno das suas atividades.
   * **[!UICONTROL Modified by]** : Nome de usuário da última pessoa que modificou esta entidade.
   * **[!UICONTROL Action]** : Última ação executada nesta entidade, Criada, Editada ou Excluída.
   * **[!UICONTROL Modification date]** : Data da última ação executada nesta entidade.

   O bloco de código fornece mais informações sobre o que foi alterado exatamente em sua entidade.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Por padrão, o período de retenção é definido como 180 dias para **[!UICONTROL Audit logs]**. Para saber mais sobre como alterar o período de retenção, consulte esta [página](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Ativar/desativar a trilha de auditoria {#enable-disable-audit-trail}

A trilha de auditoria pode ser facilmente ativada ou desativada para uma atividade específica se, por exemplo, você quiser salvar algum espaço no banco de dados.

Para fazer isso:

1. Acesse o menu **[!UICONTROL Explorer]** da sua instância.
1. No menu **[!UICONTROL Administration]**, selecione **[!UICONTROL Platform]** e **[!UICONTROL Options]**.

   ![](assets/audit_trail_4.png)

1. Selecione uma das seguintes opções, dependendo da entidade que você deseja ativar/desativar:

   * Para Fluxo de Trabalho: **[!UICONTROL XtkAudit_Workflows]**
   * Para Schemas: **[!UICONTROL XtkAudit_DataSchema]**
   * Para opções: **[!UICONTROL XtkAudit_Option]**
   * Para cada entidade: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Altere **[!UICONTROL Value]** para 1 se quiser ativar a entidade ou para 0 se quiser desativá-la.

   ![](assets/audit_trail_6.png)

1. Clique em **[!UICONTROL Save]**.

