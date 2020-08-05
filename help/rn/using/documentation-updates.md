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
source-git-commit: 51bbf50a1e9b00c25fca8e1e86ca21c314c18313
workflow-type: tm+mt
source-wordcount: '6953'
ht-degree: 97%

---


# Atualizações da documentação{#documentation-updates}

Esta página lista todos os novos recursos e atualizações de documentação por mês e versão do Campaign.

Você também pode consultar as [Notas de versão do Adobe Campaign Classic](../../rn/using/latest-release.md) para obter mais atualizações.

## Julho de 2020 {#july-2020}

Um caso de uso sobre como atualizar automaticamente uma lista usando um query incremental foi adicionado aos casos de uso do fluxo de trabalho. [Leia mais](../../workflow/using/about-workflow-use-cases.md)

As [Notas](../../rn/using/latest-release.md) de versão foram reorganizadas: uma página [de](../../rn/using/latest-release.md) visão geral foi adicionada com informações sobre status de criação, processo de atualização, recomendações e links importantes. Uma página dedicada para as versões [do](../../rn/using/gold-standard.md) Gold Standard também foi adicionada e a matriz [](../../rn/using/compatibility-matrix.md) Compatibilidade foi integrada.

Uma nova seção foi adicionada com diretrizes relacionadas ao monitoramento do Campaign Classic. [Leia mais](../../production/using/monitoring-guidelines.md)

A seção Privacidade e consentimento foi aprimorada com informações mais detalhadas e links úteis. [Leia mais](../../platform/using/privacy-and-recommendations.md).

