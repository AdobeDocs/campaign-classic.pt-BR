---
product: campaign
title: Atualizações da documentação do Adobe Campaign Classic v7
description: Esta página lista todos os novos recursos e atualizações na documentação do Adobe Campaign Classic
feature: Overview
role: User
level: Beginner
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
source-git-commit: 378788764e244dcad12018d6d703048707d4c3e6
workflow-type: tm+mt
source-wordcount: '4931'
ht-degree: 99%

---

# Atualizações da documentação{#documentation-updates}

![](../../assets/v7-only.svg)

Esta página lista todos os novos recursos e atualizações de documentação por mês e a versão do Campaign.

Consulte as [Notas de versão do Adobe Campaign Classic](../../rn/using/latest-release.md) para ver as atualizações relacionadas à versão.

## 2022

### Julho de 2022 {#july-2022}

A transição para o novo servidor de deliverability é detalhada em uma nova nota técnica. [Leia mais](../../technotes/using/deliverability-server.md)

**Atualizações da documentação que acompanha a versão 7.3.1**

Atualização da matriz de compatibilidade. [Leia mais](compatibility-matrix.md)

Atualização da seção Notas de versão. [Leia mais](rn-overview.md)

Notificações sensíveis ao tempo com o iOS 15. [Leia mais](../../delivery/using/create-notifications-ios.md)


### Março de 2022 {#mar-2022}

