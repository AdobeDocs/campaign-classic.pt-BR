---
title: Atualizações da documentação do Adobe Campaign Classic
description: Esta página lista todos os novos recursos e atualizações de documentação para cada versão do Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-documentation-updates
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '3932'
ht-degree: 98%

---


# Atualizações de documentação{#documentation-updates}

Esta página lista todos os novos recursos e atualizações de documentação por mês e versão do Campaign.

Você também pode consultar as [Notas de versão do Adobe Campaign Classic](../../rn/using/latest-release.md) para obter mais atualizações.

## Novembro de 2020 {#nov-2020}

[A versão](../../rn/using/release--20-2.md#release-20-2-3-build-9182) 20.2.3 da campanha foi transferida para a disponibilidade geral (GA).

A seção Privacidade foi movida e aprimorada com duas novas seções: [Gerenciamento](../../platform/using/privacy-management.md) de privacidade e [gerenciamento de solicitações](../../platform/using/privacy-requests.md)de privacidade.

## Outubro de 2020 {#oct-2020}

**Novos recursos incluídos na versão 20.3**

Melhorias nas notificações por push para iOS - [Saiba mais](../../delivery/using/configuring-the-mobile-application.md)

Melhorias nas notificações por push para Android - [Saiba mais](../../delivery/using/configuring-the-mobile-application-android.md)

**Outras atualizações de documentação que vêm com a versão**

A matriz de Compatibilidade foi atualizada. [Leia mais](../../rn/using/compatibility-matrix.md)

A página de recursos obsoletos e removidos foi atualizada. [Leia mais](../../rn/using/deprecated-features.md)

As notas de versão e a matriz de compatibilidade para a versão Gold Standard estão disponíveis em uma seção exclusiva.
[Leia mais](../../rn/using/gold-standard.md#gs-10).

Triggers integration originally based on oAUTH authentication setup to access pipeline has now been changed and moved to Adobe I/O. [Read more](../../integrations/using/configuring-adobe-io.md)

**Outras atualizações**

As páginas de documentação foram atualizadas para refletir a atualização do Tomcat 8.

Detalhes foram adicionados na descrição da caixa “Sobre” na seção “Obtendo sua versão do Adobe Campaign”. [Leia mais](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

Diretrizes para executar uma atualização de build foram adicionadas à seção “Atualização do Adobe Campaign Classic”. Saiba mais [Saiba mais](../../production/using/build-upgrade.md)

As perguntas frequentes sobre a atualização da build do Campaign foram adicionadas às perguntas mais frequentes do Campaign. Saiba mais [Saiba mais](../../platform/using/faq-build-upgrade.md)

Os modelos de hospedagem local, hospedados e híbridos do Campaign agora são descritos em uma seção exclusiva. [Leia mais](../../installation/using/hosting-models.md)

A matriz de recursos do Campaign por modelo de hospedagem foi atualizada e movida para a guia Instalação. [Leia mais](../../installation/using/capability-matrix.md)

A seção de recursos avançados dos relatórios do Campaign foi aprimorada para detalhar como usar parâmetros de URL e variáveis em relatórios personalizados. [Leia mais](../../reporting/using/advanced-functionalities.md)

A página de propriedades dos relatórios foi reorganizada e aprimorada para facilitar a configuração. [Leia mais](../../reporting/using/properties-of-the-report.md)

Uma nova nota técnica foi criada com detalhes sobre como migrar do protocolo binário herdado para a API do provedor APNs baseada em HTTP/2. [Leia mais](https://helpx.adobe.com/br/campaign/kb/migrate-to-apns-http2.html)

## Setembro de 2020 {#september-2020}

Uma observação foi adicionada para especificar que a contagem de perfis ativos está disponível somente para instâncias de Marketing. [Leia mais](../../platform/using/about-profiles.md#active-profiles)

Uma nova amostra sobre a edição de esquema foi adicionada para vincular um campo a uma tabela de referência existente. [Leia mais](../../configuration/using/examples-of-schemas-edition.md#uc-link)

Adição de uma observação sobre o uso de dados adicionais com seeds addresses em deliveries. [Leia mais](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## Agosto de 2020 {#aug-2020}

Conheça as práticas recomendadas relacionadas ao design do delivery e ao envio com o Campaign em uma seção dedicada. [Leia mais](../../delivery/using/delivery-best-practices.md)

Uma landing page de práticas recomendadas de deliverability foi aprimorada para facilitar o acesso às subseções. [Leia mais](../../delivery/using/deliverability-key-points.md)

Os vídeos do passo a passo estão disponíveis nos seguintes tópicos:

* [Como configurar o gerenciamento de fadiga usando regras de tipologia e filtros predefinidos](../../campaign/using/about-campaign-typologies.md)

* [Como criar um email em uma campanha](../../campaign/using/marketing-campaign-deliveries.md)

* [Como criar um informativo multilíngue com conteúdo condicional](../../delivery/using/conditional-content.md)

* [Como configurar e implantar um template do delivery](../../delivery/using/creating-a-delivery-template.md)

* [Como ativar e usar a AMP para emails](../../delivery/using/defining-interactive-content.md)

* [Como personalizar emails usando blocos de conteúdo dinâmico](../../delivery/using/personalization-blocks.md)

* [Como personalizar emails usando campos de personalização](../../delivery/using/personalization-fields.md)

* [Como gerenciar seed e provas em um email](../../delivery/using/steps-defining-the-target-population.md)

* [Como configurar um delivery recorrente](../../workflow/using/recurring-delivery.md)

* [Como configurar um delivery contínuo](../../workflow/using/continuous-delivery.md)

Foram adicionadas informações sobre as verificações e ações a serem executadas ao obter o erro “Não foi possível resolver o nome do host” após a conexão com um servidor FTP. [Leia mais](../../platform/using/sftp-server-usage.md)

Novos casos de uso são mencionados na lista de [casos de uso de workflow](../../workflow/using/about-workflow-use-cases.md):

* Automação de criação, edição e publicação de conteúdo
* Configuração de um processo de aprovação de recipient antes do envio de um delivery
* Chamada de uma variável de instância em uma query
* Aplicar uma porcentagem dividida em uma população

A seção atividade de **[!UICONTROL AND-join]** foi aprimorada com informações adicionais sobre sua utilização, bem como uma observação sobre o uso de variáveis. [Leia mais](../../workflow/using/and-join.md)

## Julho de 2020 {#july-2020}

Um caso de uso sobre como atualizar automaticamente uma lista usando um query incremental foi adicionado aos casos de uso do workflow. [Leia mais](../../workflow/using/about-workflow-use-cases.md)

As [Notas de versão](../../rn/using/latest-release.md) foram reorganizadas: uma [página de visão geral](../../rn/using/latest-release.md) foi adicionada com informações sobre status de criação, processo de atualização, recomendações e links importantes. Uma página dedicada às [versões do Gold Standard](../../rn/using/gold-standard.md) também foi adicionada e a [matriz de Compatibilidade](../../rn/using/compatibility-matrix.md) foi integrada.

Uma nova seção foi adicionada com diretrizes relacionadas ao monitoramento do Campaign Classic. [Leia mais](../../production/using/monitoring-guidelines.md)

A seção Privacidade e consentimento foi aprimorada com informações mais detalhadas e links úteis. [Leia mais](../../platform/using/privacy-and-recommendations.md).

A página de gerenciamento de privacidade no Campaign Classic foi atualizada com informações sobre o campo &quot;regulamento&quot;, que agora está disponível ao usar a API, permitindo a configuração do processo automático de solicitação de privacidade. [Leia mais](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

A página Visão geral do gerenciamento de privacidade foi atualizada para incluir informações sobre a Lei de Proteção de Dados Pessoais (PDPA) da Tailândia e sobre a Lei Geral de Dados (LGPD) do Brasil. [Leia mais](https://helpx.adobe.com/br/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

As informações foram adicionadas nos registros de subworkflows e no comportamento em caso de erro. [Leia mais](../../workflow/using/sub-workflow.md)

As práticas recomendadas foram adicionadas na seção atividade de **[!UICONTROL Scheduler]**. [Leia mais](../../workflow/using/scheduler.md)

## Junho de 2020 {#june-2020}

A seção Remoção de um endereço em quarentena foi atualizada. Ela esclarece os casos em que os endereços são removidos automaticamente da lista de quarentena. [Leia mais](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Casos de uso foram adicionados em como [criptografar](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt) e [descriptografar](../../workflow/using/importing-data.md#use-case-gpg-decrypt) dados usando o Painel de controle do Campaign e workflows do Campaign.

Os acionadores da Experience Cloud e a página de integração do Adobe Campaign Classic foram movidos [para cá](../../integrations/using/about-triggers.md).

## julho de 2020 {#release-20-2}

**Novos recursos incluídos na versão 20.2**

Suporte a emoticons – [Leia mais](../../delivery/using/customizing-emoticon-list.md)

Conector FDA do Azure Synapse - [Leia mais](../../installation/using/configure-fda-synapse.md)

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

A tabela de direitos da FDA foi movida para a documentação Acesso a um banco de dados externo (FDA). [Leia mais](../../installation/using/remote-database-access-rights.md)

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

## Janeiro de 2020 {#release-20-1}

**Novos recursos incluídos na versão 20.1**

Conector FDA do Snowflake - [Leia mais](../../installation/using/configure-fda-snowflake.md)

Aprimoramento do conector FDA do Hadoop - [Leia mais](../../installation/using/configure-fda-hadoop.md)

**Outras atualizações de documentação que vêm com a versão**

Os guias de [instalação](../../installation/using/general-architecture.md), [produção](../../production/using/foreword.md) e [configuração](../../configuration/using/additional-parameters.md) foram atualizados com a nova unidade do sistema usada pela inicialização do serviço nlserver. Ainda é possível usar o /etc/init.d/nlserver6, mas a Adobe recomenda usar o comando systemctl agora para interagir com o serviço nlserver.

O guia de instalação está atualizado e sincronizado com a versão mais recente da matriz de compatibilidade. Novos sistemas compatíveis foram adicionados. As ocorrências em sistemas obsoletos e sem suporte foram removidas. [Leia mais](../../installation/using/general-architecture.md)

A matriz de compatibilidade foi atualizada com os conectores do Hadoop 3.0 e Snowflake FDA. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

Uma prática recomendada na afinidade IP foi adicionada ao guia de instalação. [Leia mais](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

A seção workflow de limpeza de banco de dados foi atualizada. Os números de lotes fornecidos agora refletem a implementação do código. [Leia mais](../../production/using/database-cleanup-workflow.md)

Uma limitação no FDA sobre HTTP foi adicionada ao guia de mensagens transacionais. [Leia mais](../../production/using/database-cleanup-workflow.md)

Adicionamos informações sobre a nova opção que permite definir um período de tempo limite para as atividades de workflow **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]**. [Leia mais](../../workflow/using/sql-code-and-javascript-code.md)

Adicionamos informações sobre a nova visualização **[!UICONTROL Start Pending]** disponível no nó **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]**. [Leia mais](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

O guia [Envio de notificações via push](../../delivery/using/about-mobile-app-channel.md) foi movido, reorganizado e aprimorado com informações mais claras:

O novo parâmetro para a configuração do relatório de URLs está documentado [aqui](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

A página **Matriz de recursos no local e hospedada do Campaign Classic** foi atualizada com os novos conectores do FDA. [Leia mais](../../installation/using/capability-matrix.md).

A página **Matriz de recursos do Campaign Classic** foi atualizada. [Leia mais](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html)

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

## Dezembro de 2019 {#december-2019}

A opção &quot;WdbcOptions_TempDbName&quot; foi adicionada à lista de opções do Campaign. [Leia mais](../../installation/using/configuring-campaign-options.md)

A página da matriz FDA foi movida para [este local](../../installation/using/remote-database-access-rights.md).

A página da matriz de direitos de acesso foi movida [aqui](https://docs.adobe.com/content/help/pt-BR/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf).

A seção que descreve como definir conteúdo interativo com AMP foi movida. [Leia mais](../../delivery/using/defining-interactive-content.md)

**Novos recursos incluídos na versão 19.2**

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

## Maio de 2019 {#release-19-1}

**Novos recursos incluídos na versão 19.1**

Painel de controle - [Leia mais](https://docs.adobe.com/content/help/pt-BR/control-panel/using/control-panel-home.translate.html)

Trilha de auditoria - [Leia mais](../../production/using/audit-trail.md)

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

A página [Matriz de recursos no local e hospedada do Campaign Classic](../../installation/using/capability-matrix.md) foi atualizada com informações relacionadas a email Cco.

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

Os vídeos em destaque foram movidos para [este local](https://docs.adobe.com/content/help/pt-BR/campaign-classic-learn/tutorials/overview.html).

Duas notas técnicas foram adicionadas ao [Teradata](https://helpx.adobe.com/br/campaign/kb/campaign_fda_teradata.html) e ao [MySQL 5.7](https://helpx.adobe.com/br/campaign/kb/campaign_fda_mysql.html).