A página Gerenciamento de privacidade no Campaign Classic foi atualizada com informações sobre o campo &quot;regulamento&quot;, que agora está disponível ao usar a API, permitindo a configuração do processo automático de solicitação de privacidade. [Leia mais](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

A página Visão geral do Gerenciamento de privacidade foi atualizada para incluir informações sobre a Lei de Proteção de Dados Pessoais (PDPA) da Tailândia e sobre a Lei Geral de Dados (LGPD) do Brasil. [Leia mais](https://helpx.adobe.com/br/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

As informações foram adicionadas nos registros de subworkflows e no comportamento em caso de erro. [Leia mais](../../workflow/using/sub-workflow.md)

As práticas recomendadas foram adicionadas na seção **[!UICONTROL Scheduler]** atividade. [Leia mais](../../workflow/using/scheduler.md)

## Junho de 2020 {#june-2020}

A seção Remoção de um endereço em quarentena foi atualizada. Ela esclarece os casos em que os endereços são removidos automaticamente da lista de quarentena. [Leia mais](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Casos de uso foram adicionados em como [criptografar](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt) e [descriptografar](../../workflow/using/importing-data.md#use-case-gpg-decrypt) dados usando o Painel de controle do Campaign e workflows do Campaign.

Os termos &quot;white list&quot; e &quot;black list&quot; foram removidos da documentação do Adobe Campaign. Algumas ocorrências desses termos ainda podem existir na interface do usuário do produto, nos nomes de opções e no código interno, mas serão substituídas em versões futuras do Campaign por &quot;lista de bloqueios&quot; e &quot;lista de permissões&quot;.

The Experience Cloud Triggers and Adobe Campaign Classic integration page has been moved [here](../../integrations/using/about-triggers.md).

## 20.2 - 08/06/2020{#release-20-2}

**Novos recursos incluídos na versão**

Suporte a emoticons – [Leia mais](../../delivery/using/customizing-emoticon-list.md)

Conector FDA do Azure Synapse - [Leia mais](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse)

Leis de privacidade da Tailândia e do Brasil – [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**Outras atualizações de documentação que vêm com a versão**

A nova opção que permite cancelar a publicação de um template de mensagem transacional está documentada
[nesta seção](../../message-center/using/template-unpublication.md).

As novas opções que permitem definir limitações ao enviar emails que incluem imagens baixadas de um URL personalizado e anexos foram adicionadas à lista de opções do Campaign Classic. [Leia mais](../../installation/using/configuring-campaign-options.md#delivery)

A nova opção **Preparar as partes do delivery no banco de dados** está documentada [nesta seção](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis).

A seção Validação do delivery foi esclarecida e atualizada. [Leia mais](../../delivery/using/steps-validating-the-delivery.md)

Os parâmetros relacionados ao novo mecanismo de assinatura do link de rastreamento foram adicionados à seção [Arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md).

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

A seção fluxo de trabalho de limpeza foi atualizada. [Saiba mais](../../production/using/database-cleanup-workflow.md)

Os endpoints de rede do Campaign foram movidos para esta [seção](../../installation/using/campaign-network-endpoints.md).

A seção de instalação do Spam Assassin foi atualizada com o novo nome de arquivo de instalação. [Saiba mais](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

A seção sobre ambientes duplicados foi atualizada. [Saiba mais](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## Maio de 2020 {#may-2020}

A seção Monitoramento da capacidade de delivery foi movida e aprimorada. [Leia mais](../../delivery/using/monitoring-deliverability.md)

A seção Solução de problemas da capacidade de delivery foi movida e aprimorada. [Leia mais](../../delivery/using/deliverability-faq.md)

As diretrizes de capacidade de delivery ao iniciar uma nova seção da plataforma foram aprimoradas. [Leia mais](../../delivery/using/starting-new-platform.md)

A seção Enviar emails transacionais com anexos foi movida e atualizada. [Leia mais](../../message-center/using/transactional-email-with-attachments.md)

A seção Práticas recomendadas do pacote de dados foi movida e atualizada. [Leia mais](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## Abril de 2020 {#april-2020}

A tabela de direitos da FDA foi movida para a documentação Acesso a um banco de dados externo (FDA). [Leia mais](../../platform/using/remote-database-access-rights.md)

As Perguntas frequentes estão atualizadas com dicas sobre como limpar o cache flexível e rígido. [Leia mais](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

As Práticas recomendadas do modelo de dados foi aprimorada com informações adicionais sobre os índices. [Leia mais](../../configuration/using/data-model-best-practices.md#indexes)

A seção que descreve o modelo de dados integrado do Adobe Campaign foi atualizada com mais detalhes em cada tabela. [Leia mais](../../configuration/using/data-model-description.md)

Os casos de uso do fluxo de trabalho foram atualizados e reorganizados em seções temáticas. [Leia mais](../../workflow/using/about-workflow-use-cases.md)

As seções [Qualificações de email de rejeição](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) e [Regras de gerenciamento de email](../../delivery/using/understanding-delivery-failures.md#email-management-rules) foram aprimoradas com informações atualizadas.

O artigo MTA aprimorado do Adobe Campaign foi atualizado. Ele agora só se aplica ao Campaign Classic. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-campaign-enhanced-mta.html)

## Março de 2020 {#march-2020}

As Práticas recomendadas do modelo de dados foram atualizadas com novas seções, que incluem [Sequências](../../configuration/using/data-model-best-practices.md#sequences), [Desempenho](../../configuration/using/data-model-best-practices.md#performance) e [Tabelas grandes](../../configuration/using/data-model-best-practices.md#large-tables), entre outras. [Leia mais](../../configuration/using/data-model-best-practices.md)

Uma nova seção que descreve o modelo de dados integrados do Adobe Campaign e a interação entre tabelas agora está disponível. [Leia mais](../../configuration/using/data-model-description.md)

Links chave adicionais foram adicionados à página inicial da documentação. [Leia mais](../../campaign-classic-home.md)

Um caso de uso foi adicionado sobre como integrar uma oferta dinâmica do Adobe Target a um email no Adobe Campaign. [Leia mais](../../integrations/using/inserting-a-dynamic-image.md)

Uma nova seção que detalha os diferentes idiomas disponíveis no Adobe Campaign está disponível. [Leia mais](../../platform/using/adobe-campaign-workspace.md#languages)

As diretrizes Gerenciamento de acesso foram atualizadas com mais informações sobre Direitos nomeados. [Leia mais](../../platform/using/access-management.md#named-rights)

## Fevereiro de 2020 {#february-2020}

Uma nova seção que descreve as práticas recomendadas e as principais recomendações ao projetar o template de dados do Adobe Campaign está disponível. [Leia mais](../../configuration/using/data-model-best-practices.md)

Uma nova seção está disponível sobre as Configurações de email técnico. [Leia mais](../../installation/using/email-deliverability.md)

As perguntas frequentes sobre a Capacidade do delivery foram atualizadas com mais detalhes sobre a mensagem de erro de &quot;cotas atendidas&quot;. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-deliverability-faq.html#FAQ)

O AMP for Email agora é compatível com novos provedores de email: a documentação relacionada foi atualizada. [Leia mais](../../delivery/using/defining-interactive-content.md)

A seção Arquivamento de email foi aprimorada. [Leia mais](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**Novos recursos incluídos na versão**

Conector FDA do Snowflake - [Leia mais](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Aprimoramento do conector FDA do Hadoop - [Leia mais](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Outras atualizações de documentação que vêm com a versão**

Os guias de [instalação](../../installation/using/before-reading.md), [produção](../../production/using/foreword.md) e [configuração](../../configuration/using/additional-parameters.md) foram atualizados com a nova unidade do sistema usada pela inicialização do serviço nlserver. Ainda é possível usar o /etc/init.d/nlserver6, mas a Adobe recomenda usar o comando systemctl agora para interagir com o serviço nlserver.

O guia de instalação está atualizado e sincronizado com a versão mais recente da matriz de compatibilidade. Novos sistemas compatíveis foram adicionados. As ocorrências em sistemas obsoletos e sem suporte foram removidas. [Leia mais](../../installation/using/before-reading.md)

A matriz de compatibilidade foi atualizada com os conectores do Hadoop 3.0 e Snowflake FDA. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

Uma prática recomendada na afinidade IP foi adicionada ao guia de instalação. [Leia mais](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

A seção workflow de limpeza de banco de dados foi atualizada. Os números de lotes fornecidos agora refletem a implementação do código. [Leia mais](../../production/using/database-cleanup-workflow.md)

Uma limitação no FDA sobre HTTP foi adicionada ao guia de mensagens transacionais. [Leia mais](../../production/using/database-cleanup-workflow.md)

Adicionamos informações sobre a nova opção que permite definir um período de tempo limite para as atividades de workflow **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]**. [Leia mais](../../workflow/using/sql-code-and-javascript-code.md)

Adicionamos informações sobre a nova visualização **[!UICONTROL Start Pending]** disponível no nó **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]**. [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

O guia [Envio de notificações via push](../../delivery/using/about-mobile-app-channel.md) foi movido, reorganizado e aprimorado com informações mais claras:

O novo parâmetro para a configuração do relatório de URLs está documentado [aqui](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

A página **Matriz de recursos no local e hospedada do Campaign Classic** foi atualizada com os novos conectores do FDA. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-on-prem-vs-hosted.html)

A página **Matriz de recursos do Campaign Classic** foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

O novo **[!UICONTROL Cleanup of Nmsaddress]** workflow está documentado [aqui](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

Adicionamos uma limitação ao usar uma atividade de query em um workflow. [Leia mais](../../workflow/using/query.md).

Adicionamos uma nova seção para detalhar as regras aprimoradas de validação de endereço de email para enviá-lo para a quarentena em caso de erro de software. [Leia mais](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

O parâmetro do arquivo de configuração indicando se uma instância está usando ou não o MTA aprimorado foi documentado. [Leia mais](../../installation/using/the-server-configuration-file.md#mta)

## Janeiro de 2020 {#january-2020}

A seção Deliverability foi movida, reorganizada e aprimorada com conteúdo atualizado. [Leia mais](../../delivery/using/about-deliverability.md)

Uma nova seção que descreve as noções básicas do modelo de dados do Adobe Campaign Classic e como acessar a descrição de cada tabela está disponível. [Leia mais](../../configuration/using/about-data-model.md)

O artigo sobre MTA aprimorado do Adobe Campaign foi atualizado com informações mais detalhadas sobre a instalação de um pacote de Tipologia específico em instâncias que não adicionam os cabeçalhos MTA aprimorados necessários a cada mensagem. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

Os casos de uso relacionados ao design de consulta foram reorganizados em seções separadas. [Leia mais](../../workflow/using/querying-recipient-table.md)

Uma nova seção sobre dicas e truques para gerenciar ofertas e usar o módulo de interação no Adobe Campaign Classic está disponível. [Leia mais](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

A documentação da interação foi aprimorada com links para vários vídeos que ajudam a entender melhor como gerenciar ofertas. [Leia mais](../../interaction/using/interaction-and-offer-management.md)

O artigo de práticas recomendadas sobre como otimizar as consultas executadas em sua instância foi integrado à documentação. [Leia mais](../../workflow/using/query.md#optimizing-queries)

O guia de relatórios foi atualizado e reorganizado. [Leia mais](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Um exemplo de como usar uma variável de instância em um fluxo de trabalho foi adicionado. [Leia mais](../../workflow/using/javascript-scripts-and-templates.md)

## Dezembro de 2019 {#december-2019}

A opção &quot;WdbcOptions_TempDbName&quot; foi adicionada à lista de opções do Campaign. [Leia mais](../../installation/using/configuring-campaign-options.md)

A página da matriz FDA foi movida para [este local](../../platform/using/remote-database-access-rights.md).

A página da matriz de direitos de acesso foi movida [aqui](https://docs.adobe.com/content/help/pt-BR/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf).

A seção que descreve como definir conteúdo interativo com AMP foi movida. [Leia mais](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**Novos recursos incluídos na versão**

Lei de Privacidade do Consumidor da Califórnia (CCPA) - [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html)

Conteúdo interativo com AMP - [Leia mais](../../delivery/using/defining-interactive-content.md)

Monitoramento ao vivo do fluxo de trabalho - [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Sistema de Mensagens Seguras de SMS (TLS) - [Leia mais](https://helpx.adobe.com/br/campaign/kb/sms-connector-protocol-and-settings.html)

**Outras atualizações de documentação que vêm com a versão**

A documentação MTA aprimorada do Adobe Campaign está disponível. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-campaign-enhanced-mta.html)

Uma nova seção foi adicionada sobre como solucionar problemas de um workflow que permanece no estado &quot;Start as soon as possible&quot; em uma campanha. [Leia mais](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

As novas opções &quot;NmsOperation_DeliveryPreparationWindow&quot; e &quot;WdbcKillSessionPolicy&quot; foram adicionadas à lista de opções do Campaign. [Leia mais](../../installation/using/configuring-campaign-options.md)

Um novo documento que descreve as noções básicas do modelo de dados do Adobe Campaign Classic está disponível. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-datamodel.html)

A nova opção **Maximum personalization run time** nas propriedades do delivery está documentada nesta [seção](../../delivery/using/personalization-fields.md#timing-out-personalization).

Os exemplos de chamadas de API usando um **HttpServletRequest** com logon() e query() foram atualizados. [Leia mais](../../configuration/using/web-service-calls.md).

Uma recomendação para o atributo **sqlDefault** na definição do esquema foi adicionada. [Leia mais](../../configuration/using/elements-and-attributes.md#attribute-description).

A integração entre o Adobe Campaign e a Adobe Real-time Customer Data Platform agora é mencionada no guia **Integração com a Adobe Experience Cloud**. [Leia mais](../../integrations/using/about-campaign-integrations.md).

## Novembro de 2019 {#november-2019}

Um aviso foi adicionado às seções [Multiplexação do servidor mid-sourcing](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) e [Suporte a várias seções de instâncias de controle](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances), mencionando que essas implantações não são suportadas para clientes totalmente hospedados e híbridos.

Uma nova seção foi adicionada para descrever como forçar a codificação de caracteres usada ao enviar um email. [Leia mais](../../delivery/using/sending-messages.md#character-encoding)

A seção &quot;Gerenciamento de acesso&quot; foi atualizada com o **Direito de dados de privacidade**. [Leia mais](../../platform/using/access-management.md#named-rights)

Foram adicionadas informações para especificar que o conteúdo dos campos de personalização não pode exceder 1024 caracteres. [Leia mais](../../delivery/using/personalization-fields.md)

A documentação do Painel de controle do Campaign foi integrada ao novo conjunto de documentação colaborativa. [Leia mais](https://docs.adobe.com/content/help/pt-BR/control-panel/using/control-panel-home.translate.html)

O guia de introdução às práticas recomendadas de delivery foi atualizado. [Leia mais](../../delivery/using/delivery-best-practices.md)

## Outubro de 2019 {#october-2019}

A lista de mensagens de erro do Campaign Standard e do Campaign Classic foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

O guia de introdução ao GDPR foi melhorado e aprimorado. Agora se trata uma documentação de gerenciamento de privacidade, incluindo o GDPR e o CCPA. [Leia mais](https://helpx.adobe.com/content/help/br/campaign/kb/campaign-privacy.html)

Uma nova página de solução de problemas foi adicionada para rastreamento no Campaign Classic. [Leia mais](https://helpx.adobe.com/br/campaign/kb/classic-tracking-troubleshooting.html).

Uma nova página de práticas recomendadas do Adobe Analytics Data Connector foi adicionada. [Leia mais sobre o Adobe Analytics Data Connector](../../platform/using/adobe-analytics-data-connector.md)

O guia de introdução às práticas recomendadas de delivery foi movido e atualizado. [Leia mais](../../delivery/using/delivery-best-practices.md)

Uma recomendação foi adicionada à documentação do canal SMS para evitar problemas ao usar várias contas externas aproveitando o conector SMPP genérico estendido com a mesma conta do provedor. [Leia mais](../../delivery/using/sms-channel.md#automatic-reply)

Foram adicionadas informações na documentação de atividade do Scheduler sobre como evitar execuções simultâneas de um fluxo de trabalho. [Leia mais](../../workflow/using/scheduler.md)

As etapas para configurar a renderização da caixa de entrada para instalações locais foram adicionadas à documentação. [Leia mais](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## Setembro de 2019 {#september-2019}

Uma nova página foi adicionada para fornecer orientações gerais para a manutenção do Campaign Classic. [Leia mais](../../production/using/monitoring-guidelines.md)

As informações relacionadas ao monitoramento de workflows foram centralizadas em uma nova seção dedicada. [Leia mais](../../workflow/using/monitoring-workflow-execution.md).

Uma nova página sobre diretrizes gerais para rastreamento no Adobe Campaign Classic foi adicionada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-tracking.html).

As práticas recomendadas para aprimoramentos de desempenho de workflows e deliveries foram atualizadas. [Leia mais sobre workflows](../../workflow/using/workflow-best-practices.md) e [mais sobre deliveries](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 - 30/05/2019{#release-19-1}

**Novos recursos incluídos na versão**

Painel de controle - [Leia mais](https://docs.adobe.com/content/help/pt-BR/control-panel/using/control-panel-home.translate.html)

Trilha de auditoria - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Audit_trail.html)

**Outras atualizações de documentação que vêm com a versão**

Foi criada uma atualização das perguntas frequentes sobre a nova build. [Leia mais](https://helpx.adobe.com/br/campaign/kb/build-upgrade-faq.html)

A [Matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html) foi atualizada. A lista de sistemas de banco de dados suportados foi atualizada, assim como as versões do Android/iOS e SDKs relacionados. A [Matriz de compatibilidade 19.0](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix-19-0.html) foi arquivada.

A página &quot;Deprecated and Removed Features in Campaign Classic&quot; foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/deprecated-and-removed-features.html)

A descrição do arquivo de configuração do servidor foi adicionada ao guia de instalação. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Uma seção foi adicionada descrevendo as etapas de instalação e configuração para modelos hospedados e híbridos. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Uma seção foi adicionada descrevendo as etapas de desinstalação do servidor do Campaign. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

Os guias de introdução de [segurança](https://helpx.adobe.com/br/campaign/kb/acc-security.html), [delivery](https://docs.adobe.com/content/help/pt-BR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) e [privacidade](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html) foram atualizados.

A descrição da opção de fluxo de trabalho de pré-processo foi atualizada para refletir as alterações no produto. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

A nota técnica Experience Cloud Triggers foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/triggers-and-campaign.html)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Foram adicionadas mais informações sobre métodos de autenticação SOAP para mensagens transacionais. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

As etapas de configuração do Apache foram atualizadas. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

Uma nova página foi adicionada, incluindo a lista de terminais para o Campaign Standard e Classic. [Leia mais](https://helpx.adobe.com/br/campaign/kb/campaign-endpoints.html)

O artigo de práticas recomendadas do pacote de dados foi atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/data-package-best-practices.html)

A documentação de gerenciamento de ofertas foi atualizada com uma nova seção que lista as práticas recomendadas. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

Um novo artigo da knowledge base sobre como usar o catálogo de oferta no Adobe Campaign Classic foi criado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/offer-best-practices.html)

A seção Sub-workflow activity foi aprimorada com um exemplo de uso. [Leia mais](../../workflow/using/sub-workflow.md)

O artigo da Knowledge base [Campaign Classic On-premise &amp; Hosted capability matrix](https://helpx.adobe.com/br/campaign/kb/acc-on-prem-vs-hosted.html) foi atualizado com informações relacionadas a emails de arquivamento.

A documentação de Mensagens transacionais foi atualizada com uma nota relacionada à publicação do modelo. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

A seção Unprocessed bounce mails foi atualizada com mais detalhes sobre os campos Forwarding address e Address for errors. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

Uma nova seção sobre práticas recomendadas de planejamento de workflow foi adicionada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Foram adicionadas duas novas opções à lista de opções do Campaign: XtkSecurity_Restrict_EditXML e NmsOperation_OperationMgtDebug.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Foram adicionadas informações sobre as diferentes contas externas disponíveis no Campaign Classic e como configurá-las.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

Atualização da seção Updated Analytics Data Connector para refletir mudanças na interface.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Foram adicionadas informações sobre o relatório de faturamento.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

Atualização da documentação sobre a integração de públicos-alvo compartilhados.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

As seguintes notas técnicas foram atualizadas: [SMS connector protocol and settings](https://helpx.adobe.com/br/campaign/kb/sms-connector-protocol-and-settings.html) e [Sequence auto generation](https://helpx.adobe.com/br/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

A seção Technical workflows foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

O procedimento de Configuração do nome de domínio do Campaign foi aprimorado e atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/domain-name-delegation.html)

O procedimento de migração para aplicativos Android do Google Cloud Messaging (GCM) para o Firebase Cloud Messaging (FCM) foi atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/migrate-to-fcm.html)

O Guia de dimensionamento de hardware do Campaign foi atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html)

Foram adicionadas informações sobre a Faixa de consulta para a conta externa de teradados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## Janeiro de 2019{#release-doc-16-01-2019}

A nota técnica Experience Cloud Triggers foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/triggers-and-campaign.html)

Uma nota foi adicionada na seção de aprovação da oferta para especificar que a menção &quot;Content approved&quot; indica que o processo de aprovação do conteúdo foi realizado, se todas as ofertas foram habilitadas/aprovadas ou não. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

Uma nova seção foi adicionada na guia Installation, listando as opções do nó Administration / Platform / Options. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Foram adicionadas informações sobre o uso de seed addresses para proteger a lista de mala direta. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

As etapas principais ao criar e enviar um delivery foram reagrupadas em uma nova seção, com referências aos vários canais quando necessário. [Leia mais](../../delivery/using/steps-about-delivery-creation-steps.md)

A seção [Email archiving](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) foi movida, reorganizada e aprimorada com informações mais claras:

* Foram adicionadas as práticas recomendadas relacionadas aos emails por conexão e aos parâmetros de IPs de envio com Cco. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* Atualizamos as etapas para atualizar para o novo sistema de arquivamento de emails (Cco) se você já estava usando o arquivamento de emails com uma build mais antiga (antes do Adobe Campaign 17.2 - build 8795). [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Um caso de uso foi adicionado ao guia de Automatização com workflows: enviar alertas personalizados para operadores. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

A seção &quot;Migrating to a new version&quot; foi atualizada. A documentação agora só detalha as etapas de migração para o Adobe Campaign Classic v7 de qualquer versão anterior, pois não é mais possível migrar para o Adobe Campaign v6.11. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

A seção &quot;Retries after a delivery temporary failure&quot; foi esclarecida. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

Os links para a seção &quot;Digital Content Editor&quot; foram adicionados à seção &quot;Defining the email content&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

A seção &quot;Transactional messaging architecture&quot; foi atualizada com um aviso especificando que as instâncias de controle e execução não podem ser instaladas na mesma máquina. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

A seção &quot;Workflow monitoring&quot; foi atualizada com uma nota para builds entre 8700 e 8977 (18.10), incluindo um link para a nota técnica sobre como instalar o pacote HeatMap de fluxo de trabalho para essas builds. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

Foi adicionado um caso de uso sobre como enviar um email com campos de dados personalizados usando a atividade Enrichment em um fluxo de trabalho. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

Os vídeos em destaque foram movidos para [este local](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html).

Duas notas técnicas foram adicionadas ao [Teradata](https://helpx.adobe.com/br/campaign/kb/campaign_fda_teradata.html) e ao [MySQL 5.7](https://helpx.adobe.com/br/campaign/kb/campaign_fda_mysql.html).

## 18.10 - 05/11/2018{#release-18-10}

**Novos recursos incluídos na versão**

Melhorias na notificação por push - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

Atividade do Gerenciamento de dados SQL - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

Monitoramento do fluxo de trabalho - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**Outras atualizações de documentação que vêm com a versão**

As APIs do Campaign Classic agora estão disponíveis em uma [página dedicada](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Se estiver usando o arquivo jsapi.chm, agora deverá fazer referência a nova versão online.

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

A página &quot;Deprecated and Removed Features in Campaign Classic&quot; foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/deprecated-and-removed-features.html)

Nas [notas de versão](https://docs.adobe.com/content/help/pt-BR/campaign-classic/using/release-notes/latest-release.html) e [notas de versão legadas](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html), foi adicionado um aviso para builds que tiveram recall. Também foram adicionadas as builds acumuladas para 17.9, 18.4 e 18.6.

Os guias de introdução de [segurança](https://helpx.adobe.com/br/campaign/kb/acc-security.html), [entregabilidade](https://docs.adobe.com/content/help/pt-BR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) e [atualização de build](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html) foram atualizados.

O guia de introdução de [Privacidade](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html) foi atualizado com as informações sobre como chamar a API externamente e como usar o queryDef para consultar o status e baixar o arquivo do GDPR.

Foi adicionado um caso de uso de mensagem transacional para adicionar anexos de email em tempo real a remessas de saída. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

Atualização da seção de solução de problemas de limites de conexão. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

Uma seção foi adicionada sobre como configurar uma conexão proxy. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

Atualização da seção sobre a restrição de comandos externos autorizados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

Foi adicionada uma seção de solução de problemas relacionada ao uso do SFTP. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

A seção de visão geral do guia de envio de mensagens foi reorganizada. Foram adicionadas informações sobre o processo global de criação de delivery e os diferentes tipos de delivery. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

A seção sobre como usar seed addresses foi movida para o capítulo de visão geral do guia de envio de mensagens. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Foi adicionado um novo caso de uso de workflow: gerenciamento de atualizações de execuções concomitantes de workflow. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

A seção &quot;Inbox rendering&quot; foi atualizada com mais informações sobre o Litmus e um procedimento mais detalhado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

A seção &quot;SpamAssassin&quot; foi aprimorada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

Um caso de uso foi adicionado à seção &quot;Managing marketing fatigue with pressure rules&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

Um novo caso de uso que descreve como criar um workflow de delivery entre canais está disponível. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

Algumas recomendações foram adicionadas à seção &quot;Archiving emails&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

Uma nova recomendação foi adicionada em relação à resolução mínima de tela para o uso ideal do Adobe Campaign. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

O guia de integração do Experience Manager foi atualizado com alguns esclarecimentos adicionados à configuração dessa integração. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

Foram adicionadas informações sobre a diferença entre a lista de tipos de grupo e a lista de tipos de lista. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

Atualização do código para enviar uma extração de relatório como anexo por email. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

Foi adicionado um exemplo sobre como criar uma consulta para filtrar recipients que não abriram um email nos últimos 7 dias. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Atualização do guia de integração Compartilhamento de públicos-alvo com a Adobe Experience Cloud. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

A página de ajuda Common question agora contém informações sobre os idiomas disponíveis do Campaign, a tradução de formulários online e emails multilíngues. [Leia mais](../../platform/using/common-questions.md)

A diferença entre as instâncias de inglês dos EUA e inglês do Reino Unido agora está listada em uma seção dedicada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

A página de ajuda [Common questions](../../platform/using/common-questions.md) agora vincula à página de mensagens de erro.

Foram adicionadas informações sobre o modo de rastreamento &quot;Open&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

Foram adicionadas informações sobre a resolução mínima para aplicações web e formulários web. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

O guia de integração de soluções do Campaign e da Adobe Experience Cloud foi atualizado e reorganizado. [Leia mais](../../integrations/using/about-campaign-integrations.md)

Uma seção sobre o uso da variável de texto em formulários da Web foi adicionada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

Os modos de rastreamento de URL nas mensagens agora são detalhados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

A seção de criação da instância foi reorganizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

O envio de emails em celulares japoneses agora está documentado em uma nova seção. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

A seção &quot;Optimizing personalization&quot; foi atualizada com mais informações. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**Novos recursos incluídos na versão**

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

A documentação JSAPI foi atualizada. [Leia mais](https://support.neolane.net/webApp/extranetLogin)

A página de recursos obsoletos e removidos foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/deprecated-and-removed-features.html)

**Outras atualizações de documentação que vêm com a versão**

Os guias do usuário do Campaign Classic foram renomeados para simplificar a navegação, melhorar a experiência do usuário, o acesso às informações e o autoatendimento. [Leia mais](https://docs.campaign.adobe.com/doc/AC/br/browseAC.html)

A lista de funções disponíveis no editor de expressões foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

O guia de introdução à segurança foi atualizado com informações sobre como proteger páginas que contêm PI. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-security.html)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Uma seção de solução de problemas foi adicionada na documentação de integração do IMS. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

O guia de introdução à atualização da build foi atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html)

A seção de configuração de afinidade IP foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

Foi adicionada uma seção de solução de problemas de desempenho e capacidade. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

A lista de blocos de personalização incorporados foi atualizada com exemplos. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

A lista de motivos de falha de delivery foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

Uma nova seção sobre o gerenciamento de definição de pacotes foi adicionada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

A seção Campaign integration with Adobe Analytics - Data connector foi aprimorada e reorganizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Uma nova seção Tutorials foi adicionada, com links para guias passo a passo e vídeos instrutivos. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Uma nova nota técnica sobre o protocolo e as configurações do conector SMS foi criada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/sms-connector-protocol-and-settings.html)

O guia de introdução às práticas recomendadas de delivery foi atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/delivery-best-practices.html)

A configuração da conta do Microsoft Dynamics 365 com implantação da API da Web foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

O procedimento para instalar o Adobe Campaign Classic em uma plataforma Windows foi atualizado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

O período de compartilhamento de público-alvo entre a Adobe Experience Cloud e o Campaign Classic foi detalhado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

O artigo completo da knowledge base para a lista do Campaign foi atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/article-list.html)

Uma nova nota técnica sobre melhoria de desempenho e práticas recomendadas está disponível. [Leia mais](https://helpx.adobe.com/br/campaign/kb/best-practices-for-performance-improvement.html)

A amostra de teste A/B foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

A página Campaign Classic Common question/FAQ foi atualizada. [Leia mais](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**Novos recursos incluídos na versão**

Regulamento Geral sobre a Proteção de Dados da União Europeia (GDPR) - [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html)

Perfis ativos - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Aprimoramento do conector de push do Android - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**Outras atualizações de documentação que vêm com a versão**

As notas de versão foram aprimoradas para uma melhor experiência do usuário e agora incluem todas as correções relacionadas às solicitações do cliente.  [Leia mais](https://docs.adobe.com/content/help/pt-BR/campaign-classic/using/release-notes/latest-release.html)

Uma nova página foi adicionada com as perguntas mais comuns sobre o Campaign Classic. [Leia mais](../../platform/using/common-questions.md)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

A nota técnica Experience Cloud Triggers foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/triggers-and-campaign.html)

Uma nota técnica foi adicionada sobre como instalar e implantar o pacote de privacidade (GDPR) nas versões legadas do Campaign Classic. [Leia mais](https://helpx.adobe.com/br/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

Uma nota técnica sobre o novo mecanismo de geração automática de sequência foi adicionada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/sequence_auto_generation.html)

A documentação JSAPI foi atualizada. [Leia mais](https://support.neolane.net/webApp/extranetLogin)

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

Uma nova página que lista recursos e versões obsoletas está disponível. [Leia mais](https://helpx.adobe.com/br/campaign/kb/deprecated-and-removed-features.html)

Foram adicionadas algumas limitações conhecidas e práticas recomendadas relacionadas ao RDBMS. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

Saiba mais sobre as práticas recomendadas de uso do SFTP. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

A lista de workflows técnicos foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

A lista de artigos da knowledge base (anteriormente conhecida como &quot;notas técnicas&quot;) agora está disponível aqui. [Leia mais](https://helpx.adobe.com/br/campaign/kb/article-list.html)

Os [vídeos de instrução](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) foram atualizados.

A documentação LINE foi atualizada após a depreciação do pacote LINE. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

Atualização da documentação de cálculo do indicador de relatório. [Leia mais](../../reporting/using/indicator-calculation.md)

Foram adicionadas informações sobre o alinhamento do arquivo de fuso horário com o Oracle. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

Foi adicionada uma nova seção &quot;Monitoring deliveries&quot; com informações atualizadas sobre falhas de delivery e gerenciamento de quarentena. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

A seção &quot;Personalization blocks&quot; foi reorganizada com novas informações sobre blocos de personalização prontos para uso.
[Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

A seção Archiving emails foi reorganizada com novas informações sobre a ```config-<instance name>.xml``` configuração do arquivo. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

Atualização das informações sobre o workflow técnico do Centro de mensagens (Control). [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

Foram adicionadas informações sobre limitações de capacidade ao configurar uma retransmissão SMTP. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

O conjunto de [documentação do Adobe Campaign Classic](https://helpx.adobe.com/br/support/campaign/classic.html) foi reorganizado para melhorar a utilização.

Uma nova seção Tutorials foi adicionada para facilitar o acesso aos principais recursos do Campaign referentes a materiais de ajuda, instruções, amostras e vídeos. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Uma nova seção foi adicionada para ajudá-lo a monitorar o status do delivery, além de possíveis erros e aprender a corrigi-los. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

A lista de mensagens de erro foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

A nota técnica Experience Cloud Triggers foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/triggers-and-campaign.html)

O guia de migração do Campaign Classic foi adicionado à coleção. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

A Matriz de compatibilidade do Campaign foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

Quando aplicável, as instruções de configuração e instalação agora mencionam a que modelo de hospedagem se aplicam. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

Novo artigo da knowledge base para destacar as diferenças de configuração e recursos entre implantações locais, híbridas e de Managed Services. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-on-prem-vs-hosted.html)

Foram adicionadas instruções sobre como instalar um pacote padrão. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Foram adicionados detalhes sobre como configurar a integração com o Audience Manager ou com o Serviço principal de pessoas. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Atualização da documentação de instalação para mencionar que pgcrypto agora é necessário para a instalação do Campaign, caso o PostreSQL esteja sendo usado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**Novos recursos incluídos na versão**

Aprimoramentos do conector ACS

Conector SAP HANA - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Conector Hadoop via HiveSQL - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

Canal LINE: aprimoramentos de mensagens - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**Outras atualizações de documentação que vêm com a versão**

Novas amostras de consulta foram adicionadas. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

O guia de práticas recomendadas de delivery foi atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/delivery-best-practices.html)

A amostra de teste A/B foi atualizada com instruções que estavam ausentes. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Os vídeos de instruções foram atualizados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Atualizar seção de arquivamento de e-mail. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

Esclarecer o uso do Scheduler em um fluxo de trabalho. [Leia mais](../../workflow/using/scheduler.md)

Adicionar prática recomendada do fluxo de trabalho pausado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

Novo procedimento sobre o arquivo de pré-processamento ao importar e pós-processar durante a exportação de dados em um fluxo de trabalho. Leia [aqui](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html).

O mecanismo de quarentena para a documentação de mensagens SMS foi atualizado para refletir as especificidades do gerenciamento de erros do conector SMPP genérico estendido. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines).

A documentação do Canal do aplicativo móvel foi aprimorada com um procedimento detalhado para enviar notificações avançadas no Android. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications).

A documentação de renderização da Caixa de entrada foi atualizada. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html).

A documentação de Configuração do rastreamento web foi aprimorada com um exemplo e notas atualizadas. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration).

A documentação do Canal SMS foi atualizada com alguns esclarecimentos adicionados à seção de resposta automática que se aplicam ao conector SMPP genérico estendido. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account).

A documentação do Social Marketing foi atualizada. [Leia mais](../../social/using/about-social-marketing.md).

Foi adicionada uma nova nota técnica sobre o aquecimento de IP. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf).

Foi adicionada uma nova introdução à atualização da build. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-build-upgrade.html).

## Maio de 2017 {#release-doc-30-05-2017}

Um novo guia de introdução está disponível: ele apresenta algumas práticas recomendadas que podem ser usadas para fazer entregas com o Adobe Campaign, desde a criação e o direcionamento até o envio e o monitoramento. [Leia mais](https://helpx.adobe.com/br/campaign/kb/delivery-best-practices.html)

O guia de introdução à segurança foi atualizado. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-security.html)

A [documentação &quot;Archiving emails&quot; documentation&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) foi atualizada com a seção [&quot;Email BCC&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) e as [etapas detalhadas para ativar o recurso](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails).

Alguns vídeos foram adicionados e atualizados. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Saiba como enviar um delivery para recipients carregados de um arquivo externo sem atualizar o banco de dados. [Leia mais](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

O exemplo de aceitação dupla foi atualizado. [Leia mais](../../web/using/use-cases--web-forms.md)

## Março de 2017{#release-doc-31-03-2017}

Deliverability: o [guia de introdução](https://docs.adobe.com/content/help/pt-BR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) foi atualizado. A documentação de deliverability agora inclui uma [visão geral](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) mais detalhada e uma descrição do processo de [implementação e das principais etapas](../../delivery/using/deliverability-key-points.md).

A seção &quot;Sending using waves&quot; foi movida e aprimorada com exemplos detalhados, recomendações e casos de uso.    [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

Uma tabela que descreve os erros específicos das mensagens SMS foi adicionada à seção &quot;Quarantine Management&quot;. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Workflows: um novo exemplo de fluxo de trabalho multicanal foi adicionado. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Experience Cloud Triggers: uma nota técnica sobre como configurá-la e usá-la com o Adobe Campaign foi adicionada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/triggers-and-campaign.html)

O Guia do Fluxo de Trabalho foi reorganizado e estendido. Descubra com facilidade como [criar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) e [executar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) um workflow, como [direcionar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) e [gerenciar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) os dados, como [importar dados](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html) e como usar os dados do fluxo de trabalho para [atualizar o banco de dados](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database) ou [enviar deliveries](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow).

Um exemplo de [workflow de importação](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) criado após as [práticas recomendadas de importação](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices) está disponível.
O guia de instalação foi atualizado para essa nova versão. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

A matriz de Compatibilidade foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

Os recipients obtêm valor agregado ao incluir cupons em seus deliveries de email. [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 16/03/2017{#release-17-2}

**Novos recursos incluídos na versão**

ACS Connector

API da Web para Microsoft Dynamics - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Método CCO de arquivamento de email - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Conector S3 (Simple Storage Service) da Amazon - [Leia mais](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

