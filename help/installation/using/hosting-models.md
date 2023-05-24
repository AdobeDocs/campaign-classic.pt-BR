---
product: campaign
title: Modelos de hospedagem
description: Descubra modelos de hospedagem do Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 2%

---

# Modelos de hospedagem{#hosting-models}



A Adobe Campaign oferece três opções de modelos de hospedagem, proporcionando flexibilidade e liberdade para escolher o melhor modelo ou modelos para atender às necessidades da empresa.

>[!NOTE]
>
>Para ambientes hospedados por Adobe, as etapas principais de instalação e configuração só podem ser executadas por Adobe, como configuração do servidor e personalização dos arquivos de configuração da instância. Para saber mais sobre as principais diferenças entre modos de implantação, consulte [esta página](../../installation/using/capability-matrix.md).

## Managed Services / hospedado

O Adobe Campaign pode ser implantado de forma as a Managed Service: todos os componentes do Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados do Campaign do cliente, são totalmente hospedados pelo Adobe, incluindo execução de email, mirror pages, servidor de rastreamento e componentes da Web voltados para o exterior, como página de cancelamento de inscrição/centro de preferências e páginas de aterrissagem.

![](assets/deployment_hosted.png)

Como cliente hospedado, a maioria das etapas de instalação e configuração é executada pelo Adobe. Você pode acessar as seguintes seções para personalizar a implementação:

* Configurar URLs de rastreamento e mirror page por marca. Para mensagens transacionais, consulte [nesta seção](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instalar o console do cliente: consulte [nesta seção](../../installation/using/installing-the-client-console.md).
* Saiba mais sobre as ferramentas de entrega e as práticas recomendadas lendo o [documentação detalhada](../../delivery/using/about-deliverability.md).
* Configure as opções do Campaign: consulte [nesta seção](../../installation/using/configuring-campaign-options.md).
* Configurar conectores CRM: consulte [nesta seção](../../platform/using/crm-connectors.md).

## No local

O Adobe Campaign pode ser implantado no local: todos os componentes do Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados, residem no local no data center do cliente. Nesse modelo de implantação, o cliente gerencia todas as atualizações de software e hardware, e um administrador de banco de dados dedicado precisa executar tarefas de manutenção e otimização para garantir o gerenciamento da instância do Campaign.

![](assets/deployment_onpremise.png)

Como cliente local, antes de começar a implantar o Campaign Classic, atenda aos seguintes pré-requisitos e recomendações:

* Leia o [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md) que lista todas as versões dos sistemas e componentes compatíveis com o Adobe Campaign.
* Dependendo do seu ambiente, leia a [pré-requisitos para o Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) e [pré-requisitos para Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Saiba mais sobre recomendações relacionadas a mecanismos de banco de dados [nesta seção](../../installation/using/database.md).
* Verifique se as camadas de acesso ao banco de dados necessárias estão instaladas no servidor e acessíveis na conta do Adobe Campaign. [Saiba mais](../../installation/using/application-server.md).
* Configure suas redes, pois alguns processos precisam se comunicar com outros ou acessar a LAN e a Internet. Isso significa que algumas portas TCP precisam estar abertas para esses processos. [Saiba mais](../../installation/using/network-configuration.md) sobre os requisitos de configuração de rede.
* Ler [Lista de verificação de segurança e privacidade do Campaign](https://helpx.adobe.com/br/campaign/kb/acc-security.html).
* Verifique as diretrizes gerais para estimar os requisitos de hardware para implantação no local [neste artigo](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html).

## Híbrido

Quando implantado como um modelo híbrido, o software da solução Adobe Campaign reside no local do cliente e o gerenciamento de execução é fornecido como um serviço em nuvem pela Adobe. A instância de marketing do Adobe Campaign é instalada no firewall do cliente, portanto, as informações de identificação pessoal (PII) permanecem na empresa e somente os dados necessários para personalizar emails são enviados para a nuvem para execução de email. A instância de execução, hospedada na nuvem, recebe as solicitações da instância no local para entregar emails. Essa instância personaliza todos os emails e os entrega. Nenhum tipo de dado é armazenado permanentemente na nuvem.

![](assets/deployment_hybrid.png)

Como cliente híbrido, a maioria das etapas de instalação e configuração é executada pelo Adobe. Você pode acessar as seguintes seções para personalizar a implementação:

* Configurar mensagens transacionais: consulte [nesta seção](../../message-center/using/transactional-messaging-architecture.md).
* Configurar URLs de rastreamento e mirror page por marca. Para mensagens transacionais, consulte [nesta seção](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instalar o console do cliente: consulte [nesta seção](../../installation/using/installing-the-client-console.md).
* Instalar pacotes integrados: consulte [nesta seção](../../installation/using/installing-campaign-standard-packages.md).
* Capacidade de entrega: configurar [Regras MX](../../installation/using/email-deliverability.md#mx-configuration) e [formatos de email](../../installation/using/email-deliverability.md#managing-email-formats). Saiba mais sobre as ferramentas de entrega e as práticas recomendadas lendo o [documentação detalhada](../../delivery/using/about-deliverability.md).
* Configure as opções do Campaign: consulte [nesta seção](../../installation/using/configuring-campaign-options.md).
* Configure um banco de dados externo (Federated Data Access): consulte [nesta seção](../../installation/using/about-fda.md).
* Configurar conectores CRM: consulte [nesta seção](../../platform/using/crm-connectors.md).
* Para saber mais sobre os princípios de implantação do mid-sourcing, consulte [nesta seção](../../installation/using/mid-sourcing-deployment.md).
