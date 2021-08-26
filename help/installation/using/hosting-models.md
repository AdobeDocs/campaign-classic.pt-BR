---
product: campaign
title: Modelos de hospedagem
description: Modelos de hospedagem do Discover Campaign
feature: Overview
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 2%

---

# Modelos de hospedagem{#hosting-models}

![](../../assets/v7-only.svg)

A Adobe Campaign oferece uma escolha de três modelos de hospedagem, proporcionando flexibilidade e liberdade para escolher o melhor modelo ou modelos para atender às necessidades dos negócios.

>[!NOTE]
>
>Para ambientes hospedados no Adobe, as etapas principais de instalação e configuração só podem ser executadas pelo Adobe, como configurar o servidor e personalizar os arquivos de configuração da instância. Para saber mais sobre as principais diferenças entre modos de implantação, consulte [esta página](../../installation/using/capability-matrix.md).

## Managed Services / Hospedado

O Adobe Campaign pode ser implantado como um Serviço gerenciado: todos os componentes do Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados do Campaign do cliente são totalmente hospedados pelo Adobe, incluindo execução de email, mirror pages, servidor de rastreamento e componentes da Web voltados para o exterior, como cancelar a assinatura da página/centro de preferências e landing pages.

![](assets/deployment_hosted.png)

Como cliente hospedado, a maioria das etapas de instalação e configuração é executada pelo Adobe. Você pode acessar as seguintes seções para personalizar sua implementação:

* Configurar URLs de página de rastreamento e mirror page por marca. Para mensagens transacionais, consulte [nesta seção](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instale o console do cliente: consulte [nesta seção](../../installation/using/installing-the-client-console.md).
* Saiba mais sobre as ferramentas de deliverability e as práticas recomendadas lendo a [documentação detalhada](../../delivery/using/about-deliverability.md).
* Configure as opções do Campaign: consulte [nesta seção](../../installation/using/configuring-campaign-options.md).
* Configurar conectores CRM: consulte [nesta seção](../../platform/using/crm-connectors.md).

## No local

O Adobe Campaign pode ser implantado no local: todos os componentes do Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados, residem no local no data center do cliente. Neste modelo de implantação, o cliente gerencia todas as atualizações e atualizações de software e hardware, e um administrador de banco de dados dedicado precisa executar tarefas de manutenção e otimização para garantir o gerenciamento da instância do Campaign.

![](assets/deployment_onpremise.png)

Como cliente local, antes de começar a implantar o Campaign Classic, atenda aos seguintes pré-requisitos e recomendações:

* Leia a [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md) que lista todas as versões dos sistemas e componentes compatíveis com o Adobe Campaign.
* Dependendo do seu ambiente, leia os [pré-requisitos para Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) e [pré-requisitos para Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Saiba mais sobre as recomendações relacionadas aos mecanismos de banco de dados [nesta seção](../../installation/using/database.md).
* Verifique se as camadas de acesso ao banco de dados necessárias estão instaladas no servidor e acessíveis na conta do Adobe Campaign. [Saiba mais](../../installation/using/application-server.md).
* Configure suas redes, pois alguns processos precisam se comunicar com outras pessoas ou acessar a LAN e a Internet. Isso significa que algumas portas TCP precisam estar abertas para esses processos. [Saiba ](../../installation/using/network-configuration.md) mais sobre os requisitos de configuração de rede.
* Leia [Lista de verificação de segurança e privacidade da campanha](https://helpx.adobe.com/br/campaign/kb/acc-security.html).
* Verifique as diretrizes gerais para estimar os requisitos de hardware para a implantação no local [neste artigo](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html).

## Híbrido

Quando implantado como um modelo híbrido, o software da solução Adobe Campaign fica no local, no local do cliente, e o gerenciamento de execução é fornecido como um serviço em nuvem pelo Adobe. A instância de marketing do Adobe Campaign é instalada dentro do firewall de um cliente, portanto, as informações de identificação pessoal (PII) permanecem internas e somente os dados necessários para personalizar emails são enviados para a nuvem para execução de email. A instância de execução, hospedada na nuvem, recebe as solicitações da instância No local para fornecer emails. Essa instância personaliza todos os emails e os entrega. Nenhum dado de qualquer tipo é permanentemente armazenado na nuvem.

![](assets/deployment_hybrid.png)

Como cliente híbrido, a maioria das etapas de instalação e configuração é executada pelo Adobe. Você pode acessar as seguintes seções para personalizar sua implementação:

* Configurar mensagens transacionais: consulte [nesta seção](../../message-center/using/transactional-messaging-architecture.md).
* Configurar URLs de página de rastreamento e mirror page por marca. Para mensagens transacionais, consulte [nesta seção](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instale o console do cliente: consulte [nesta seção](../../installation/using/installing-the-client-console.md).
* Instalar pacotes incorporados: consulte [nesta seção](../../installation/using/installing-campaign-standard-packages.md).
* Capacidade de entrega: configure [MX rules](../../installation/using/email-deliverability.md#mx-configuration) e [formatos de email](../../installation/using/email-deliverability.md#managing-email-formats). Saiba mais sobre as ferramentas de deliverability e as práticas recomendadas lendo a [documentação detalhada](../../delivery/using/about-deliverability.md).
* Configure as opções do Campaign: consulte [nesta seção](../../installation/using/configuring-campaign-options.md).
* Configure um banco de dados externo (Federated Data Access): consulte [nesta seção](../../installation/using/about-fda.md).
* Configuração de conectores CRM: consulte [nesta seção](../../platform/using/crm-connectors.md).
* Para saber mais sobre os princípios de implantação de mid-sourcing, consulte [nesta seção](../../installation/using/mid-sourcing-deployment.md).
