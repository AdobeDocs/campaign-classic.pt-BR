---
product: campaign
title: Trilha de auditoria
description: Saiba como monitorar sua instância com a trilha de auditoria do Campaign
feature: Audit Trail, Monitoring
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 3%

---

# Trilha de auditoria{#audit-trail}

![](../../assets/v7-only.svg)

No Adobe Campaign, a variável **[!UICONTROL Audit trail]** O fornece acesso ao histórico completo das alterações feitas na instância.

**[!UICONTROL Audit trail]** A captura, em tempo real, uma lista abrangente de ações e eventos que ocorrem em sua instância do Adobe Campaign. Ele inclui uma maneira de autoatendimento para acessar um histórico de dados que ajudam a responder perguntas como: o que aconteceu com seus fluxos de trabalho e quem os atualizou pela última vez ou o que seus usuários fizeram na instância .

>[!NOTE]
>
>O Adobe Campaign não está auditando alterações feitas em direitos de usuário, modelos, personalização ou campanhas.\
>A trilha de auditoria só pode ser gerenciada pelos administradores da instância.

A trilha de auditoria consiste em três componentes:

* **Trilha de auditoria do esquema**: Verifique as atividades e as últimas modificações feitas em seus esquemas.

   Para obter mais informações sobre schemas, consulte esta seção [página](../../configuration/using/data-schemas.md).

* **Trilha de auditoria de workflow**: Verifique as atividades e as últimas modificações feitas nos workflows e, além disso, o estado dos workflows, como:

   * Start
   * Pause
   * Stop
   * Restart
   * Cleanup que é igual ao histórico de Expurgação de ação
   * Simular o que é igual à ação Iniciar no modo de simulação
   * Wakeup que é igual à ação Execute pending tasks now
   * Unconditional Stop

   Para obter mais informações sobre workflows, consulte esta seção [página](../../workflow/using/about-workflows.md).

   Para obter mais informações sobre como monitorar workflows, consulte o [seção dedicada](../../workflow/using/monitoring-workflow-execution.md).

* **Trilha de auditoria de opções**: Verifique as atividades e as últimas modificações feitas em suas opções.

   Para obter mais informações sobre opções, consulte esta seção [página](../../installation/using/configuring-campaign-options.md).

## Acessar a trilha de auditoria {#accessing-audit-trail}

Para acessar o **[!UICONTROL Audit trail]** :

1. Acesse o **[!UICONTROL Explorer]** da sua instância.
1. Em **[!UICONTROL Administration]** selecione **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. O **[!UICONTROL Audit trail]** será aberta com a lista de suas entidades. A Adobe Campaign auditará as ações criar, editar e excluir ações de fluxos de trabalho, opções e esquemas.

   Selecione uma das entidades para saber mais sobre as últimas modificações.

   ![](assets/audit_trail_2.png)

1. O **[!UICONTROL Audit entity]** A janela fornece informações mais detalhadas sobre a entidade escolhida, como:

   * **[!UICONTROL Type]** : Fluxo de trabalho, opções ou esquemas.
   * **[!UICONTROL Entity]** : Nome interno das suas atividades.
   * **[!UICONTROL Modified by]** : Nome de usuário da última pessoa que modificou esta entidade pela última vez.
   * **[!UICONTROL Action]** : Última ação executada nesta entidade, Criada, Editada ou Excluída.
   * **[!UICONTROL Modification date]** : Data da última ação executada nesta entidade.

   O bloco de código fornece mais informações sobre o que foi alterado exatamente na sua entidade.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Por padrão, o período de retenção é definido como 180 dias para **[!UICONTROL Audit logs]** . Para saber mais sobre como alterar o período de retenção, consulte esta seção [página](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Ativar/desativar Trilha de Auditoria {#enable-disable-audit-trail}

A trilha de auditoria pode ser facilmente ativada ou desativada para uma atividade específica se, por exemplo, você quiser salvar espaço no banco de dados.

Para fazer isso:

1. Acesse o **[!UICONTROL Explorer]** da sua instância.
1. Em **[!UICONTROL Administration]** selecione **[!UICONTROL Platform]** then **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Selecione uma das seguintes opções, dependendo da entidade que você deseja ativar/desativar:

   * Para Fluxo de Trabalho: **[!UICONTROL XtkAudit_Workflows]**
   * Para esquemas: **[!UICONTROL XtkAudit_DataSchema]**
   * Para opções: **[!UICONTROL XtkAudit_Option]**
   * Para cada entidade: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Altere o **[!UICONTROL Value]** para 1 se quiser ativar a entidade ou para 0 se quiser desativá-la.

   ![](assets/audit_trail_6.png)

1. Clique em **[!UICONTROL Save]** .
