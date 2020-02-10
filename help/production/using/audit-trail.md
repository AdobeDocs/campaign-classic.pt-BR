---
title: Trilha de auditoria
seo-title: Trilha de auditoria
description: Trilha de auditoria
seo-description: null
page-status-flag: never-activated
uuid: b96b93b6-e002-4c67-b9ce-b66cdcd395d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: aa147a8c-9d93-45c8-bb4a-db714739f4c0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# Audit trail{#audit-trail}

No Adobe Campaign, o **[!UICONTROL Audit trail]** oferece acesso ao histórico completo das alterações feitas em sua instância.

**[!UICONTROL Audit trail]** captura, em tempo real, uma lista abrangente de ações e eventos que ocorrem na sua instância do Adobe Campaign. Ele inclui uma forma de autoatendimento para acessar um histórico de dados para ajudar a responder perguntas como: o que aconteceu com seus fluxos de trabalho e quem os atualizou pela última vez ou o que seus usuários fizeram na instância.

>[!NOTE]
>
>O Adobe Campaign não está auditando alterações feitas em direitos do usuário, modelos, personalização ou campanhas.\
>A trilha de auditoria só pode ser gerenciada por administradores da instância.

A Trilha de auditoria consiste em três componentes:

* **Trilha** de auditoria do esquema: Verifique as atividades e as últimas modificações feitas em seus esquemas.

   For more information on schemas, refer to this [page](../../configuration/using/data-schemas.md).

* **Trilha** de auditoria do fluxo de trabalho: Verifique as atividades e as últimas modificações feitas nos fluxos de trabalho e, além disso, o estado dos fluxos de trabalho, como:

   * Início
   * Pausar
   * Parar
   * Reiniciar
   * Limpeza igual à ação Expurgar histórico
   * Simular o que é igual à ação Iniciar no modo de simulação
   * Reativação igual à ação Executar tarefas pendentes agora
   * Interrupção incondicional
   For more information on workflows, refer to this [page](../../workflow/using/about-workflows.md).

   For more on how to monitor workflows, refer to the [dedicated section](../../workflow/using/monitoring-workflow-execution.md).

* **Trilha** de auditoria de opções: Verifique as atividades e as últimas modificações feitas em suas opções.

   For more information on options, refer to this [page](../../installation/using/configuring-campaign-options.md).

## Acessar a trilha de auditoria {#accessing-audit-trail}

Para acessar as instâncias **[!UICONTROL Audit trail]** :

1. Acesse o **[!UICONTROL Explorer]** menu da sua instância.
1. No **[!UICONTROL Administration]** menu, selecione **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. A **[!UICONTROL Audit trail]** janela é aberta com a lista de suas entidades. O Adobe Campaign verificará as ações de criação, edição e exclusão de fluxos de trabalho, opções e esquemas.

   Selecione uma das entidades para saber mais sobre as últimas modificações.

   ![](assets/audit_trail_2.png)

1. A **[!UICONTROL Audit entity]** janela fornece informações mais detalhadas sobre a entidade escolhida, como:

   * **[!UICONTROL Type]** : Fluxo de trabalho, opções ou esquemas.
   * **[!UICONTROL Entity]** : Nome interno das suas atividades.
   * **[!UICONTROL Modified by]** : Nome de usuário da última pessoa que modificou esta entidade.
   * **[!UICONTROL Action]** : Última ação executada nesta entidade, Criada, Editada ou Excluída.
   * **[!UICONTROL Modification date]** : Data da última ação executada nesta entidade.
   O bloco de código fornece mais informações sobre o que foi alterado exatamente em sua entidade.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Por padrão, o período de retenção é definido como 180 dias para **[!UICONTROL Audit logs]** . Para saber mais sobre como alterar o período de retenção, consulte esta [página](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Ativar/desativar a trilha de auditoria {#enable-disable-audit-trail}

A trilha de auditoria pode ser facilmente ativada ou desativada para uma atividade específica se, por exemplo, você quiser salvar algum espaço no banco de dados.

Para fazer isso:

1. Acesse o **[!UICONTROL Explorer]** menu da sua instância.
1. No **[!UICONTROL Administration]** menu, selecione **[!UICONTROL Platform]** e depois **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Selecione uma das seguintes opções, dependendo da entidade que você deseja ativar/desativar:

   * Para Fluxo de Trabalho: **[!UICONTROL XtkAudit_Workflows]**
   * Para Esquemas: **[!UICONTROL XtkAudit_DataSchema]**
   * Para opções: **[!UICONTROL XtkAudit_Option]**
   * Para cada entidade: **[!UICONTROL XtkAudit_Enable_All]**
   ![](assets/audit_trail_5.png)

1. Altere **[!UICONTROL Value]** para 1 se quiser ativar a entidade ou para 0 se quiser desativá-la.

   ![](assets/audit_trail_6.png)

1. Clique em **[!UICONTROL Save]** .

