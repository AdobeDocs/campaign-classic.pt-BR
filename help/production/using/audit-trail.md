---
product: campaign
title: Trilha de auditoria
description: Saiba como monitorar sua instância com a Trilha de auditoria do Campaign
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 3d1ed85dcafc5afc4088db98c09d78fb7e9c0a39
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 10%

---

# Trilha de auditoria{#audit-trail}

>[!INFO]
>
>Saiba mais sobre a funcionalidade Trilha de auditoria na [documentação do Adobe Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/audit-trail).

No Adobe Campaign, o **[!UICONTROL Audit trail]** fornece acesso ao histórico completo de alterações feitas na instância.

O **[!UICONTROL Audit trail]** captura, em tempo real, uma lista abrangente de ações e eventos que ocorrem na sua instância do Adobe Campaign. Ele inclui uma maneira de autoatendimento para acessar um histórico de dados que ajudam a responder perguntas como: o que aconteceu com seus workflows e quem os atualizou por último ou o que seus usuários fizeram na instância .

>[!NOTE]
>
>O Adobe Campaign não está auditando alterações feitas em direitos de usuário, modelos, personalização ou campanhas.\
>A trilha de auditoria só pode ser gerenciada por administradores da instância.

![](assets/audit_trail_2.png)

+++ Saiba mais sobre entidades disponíveis da Trilha de auditoria

* **Trilha de auditoria do esquema**: permite explorar as alterações feitas em seus esquemas, bem como identificar quem fez essas modificações e quando elas ocorreram.

  Para obter informações detalhadas sobre esquemas, consulte esta [página](../../configuration/using/data-schemas.md).

* A **trilha de auditoria do fluxo de trabalho** rastreia todas as ações relacionadas aos seus fluxos de trabalho, incluindo:

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

* **A opção trilha de auditoria** permite que você verifique as atividades e as últimas modificações feitas em suas opções.

  Para obter mais informações sobre opções, consulte esta [página](../../installation/using/configuring-campaign-options.md).

* **Trilha de auditoria de entrega** permite que você verifique as atividades e as últimas modificações feitas em suas entregas.

  Para obter mais informações sobre entregas, consulte esta [página](../../delivery/using/communication-channels.md).

* **Conta Externa** permite que você verifique modificações feitas em contas externas, usadas por processos técnicos, como fluxos de trabalho técnicos ou fluxos de trabalho de campanha.

  Para obter mais informações sobre a conta externa, consulte esta [página](../../installation/using/external-accounts.md).

* **Mapeamento de Entrega** permite que você monitore atividades e modificações recentes feitas em seus Mapeamentos de Entrega.

  Para obter mais informações sobre mapeamento de entrega, consulte esta [página](../../configuration/using/target-mapping.md).

* O **Aplicativo Web** permite verificar as modificações feitas em formulários Web no Campaign V8 usados para criar páginas com campos de entrada e seleção e que podem incluir dados do banco de dados.

  Para obter mais informações sobre o aplicativo Web, consulte esta [página](../../web/using/about-web-applications.md).

* A **Oferta** permite que você verifique as atividades e as últimas modificações feitas em suas ofertas.

  Para obter mais informações sobre a oferta, consulte esta [página](../../interaction/using/interaction-and-offer-management.md).

* **Operador** permite monitorar atividades e modificações recentes feitas em seus Operadores.

  Para obter mais informações sobre operadores, consulte esta [página](../../platform/using/access-management-operators.md).

+++