Adição de uma descrição detalhada para a opção **[!UICONTROL Test SMTP delivery]**. [Saiba mais](../../delivery/using/steps-sending-the-delivery.md#delivery-additiona-parameters)

A página Introdução às atualizações foi atualizada para esclarecer as diretrizes de atualização do Console do Campaign. [Leia mais](../../rn/using/rn-overview.md)

O novo build do Campaign v7.2.2 está disponível. [Leia mais](../../rn/using/latest-release.md)

Adição de informações de solução de problemas relacionadas ao conector ACS. [Saiba mais](../../integrations/using/troubleshooting-the-acs-connector.md)

As versões herdadas do PostgreSQL que atingiram o fim de vida útil foram adicionadas à página [Recursos obsoletos e removidos](../../rn/using/deprecated-features.md#dbe-eol).

### Fevereiro de 2022 {#february-2022}

Atualização da seção de atividade **Transferência de arquivos**, incluindo um lembrete para monitorar manualmente o tamanho do conteúdo arquivado no diretório SFTP, caso a opção **Excluir os arquivos de origem após a transferência** não esteja selecionada. [Saiba mais](../../workflow/using/file-transfer.md#properties)

A seção Quarentena versus Lista de bloqueios foi esclarecida. [Saiba mais](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

As seções sobre como enviar um endereço para quarentena e como remover endereços da lista de quarentena foram atualizadas. [Saiba mais](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Adição de uma prática recomendada do fluxo de trabalho que orienta a não realizar várias solicitações de interrupção no mesmo fluxo de trabalho. [Saiba mais](../../workflow/using/workflow-best-practices.md)

Foram adicionadas informações sobre como interromper a execução de um delivery recorrente em uma campanha. [Saiba mais](../../workflow/using/recurring-delivery.md)

### Janeiro de 2022 {#january-2022}

**Atualizações da documentação que acompanha a versão 7.2.1**

Atualização da matriz de compatibilidade. [Leia mais](compatibility-matrix.md)

Atualização da seção Notas de versão. [Leia mais](rn-overview.md)

Atualização da configuração da conta externa FDA para o Snowflake. [Leia mais](../../installation/using/configure-fda-snowflake.md)

Atualização da configuração da conta externa FDA para o Azure Synapse Analytics. [Leia mais](../../installation/using/configure-fda-synapse.md#azure-external)

Atualização do conector FDA do Google BigQuery. [Leia mais](../../installation/using/configure-fda-google-big-query.md)

Após serem descontinuados, o Microsoft CRM, o Salesforce e o Oracle CRM tiveram suas atividades de ações por demanda removidas da documentação.

Nova opção **Abort on error** adicionada à seção Error Management do fluxo de trabalho. [Leia mais](../../workflow/using/advanced-parameters.md#in-case-of-errors)

Adicionada a opção de atualização em lote na atividade do conector CRM. [Leia mais](../../workflow/using/crm-connector.md)

## 2021

### Dezembro de 2021{#dec-2021}

As notas de versão do Campaign Classic v7 foram reorganizadas para simplificar a navegação. [Leia mais](rn-overview.md)

A documentação sobre Edição de formulários no Campaign foi atualizada e aprimorada. [Leia mais](../../configuration/using/editing-forms.md)

O CentOs 8 chegou ao fim da vida útil e agora está obsoleto no Adobe Campaign Classic. [Leia mais](deprecated-features.md)

### Novembro de 2021{#nov-2021}

Adição de uma limitação sobre o SMS de Entrada (MO). [Leia mais](../../delivery/using/sms-protocol.md#multipart)

Atualização dos detalhes dos logs do processo de migração para a implantação do conector do CRM. [Leia mais](../../migration/using/testing-the-migration.md#verification-process)

Adição de requisitos sobre permissões de IMS para implementar a integração do Adobe Campaign-Adobe Analytics. [Leia mais](../../platform/using/adobe-analytics-provisioning.md)

Atualização da data de término da vida útil do conector de dados do Adobe Analytics de 1 de março de 2022 para 17 de agosto de 2022. [Leia mais](deprecated-features.md)

Adição de um link para a documentação do SDK móvel da Adobe Experience Platform para saber como configurar a extensão do Campaign no Adobe Launch. [Leia mais](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)

Adição de uma seção sobre como usar o JavaScript para calcular valores, trocar dados e executar operações específicas usando chamadas SOAP.[Leia mais](../../workflow/using/javascript-scripts-and-templates.md)

Adição de amostras de implementação de códigos JavaScript em workflows. [Leia mais](../../workflow/using/javascript-in-workflows.md)


### Outubro de 2021{#oct-2021}

As notas técnicas existentes foram agrupadas na nova seção **Technote**.

A página **Recomendações de dimensionamento de hardware** foi atualizada e adicionada à seção de **Notas técnicas**. [Leia mais](../../technotes/using/hardware-sizing.md)

### Setembro de 2021{#sept-2021}

**Atualizações da documentação que vêm com a versão 21.1.4**

O tipo de gráfico **Gauge** foi removido.

As capturas de tela e os parâmetros de relatórios e aplicativos da web foram atualizados após a remoção do Adobe Flash.

A descrição do [fluxo de trabalho técnico de faturamento](../../production/using/monitoring-processes.md#billing-report) foi atualizada com uma nova garantia.

### Agosto de 2021{#aug-2021}

Adição de uma nova atividade de workflow: Alterar fonte de dados - [Saiba mais](../../workflow/using/change-data-source.md)

Os emblemas de aplicabilidade foram adicionados às páginas de documentação: **Aplica-se a v7**, somente para recursos do Campaign Classic v7 e **Aplica-se a v7 e v8**, para recursos comuns.

Adição de uma observação sobre a integração entre o Campaign e o AEM Assets que foi descontinuada a partir do Adobe Experience Manager 6.4. [Saiba mais](../../integrations/using/configuring-access-to-assets.md)


### Julho de 2021 {#july-2021}

A [versão 21.1.3 do Campaign](../../rn/using/latest-release.md#release-21-1-3-build-9330) foi movida para Disponibilidade Geral (GA).


### Junho de 2021 {#june-2021}

A seção **Mensagens transacionais** foi reorganizada e esclarecida com uma nova seção de Introdução, incluindo um [esquema aprimorado](../../message-center/using/about-transactional-messaging.md#transactional-messaging-operating-principle) para compreender melhor o processo. [Leia mais](../../message-center/using/about-transactional-messaging.md)

**Atualizações da documentação que vêm com a versão 21.1.3**

Integração com o Adobe Journey Orchestration - [Saiba mais](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=pt-BR). Um caso de uso passo a passo é apresentado [nesta página](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=pt-BR)

Aprimoramentos do canal LINE - [Saiba mais](../../delivery/using/line-channel.md)

Novo conector FDA Vertica - [Saiba mais](../../installation/using/configure-fda-vertica.md)

Novo conector FDA do Google BigQuery - [Saiba mais](../../installation/using/configure-fda-google-big-query.md)

A descrição do fluxo de trabalho técnico &quot;Faturamento (faturamento)&quot; agora inclui as tarefas originalmente executadas pelo &quot;Número de perfis de faturamento ativos (billingActiveContactCount)&quot;. [Leia mais](../../workflow/using/about-technical-workflows.md)

### Maio de 2021 {#may-2021}

A documentação do relatório do Workflow Heatmap foi atualizada e aprimorada. [Leia mais](../../workflow/using/heatmap.md)

Os requisitos do console do cliente do Campaign foram atualizados na Matriz de compatibilidade. [Leia mais](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

A instalação do Console do cliente do Campaign em etapas foi aprimorada e esclarecida. [Leia mais](../../installation/using/installing-the-client-console.md)

Uma nova nota técnica foi criada sobre o problema de assinatura de URLs rastreados. [Leia mais](../../technotes/using/tracked-urls.md)

### Abril de 2021 {#april-2021}

Uma nova seção foi adicionada sobre como trabalhar com Origens e Destinos da Adobe Experience Platform para compartilhar dados entre o Campaign Classic e a Plataforma de dados do cliente em tempo real (RTCDP). [Leia mais](../../integrations/using/get-started-sources-destinations.md)

Uma nova nota técnica foi criada para saber como atualizar a qualificação de rejeição após uma interrupção do ISP. [Leia mais](../../delivery/using/update-bounce-qualification.md)

### Março de 2021 {#march-2021}

A [seção Introdução ao SMS](../../delivery/using/sms-channel.md) foi reorganizada e aprimorada. Agora você pode aprender a [configurar o canal de SMS](../../delivery/using/sms-set-up.md), [criar um SMS](../../delivery/using/sms-create.md), [enviar e rastrear SMS](../../delivery/using/sms-send.md) em seções dedicadas.

A página &quot;Opções de ajuda e suporte&quot; do Campaign Classic foi integrada à documentação principal. [Leia mais](../../support.md)

Uma nova seção foi adicionada com práticas recomendadas e verificações que devem ser executadas em relação à segurança e à privacidade. [Leia mais](../../installation/using/get-started-security-privacy.md)

O [capítulo de gerenciamento de permissões](../../platform/using/access-management.md) foi aprimorado e dividido em seções, incluindo detalhes sobre [Operadores](../../platform/using/access-management-operators.md), [Grupos de operadores](../../platform/using/access-management-groups.md), [Direitos nomeados](../../platform/using/access-management-named-rights.md) e [Gerenciamento de pastas](../../platform/using/access-management-folders.md).

Saiba como criar e gerenciar campanhas por meio destas novas páginas:
* [Criar e configurar modelos de campanha](../../campaign/using/marketing-campaign-templates.md)
* [Entregas de campanha de marketing](../../campaign/using/marketing-campaign-deliveries.md)
* [Selecionar o público das campanhas](../../campaign/using/marketing-campaign-target.md)
* [Gerenciar documentos associados](../../campaign/using/marketing-campaign-assets.md)
* [Configurar e gerenciar o processo de aprovação](../../campaign/using/marketing-campaign-approval.md)

Foram adicionadas informações à seção de atividade **[!UICONTROL Advanced JavaScript]** sobre como usar o método task.setCompleted() para finalizar a tarefa e impedir futuras recuperações. [Leia mais](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

A seção [Capacidade de delivery](../../delivery/using/about-deliverability.md) foi atualizada e agora inclui links para o novo [Manual de práticas recomendadas de capacidade de delivery da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR). Todas as informações genéricas relacionadas à capacidade de delivery que podem ser aplicadas a várias soluções da Adobe foram movidas para o [Apêndice do manual de práticas recomendadas](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html?lang=pt-BR#additional-resources).

### Fevereiro de 2021 {#release-21.1}

**Atualizações da documentação que vêm com a versão 21.1**

O novo recurso **Serviço de email de feedback** (beta privado) está documentado [aqui](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service).

A seção **Arquivo de configuração do servidor** foi atualizada com os parâmetros de configuração necessários para que o Campaign se conecte a outro serviço usando IMS. [Leia mais](../../installation/using/the-server-configuration-file.md#ims)

Na lista dos status do delivery, a descrição de **Levado em consideração pelo provedor de serviço** foi atualizada: esse status agora também é usado para deliveries de email enviados usando o [Serviço de feedback de email](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service). [Leia mais](../../delivery/using/delivery-statuses.md#list-delivery-statuses)

Os atalhos de teclado disponíveis na nova tela de logon para conexão com o Adobe Campaign agora estão documentados. [Leia mais](../../platform/using/launching-adobe-campaign.md#connecting-to-adobe-campaign)

**Outras atualizações**

Uma nova seção foi adicionada com informações detalhadas sobre como executar o teste A/B usando workflows. [Leia mais](../../delivery/using/get-started-a-b-testing.md)

A seção do MTA aprimorado do Adobe Campaign foi movida para [este local](../../delivery/using/sending-with-enhanced-mta.md).

Uma nova página foi adicionada para fornecer uma visão geral dos recursos de rastreamento no [!DNL Campaign Classic]. [Leia mais](../../delivery/using/about-message-tracking.md)

Uma seção de solução de problemas foi adicionada para ajudar você a resolver problemas comuns relacionados ao rastreamento. [Leia mais](../../delivery/using/tracking-troubleshooting.md)

A seção **Enviar um email** foi reorganizada e esclarecida com novas subseções. [Leia mais](../../delivery/using/sending-messages.md)

Foram incluídas informações sobre como adicionar links a emails que podem ser personalizados e que oferecem suporte ao rastreamento. [Leia mais](../../delivery/using/tracking-personalized-links.md).

### Janeiro de 2021 {#jan-2021}

A seção de atividade **[!UICONTROL Fork]** foi aprimorada com práticas recomendadas. [Leia mais](../../workflow/using/fork.md)

A seção **Conectores CRM** foi atualizada, melhorada e reorganizada. [Leia mais](../../platform/using/crm-connectors.md).

As etapas para conectar **o Adobe Campaign e o Microsoft Dynamics** agora estão detalhadas em uma página dedicada. [Leia mais](../../platform/using/crm-ms-dynamics.md).

A API Oracle On Demand agora está obsoleta como um CRM conectado ao Campaign. [Leia mais](../../rn/using/deprecated-features.md).

Saiba como descobrir a versão atual do servlet Web Tomcat incorporado usado em uma instância do Adobe Campaign [aqui](../../production/using/locate-tomcat-version.md).

A lista de workflows técnicos com seus pacotes associados foi aprimorada e centralizada em uma página única. [Leia mais](../../workflow/using/about-technical-workflows.md)

A seção de solução de problemas do manual de **Monitoramento** foi reorganizada e aprimorada com uma página de aterrissagem. [Leia mais](../../production/using/troubleshooting.md).

Uma nova seção **Importar e exportar dados** está disponível com novas páginas relacionadas a workflows, compactação de dados, criptografia e práticas recomendadas de importação. [Leia mais](../../platform/using/get-started-data-import-export.md)






## 2020

### Dezembro de 2020 {#dec-2020}

A seção de **Monitoramento de entrega** foi reorganizada por tópicos temáticos. [Leia mais](../../delivery/using/about-delivery-monitoring.md)

Foi adicionado um caso de uso sobre como adicionar endereços IP de remetentes aos logs do delivery. [Leia mais](../../delivery/using/delivery-dashboard.md#use-case)

As perguntas frequentes sobre privacidade foram movidas para [esta seção](../../platform/using/privacy-faq.md).

Foi adicionado um caso de uso sobre como usar a funcionalidade de mesclagem da atividade de **[!UICONTROL Deduplication]**. [Leia mais](../../workflow/using/deduplication-merge.md)

A descrição completa do protocolo e da página de configurações do conector SMS agora está disponível [aqui](../../delivery/using/sms-protocol.md).

Uma observação foi adicionada à seção **Mensagens transacionais** para avisar que as pastas de eventos não devem ser definidas como visualizações nas instâncias de execução para evitar problemas de direitos de acesso. [Leia mais](../../message-center/using/about-event-processing.md#event-collection)

### Novembro de 2020 {#nov-2020}

A visão geral do modelo de dados do Campaign foi aprimorada e reorganizada. [Leia mais](../../configuration/using/about-data-model.md).

A configuração da conta externa foi movida para [esta seção](../../installation/using/external-accounts.md).

A documentação do Federated Data Acces (FDA) do Campaign foi aprimorada com detalhes para cada configuração de banco de dados externo e foi movida para [esta seção](../../installation/using/about-fda.md).

A [versão 20.2.3 do Campaign](../../rn/using/release--2020.md#release-20-2-3-build-9182) foi movida para Disponibilidade Geral (GA).

A seção Privacidade foi movida e aprimorada com duas novas seções: [Gerenciamento de privacidade](../../platform/using/privacy-management.md) e [Gerenciamento de solicitações de privacidade](../../platform/using/privacy-requests.md).

Foi adicionada uma observação na página de configuração do servidor mid-sourcing para especificar que o nome interno da conta externa não deve ser atualizado depois que o servidor for configurado. [Leia mais](../../installation/using/mid-sourcing-server.md)

Foram adicionadas informações sobre a sintaxe a ser usada ao especificar um caminho para um servidor SFTP externo. [Leia mais](../../platform/using/sftp-server-usage.md#external-SFTP-server)

A seção Dados pessoais e personalidades foi atualizada com um cenário de caso de uso para ilustrar como as diferentes personalidades estão interagindo no que diz respeito à privacidade. [Leia mais](../../platform/using/privacy-and-recommendations.md#use-case-scenario)

Adição de uma nova seção listando Perguntas frequentes sobre privacidade. [Leia mais](../../platform/using/privacy-faq.md)

### Outubro de 2020 {#oct-2020}

**Novos recursos incluídos na versão 20.3**

Melhorias nas notificações por push para iOS - [Saiba mais](../../delivery/using/configuring-the-mobile-application.md)

Melhorias nas notificações por push para Android - [Saiba mais](../../delivery/using/configuring-the-mobile-application-android.md)

**Outras atualizações de documentação que vêm com a versão**

A matriz de Compatibilidade foi atualizada. [Leia mais](../../rn/using/compatibility-matrix.md)

A página de recursos obsoletos e removidos foi atualizada. [Leia mais](../../rn/using/deprecated-features.md)

As Notas de versão e a Matriz de compatibilidade da versão [!DNL Gold Standard] agora estão disponíveis em uma página dedicada.
[Leia mais](../../rn/using/gold-standard.md).

A integração dos acionadores originalmente baseada na configuração da autenticação oAUTH para acessar o pipeline, agora foi alterada e movida para o Adobe I/O. [Saiba mais](../../integrations/using/configuring-adobe-io.md)

**Outras atualizações**

As páginas de documentação foram atualizadas para refletir a atualização do Tomcat 8.

Detalhes foram adicionados na descrição da caixa “Sobre” na seção “Obtendo sua versão do Adobe Campaign”. [Leia mais](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

Diretrizes para executar uma atualização de build foram adicionadas à seção “Atualização do Adobe Campaign Classic”. [Leia mais](../../production/using/build-upgrade.md)

As perguntas frequentes sobre a atualização da build do Campaign foram adicionadas às perguntas mais frequentes do Campaign. Saiba mais [Saiba mais](../../platform/using/faq-build-upgrade.md)

Os modelos de hospedagem local, hospedados e híbridos do Campaign agora são descritos em uma seção exclusiva. [Leia mais](../../installation/using/hosting-models.md)

A matriz de recursos do Campaign por modelo de hospedagem foi atualizada e movida para a guia Instalação. [Leia mais](../../installation/using/capability-matrix.md)

A seção de recursos avançados dos relatórios do Campaign foi aprimorada para detalhar como usar parâmetros de URL e variáveis em relatórios personalizados. [Leia mais](../../reporting/using/advanced-functionalities.md)

A página de propriedades dos relatórios foi reorganizada e aprimorada para facilitar a configuração. [Leia mais](../../reporting/using/properties-of-the-report.md)

### Setembro de 2020 {#september-2020}

Uma observação foi adicionada para especificar que a contagem de perfis ativos está disponível somente para instâncias de Marketing. [Leia mais](../../platform/using/about-profiles.md#active-profiles)

Uma nova amostra sobre a edição de esquema foi adicionada para vincular um campo a uma tabela de referência existente. [Leia mais](../../configuration/using/examples-of-schemas-edition.md#uc-link)

Adição de uma observação sobre o uso de dados adicionais com seeds addresses em deliveries. [Leia mais](../../delivery/using/creating-seed-addresses.md#defining-addresses)

### Agosto de 2020 {#aug-2020}

Conheça as práticas recomendadas relacionadas ao design do delivery e ao envio com o Campaign em uma seção dedicada. [Leia mais](../../delivery/using/delivery-best-practices.md)

Uma landing page de práticas recomendadas de deliverability foi aprimorada para facilitar o acesso às subseções. [Leia mais](../../delivery/using/about-deliverability.md)

Os vídeos do passo a passo estão disponíveis nos seguintes tópicos:

* [Como configurar o gerenciamento de fadiga usando regras de tipologia e filtros predefinidos](../../campaign-opt/using/about-campaign-typologies.md)

* [Como criar um email em uma campanha](../../campaign/using/marketing-campaign-deliveries.md)

* [Como criar um informativo multilíngue com conteúdo condicional](../../delivery/using/conditional-content.md)

* [Como configurar e implantar um template do delivery](../../delivery/using/creating-a-delivery-template.md)

* [Como ativar e usar o AMP para emails](../../delivery/using/defining-interactive-content.md)

* [Como personalizar emails usando blocos de conteúdo dinâmico](../../delivery/using/personalization-blocks.md)

* [Como personalizar emails usando campos de personalização](../../delivery/using/personalization-fields.md)

* [Como gerenciar seed e provas em um email](../../delivery/using/steps-defining-the-target-population.md)

* [Como configurar uma entrega recorrente](../../workflow/using/recurring-delivery.md)

* [Como configurar uma entrega contínua](../../workflow/using/continuous-delivery.md)

Foram adicionadas informações sobre as verificações e ações a serem executadas ao obter o erro “Não foi possível resolver o nome do host” após a conexão com um servidor FTP. [Leia mais](../../platform/using/sftp-server-usage.md)

Novos casos de uso são mencionados na lista de [casos de uso de workflow](../../workflow/using/about-workflow-use-cases.md):

* Automação de criação, edição e publicação de conteúdo
* Configuração de um processo de aprovação de recipient antes do envio de um delivery
* Chamada de uma variável de instância em uma query
* Aplicar uma porcentagem dividida em uma população

A seção de atividade de **[!UICONTROL AND-join]** foi aprimorada com informações adicionais sobre sua utilização, bem como uma observação sobre o uso de variáveis. [Leia mais](../../workflow/using/and-join.md)

### Julho de 2020 {#july-2020}

Um caso de uso sobre como atualizar automaticamente uma lista usando um query incremental foi adicionado aos casos de uso do workflow. [Leia mais](../../workflow/using/about-workflow-use-cases.md)

As [Notas de versão](../../rn/using/latest-release.md) foram reorganizadas: uma [página de visão geral](../../rn/using/latest-release.md) foi adicionada com informações sobre status de criação, processo de atualização, recomendações e links importantes. Uma página dedicada às versões do [[!DNL Gold Standard] também foi ](../../rn/using/gold-standard.md) adicionada e a [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md) foi integrada.

Uma nova seção foi adicionada com diretrizes relacionadas ao monitoramento do Campaign Classic. [Leia mais](../../production/using/monitoring-guidelines.md)

A seção Privacidade e consentimento foi aprimorada com informações mais detalhadas e links úteis. [Leia mais](../../platform/using/privacy-and-recommendations.md)

A página de gerenciamento de privacidade no Campaign Classic foi atualizada com informações sobre o campo &quot;regulamento&quot;, que agora está disponível ao usar a API, permitindo a configuração do processo automático de solicitação de privacidade. [Leia mais](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

A página Visão geral do gerenciamento de privacidade foi atualizada para incluir informações sobre a Lei de Proteção de Dados Pessoais (PDPA) da Tailândia e sobre a Lei Geral de Dados (LGPD) do Brasil. [Leia mais](../../platform/using/privacy-and-recommendations.md)

Foram adicionadas informações sobre registros de subfluxos de trabalho e comportamento em caso de erro. [Leia mais](../../workflow/using/sub-workflow.md)

As práticas recomendadas foram adicionadas na seção atividade de **[!UICONTROL Scheduler]**. [Leia mais](../../workflow/using/scheduler.md)

### Junho de 2020 {#june-2020}

A seção Remoção de um endereço em quarentena foi atualizada. Ela esclarece os casos em que os endereços são removidos automaticamente da lista de quarentena. [Leia mais](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Casos de uso foram adicionados em como [criptografar](../../platform/using/zip-encrypt.md) e [descriptografar](../../platform/using/unzip-decrypt.md) dados usando o Painel de controle do Campaign e workflows do Campaign.

Os acionadores da Experience Cloud e a página de integração do Adobe Campaign Classic foram movidos [para cá](../../integrations/using/about-triggers.md).

### Julho de 2020 {#release-20-2}

**Novos recursos incluídos na versão 20.2**

Suporte a emoticons – [Leia mais](../../delivery/using/customizing-emoticon-list.md)

Conector FDA do Azure Synapse - [Leia mais](../../installation/using/configure-fda-synapse.md)

Leis de privacidade da Tailândia e do Brasil – [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**Outras atualizações de documentação que vêm com a versão**

A nova opção que permite desfazer a publicação de um template de mensagem transacional está documentada [nesta seção](../../message-center/using/publishing-message-templates.md#template-unpublication).

As novas opções que permitem definir limitações ao enviar emails que incluem imagens baixadas de um URL personalizado e anexos foram adicionadas à lista de opções do Campaign Classic. [Leia mais](../../installation/using/configuring-campaign-options.md#delivery)

A nova opção **Preparar as partes do delivery no banco de dados** está documentada [nesta seção](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis).

A seção Validação do delivery foi esclarecida e atualizada. [Leia mais](../../delivery/using/steps-validating-the-delivery.md)

Os parâmetros relacionados ao novo mecanismo de assinatura do link de rastreamento foram adicionados à seção [Arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md).

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

A seção fluxo de trabalho de limpeza foi atualizada. [Saiba mais](../../production/using/database-cleanup-workflow.md)

Os endpoints de rede do Campaign foram movidos para esta [seção](../../installation/using/campaign-network-endpoints.md).

A seção de instalação do Spam Assassin foi atualizada com o novo nome de arquivo de instalação. [Saiba mais](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

A seção sobre ambientes duplicados foi atualizada. [Saiba mais](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

### Maio de 2020 {#may-2020}

A seção Monitoramento da capacidade de delivery foi movida e aprimorada. [Leia mais](../../delivery/using/monitoring-deliverability.md)

A seção Solução de problemas da capacidade de delivery foi movida e aprimorada. [Leia mais](../../delivery/using/deliverability-faq.md)

As diretrizes de capacidade de delivery ao iniciar uma nova seção da plataforma foram aprimoradas. [Leia mais](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR)

A seção Enviar emails transacionais com anexos foi movida e atualizada. [Leia mais](../../message-center/using/transactional-email-with-attachments.md)

A seção Práticas recomendadas do pacote de dados foi movida e atualizada. [Leia mais](../../platform/using/working-with-data-packages.md#data-package-best-practices)

### Abril de 2020 {#april-2020}

A tabela de direitos da FDA foi movida para a documentação Acesso a um banco de dados externo (FDA). [Leia mais](../../installation/using/remote-database-access-rights.md)

As Perguntas frequentes estão atualizadas com dicas sobre como limpar o cache flexível e rígido. [Leia mais](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

As Práticas recomendadas do modelo de dados foi aprimorada com informações adicionais sobre os índices. [Leia mais](../../configuration/using/data-model-best-practices.md#indexes)

A seção que descreve o modelo de dados integrado do Adobe Campaign foi atualizada com mais detalhes em cada tabela. [Leia mais](../../configuration/using/data-model-description.md)

Os casos de uso do fluxo de trabalho foram atualizados e reorganizados em seções temáticas. [Leia mais](../../workflow/using/about-workflow-use-cases.md)

As seções [Qualificações de email de rejeição](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) e [Regras de gerenciamento de email](../../delivery/using/understanding-delivery-failures.md#email-management-rules) foram aprimoradas com informações atualizadas.

O artigo MTA aprimorado do Adobe Campaign foi atualizado. Ele agora só se aplica ao Campaign Classic. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-campaign-enhanced-mta.html)

### Março de 2020 {#march-2020}

As Práticas recomendadas do modelo de dados foram atualizadas com novas seções, que incluem [Sequências](../../configuration/using/data-model-best-practices.md#sequences), [Desempenho](../../configuration/using/data-model-best-practices.md#performance) e [Tabelas grandes](../../configuration/using/data-model-best-practices.md#large-tables), entre outras. [Leia mais](../../configuration/using/data-model-best-practices.md)

Uma nova seção que descreve o modelo de dados integrados do Adobe Campaign e a interação entre tabelas agora está disponível. [Leia mais](../../configuration/using/data-model-description.md)

Links chave adicionais foram adicionados à página inicial da documentação. [Leia mais](../../campaign-classic-home.md)

Um caso de uso foi adicionado sobre como integrar uma oferta dinâmica do Adobe Target a um email no Adobe Campaign. [Leia mais](../../integrations/using/inserting-a-dynamic-image.md)

Uma nova seção que detalha os diferentes idiomas disponíveis no Adobe Campaign está disponível. [Leia mais](../../platform/using/adobe-campaign-workspace.md#languages)

As diretrizes Gerenciamento de acesso foram atualizadas com mais informações sobre Direitos nomeados. [Leia mais](../../platform/using/access-management-named-rights.md)

### Fevereiro de 2020 {#february-2020}

Uma nova seção que descreve as práticas recomendadas e as principais recomendações ao projetar o template de dados do Adobe Campaign está disponível. [Leia mais](../../configuration/using/data-model-best-practices.md)

Uma nova seção está disponível sobre as Configurações de email técnico. [Leia mais](../../installation/using/email-deliverability.md)

As perguntas frequentes sobre a Capacidade do delivery foram atualizadas com mais detalhes sobre a mensagem de erro de &quot;cotas atendidas&quot;. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-deliverability-faq.html#FAQ)

O AMP for Email agora é compatível com novos provedores de email: a documentação relacionada foi atualizada. [Leia mais](../../delivery/using/defining-interactive-content.md)

A seção Arquivamento de email foi aprimorada. [Leia mais](../../installation/using/email-archiving.md#recommendations-and-limitations)

### Janeiro de 2020 {#release-20-1}

**Novos recursos incluídos na versão 20.1**

Conector FDA do Snowflake - [Leia mais](../../installation/using/configure-fda-snowflake.md)

Aprimoramento do conector FDA do Hadoop - [Leia mais](../../installation/using/configure-fda-hadoop.md)

**Outras atualizações de documentação que vêm com a versão**

Os guias de [instalação](../../installation/using/general-architecture.md), [produção](../../production/using/foreword.md) e [configuração](../../configuration/using/additional-parameters.md) foram atualizados com a nova unidade do sistema usada pela inicialização do serviço nlserver. Ainda é possível usar o /etc/init.d/nlserver6, mas a Adobe recomenda usar o comando systemctl agora para interagir com o serviço nlserver.

O guia de instalação foi atualizado e sincronizado com a versão mais recente da matriz de compatibilidade. Novos sistemas compatíveis foram adicionados. As ocorrências em sistemas obsoletos e sem suporte foram removidas. [Leia mais](../../installation/using/general-architecture.md)

A matriz de compatibilidade foi atualizada com os conectores do Hadoop 3.0 e Snowflake FDA. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Uma prática recomendada na afinidade IP foi adicionada ao guia de instalação. [Leia mais](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

A seção workflow de limpeza de banco de dados foi atualizada. Os números de lotes fornecidos agora refletem a implementação do código. [Leia mais](../../production/using/database-cleanup-workflow.md)

Uma limitação no FDA sobre HTTP foi adicionada ao guia de mensagens transacionais. [Leia mais](../../production/using/database-cleanup-workflow.md)

Adicionamos informações sobre a nova opção que permite definir um período de tempo limite para as atividades de workflow **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]**. [Leia mais](../../workflow/using/sql-code-and-javascript-code.md)

Adicionamos informações sobre a nova visualização **[!UICONTROL Start Pending]** disponível no nó **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]**. [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

O guia [Envio de notificações via push](../../delivery/using/about-mobile-app-channel.md) foi movido, reorganizado e aprimorado com informações mais claras:

O novo parâmetro para a configuração do relatório de URLs está documentado [aqui](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

A página **Matriz de recursos no local e hospedada do Campaign Classic** foi atualizada com os novos conectores do FDA. [Leia mais](../../installation/using/capability-matrix.md).

A página **Matriz de recursos do Campaign Classic** foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

O novo **[!UICONTROL Cleanup of Nmsaddress]** workflow está documentado [aqui](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

Adicionamos uma limitação ao usar uma atividade de query em um workflow. [Leia mais](../../workflow/using/query.md).

Adicionamos uma nova seção para detalhar as regras aprimoradas de validação de endereço de email para enviá-lo para a quarentena em caso de erro de software. [Leia mais](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

O parâmetro do arquivo de configuração indicando se uma instância está usando ou não o MTA aprimorado foi documentado. [Leia mais](../../installation/using/the-server-configuration-file.md#mta)

A seção Deliverability foi movida, reorganizada e aprimorada com conteúdo atualizado. [Leia mais](../../delivery/using/about-deliverability.md)

Uma nova seção que descreve as noções básicas do modelo de dados do Adobe Campaign Classic e como acessar a descrição de cada tabela está disponível. [Leia mais](../../configuration/using/about-data-model.md)

O artigo sobre MTA aprimorado do Adobe Campaign foi atualizado com informações mais detalhadas sobre a instalação de um pacote de Tipologia específico em instâncias que não adicionam os cabeçalhos MTA aprimorados necessários a cada mensagem. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

Os casos de uso relacionados ao design de consulta foram reorganizados em seções separadas. [Leia mais](../../workflow/using/querying-recipient-table.md)

Uma nova seção sobre dicas e truques para gerenciar ofertas e usar o módulo de interação no Adobe Campaign Classic está disponível. [Leia mais](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

A documentação da interação foi aprimorada com links para vários vídeos que ajudam a entender melhor como gerenciar ofertas. [Leia mais](../../interaction/using/interaction-and-offer-management.md)

O artigo de práticas recomendadas sobre como otimizar as consultas executadas em sua instância foi integrado à documentação. [Leia mais](../../workflow/using/query.md#optimizing-queries)

O guia de relatórios foi atualizado e reorganizado. [Leia mais](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Um exemplo de como usar uma variável de instância em um fluxo de trabalho foi adicionado. [Leia mais](../../workflow/using/javascript-scripts-and-templates.md)

## 2019

### Dezembro de 2019 {#december-2019}

A opção &quot;WdbcOptions_TempDbName&quot; foi adicionada à lista de opções do Campaign. [Leia mais](../../installation/using/configuring-campaign-options.md)

A página da matriz FDA foi movida para [este local](../../installation/using/remote-database-access-rights.md).

A página da matriz de direitos de acesso foi movida [aqui](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en).

A seção que descreve como definir conteúdo interativo com AMP foi movida. [Leia mais](../../delivery/using/defining-interactive-content.md)

**Novos recursos incluídos na versão 19.2**

Lei de Privacidade do Consumidor da Califórnia (CCPA) - [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html)

Conteúdo interativo com AMP - [Leia mais](../../delivery/using/defining-interactive-content.md)

Monitoramento ao vivo do fluxo de trabalho - [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Sistema de Mensagens Seguras de SMS (TLS) - [Leia mais](https://helpx.adobe.com/br/campaign/kb/sms-connector-protocol-and-settings.html)

**Outras atualizações de documentação que vêm com a versão**

A documentação MTA aprimorada do Adobe Campaign está disponível. [Leia mais](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

Uma nova seção foi adicionada sobre como solucionar problemas de um workflow que permanece no estado &quot;Start as soon as possible&quot; em uma campanha. [Leia mais](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

As novas opções &quot;NmsOperation_DeliveryPreparationWindow&quot; e &quot;WdbcKillSessionPolicy&quot; foram adicionadas à lista de opções do Campaign. [Leia mais](../../installation/using/configuring-campaign-options.md)

Um novo documento que descreve as noções básicas do modelo de dados do Adobe Campaign Classic está disponível. [Leia mais](https://experienceleague.adobe.com/docs/campaign-classic/using/configuring-campaign-classic/data-model/about-data-model.html?lang=pt-BR)

A nova opção **Maximum personalization run time** nas propriedades do delivery está documentada nesta [seção](../../delivery/using/personalization-fields.md#timing-out-personalization).

Os exemplos de chamadas de API usando um **HttpServletRequest** com logon() e query() foram atualizados. [Leia mais](../../configuration/using/web-service-calls.md).

Uma recomendação para o atributo **sqlDefault** na definição do esquema foi adicionada. [Leia mais](../../configuration/using/schema/attribute.md)).

A integração entre o Adobe Campaign e a Adobe Real-time Customer Data Platform agora é mencionada no guia **Integração com a Adobe Experience Cloud**. [Leia mais](../../integrations/using/about-campaign-integrations.md).

### Novembro de 2019 {#november-2019}

Um aviso foi adicionado às seções [Multiplexação do servidor mid-sourcing](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) e [Suporte a várias seções de instâncias de controle](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances), mencionando que essas implantações não são suportadas para clientes totalmente hospedados e híbridos.

Uma nova seção foi adicionada para descrever como forçar a codificação de caracteres usada ao enviar um email. [Leia mais](../../delivery/using/sending-messages.md#character-encoding)

A seção &quot;Gerenciamento de acesso&quot; foi atualizada com o **Direito de dados de privacidade**. [Leia mais](../../platform/using/access-management-named-rights.md)

Foram adicionadas informações para especificar que o conteúdo dos campos de personalização não pode exceder 1024 caracteres. [Leia mais](../../delivery/using/personalization-fields.md)

A documentação do Painel de controle do Campaign foi integrada ao novo conjunto de documentação colaborativa. [Leia mais](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR)

O guia de introdução às práticas recomendadas de delivery foi atualizado. [Leia mais](../../delivery/using/delivery-best-practices.md)

### Outubro de 2019 {#october-2019}

A lista de mensagens de erro para o Campaign foi atualizada. [Leia mais](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=pt-BR)

O guia de introdução ao GDPR foi melhorado e aprimorado. Agora se trata uma documentação de gerenciamento de privacidade, incluindo o GDPR e o CCPA. [Leia mais](https://helpx.adobe.com/content/help/br/campaign/kb/campaign-privacy.html)

Uma nova página de solução de problemas foi adicionada para rastreamento no Campaign Classic. [Leia mais](https://helpx.adobe.com/br/campaign/kb/classic-tracking-troubleshooting.html).

Uma nova página de práticas recomendadas do Adobe Analytics Connector foi adicionada. [Leia mais sobre o Adobe Analytics Connector](../../platform/using/adobe-analytics-connector.md)

O guia de introdução às práticas recomendadas de delivery foi movido e atualizado. [Leia mais](../../delivery/using/delivery-best-practices.md)

Uma recomendação foi adicionada à documentação do canal SMS para evitar problemas ao usar várias contas externas aproveitando o conector SMPP genérico estendido com a mesma conta do provedor. [Leia mais](../../delivery/using/sms-set-up.md#automatic-reply)

Foram adicionadas informações na documentação de atividade do Scheduler sobre como evitar execuções simultâneas de um fluxo de trabalho. [Leia mais](../../workflow/using/scheduler.md)

As etapas para configurar a renderização da caixa de entrada para instalações locais foram adicionadas à documentação. [Leia mais](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

### Setembro de 2019 {#september-2019}

Uma nova página foi adicionada para fornecer orientações gerais para a manutenção do Campaign Classic. [Leia mais](../../production/using/monitoring-guidelines.md)

As informações relacionadas ao monitoramento de workflows foram centralizadas em uma nova seção dedicada. [Leia mais](../../workflow/using/monitoring-workflow-execution.md).

Uma nova página sobre diretrizes gerais para rastreamento no Adobe Campaign Classic foi adicionada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-tracking.html).

As práticas recomendadas para aprimoramentos de desempenho de workflows e deliveries foram atualizadas. [Leia mais sobre workflows](../../workflow/using/workflow-best-practices.md) e [mais sobre deliveries](../../delivery/using/delivery-performances.md#best-practices-performance).

### Maio de 2019 {#release-19-1}

**Novos recursos incluídos na versão 19.1**

Painel de controle - [Leia mais](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)

Trilha de auditoria - [Leia mais](../../production/using/audit-trail.md)

**Outras atualizações de documentação que vêm com a versão**

Foi criada uma atualização das perguntas frequentes sobre a nova build. [Leia mais](https://helpx.adobe.com/br/campaign/kb/build-upgrade-faq.html)

A [Matriz de compatibilidade](compatibility-matrix.md) foi atualizada. A lista de sistemas de banco de dados permitidos foi atualizada, assim como as versões do Android/iOS e SDKs relacionados. A Matriz de compatibilidade 19.0 foi arquivada.

A página &quot;Deprecated and Removed Features in Campaign Classic&quot; foi atualizada. [Leia mais](deprecated-features.md)

A descrição do arquivo de configuração do servidor foi adicionada ao guia de instalação. [Leia mais](../../installation/using/the-server-configuration-file.md)

Uma seção foi adicionada descrevendo as etapas de instalação e configuração para modelos hospedados e híbridos. [Leia mais](../../installation/using/hosting-models.md)

Uma seção foi adicionada descrevendo as etapas de desinstalação do servidor do Campaign. [Leia mais](../../installation/using/uninstalling-campaign.md)

Os guias de introdução de [segurança](https://helpx.adobe.com/br/campaign/kb/acc-security.html), [delivery](../../delivery/using/about-deliverability.md) e [privacidade](../../platform/using/privacy-management.md) foram atualizados.

A descrição da opção de fluxo de trabalho de pré-processo foi atualizada para refletir as alterações no produto. [Leia mais](../../workflow/using/data-loading--file-.md)

A nota técnica de Acionadores da Experience Cloud foi atualizada. [Leia mais](../../integrations/using/about-triggers.md)

A lista de mensagens de erro foi atualizada. [Leia mais](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html)

Foram adicionadas mais informações sobre métodos de autenticação SOAP para mensagens transacionais. [Leia mais](../../message-center/using/event-description.md)

As etapas de configuração do Apache foram atualizadas. [Leia mais](../../installation/using/integration-into-a-web-server-for-linux.md)

Uma nova página foi adicionada, incluindo a lista de terminais para o Classic. [Leia mais](../../installation/using/campaign-network-endpoints.md)

O artigo de práticas recomendadas do pacote de dados foi atualizado. [Leia mais](../../configuration/using/data-model-best-practices.md)

A documentação de gerenciamento de ofertas foi atualizada com uma nova seção que lista as práticas recomendadas. [Leia mais](../../interaction/using/interaction-best-practices.md)

Um novo artigo da knowledge base sobre como usar o catálogo de oferta no Adobe Campaign Classic foi criado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/offer-best-practices.html)

A seção Sub-workflow activity foi aprimorada com um exemplo de uso. [Leia mais](../../workflow/using/sub-workflow.md)

A página [Matriz de recursos no local e hospedada do Campaign Classic](../../installation/using/capability-matrix.md) foi atualizada com informações relacionadas a email Cco.

A documentação de Mensagens transacionais foi atualizada com uma nota relacionada à publicação do modelo. [Leia mais](../../message-center/using/publishing-message-templates.md#template-publication)

A seção Unprocessed bounce mails foi atualizada com mais detalhes sobre os campos Forwarding address e Address for errors. [Leia mais](../../installation/using/deploying-an-instance.md)

Uma nova seção sobre práticas recomendadas de planejamento de workflow foi adicionada. [Leia mais](../../workflow/using/workflow-best-practices.md)

Foram adicionadas duas novas opções à lista de opções do Campaign: XtkSecurity_Restrict_EditXML e NmsOperation_OperationMgtDebug.
[Leia mais](../../installation/using/configuring-campaign-options.md)

Foram adicionadas informações sobre as diferentes contas externas disponíveis no Campaign Classic e como configurá-las.
[Leia mais](../../installation/using/external-accounts.md)

Atualização da seção do Analytics Connector para refletir mudanças na interface.
[Leia mais](../../platform/using/adobe-analytics-connector.md)

Foram adicionadas informações sobre o relatório de faturamento.
[Leia mais](../../production/using/monitoring-processes.md)

Atualização da documentação sobre a integração de públicos-alvo compartilhados.
[Leia mais](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

A nota técnica a seguir foi atualizada: [Protocolo e configurações do conector SMS](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html).

A seção Technical workflows foi atualizada. [Leia mais](../../workflow/using/about-technical-workflows.md)

O procedimento de Configuração do nome de domínio do Campaign foi aprimorado e atualizado.

O Guia de dimensionamento de hardware do Campaign foi atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html)

Foram adicionadas informações sobre a Faixa de consulta para a conta externa de teradados. [Leia mais](../../installation/using/external-accounts.md)

### Janeiro de 2019{#release-doc-16-01-2019}

A nota técnica de Acionadores da Experience Cloud foi atualizada. [Leia mais](../../integrations/using/about-triggers.md)

Uma nota foi adicionada na seção de aprovação da oferta para especificar que a menção &quot;Content approved&quot; indica que o processo de aprovação do conteúdo foi realizado, se todas as ofertas foram habilitadas/aprovadas ou não. [Leia mais](../../interaction/using/offer-catalog-overview.md)

Uma nova seção foi adicionada na guia Installation, listando as opções do nó Administration / Platform / Options. [Leia mais](../../installation/using/configuring-campaign-options.md)

Foram adicionadas informações sobre o uso de seed addresses para proteger a lista de mala direta. [Leia mais](../../delivery/using/creating-seed-addresses.md)

As etapas principais ao criar e enviar um delivery foram reagrupadas em uma nova seção, com referências aos vários canais quando necessário. [Leia mais](../../delivery/using/steps-about-delivery-creation-steps.md)

A seção [Email archiving](../../installation/using/email-archiving.md) foi movida, reorganizada e aprimorada com informações mais claras:

* Foram adicionadas as práticas recomendadas relacionadas aos emails por conexão e aos parâmetros de IPs de envio com Cco.

* Atualizamos as etapas para migrar para o novo sistema de arquivamento de emails (Cco) se você já estava usando o arquivamento de emails com uma build mais antiga (antes do Adobe Campaign 17.2 - build 8795).

Um caso de uso foi adicionado ao guia de Automatização com workflows: enviar alertas personalizados para operadores. [Leia mais](../../workflow/using/sending-personalized-alerts-to-operators.md)

A seção &quot;Migrating to a new version&quot; foi atualizada. A documentação agora só detalha as etapas de migração para o Adobe Campaign Classic v7 de qualquer versão anterior, pois não é mais possível migrar para o Adobe Campaign v6.11. [Leia mais](../../migration/using/about-migration.md)

A seção &quot;Retries after a delivery temporary failure&quot; foi esclarecida. [Leia mais](../../delivery/using/understanding-delivery-failures.md)

Os links para a seção &quot;Digital Content Editor&quot; foram adicionados à seção &quot;Defining the email content&quot;. [Leia mais](../../delivery/using/defining-the-email-content.md)

A seção &quot;Transactional messaging architecture&quot; foi atualizada com um aviso especificando que as instâncias de controle e execução não podem ser instaladas na mesma máquina. [Leia mais](../../message-center/using/transactional-messaging-architecture.md)

A seção &quot;Workflow monitoring&quot; foi atualizada com uma nota para builds entre 8700 e 8977 (18.10), incluindo um link para a nota técnica sobre como instalar o pacote HeatMap de fluxo de trabalho para essas builds. [Leia mais](../../workflow/using/heatmap.md)

Foi adicionado um caso de uso sobre como enviar um email com campos de dados personalizados usando a atividade Enrichment em um fluxo de trabalho. [Leia mais](../../workflow/using/email-enrichment-with-custom-date-fields.md)

Os vídeos em destaque foram movidos para [este local](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
