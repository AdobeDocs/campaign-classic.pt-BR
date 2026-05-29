---
product: campaign
title: Trilha de auditoria
description: Saiba como monitorar sua instância com a Trilha de auditoria do Campaign
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
TQID: https://experienceleague.adobe.com/y8kDwxCY0MkBcDPUPY7hmFlpJc3l3qsEiDRhhMGqT00
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 444
ht-degree: 13%

---

# Trilha de auditoria{#audit-trail}

>[!INFO]
>
>Saiba mais sobre a funcionalidade Trilha de auditoria na [documentação do Adobe Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/audit-trail).

No Adobe Campaign, o **[!UICONTROL Audit trail]** fornece acesso ao histórico completo de alterações feitas na instância.

O **[!UICONTROL Audit trail]** captura, em tempo real, uma lista abrangente de ações e eventos que ocorrem na sua instância do Adobe Campaign. Ele inclui uma maneira de autoatendimento para acessar um histórico de dados que ajudam a responder perguntas como: o que aconteceu com seus fluxos de trabalho e quem os atualizou por último ou o que seus usuários fizeram na instância .

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
   * Parar
   * Restart
   * Limpeza que é igual ao histórico de Expurgação da ação
   * Simular qual é igual ao Início da ação no modo de simulação
   * Ativar que é igual à ação Executar tarefas pendentes agora
   * Interrupção incondicional

  Para obter mais informações sobre fluxos de trabalho, consulte esta [página](../../workflow/using/about-workflows.md).

  Para obter mais informações sobre como monitorar workflows, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=pt-BR){target="_blank"}.


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
