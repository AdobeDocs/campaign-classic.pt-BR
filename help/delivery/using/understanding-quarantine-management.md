---
product: campaign
title: Entender o gerenciamento de quarentena
description: Entender o gerenciamento de quarentena
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# Entender o gerenciamento de quarentena{#understanding-quarantine-management}

>[!NOTE]
>
>Orientações abrangentes sobre gerenciamento de quarentena estão documentadas na página [Gerenciamento de quarentena do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines). Esse conteúdo se aplica aos usuários do Campaign Classic v7 e do Campaign v8, abrangendo:
>
>* Quarentena versus conceitos de inclui na lista de bloqueios
>* Por que os endereços são enviados para quarentena (erros de hardware/software)
>* Limites de contador de erros e gerenciamento de erros leves
>* Como acessar e identificar endereços em quarentena
>* Como remover endereços da quarentena (automático, manual, em massa)
>* Relatórios de gerenciamento de quarentena
>
>Esta página documenta a **configuração específica do Campaign Classic v7** para gerenciamento de quarentena em implantações híbridas e locais.

Para obter orientação abrangente sobre gerenciamento de quarentena, consulte a [documentação sobre o gerenciamento de quarentena do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Configuração de quarentena {#v7-quarantine-config}

As seguintes opções de configuração estão disponíveis para **implantações híbridas/no local do Campaign Classic v7** para personalizar o comportamento da quarentena.

### Configuração de limite de erro leve {#soft-error-threshold}

Para instalações locais que usam o MTA herdado do Campaign, você pode modificar o número de erros e o período entre dois erros antes que um endereço seja colocado em quarentena.

Para definir essas configurações:

1. Acessar o assistente de implantação de **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**
2. Navegue até **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. Configurar:
   * **Número de erros**: o número máximo de erros leves antes que um endereço seja colocado em quarentena (padrão: 5)
   * **Período entre dois erros significativos**: a janela de tempo (em segundos) para contagem de erros (padrão: 86.400 segundos = 1 dia)

Quando o contador de erros atinge o limite, o endereço é colocado em quarentena. Se o último erro significativo ocorreu há mais de 10 dias, o contador de erros é reinicializado.

Para obter mais detalhes, consulte [esta página](communication-channels.md) em **Envio de entrega** > **Configurar novas tentativas**.

>[!NOTE]
>
>Para usuários do Campaign v8 Managed Cloud Services, as configurações de repetição e os limites de erro são gerenciados pela Adobe com base no desempenho de IP e na reputação do domínio. Nenhuma configuração é necessária.

### Fluxo de trabalho de limpeza do banco de dados {#database-cleanup-workflow}

Para instalações locais, o fluxo de trabalho técnico do **[!UICONTROL Database cleanup]** remove automaticamente os endereços em quarentena que correspondem a condições específicas.

Acesse este fluxo de trabalho de **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**.

O workflow remove endereços da quarentena nos seguintes casos:

* Endereços no status **[!UICONTROL With errors]** após uma entrega bem-sucedida
* Endereços no status **[!UICONTROL With errors]** se a última rejeição temporária tiver ocorrido há mais de 10 dias
* Endereços no status **[!UICONTROL With errors]** com erro **[!UICONTROL Mailbox full]** após 30 dias

Verifique se esse workflow é executado regularmente (recomendado: diariamente) para manter a higiene das listas de quarentena.

Para obter mais informações sobre limpeza de banco de dados, consulte [esta seção](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>Para usuários do Campaign v8 Managed Cloud Services, o fluxo de trabalho de limpeza do banco de dados é monitorado e gerenciado pela Adobe.

### Especificações da quarentena de notificação por push {#push-quarantine-specifics}

Para o Campaign Classic v7, as quarentenas de notificação por push seguem o mecanismo geral de quarentena com alguns comportamentos específicos de canal.

Para notificações por push do **iOS** e do **Android**, o mecanismo de quarentena usa tokens de dispositivo em vez de endereços de email. Quando um aplicativo móvel é desinstalado ou reinstalado, o token associado é colocado em quarentena.

Para obter informações detalhadas sobre cenários de quarentena de notificação por push (tipos de erro do iOS e do Android, comportamento de repetição etc.), consulte a [Documentação de noções básicas sobre falhas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}, que inclui tabelas de tipo de erro de notificação por push abrangentes.

### Especificações da quarentena de SMS {#sms-quarantine-specifics}

Para o Campaign Classic v7, as quarentenas de SMS seguem o mecanismo de quarentena geral com alguns comportamentos específicos de canal relacionados a números de telefone em vez de endereços de email.

O mecanismo de quarentena de SMS varia dependendo do conector usado:

* **Conectores SMPP padrão**: as regras de qualificação de erro definidas em **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** se aplicam às entregas de SMS.

* **Conector SMPP genérico estendido**: o gerenciamento de erros é tratado de forma diferente usando expressões regulares (regexes) para analisar mensagens de Relatório de Status (SR) retornadas pelo provedor SMSC.

Para obter informações detalhadas sobre cenários de quarentena de SMS e tipos de erro, consulte a documentação [Noções básicas sobre falhas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}, que inclui tabelas abrangentes de tipos de erro de SMS.

## Tópicos relacionados

* [Gerenciamento de quarentena](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentação do Campaign v8)
* [Noções básicas sobre falhas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentação do Campaign v8)
* [Práticas recomendadas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentação do Campaign v8)
* [Fluxo de trabalho de limpeza do banco de dados](../../production/using/database-cleanup-workflow.md) (v7 híbrido/no local)
* [Configurar novas tentativas de entrega](communication-channels.md) (v7 híbrido/no local)
