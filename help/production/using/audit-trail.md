---
product: campaign
title: Trilha de auditoria
description: Saiba como monitorar sua instância com a Trilha de auditoria do Campaign
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 10%

---

# Trilha de auditoria{#audit-trail}



No Adobe Campaign, o **[!UICONTROL Audit trail]** fornece acesso ao histórico completo de alterações feitas na instância.

O **[!UICONTROL Audit trail]** captura, em tempo real, uma lista abrangente de ações e eventos que ocorrem na sua instância do Adobe Campaign. Ele inclui uma maneira de autoatendimento para acessar um histórico de dados que ajudam a responder perguntas como: o que aconteceu com seus workflows e quem os atualizou por último ou o que seus usuários fizeram na instância .

>[!NOTE]
>
>O Adobe Campaign não está auditando alterações feitas em direitos de usuário, modelos, personalização ou campanhas.\
>A trilha de auditoria só pode ser gerenciada por administradores da instância.

A Trilha de auditoria consiste em três componentes:

* **Trilha de auditoria do esquema**: verifique as atividades e as últimas modificações feitas em seus esquemas.

  Para obter mais informações sobre esquemas, consulte esta [página](../../configuration/using/data-schemas.md).

* **Trilha de auditoria do fluxo de trabalho**: verifique as atividades e as últimas modificações feitas nos fluxos de trabalho e, além disso, o estado dos fluxos de trabalho, como:

   * Start
   * Pause
   * Stop
   * Restart
   * Limpeza que é igual ao histórico de Expurgação da ação
   * Simular qual é igual ao Início da ação no modo de simulação
   * Ativar que é igual à ação Executar tarefas pendentes agora
   * Unconditional Stop

  Para obter mais informações sobre fluxos de trabalho, consulte esta [página](../../workflow/using/about-workflows.md).

  Para obter mais informações sobre como monitorar fluxos de trabalho, consulte a [seção dedicada](../../workflow/using/monitoring-workflow-execution.md).

* **Trilha de auditoria da opção**: verifique as atividades e as últimas modificações feitas em suas opções.

  Para obter mais informações sobre opções, consulte esta [página](../../installation/using/configuring-campaign-options.md).

## Acessando a Trilha de auditoria {#accessing-audit-trail}

Para acessar o **[!UICONTROL Audit trail]** da sua instância:

1. Acesse o menu **[!UICONTROL Explorer]** da sua instância.
1. No menu **[!UICONTROL Administration]**, selecione **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. A janela **[!UICONTROL Audit trail]** é aberta com a lista de suas entidades. O Adobe Campaign auditará a criação, edição e exclusão de ações para workflows, opções e esquemas.

   Selecione uma das entidades para saber mais sobre as últimas modificações.

   ![](assets/audit_trail_2.png)

1. A janela **[!UICONTROL Audit entity]** fornece informações mais detalhadas sobre a entidade escolhida, como:

   * **[!UICONTROL Type]**: Fluxo de Trabalho, Opções ou Esquemas.
   * **[!UICONTROL Entity]** : nome interno de suas atividades.
   * **[!UICONTROL Modified by]** : Nome de usuário da última pessoa que modificou esta entidade pela última vez.
   * **[!UICONTROL Action]**: Última ação executada nesta entidade: Criada, Editada ou Excluída.
   * **[!UICONTROL Modification date]** : Data da última ação executada nesta entidade.

   O bloco de código fornece mais informações sobre o que foi alterado exatamente em sua entidade.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Por padrão, o período de retenção está definido como 180 dias para **[!UICONTROL Audit logs]**. Para saber mais sobre como alterar o período de retenção, consulte esta [página](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Ativar/desativar trilha de auditoria {#enable-disable-audit-trail}

A trilha de auditoria pode ser facilmente ativada ou desativada para uma atividade específica se, por exemplo, você quiser salvar algum espaço no banco de dados.

Para fazer isso:

1. Acesse o menu **[!UICONTROL Explorer]** da sua instância.
1. No menu **[!UICONTROL Administration]**, selecione **[!UICONTROL Platform]** depois **[!UICONTROL Options]**.

   ![](assets/audit_trail_4.png)

1. Selecione uma das seguintes opções dependendo da entidade que você deseja ativar/desativar:

   * Para Fluxo de Trabalho: **[!UICONTROL XtkAudit_Workflows]**
   * Para esquemas: **[!UICONTROL XtkAudit_DataSchema]**
   * Para Opções: **[!UICONTROL XtkAudit_Option]**
   * Para cada entidade: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Altere o **[!UICONTROL Value]** para 1 se quiser habilitar a entidade ou para 0 se quiser desabilitá-la.

   ![](assets/audit_trail_6.png)

1. Clique em **[!UICONTROL Save]**.
