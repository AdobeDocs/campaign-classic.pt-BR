---
title: Atualizações da documentação do Adobe Campaign Classic
description: Esta página lista todos os novos recursos e atualizações de documentação para cada versão do Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 295dcd0ac302194df5e202ccabb579f006ed5651

---


# Atualizações da documentação{#documentation-updates}

Saiba mais sobre todas as atualizações mais recentes da documentação do Adobe Campaign Classic.

Esta página lista todos os novos recursos e atualizações de documentação para cada versão do Adobe Campaign Classic.

Você também pode consultar as Notas [de versão do](../../rn/using/latest-release.md)Adobe Campaign Classic.

## Março de 2020 {#march-2020}

A página de práticas recomendadas do modelo de dados foi atualizada com novas seções, incluindo [Sequências](../../configuration/using/data-model-best-practices.md#sequences), [Desempenho](../../configuration/using/data-model-best-practices.md#performance) e tabelas [](../../configuration/using/data-model-best-practices.md#large-tables)Grandes, entre outras. [Leia mais](../../configuration/using/data-model-best-practices.md)

Uma nova seção que descreve o modelo de dados predefinido do Adobe Campaign e a interação das tabelas predefinidas está disponível. [Leia mais](../../configuration/using/data-model-description.md)

Recursos adicionais foram adicionados ao home page de documentação. [Leia mais](../../campaign-classic-home.md)

Um caso de uso foi adicionado sobre como integrar uma oferta dinâmica do Público alvo da Adobe a um email no Adobe Campaign. [Leia mais](../../integrations/using/inserting-a-dynamic-image.md)

Uma nova seção que detalha os diferentes idiomas disponíveis no Adobe Campaign está disponível. [Leia mais](../../platform/using/adobe-campaign-workspace.md#languages)

A página Gerenciamento de acesso foi atualizada com mais informações sobre Direitos nomeados. [Leia mais](../../platform/using/access-management.md#named-rights)

## Fevereiro de 2020 {#february-2020}

Uma nova seção que descreve as práticas recomendadas e as principais recomendações enquanto projeta o modelo de dados do Adobe Campaign está disponível. [Leia mais](../../configuration/using/data-model-best-practices.md)

A seção &quot;Enviabilidade por email&quot; foi renomeada para &quot;Configurações de email técnico&quot;. [Leia mais](../../installation/using/email-deliverability.md)

O documento de perguntas frequentes sobre a entrega foi atualizado com mais detalhes sobre a mensagem de erro &quot;cotas atendidas&quot;. [Leia mais](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ)

A AMP para email agora é suportada por três provedores de email (Gmail, Outlook e Mail.ru), a seção que descreve como definir conteúdo interativo com AMP foi atualizada. [Leia mais](../../delivery/using/defining-interactive-content.md)

A seção de arquivamento de e-mail foi esclarecida. [Leia mais](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**Novos recursos incluídos na versão**

Conector FDA Floco de Neve - [Leia mais](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Aprimoramentos do conector FDA Hadoop - [Leia mais](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Outras atualizações de documentação que vêm com a versão**

Os guias [de instalação](../../installation/using/before-reading.md), [produção](../../production/using/foreword.md) e [configuração](../../configuration/using/additional-parameters.md) foram atualizados com a nova unidade do sistema usada pela inicialização do serviço nlserver. Você ainda pode usar /etc/init.d/nlserver6, mas recomendamos que agora você use o comando systemctl para interagir com o serviço nlserver.

O guia de instalação foi atualizado e sincronizado com a versão mais recente da matriz de compatibilidade. Novos sistemas suportados foram adicionados. Ocorrências em sistemas obsoletos e sem suporte foram removidas. [Leia mais](../../installation/using/before-reading.md)

A matriz de compatibilidade foi atualizada com os conectores Hadoop 3.0 e Snowflake FDA. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Uma prática recomendada na afinidade IP foi adicionada ao guia de instalação. [Leia mais](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

A seção de fluxo de trabalho de limpeza do banco de dados foi atualizada. Os números de lote fornecidos agora refletem a implementação do código. [Leia mais](../../production/using/database-cleanup-workflow.md)

Uma limitação em FDA sobre HTTP foi adicionada ao guia de mensagens transacionais. [Leia mais](../../production/using/database-cleanup-workflow.md)

Foram adicionadas informações sobre a nova opção que permite definir um período de tempo limite para as atividades de fluxo de trabalho **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** . [Leia mais](../../workflow/using/sql-code-and-javascript-code.md)

Foram adicionadas informações sobre a nova **[!UICONTROL Start Pending]** visualização disponível no nó **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** . [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

O guia [Enviar notificações](../../delivery/using/about-mobile-app-channel.md) por push foi movido, reorganizado e aprimorado com informações esclarecidas.

O novo parâmetro para a configuração do relatório de URLs foi documentado [aqui](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

A página de matriz **de recursos no local e hospedado do** Campaign Classic foi atualizada com os novos conectores de FDA. [Leia mais](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

A página da matriz **de recursos do** Campaign Classic foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

O novo **[!UICONTROL Cleanup of Nmsaddress]** fluxo de trabalho foi documentado [aqui](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

Uma limitação foi adicionada ao usar uma atividade de query em um fluxo de trabalho. [Leia mais](../../workflow/using/query.md).

Uma nova seção foi adicionada para detalhar as regras aprimoradas de validação de endereço de email para enviar um endereço para a quarentena em caso de erro de software. [Leia mais](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

O parâmetro do arquivo de configuração que indica que uma instância está usando o MTA aprimorado ou não está documentado. [Leia mais](../../installation/using/the-server-configuration-file.md#mta)

## January 2020 {#january-2020}

A seção Disponibilidade foi movida, reorganizada e aprimorada com conteúdo atualizado. [Leia mais](../../delivery/using/about-deliverability.md)

Uma nova seção que descreve as noções básicas do modelo de dados Adobe Campaign Classic e como acessar a descrição de cada tabela está disponível. [Leia mais](../../configuration/using/about-data-model.md)

O artigo MTA aprimorado de Adobe Campaign foi atualizado com informações mais detalhadas sobre a instalação de um pacote de Tipologia específico em instâncias que não adicionam os cabeçalhos MTA aprimorados necessários a cada mensagem. [Leia mais](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html#impacts)

Os casos de uso relacionados à criação de query foram reorganizados em seções separadas. [Leia mais](../../workflow/using/querying-recipient-table.md)

Uma nova seção sobre dicas e truques para gerenciar o oferta e usar o módulo de interação no Adobe Campaign Classic está disponível. [Leia mais](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

A documentação de Interação foi aprimorada com links para vários vídeos que ajudam a entender melhor como gerenciar o oferta. [Leia mais](../../interaction/using/interaction-and-offer-management.md)

O artigo de práticas recomendadas sobre como otimizar os query em execução em sua instância foi integrado à documentação. [Leia mais](../../workflow/using/query.md#optimizing-queries)

O guia do Relatórios foi atualizado e reorganizado. [Leia mais](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Um exemplo de como usar uma variável de instância em um fluxo de trabalho foi adicionado. [Leia mais](../../workflow/using/javascript-scripts-and-templates.md)

## December 2019 {#december-2019}

A opção &quot;WdbcOptions_TempDbName&quot; foi adicionada à lista de opções de Campanha. [Leia mais](../../installation/using/configuring-campaign-options.md)

A página da matriz FDA foi movida [aqui](/help/rn/using/assets/fda_rdbms_rights.pdf).

A página da Matriz de direitos de acesso foi movida [aqui](https://docs.adobe.com/content/help/en/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf).

A seção que descreve como definir conteúdo interativo com AMP foi movida. [Leia mais](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**Novos recursos incluídos na versão**

California Consumer Privacy Act (CCPA) - [Leia mais](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Conteúdo interativo com AMP - [Leia mais](../../delivery/using/defining-interactive-content.md)

Monitoramento ao vivo do fluxo de trabalho - [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

TLS (Secure SMS Messaging) - [Leia mais](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**Outras atualizações de documentação que vêm com a versão**

A documentação MTA aprimorada do Adobe Campaign agora está disponível. [Leia mais](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)

Uma nova seção foi adicionada sobre como solucionar problemas de um fluxo de trabalho que permanece no estado &quot;Start assim que possível&quot; em uma campanha. [Read more](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

As novas opções &quot;NmsOperation_DeliveryPreparationWindow&quot; e &quot;WdbcKillSessionPolicy&quot; foram adicionadas à lista de opções de Campanha. [Leia mais](../../installation/using/configuring-campaign-options.md)

Um novo documento que descreve as noções básicas do modelo de dados Adobe Campaign Classic está disponível. [Leia mais](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

A nova opção **Máximo de tempo** de execução de personalização nas propriedades do delivery está documentada nesta [seção](../../delivery/using/personalization-fields.md#timing-out-personalization).

Os exemplos de chamadas de API usando um **HttpServletRequest** com logon() e query() foram atualizados. [Leia mais](../../configuration/using/web-service-calls.md).

Uma recomendação para o atributo **sqlDefault** na definição do schema foi adicionada. [Leia mais](../../configuration/using/elements-and-attributes.md#attribute-description).

A integração entre o Adobe Campaign e a Plataforma de dados do cliente em tempo real da Adobe agora é mencionada no guia **Integração com a Adobe Experience Cloud** . [Leia mais](../../integrations/using/about-campaign-integrations.md).

## November 2019 {#november-2019}

Foi adicionado um aviso ao [Multiplexing the mid-sourcing server](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) e ao [Supporting várias seções do instância de controle](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) mencionando que essas implantações não são compatíveis com clientes totalmente hospedados e híbridos.

Uma nova seção foi adicionada para descrever como forçar a codificação de caracteres usada ao enviar um email. [Leia mais](../../delivery/using/sending-messages.md#character-encoding)

A seção Gerenciamento de acesso foi atualizada com o direito **de dados de** privacidade. [Leia mais](../../platform/using/access-management.md#named-rights)

Foram adicionadas informações para especificar que o conteúdo dos campos de personalização não pode exceder 1024 caracteres. [Leia mais](../../delivery/using/personalization-fields.md)

A documentação do Painel de controle foi integrada ao novo conjunto de documentação colaborativa. [Leia mais](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

O guia Práticas recomendadas de introdução ao Delivery foi atualizado. [Leia mais](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

## Outubro de 2019 {#october-2019}

A lista de mensagens de erro para Campaign Standard e Campaign Classic foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

O guia de introdução ao RGPD foi melhorado e enriquecido. Agora é uma documentação de gerenciamento de privacidade, incluindo o RGPD e o CCPA. [Leia mais](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

Uma nova página de solução de problemas foi adicionada para rastreamento no Campaign Classic. [Leia mais](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html).

Uma nova página de práticas recomendadas para o Adobe Analytics Data Connector foi adicionada. [Leia mais sobre o Adobe Analytics Data Connector](../../platform/using/adobe-analytics-data-connector.md)

O guia de introdução às práticas recomendadas do Delivery foi movido e atualizado. [Leia mais](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

Uma recomendação foi adicionada à documentação do canal SMS para evitar problemas ao usar várias contas externas aproveitando o conector SMPP genérico estendido com a mesma conta do provedor. [Leia mais](../../delivery/using/sms-channel.md#automatic-reply)

Foram adicionadas informações na documentação da atividade do Scheduler sobre como evitar execuções simultâneas de um fluxo de trabalho. [Leia mais](../../workflow/using/scheduler.md)

As etapas para configurar a renderização da Caixa de entrada para instalações locais foram adicionadas à documentação. [Leia mais](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## Setembro de 2019 {#september-2019}

Uma nova página foi adicionada para fornecer orientações gerais para a manutenção da Campaign Classic. [Leia mais](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)

As informações relacionadas com a monitorização de workflows foram centralizadas numa nova seção dedicada. [Leia mais](../../workflow/using/monitoring-workflow-execution.md).

Uma nova página sobre as diretrizes gerais para rastreamento no Adobe Campaign Classic foi adicionada. [Leia mais](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

As práticas recomendadas para melhorias de desempenho de workflows e delivery foram atualizadas. [Leia mais sobre workflows](../../workflow/using/workflow-best-practices.md) e [mais sobre delivery](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 - 30/05/2019{#release-19-1}

**Novos recursos incluídos na versão**

Painel de controle - [Leia mais](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

Trilha de auditoria - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Audit_trail.html)

**Outras atualizações de documentação que vêm com a versão**

Uma nova pergunta frequentes sobre atualização da compilação foi criada. [Leia mais](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

A matriz [Compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) foi atualizada. A lista de sistemas de banco de dados suportados foi atualizada, assim como versões Android/iOS e SDKs relacionados. A matriz [de compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html) 19.0 foi arquivada.

A página &#39;Recursos removidos e obsoletos no Campaign Classic&#39; foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

A descrição do arquivo de configuração do servidor foi adicionada ao guia de instalação. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Uma seção foi adicionada descrevendo as etapas de instalação e configuração para modelos hospedados e híbridos. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Uma seção foi adicionada descrevendo as etapas de desinstalação do servidor de Campanha. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

Os guias de [segurança](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html), [entrega](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) e [privacidade](https://helpx.adobe.com/campaign/kb/acc-privacy.html) de introdução foram atualizados.

A descrição da opção de fluxo de trabalho pré-processo foi atualizada para refletir as alterações no produto. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

A nota técnica dos Acionadores da Marketing Cloud foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Foram adicionadas mais informações sobre métodos de autenticação SOAP para mensagens transacionais. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

As etapas de configuração do Apache foram atualizadas. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

Uma nova página foi adicionada, incluindo a lista de pontos de extremidade para Campaign Standard e Classic. [Leia mais](https://helpx.adobe.com/campaign/kb/campaign-endpoints.html)

O artigo de práticas recomendadas para o Pacote de dados foi atualizado. [Leia mais](https://helpx.adobe.com/campaign/kb/data-package-best-practices.html)

A documentação de Gerenciamento de Ofertas foi atualizada com uma nova seção que lista as práticas recomendadas. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

Um novo artigo da Base de conhecimento sobre como usar o catálogo de oferta no Adobe Campaign Classic foi criado. [Leia mais](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

A seção atividade Sub-fluxo de trabalho foi aprimorada com um exemplo de uso. [Leia mais](../../workflow/using/sub-workflow.md)

O artigo da base de conhecimento da matriz [de recursos local e hospedada do](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html) Campaign Classic foi atualizado com informações relacionadas a e-mails de arquivamento.

A documentação de Mensagens transacionais foi atualizada com uma nota relacionada à publicação do modelo. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

A seção Mensagens de rejeição não processadas foi atualizada com mais detalhes sobre os campos Endereço de encaminhamento e Endereço para erros. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

Uma nova seção sobre práticas recomendadas de planejamento de fluxo de trabalho foi adicionada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Adicionadas duas novas opções à lista de opções de Campanha: XtkSecurity_Restrict_EditXML e NmsOperation_OperationMgtDebug.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Foram adicionadas informações sobre as diferentes contas externas disponíveis no Campaign Classic e como configurá-las.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

Atualização da seção Conector de dados do Analytics para refletir alterações na interface.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Foram adicionadas informações sobre o relatório Faturamento.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

Atualização da documentação sobre a integração do Shared audiência.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

As seguintes notas técnicas foram atualizadas: protocolo e configurações [do conector](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html) SMS e geração [automática](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)de sequência.

A seção Workflows técnicos foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

O procedimento de Configuração de Nome de Domínio de Campanha foi melhorado e atualizado. [Leia mais](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)

O procedimento de migração para aplicativos Android do Google Cloud Messaging (GCM) para o Firebase Cloud Messaging (FCM) foi atualizado. [Leia mais](https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html)

O Guia de dimensionamento de hardware da Campanha foi atualizado. [Leia mais](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

Foram adicionadas informações sobre a marca do Query para a conta externa Teradata. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## January 2019{#release-doc-16-01-2019}

A nota técnica dos Acionadores da Marketing Cloud foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Uma nota foi adicionada na seção de aprovação da oferta para especificar que a menção &quot;Conteúdo aprovado&quot; indica que o processo de aprovação do conteúdo foi realizado, se todas as ofertas foram ativadas/aprovadas ou não. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

Uma nova seção foi adicionada no guia Instalação, listando as opções do nó Administração / Plataforma / Opções. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Foram adicionadas informações sobre o uso de seeds addresses para proteger sua lista de correio. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

As etapas principais ao criar e enviar um delivery foram agrupadas em uma nova seção, com referências aos vários canais, quando necessário. [Leia mais](../../delivery/using/steps-about-delivery-creation-steps.md)

A seção de arquivamento [de](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) email foi movida, reorganizada e aprimorada com informações esclarecidas:

* Foram adicionadas as práticas recomendadas relacionadas aos emails por conexão e aos parâmetros de IPs de envio de Cco. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* Atualizamos as etapas para atualizar para o novo sistema de arquivamento de e-mails (BCC) se você já estava usando o arquivamento de e-mails com uma versão mais antiga (anterior ao Adobe Campaign 17.2 - build 8795). [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Um caso de uso foi adicionado ao guia Automatização com Workflows: Envio de alertas personalizados para operadores. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

A seção &quot;Migração para uma nova versão&quot; foi atualizada. A documentação agora só detalha as etapas para a migração para o Adobe Campaign Classic v7 de qualquer versão mais antiga, pois não é mais possível migrar para o Adobe Campaign v6.11. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

A seção &quot;Tentativas após uma falha temporária de delivery&quot; foi esclarecida. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

Links para a seção &quot;Editor de conteúdo digital&quot; foram adicionados à seção &quot;Definição do conteúdo do email&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

A seção &quot;Transactional Messaging Architecture&quot; foi atualizada com um aviso especificando que o controle e as instâncias de execução não podem ser instalados na mesma máquina. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

A seção &quot;Monitoramento de fluxo de trabalho&quot; foi atualizada com uma nota para compilações entre 8700 e 8977 (18.10), incluindo um link para a nota técnica sobre como instalar o pacote HeatMap de fluxo de trabalho para essas compilações. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

Adicionado um caso de uso sobre como enviar um email com campos de dados personalizados usando a atividade do Enriquecimento em um fluxo de trabalho. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

Os vídeos de recursos foram movidos [aqui](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html).

Duas notas técnicas foram adicionadas ao [Teradata](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html) e ao [MySQL 5.7](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html).

## 18.10 - 05/11/2018{#release-18-10}

**Novos recursos incluídos na versão**

Melhorias na notificação por push - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

atividade de Gestão de dados SQL - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

Monitoramento do fluxo de trabalho - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**Outras atualizações de documentação que vêm com a versão**

As APIs do Campaign Classic agora estão disponíveis em uma [página dedicada](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Se estiver usando o arquivo jsapi.chm, agora deverá fazer referência a nova versão online.

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

A página &#39;Recursos removidos e obsoletos no Campaign Classic&#39; foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

Nas notas [de](https://docs.campaign.adobe.com/doc/AC/en/RN.html) versão e notas [de versão](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html)herdadas, foi adicionado um aviso para compilações que foram lembradas. Também foram adicionados os builds acumulados para 17.9, 18.4 e 18.6.

Os guias de [segurança](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html), [entrega](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) e atualização [de](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) compilação foram atualizados.

O guia de introdução da [privacidade](https://helpx.adobe.com/campaign/kb/acc-privacy.html) foi atualizado com informações sobre como chamar a API externamente e como usar queryDef para o query para obter o status e baixar o arquivo RGPD.

Adicionado um caso de uso de mensagens transacionais para adicionar anexos de e-mail dinamicamente aos despachos enviados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

Atualização da seção de solução de problemas de limites de conexão. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

Uma seção foi adicionada sobre como configurar uma conexão proxy. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

Atualização da seção sobre a restrição de comandos externos autorizados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

Adicionada uma seção de solução de problemas relacionada ao uso do SFTP. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

A seção de visão geral do guia Enviar mensagens foi reorganizada. Foram adicionadas informações sobre o processo global de criação de delivery e os diferentes tipos de delivery. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

A seção sobre como usar seeds addresses foi movida para o capítulo de visão geral do guia Enviar mensagens. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Adicionado um novo caso de uso do fluxo de trabalho: Gerenciando atualizações de execuções concomitantes de fluxo de trabalho. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

A seção &quot;Renderização da caixa de entrada&quot; foi atualizada com mais informações sobre o Litmus e um procedimento mais detalhado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

A seção &quot;SpamAssassin&quot; foi aprimorada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

Um caso de uso foi adicionado à seção &quot;Gerenciamento da fadiga de marketing com regras de pressão&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

Um novo caso de uso que descreve como criar um fluxo de trabalho de delivery entre canais está disponível. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

Algumas recomendações foram adicionadas à seção &quot;Arquivamento de e-mails&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

Uma nova recomendação foi adicionada em relação à resolução mínima de tela para o uso ideal do Adobe Campaign. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

O guia de integração do Experience Manager foi atualizado com alguns esclarecimentos adicionados à configuração dessa integração. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

Foram adicionadas informações sobre a diferença entre a lista de tipo de grupo e a lista de tipo de lista. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

Atualização do código para enviar uma extração de relatório como anexo por email. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

Foi adicionado um exemplo de como criar um query para filtrar recipient que não abriram um email nos últimos 7 dias. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Atualização do guia de integração Compartilhamento de audiências com a Adobe Experience Cloud. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

A página de ajuda Perguntas comuns agora contém informações sobre idiomas disponíveis para Campanha, tradução de formulários online e emails multilíngues. [Leia mais](../../platform/using/common-questions.md)

A diferença entre as instâncias de inglês dos EUA e inglês do Reino Unido agora está listada em uma seção dedicada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

A página de ajuda [Perguntas](../../platform/using/common-questions.md) comuns agora vincula à página de mensagens de erro.

Foram adicionadas informações sobre o modo de rastreamento &quot;Abrir&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

Adicione informações sobre a resolução mínima para aplicativos da Web e formulários da Web. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

O guia de integração de soluções da Campaign e da Adobe Experience Cloud foi atualizado e reorganizado. [Leia mais](../../integrations/using/about-campaign-integrations.md)

Uma seção sobre o uso da variável de texto em formulários da Web foi adicionada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

Os modos de rastreamento de URL nas mensagens agora são detalhados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

A seção de criação da instância foi reorganizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

O envio de e-mails em celulares japoneses agora está documentado em uma nova seção. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

A seção &quot;Otimização da personalização&quot; foi atualizada com mais informações. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**Novos recursos incluídos na versão**

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

A documentação JSAPI foi atualizada. [Leia mais](https://support.neolane.net/webApp/extranetLogin)

A página Recursos obsoletos e removidos foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

**Outras atualizações de documentação que vêm com a versão**

Os guias de usuário do Campaign Classic foram renomeados para simplificar a navegação, melhorar a experiência do usuário, o acesso às informações e a autoajuda. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/browseAC.html)

A lista de funções disponíveis no editor de expressões foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

O guia Introdução à segurança foi atualizado com informações sobre como proteger páginas que contêm PI. [Leia mais](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Uma seção de solução de problemas foi adicionada na documentação de integração do IMS. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

O guia Introdução à atualização da criação foi atualizado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

A seção de configuração da afinidade IP foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

Uma seção Solução de problemas de desempenho e throughput foi adicionada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

A lista de alocos de personalização integrados foi atualizada com exemplos. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

A lista de motivos de falha do Delivery foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

Uma nova seção sobre o gerenciamento de definição de pacotes foi adicionada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

A integração da Campanha com o Adobe Analytics - seção Conector de dados foi aprimorada e reorganizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Uma nova seção Tutoriais foi adicionada, com links para guias passo a passo e vídeos passo. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Uma nova nota técnica sobre o protocolo e as configurações do conector SMS foi criada. [Leia mais](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

O guia Introdução das práticas recomendadas do Delivery foi atualizado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

A configuração da conta do Microsoft Dynamics 365 com implantação da API da Web foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

O procedimento para instalar o Adobe Campaign Classic em uma plataforma Windows foi atualizado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

O período de compartilhamento de Audiências entre a Adobe Experience Cloud e a Campaign Classic foi detalhado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

O artigo da base de conhecimento cheio para a lista de Campaign Classic foi atualizado. [Leia mais](https://helpx.adobe.com/campaign/kb/article-list.html)

Uma nova nota técnica sobre melhoria de desempenho e práticas recomendadas está disponível. [Leia mais](https://helpx.adobe.com/campaign/kb/best-practices-for-performance-improvement.html)

A amostra de teste A/B foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

A página de Perguntas frequentes/Perguntas frequentes do Campaign Classic foi atualizada. [Leia mais](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**Novos recursos incluídos na versão**

Regulamento geral da UE sobre a proteção de dados (RGPD) - [Leia mais](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

perfis ativos - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Aprimoramento do conector de push do Android - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**Outras atualizações de documentação que vêm com a versão**

As notas de versão foram aprimoradas para uma melhor experiência do usuário e agora incluem todos os patches relacionados às solicitações do cliente.  [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/RN.html)

Uma nova página foi adicionada com as perguntas mais comuns sobre o Campaign Classic. [Leia mais](../../platform/using/common-questions.md)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

A nota técnica dos Acionadores da Marketing Cloud foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Uma nota técnica foi adicionada sobre como instalar e implantar o pacote Privacidade (RGPD) nas versões herdadas do Campaign Classic. [Leia mais](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

Uma nota técnica sobre o novo mecanismo de geração automática de sequência foi adicionada. [Leia mais](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)

A documentação JSAPI foi atualizada. [Leia mais](https://support.neolane.net/webApp/extranetLogin)

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Uma nova página que lista recursos e versões obsoletos está disponível. [Leia mais](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

Foram adicionadas algumas limitações conhecidas e práticas recomendadas relacionadas ao RDBMS. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

Saiba mais sobre as práticas recomendadas relacionadas ao uso do SFTP. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

A lista dos workflows técnicos foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

A lista de artigos da base de conhecimento (anteriormente conhecida como &quot;notas técnicas&quot;) está agora disponível aqui. [Leia mais](https://helpx.adobe.com/campaign/kb/article-list.html)

Os vídeos [](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) &quot;como fazer&quot; foram atualizados.

A documentação de LINHA foi atualizada após a depreciação do pacote de LINHA. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

Atualização da documentação de cálculo do indicador de relatório. [Leia mais](../../reporting/using/indicator-calculation.md)

Foram adicionadas informações sobre o alinhamento do arquivo Timezone com o Oracle. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

Adicionada uma nova seção &quot;Monitoramento de delivery&quot; com informações atualizadas sobre falhas de delivery e gerenciamento do quarentena. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

A seção &quot;Alocos de personalização&quot; foi reorganizada com novas informações sobre alocos de personalização prontos para uso.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

Reorganizada a seção Arquivamento de e-mails com novas informações sobre a configuração do ```config-<instance name>.xml``` arquivo. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

Atualizadas as informações sobre o fluxo de trabalho técnico do Centro de mensagens (Control). [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

Foram adicionadas informações sobre limitações de throughput ao configurar uma retransmissão SMTP. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

O conjunto de documentação [do](https://helpx.adobe.com/support/campaign/classic.html) Adobe Campaign Classic foi reorganizado para melhorar a utilização.

Uma nova seção Tutoriais foi adicionada para facilitar o acesso aos recursos de Campanha principal e ajudar materiais, instruções, amostras e vídeos. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Uma nova seção foi adicionada para ajudá-lo a monitorar o status do seu delivery, mas também possíveis erros e aprender a corrigi-los. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

A nota técnica dos Acionadores da Marketing Cloud foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

O guia de migração do Campaign Classic foi adicionado à coleção. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Matriz de compatibilidade de Campanha atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Quando aplicável, as instruções de configuração e instalação agora mencionam a que modelo de hospedagem se aplicam. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

Novo artigo da Base de conhecimento para destacar as diferenças de configuração e recursos entre implantações locais, híbridas e de serviços gerenciados. [Leia mais](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

Adicionadas instruções sobre como instalar um pacote padrão. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Foram adicionados detalhes sobre como configurar a integração com o Audiência Manager ou com o serviço principal de Pessoas. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Atualização da documentação de instalação para mencionar que pgcrypto agora é necessário para a instalação da Campanha se estiver usando o PostreSQL. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**Novos recursos incluídos na versão**

Aprimoramentos do conector ACS

Conector SAP HANA - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Conector Hadoop via HiveSQL - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

Canal DE LINHA: Aprimoramentos de mensagens - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**Outras atualizações de documentação que vêm com a versão**

Foram adicionadas novas amostras de query. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

O guia Práticas recomendadas do Delivery foi atualizado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

A amostra de teste A/B foi atualizada com instruções em falta. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Os vídeos de procedimentos foram atualizados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Atualizar a seção de arquivamento de e-mails. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

Esclareça o uso do Scheduler em um fluxo de trabalho. [Leia mais](../../workflow/using/scheduler.md)

Adicionar prática recomendada do fluxo de trabalho pausado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

Novo procedimento sobre o arquivo de pré-processamento ao importar e pós-processar ao exportar dados em um fluxo de trabalho. Leia [aqui](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html).

O mecanismo de quarentena da documentação de mensagens SMS foi atualizado para refletir as especificidades do gerenciamento de erros do conector SMPP genérico estendido. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines).

A documentação do Canal do aplicativo móvel foi aprimorada com um procedimento detalhado para enviar notificações avançadas no Android. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications).

A documentação de renderização da Caixa de entrada foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html).

A documentação de Configuração do rastreamento da Web foi aprimorada com um exemplo e observações atualizados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration).

A documentação do Canal SMS foi atualizada com alguns esclarecimentos adicionados à seção de resposta automática que se aplica ao conector SMPP genérico estendido. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account).

A documentação do Social Marketing foi atualizada. [Leia mais](../../social/using/about-social-marketing.md).

Uma nova nota técnica sobre o aquecimento de IP foi adicionada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf).

Uma nova introdução à atualização da compilação foi adicionada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html).

## May 2017{#release-doc-30-05-2017}

Um novo guia de introdução está disponível: apresenta algumas das práticas recomendadas que podem ser usadas para fornecer Adobe Campaign, desde a criação e a definição de metas até o envio e o monitoramento. [Leia mais](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

O guia de introdução à segurança foi atualizado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

A documentação [&quot;Arquivamento de emails&quot;&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) foi atualizada com a seção [&quot;Cco por email&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) e as etapas [detalhadas para ativar o recurso](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails).

Alguns vídeos foram adicionados e atualizados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Saiba como enviar um delivery para recipient carregados de um arquivo externo sem atualizar o banco de dados. [Leia mais](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

O exemplo de aceitação de duplo foi atualizado. [Leia mais](../../web/using/use-cases--web-forms.md)

## Março de 2017{#release-doc-31-03-2017}

Disponibilidade: o guia [de](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) introdução foi atualizado. A documentação de capacidade de entrega agora inclui uma [visão geral](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) mais detalhada e uma descrição do processo de [implementação e das principais etapas](../../delivery/using/deliverability-key-points.md).

A seção &quot;Enviar usando ondas&quot; foi movida e aprimorada com exemplos detalhados, recomendações e casos de uso.    [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

Uma tabela que descreve os erros específicos das mensagens SMS foi adicionada à seção &quot;Gerenciamento de Quarentenas&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Workflows: um novo exemplo de fluxo de trabalho de vários canais foi adicionado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Acionadores da Marketing Cloud: foi adicionada uma nota técnica sobre como configurá-la e usá-la com Adobe Campaign. [Leia mais](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

O guia Fluxo de trabalho foi reorganizado e estendido. Encontre com facilidade como [criar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) e [executar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) um fluxo de trabalho, como [público alvo](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) e [gerenciar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) seus dados, como [importar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html) [](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database) [](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow)dados e como usar os dados do fluxo de trabalho paraatualizar o banco de dados ou como enviar delivery.

Um exemplo de fluxo de trabalho [de](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) importação criado após as práticas [recomendadas de](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices) importação está disponível.
O guia de instalação foi atualizado para esta nova versão. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Os Recipient têm valor agregado ao incluir cupons em seus delivery de email. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 03/16/2017{#release-17-2}

**Novos recursos incluídos na versão**

ACS Connector

API da Web para Microsoft Dynamics - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Método CCO de arquivamento de email - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Conector S3 (Simple Armazenamento Service) da Amazon - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

