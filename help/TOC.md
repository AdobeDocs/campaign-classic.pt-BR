---
audience: end-user
breadcrumb-title: Documentação do Campaign Classic v7
product: campaign
title: Guia do Campaign Classic v7
user-guide-title: Guia do Campaign Classic v7
user-guide-description: Documentação do produto do Adobe Campaign Classic v7.
sub-product: adobe campaign classic
type: Documentation
nudge: false
source-git-commit: 77efa1dcdb82a478e93565e84099d568f6a5f5fe
workflow-type: tm+mt
source-wordcount: '1353'
ht-degree: 97%
---

# Documentação do Adobe Campaign Classic v7 {#using}

+ [Documentação do Campaign v7](campaign-classic-home.md)
+ Notas de versão e compatibilidade {#release-notes}
  + [Introdução a atualizações](rn/using/rn-overview.md)
  + [Versão mais recente](rn/using/latest-release.md)
  + Versões anteriores {#previous-releases}
    + [2025](rn/using/release-2025.md)
    + [2024](rn/using/release-2024.md)
  + [Recursos obsoletos](rn/using/deprecated-features.md)
  + [Matriz de compatibilidade](rn/using/compatibility-matrix.md)
+ Introdução {#getting-started}
  + [Introdução ao Adobe Campaign Classic](platform/using/about-adobe-campaign-classic.md)
  + [Iniciar o Adobe Campaign](platform/using/launching-adobe-campaign.md)
  + [Conectores do Campaign](platform/using/about-connectors.md)
  + Perguntas frequentes {#faq}
    + [Perguntas frequentes sobre o Campaign Classic](platform/using/faq-campaign-classic-v7.md)
    + [Atualização da build](platform/using/faq-build-upgrade.md)
  + Privacidade {#privacy}
    + [Privacidade e consentimento](platform/using/privacy-and-recommendations.md)
    + [Gerenciamento de privacidade](platform/using/privacy-management.md)
    + Solicitações de privacidade {#privacy-requests}
      + [Criar e gerenciar solicitações de privacidade](platform/using/privacy-requests-ui.md)
      + [Processo automático de solicitação de privacidade](platform/using/privacy-requests-api.md)
    + [Recusar a venda de informações pessoais](platform/using/privacy-requests-ccpa.md)
  + Gerenciamento de perfis {#profile-management}
    + [Sobre perfis](platform/using/about-profiles.md)
    + [Atualizar dados](platform/using/updating-data.md)
  + Importar e exportar dados {#importing-and-exporting-data}
    + Criar importações e exportações genéricas {#generic-imports-exports}
      + [Monitorar a execução de processos](platform/using/monitoring-jobs-execution.md)
      + [Modelos de importação genérica](platform/using/import-operations-samples.md)
    + Gerenciar a criptografia e a compactação de dados {#managing-data-encryption-compression}
      + [Descompactar ou descriptografar um arquivo antes do processamento](platform/using/unzip-decrypt.md)
      + [Compactar ou criptografar um arquivo antes do processamento](platform/using/zip-encrypt.md)
    + Práticas recomendadas e solução de problemas {#best-practices}
      + [Práticas recomendadas de importação e exportação](platform/using/import-export-best-practices.md)
      + [Práticas recomendadas e solução de problemas do servidor SFTP](platform/using/sftp-server-usage.md)
  + Permissões {#permissions}
    + [Introdução às permissões](platform/using/access-management.md)
    + Autenticação nativa (herdada) {#native}
      + [Criar e gerenciar operadores](platform/using/access-management-operators.md)
      + [Criar e gerenciar grupos](platform/using/access-management-groups.md)
  + Conectores CRM {#connectors}
    + [Introdução aos Conectores CRM](platform/using/crm-connectors.md)
+ Instalar e configurar {#installing-campaign-classic}
  + Princípios de arquitetura {#architecture-and-hosting-models}
    + [Arquitetura geral](installation/using/general-architecture.md)
    + Modelos de hospedagem{#hosting-models-lp}
      + [Modelos de hospedagem do Campaign](installation/using/hosting-models.md)
      + [Matriz de recursos](installation/using/capability-matrix.md)
  + Tipos de implantação {#deployment-types}
    + [Sobre os tipos de implantação](installation/using/about-deployment-types.md)
    + [Implantação independente](installation/using/standalone-deployment.md)
    + [Implantação padrão](installation/using/standard-deployment.md)
    + [Implantação empresarial](installation/using/enterprise-deployment.md)
    + [Implantação mid-sourcing](installation/using/mid-sourcing-deployment.md)
    + [Power Boster e Power Cluster](installation/using/power-booster-and-power-cluster.md)
  + Configurações de segurança e privacidade {#security-privacy}
    + [Lista de verificação de segurança e privacidade](installation/using/get-started-security-privacy.md)
    + [Personalização e privacidade](installation/using/privacy.md)
    + [Gerenciamento de acesso seguro](installation/using/secure-access-management.md)
    + [Diretrizes de script e codificação](installation/using/scripting-coding-guidelines.md)
    + [Rede, banco de dados e SSL/TLS](installation/using/network-database.md)
    + [Configurações de segurança do servidor](installation/using/server-configuration.md)
    + [Configurações de segurança do servidor da Web](installation/using/web-server-configuration.md)
  + Instalar o Campaign (no local){#install-campaign-on-prem}
    + Diretrizes de implantação {#deployment-guidelines}
      + [Servidor de banco de dados](installation/using/database.md)
      + [Servidor de aplicativos](installation/using/application-server.md)
      + [Servidor de mensagens](installation/using/messaging-server.md)
      + [Configuração de rede](installation/using/network-configuration.md)
    + Campaign no Windows {#installing-campaign-in-windows}
      + [Introdução](installation/using/prerequisites-of-campaign-installation-in-windows.md)
      + [Instalar o servidor](installation/using/installing-the-server.md)
      + [Integrar em um servidor Web (Windows)](installation/using/integration-into-a-web-server-for-windows.md)
      + [Disponibilidade do console do cliente para Windows](installation/using/client-console-availability-for-windows.md)
    + Campaign no Linux {#installing-campaign-in-linux}
      + [Pré-requisitos](installation/using/prerequisites-of-campaign-installation-in-linux.md)
      + [Instalar pacotes](installation/using/installing-packages-with-linux.md)
      + [Integrar em um servidor Web](installation/using/integration-into-a-web-server-for-linux.md)
    + [Gerenciamento de fuso horário](installation/using/time-zone-management.md)
    + [Instalar um servidor mid-sourcing](installation/using/mid-sourcing-server.md)
    + Implantar o Campaign (no local) {#initial-configuration}
      + [Principais etapas](installation/using/about-initial-configuration.md)
      + [Criar uma instância e fazer logon](installation/using/creating-an-instance-and-logging-on.md)
      + [Criar e configurar o banco de dados](installation/using/creating-and-configuring-the-database.md)
      + [Implantar uma instância](installation/using/deploying-an-instance.md)
      + [Instalar pacotes integrados](installation/using/installing-campaign-standard-packages.md)
  + Configurar o Campaign {#additional-configurations}
    + [Configuração do servidor do Campaign](installation/using/configuring-campaign-server.md)
    + [Definir zonas de segurança](installation/using/security-zones.md)
    + [Definir permissões de URL](installation/using/url-permissions.md)
    + [Arquivos e recursos](installation/using/file-res-management.md)
    + [Configurar Tomcat](installation/using/configure-tomcat.md)
    + [Definir configurações de entrega](installation/using/configure-delivery-settings.md)
    + [Configurações técnicas de email](installation/using/email-deliverability.md)
    + {hide-from-toc}[Utilização de servidores MX com o Campaign](installation/using/using-mx-servers.md)
    + [Configurar email Cco](installation/using/email-archiving.md)
    + [Configurar o SpamAssassin](installation/using/configuring-spamassassin.md)
  + Conectar ao Campaign{#connect-to-campaign}
    + [Instalar o console do cliente](installation/using/installing-the-client-console.md)
    + Conectar via Adobe ID {#connecting-via-an-adobe-id}
      + [Sobre [!DNL Adobe ID]](integrations/using/about-adobe-id.md)
      + [Configurar o Adobe [!DNL IMS]](integrations/using/configuring-ims.md)
      + [Implementar o Adobe [!DNL IMS]](integrations/using/implementing-ims.md)
      + [Solução de problemas com o IMS](integrations/using/ims-troubleshooting.md)
    + [Conectar-se por meio do LDAP](installation/using/connecting-through-ldap.md)
  + Conectar o Campaign a sistemas externos {#accessing-external-database}
    + [Configurar contas externas](installation/using/external-accounts.md)
    + Configurar o Federated Data Access{#configure-fda}
      + [Introdução ao Federated Data Access](installation/using/about-fda.md)
      + Diretrizes de configuração {#config-databases}
        + [Etapas de configuração](installation/using/configure-fda.md)
        + [Configurar Amazon Redshift](installation/using/configure-fda-redshift.md)
        + [Configurar Azure Synapse](installation/using/configure-fda-synapse.md)
        + [Configurar o Google BigQuery](installation/using/configure-fda-google-big-query.md)
        + [Configurar Hadoop](installation/using/configure-fda-hadoop.md)
        + [Configurar o Microsoft SQL Server](installation/using/configure-fda-sql.md)
        + [Configurar Netezza](installation/using/configure-fda-netezza.md)
        + [Configurar Oracle](installation/using/configure-fda-oracle.md)
        + [Configurar o PostgreSQL](installation/using/configure-fda-postgresql.md)
        + [Configurar SAP HANA](installation/using/configure-fda-sap-hana.md)
        + [Configurar Snowflake](installation/using/configure-fda-snowflake.md)
        + [Configurar Sybase IQ](installation/using/configure-fda-sybase.md)
        + [Configurar Teradata](installation/using/configure-fda-teradata.md)
        + [Configurar Vertica Analytics](installation/using/configure-fda-vertica.md)
    + [Direitos de acesso remoto](installation/using/remote-database-access-rights.md)
    + [Conectar ao banco de dados](installation/using/connecting-to-database.md)
    + [Criar o esquema de dados](installation/using/creating-data-schema.md)
    + [Definir mapeamento de dados](installation/using/defining-data-mapping.md)
  + Apêndices {#appendices}
    + [Arquivo de configuração do servidor](installation/using/the-server-configuration-file.md)
    + [Pontos de acesso de rede do Campaign](installation/using/campaign-network-endpoints.md)
    + [Linhas de comando](installation/using/command-lines.md)
    + [Criar novas instâncias](installation/using/creating-new-instances.md)
    + [Lista de opções do Campaign](installation/using/configuring-campaign-options.md)
    + {hide-from-toc}[Desinstalar o Campaign](installation/using/uninstalling-campaign.md)
+ Guia de migração {#migrating-to-a-new-version}
  + {hide-from-toc}[Migração para o Adobe Campaign v7](migration/using/about-migration.md)
  + Procedimento de migração {#migration-procedure}
    + {hide-from-toc}[Pré-requisitos](migration/using/before-starting-migration.md)
    + {hide-from-toc}[Sobre testes de migração](migration/using/testing-the-migration.md)
    + {hide-from-toc}[Adaptar sua configuração](migration/using/configuring-your-platform.md)
  + Iniciar a migração {#migrating-to-adobe-campaign-7}
    + {hide-from-toc}[Migrar uma plataforma do Microsoft Windows](migration/using/migrating-in-windows-for-adobe-campaign-7.md)
    + {hide-from-toc}[Migrar uma plataforma do Linux](migration/using/migrating-in-linux-for-adobe-campaign-v7.md)
  + {hide-from-toc}[Procedimento de reversão](migration/using/about-rollback.md)
+ Operar e monitorar {#monitoring-campaign-classic}
  + Introdução {#introduction}
    + [Prefácio](production/using/foreword.md)
    + [Arquitetura e portas abertas](production/using/architecture-and-open-ports.md)
    + [Diretrizes de monitoramento](production/using/monitoring-guidelines.md)
  + Procedimentos de produção {#production-procedures}
    + [Princípio de configuração](production/using/configuration-principle.md)
    + [Princípio operacional](production/using/operating-principle.md)
    + [Administração](production/using/administration.md)
    + [Porta Syslogd e zonas de segurança](production/using/syslogd-port-and-security-zones.md)
    + [Arquivos de log](production/using/log-files.md)
    + [Monitorar processos](production/using/monitoring-processes.md)
    + [Comandos usuais](production/using/usual-commands.md)
  + Processamento de dados {#data-processing}
    + [Backup](production/using/backup.md)
    + [Restauração](production/using/restoration.md)
    + [Ambientes duplicados](production/using/duplicating-environments.md)
    + [Fluxo de trabalho de limpeza do banco de dados](production/using/database-cleanup-workflow.md)
  + Atualizar o Adobe Campaign {#updating-adobe-campaign}
    + [Sobre a atualização do Campaign](production/using/introduction.md)
    + [Executar uma atualização de build](production/using/build-upgrade.md)
    + [Atualizar procedimento (no local)](production/using/upgrading.md)
    + [Alternar para Unicode](production/using/switching-to-unicode.md)
    + {hide-from-toc}[Procedimentos de migração](production/using/migration-procedures.md)
  + Manutenção do banco de dados {#database-maintenance}
    + [Recomendações](production/using/recommendations.md)
    + [Tabelas a serem preservadas](production/using/tables-to-maintain.md)
    + [Tipos de manutenção](production/using/types-of-maintenance.md)
    + [Recomendações específicas do RDBMS](production/using/rdbms-specific-recommendations.md)
    + [Objetos de aplicativo](production/using/application-objects.md)
  + Solução de problemas {#troubleshooting-toc}
    + [Visão geral da solução de problemas de produção](production/using/troubleshooting.md)
    + Problemas comuns e gerais {#common-general-issues-toc}
      + [Módulos e problemas frequentes](production/using/modules-and-frequent-issues.md)
      + [Execução do fluxo de trabalho](production/using/workflow-execution.md)
      + [Senha perdida](production/using/lost-password.md)
      + [Atualização do console](production/using/console-update.md)
    + Solução de problemas de entrega {#delivery-troubleshooting-toc}
      + [Problemas de desempenho e de taxa de transferência](production/using/performance-and-throughput-issues.md)
      + [Problemas de exibição de imagem](production/using/image-display-issues.md)
      + [Imagens ausentes](production/using/images-missing.md)
      + [Arquivos temporários](production/using/temporary-files.md)
    + Trabalhar com logs {#working-with-log-toc}
      + [Precisão do log](production/using/log-precision.md)
      + [Problemas de logs de rastreamento](production/using/tracking-logs-issues.md)
    + Problemas de banco de dados {#database-issues-toc}
      + [Desempenho do banco de dados](production/using/database-performances.md)
      + [Codificação do banco de dados Oracle](production/using/encoding-of-the-oracle-database.md)
    + Melhorias na conexão {#connection-improvements-toc}
      + [Falha ao conectar](production/using/failure-to-connect.md)
      + [Limites de conexão](production/using/connection-thresholds.md)
    + Solução de problemas técnicos {#technical-troubleshooting-toc}
      + [Rastreamento em pilha no Linux](production/using/stack-trace-in-linux.md)
      + [Comportamento JSP](production/using/jsp-behavior.md)
      + [Localizar versão do Tomcat](production/using/locate-tomcat-version.md)
+ Desenvolver e estender {#configuring-campaign-classic}
  + [Pacotes de dados](platform/using/working-with-data-packages.md)
  + Modelo de dados {#data-model}
    + [Descrição do modelo de dados](configuration/using/data-model-description.md)
    + [Práticas recomendadas](configuration/using/data-model-best-practices.md)
  + Trabalhar com esquemas {#schema-reference}
    + [Introdução a esquemas](configuration/using/about-schema-reference.md)
    + [Estrutura de esquema](configuration/using/schema-structure.md)
    + [Mapeamento de banco de dados](configuration/using/database-mapping.md)
    + [Gerenciamento de chaves](configuration/using/database-keys.md)
    + Elementos e atributos {#elements-attributes}
      + [Introdução a elementos e atributos](configuration/using/schema-introduction.md)
      + [Atributo](configuration/using/schema/attribute.md)
      + [Cálculo de string](configuration/using/schema/compute-string.md)
      + [Condição](configuration/using/schema/condition.md)
      + [Índice DB](configuration/using/schema/db-index.md)
      + [Elemento](configuration/using/schema/element.md)
      + [Enumeração](configuration/using/schema/enumeration.md)
      + [Ajuda](configuration/using/schema/help.md)
      + [Associar-se](configuration/using/schema/join.md)
      + [Chave](configuration/using/schema/key.md)
      + [Campo principal](configuration/using/schema/keyfield.md)
      + [Método](configuration/using/schema/method.md)
      + [Métodos](configuration/using/schema/methods.md)
      + [Parâm](configuration/using/schema/param.md)
      + [Parâmetros](configuration/using/schema/parameters.md)
      + [SrcSchema](configuration/using/schema/srcschema.md)
      + [Sysfilter](configuration/using/schema/sysfilter.md)
      + [Valor](configuration/using/schema/value.md)
  + Edição de esquemas {#editing-schemas}
    + [Esquema de uma tabela existente](configuration/using/schema-of-an-existing-table.md)
    + [Extensão de um esquema](configuration/using/extending-a-schema.md)
    + [Atualização da estrutura do banco de dados](configuration/using/updating-the-database-structure.md)
    + [Novo assistente de campo](configuration/using/new-field-wizard.md)
    + [Estrutura de um esquema de dados](configuration/using/structure-of-a-data-schema.md)
    + [Regeneração de esquemas](configuration/using/regenerating-schemas.md)
    + [Exemplos de edição de esquemas](configuration/using/examples-of-schemas-edition.md)
  + Formulários de entrada {#input-forms}
    + [Editar formulários](configuration/using/editing-forms.md)
  + API {#api}
    + [Sobre serviços da Web](configuration/using/about-web-services.md)
    + [Chamadas de serviço da Web](configuration/using/web-service-calls.md)
    + [APIs orientadas por dados](configuration/using/data-oriented-apis.md)
    + [APIs direcionadas por empresas](configuration/using/business-oriented-apis.md)
    + [Implementação de métodos SOAP](configuration/using/implementing-soap-methods.md)
    + [Métodos SOAP em JavaScript](configuration/using/soap-methods-in-javascript.md)
    + [Adição de funções SQL extras](configuration/using/adding-additional-sql-functions.md)
  + Hierarquia de navegação {#navigation-hierarchy}
    + [Configurar a hierarquia do Explorer](configuration/using/configuration.md)
    + [Editar a hierarquia do Explorer](configuration/using/edition.md)
  + Usar tabela de destinatário personalizada {#use-a-custom-recipient-table}
    + [Sobre tabela de destinatário personalizada](configuration/using/about-custom-recipient-table.md)
    + [Características do esquema](configuration/using/schema-characteristics.md)
    + [Target mapping](configuration/using/target-mapping.md)
    + [Configuração da interface](configuration/using/configuring-the-interface.md)
    + [Seed addresses](configuration/using/seed-addresses.md)
    + [Criação de filtros](configuration/using/creating-filters.md)
    + [Criação de uma lista de perfis com base em um fluxo de trabalho](configuration/using/creating-a-profile-list-with-a-workflow.md)
    + [Gerenciamento de fluxos de trabalho](configuration/using/managing-workflows.md)
    + [Gerenciamento de relatórios](configuration/using/managing-reports.md)
  + Configuração do rastreamento web {#setting-up-web-tracking}
    + [Sobre o rastreamento Web](configuration/using/about-web-tracking.md)
    + [Modo de rastreamento Web](configuration/using/web-tracking-mode.md)
    + [Tag de rastreamento Web: definição](configuration/using/web-tracking-tag-definition.md)
    + [Etapas de configuração](configuration/using/setup-stages.md)
    + [Parâmetros adicionais](configuration/using/additional-parameters.md)
    + [Criação de tags de rastreamento Web](configuration/using/creating-web-tracking-tags.md)
    + [Inserir tags no site](configuration/using/inserting-tags-in-your-site.md)
    + [Coleta de todas as visitas](configuration/using/collecting-all-visits.md)
    + [Tracking anônimo](configuration/using/anonymous-tracking.md)
+ Criar e enviar mensagens {#sending-messages}
  + [Introdução a mensagens](delivery/using/communication-channels.md)
  + {hide-from-toc}[Configurações de entrega – OCULTO](delivery/using/delivery-settings.md)
  + [Enviar emails](delivery/using/about-email-channel.md)
  + Enviar SMS {#sending-messages-on-mobiles}
    + Configurar canal de SMS {#sms-set-up}
      + [Configurar SMS em uma instância independente](delivery/using/sms-set-up.md)
      + [Configurar SMS em uma infraestrutura de mid-sourcing](delivery/using/sms-set-up-mid.md)
      + [Protocolo e configurações do conector de SMS](delivery/using/sms-protocol.md)
      + [Configuração adicional](delivery/using/sms-send.md)
      + [Solução de problemas de SMS](delivery/using/troubleshooting-sms.md)
  + [Enviar notificações por push](delivery/using/about-mobile-app-channel.md)
  + Enviar notificações por push {#sending-push-notifications}
    + {hide-from-toc}[Solução de problemas – OCULTO](delivery/using/push-troubleshooting.md)
  + [Enviar correspondências diretas](delivery/using/about-direct-mail-channel.md)
  + Personalizar entregas {#personalizing-deliveries}
    + [Sobre personalização](delivery/using/about-personalization.md)
  + Usar seed addresses {#using-seed-addresses}
    + [Caso de uso: selecionar seed addresses de acordo com critérios](delivery/using/use-case-selecting-seed-addresses-on-criteria.md)
    + [Caso de uso: configurar a substituição de campo](delivery/using/use-case-configuring-the-field-substitution.md)
  + Teste A/B {#a-b-testing}
    + [Introdução ao teste A/B](delivery/using/get-started-a-b-testing.md)
    + [Configurar teste A/B](delivery/using/configuring-a-b-testing.md)
    + Caso de uso {#use-case}
      + [Sobre este caso de uso](delivery/using/a-b-testing-use-case.md)
      + [Criar um fluxo de trabalho de direcionamento](delivery/using/a-b-testing-uc-targeting-workflow.md)
      + [Configurar amostras de população](delivery/using/a-b-testing-uc-population-samples.md)
      + [Criar os modelos de entrega](delivery/using/a-b-testing-uc-delivery-templates.md)
      + [Configurar as entregas](delivery/using/a-b-testing-uc-configuring-deliveries.md)
      + [Criar o script](delivery/using/a-b-testing-uc-script.md)
      + [Definir a entrega final](delivery/using/a-b-testing-uc-final-delivery.md)
      + [Iniciar o fluxo de trabalho](delivery/using/a-b-testing-uc-start-workflow.md)
      + [Analisar o resultado](delivery/using/a-b-testing-uc-analyzing.md)
  + Serviços e assinaturas {#subscriptions-and-referrals}
    + [Sobre serviços e subscrições](delivery/using/about-services-and-subscriptions.md)
    + [Gerenciar subscrições](delivery/using/managing-subscriptions.md)
    + [Marketing viral e social](delivery/using/viral-and-social-marketing.md)
  + Monitorar entregas {#monitoring-deliveries}
    + [Monitorar desempenho da entrega](delivery/using/about-delivery-monitoring.md)
    + [Rastrear mensagens](delivery/using/about-message-tracking.md)
    + [Desempenho da entrega e solução de problemas](delivery/using/delivery-performance-troubleshooting.md)
    + [Falhas de entrega e gerenciamento de quarentena](delivery/using/delivery-failures-quarantine.md)
    + [Avançado: logs de entrega personalizados](delivery/using/customize-delivery-logs.md)
  + Gerenciamento de capacidade de entrega {#deliverability-management}
    + [O que é capacidade de entrega](delivery/using/about-deliverability.md)
    + [Renderização da caixa de entrada](delivery/using/inbox-rendering.md)
    + [Solução de problemas](delivery/using/deliverability-faq.md)
  + Módulo de gerenciamento de conteúdo {#content-management}
    + [Sobre gerenciamento de conteúdo](delivery/using/about-content-management.md)
    + [Recursos e princípios do gerenciador de conteúdo](delivery/using/content-manager-resources-and-principles.md)
    + [Caso de uso: criação de gerenciamento de conteúdo](delivery/using/use-case-creating-content-management.md)
    + [Esquemas de dados](delivery/using/data-schemas.md)
    + [Formulários de entrada](delivery/using/input-forms.md)
    + [Formatação](delivery/using/formatting.md)
    + [Modelos de publicação](delivery/using/publication-templates.md)
    + [Usar um modelo de conteúdo](delivery/using/using-a-content-template.md)
    + [Enriquecer conteúdo](delivery/using/enriching-content.md)
    + [Automatizar via fluxos de trabalho](delivery/using/automating-via-workflows.md)
+ Mensagens transacionais {#transactional-messaging}
  + [Introdução a mensagens transacionais](message-center/using/about-transactional-messaging.md)
  + Configurar mensagens transacionais {#configure-transactional-messaging}
    + [Arquitetura de mensagens transacionais](message-center/using/transactional-messaging-architecture.md)
    + [Configurar instâncias](message-center/using/configuring-instances.md)
    + [Configurações adicionais](message-center/using/additional-configurations.md)
  + Modelos de mensagem {#message-templates}
    + [Testar modelos de mensagem](message-center/using/testing-message-templates.md)
  + [Caso de uso](message-center/using/transactional-email-with-attachments.md)
+ Gerenciar ofertas {#managing-offers}
  + Introdução à interação {#interaction-overview}
    + [Interação e gerenciamento de ofertas](interaction/using/interaction-and-offer-management.md)
  + Parâmetros avançados {#advanced-parameters}
    + [Usar parâmetros avançados](interaction/using/using-advanced-parameters.md)
    + [Dados adicionais](interaction/using/additional-data.md)
    + [Criar um ambiente de teste](interaction/using/creating-a-test-environment.md)
    + [Modificar o comportamento padrão do mecanismo](interaction/using/hooks.md)
    + [Arquiteturas distribuídas](interaction/using/distributed-architectures.md)
    + [Configuração do buffer de dados](installation/using/interaction-data-buffer.md)
+ Criar e compartilhar relatórios {#reporting}
  + Introdução aos relatórios {#reporting-in-adobe-campaign}
    + [Práticas recomendadas para relatórios](reporting/using/best-practices.md)
  + Acessar relatórios integrados {#accessing-built-in-reports}
    + [Sobre relatórios integrados](reporting/using/about-campaign-built-in-reports.md)
  + Analisar populações {#analyzing-populations}
    + [O que é análise descritiva?](reporting/using/about-descriptive-analysis.md)
    + [Crie seu primeiro relatório de análise descritiva](reporting/using/using-the-descriptive-analysis-wizard.md)
    + [Gerenciar e configurar o seu relatório de análise](reporting/using/processing-a-report.md)
    + [Casos de uso de relatórios de análise](reporting/using/use-cases.md)
  + Criar novos relatórios {#creating-new-reports}
    + [Etapas principais para criar um relatório](reporting/using/about-reports-creation-in-campaign.md)
    + [Criar um novo relatório](reporting/using/creating-a-new-report.md)
    + [Coletar dados para analisar](reporting/using/collecting-data-to-analyze.md)
    + [Usar o contexto](reporting/using/using-the-context.md)
    + [Criar uma tabela](reporting/using/creating-a-table.md)
    + [Criar um gráfico](reporting/using/creating-a-chart.md)
    + [Layout do elemento](reporting/using/element-layout.md)
    + [Definir um conteúdo condicional](reporting/using/defining-a-conditional-content.md)
    + [Recursos avançados](reporting/using/advanced-functionalities.md)
    + [Propriedades do relatório](reporting/using/properties-of-the-report.md)
    + [Configurar acesso ao relatório](reporting/using/configuring-access-to-the-report.md)
    + [Ações em relatórios](reporting/using/actions-on-reports.md)
  + [Criar relatórios com cubos](reporting/using/ac-cubes.md)
+ Integrar com a Adobe Experience Cloud {#integrating-with-adobe-experience-cloud}
  + [Introdução às integrações do Campaign](integrations/using/about-campaign-integrations.md)
  + [Crie sua conta técnica da Adobe](integrations/using/oauth-technical-account.md)
  + Adobe Experience Cloud Triggers {#experience-triggers}
    + [Trabalhar com o  [!DNL Experience Cloud Triggers]](integrations/using/about-triggers.md)
    + [Configurar pipeline](integrations/using/configuring-pipeline.md)
    + [Configurar eventos para implementação personalizada](integrations/using/events.md)
    + [Monitoramento de pipeline](integrations/using/pipeline-monitoring.md)
    + [Solução de problemas de pipeline](integrations/using/pipeline-troubleshooting.md)
  + Origens e destinos da Adobe Experience Platform {#aep-sources-destinations}
    + [Trabalhar com origens e destinos](integrations/using/get-started-sources-destinations.md)
    + [Assimilar públicos-alvos da Adobe Experience Platform no Campaign](integrations/using/ingest-aep-data.md)
    + [Exportar dados do Campaign para a Adobe Experience Platform](integrations/using/export-campaign-data.md)
  + Adobe Analytics Connector{#analytics-connector}
    + [Introdução ao conector do Adobe Analytics](integrations/using/gs-aa.md)
    + [Provisionamento do conector do Adobe Analytics](integrations/using/adobe-analytics-provisioning.md)
  + Compartilhamento de público-alvo {#audience-sharing}
    + [Compartilhar públicos-alvos com a [!DNL Adobe Experience Cloud]](integrations/using/sharing-audiences-with-adobe-experience-cloud.md)
    + [Enviar solicitação à Adobe](integrations/using/submitting-request-to-adobe.md)
    + [Configurar a integração de públicos-alvos compartilhados no [!DNL Adobe Campaign]](integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
    + {hide-from-toc}[Solução de problemas](integrations/using/integrations-troubleshooting.md)
    + [Importar e exportar públicos-alvos](integrations/using/importing-and-exporting-audiences.md)
  + Compartilhamento de ativos {#asset-sharing}
    + [Compartilhar ativos com a [!DNL Adobe Experience Cloud]](integrations/using/sharing-assets-with-adobe-experience-cloud.md)
    + [Configurar acesso ao [!DNL Assets]](integrations/using/configuring-access-to-assets.md)
    + [Inserir um ativo compartilhado](integrations/using/inserting-a-shared-asset.md)
  + Adobe Experience Manager {#adobe-experience-manager}
    + [Configurar a integração](integrations/using/configuring-the-integration.md)
  + Adobe Target {#adobe-target}
    + [Configurar a integração com o [!DNL Adobe Target]](integrations/using/configuring-the-integration-with-adobe-target.md)
+ Integrar a redes sociais {#integrating-with-social-media}
  + [Sobre marketing social](social/using/about-social-marketing.md)
+ Notas técnicas {#technotes}
  + [Recomendações para dimensionamento de hardware](technotes/using/hardware-sizing.md)
  + [Enviar com o MTA aprimorado](delivery/using/sending-with-enhanced-mta.md)
  + [Atividade de fluxo de trabalho de SMS de entrada para infraestrutura mid-sourcing](technotes/using/inbound-sms-wf.md)
  + Atualização para o IMS{#ims}
    + [Transição para o Adobe IMS](technotes/using/ac-ims.md)
    + [Migração de usuários para o IMS](technotes/using/migrate-users-to-ims.md)
    + [Migração de operadores técnicos para o Developer Console](technotes/using/ims-migration.md)
    + [Impacto da interface após a migração do IMS](technotes/using/impact-ims-migration.md)
  + Atualizações e compatibilidade{#technote-migration}
    + [Habilitar o Microsoft Edge Chromium](technotes/using/edge-chromium.md)
    + {hide-from-toc}[Atualização de segurança do Apache](technotes/using/acc-apache-upgrade.md)
    + {hide-from-toc}[Atualizações de sistema de 2023](technotes/using/tech-stack-upgrade.md)
    + {hide-from-toc}[Migrar para a API do Adobe Analytics 2.0](technotes/using/analytics-2-migration.md)
  + Emails e notificações por push{#technotes-email}
    + [Proteção de privacidade do App Mail no Apple iOS](technotes/using/apple-mail-app-privacy-protection.md)
    + [Atualização de certificado do iOS](technotes/using/ios-certificate-update.md)
  + Migração para o Adobe Managed Services{#dc-migration}
    + {hide-from-toc}[Migração para a Nuvem pública](technotes/using/dc-migration.md)
    + {hide-from-toc}[Perguntas frequentes](technotes/using/dc-migration-faq.md)
  + [Funções baseadas em GCM](technotes/using/gcm-functions.md)
+ [Painel de controle do Campaign](https://experienceleague.adobe.com/pt-br/docs/control-panel/using/control-panel-home)
