---
product: campaign
title: Modelos de hospedagem
description: Descubra modelos de hospedagem do Campaign
feature: Installation, Architecture, Deployment
role: Developer
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 1%

---

# Modelos de hospedagem{#hosting-models}



A Adobe Campaign oferece três opções de modelos de hospedagem, proporcionando flexibilidade e liberdade para escolher o melhor modelo ou modelos para atender às necessidades da empresa.

>[!NOTE]
>
>Para ambientes hospedados pelo Adobe, as etapas principais de instalação e configuração só podem ser executadas pelo Adobe, como configuração do servidor e personalização de arquivos de configuração de instância. Para saber mais sobre as principais diferenças entre os modos de implantação, consulte [esta página](../../installation/using/capability-matrix.md).

## Managed Services / hospedado

O Adobe Campaign pode ser implantado no as a Managed Service: todos os componentes do Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados do Campaign do cliente, são totalmente hospedados pelo Adobe, incluindo execução de email, mirror pages, servidor de rastreamento e componentes da Web voltados para o exterior, como página de cancelamento de inscrição/centro de preferências e páginas de aterrissagem.

![](assets/deployment_hosted.png)

Como cliente hospedado, a maioria das etapas de instalação e configuração é executada pela Adobe. Você pode acessar as seguintes seções para personalizar a implementação:

* Configurar URLs de rastreamento e mirror page por marca. Para mensagens transacionais, consulte [esta seção](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instalar o console do cliente: consulte [esta seção](../../installation/using/installing-the-client-console.md).
* Saiba mais sobre as ferramentas de entrega e as práticas recomendadas lendo a [documentação detalhada](../../delivery/using/about-deliverability.md).
* Configurar opções do Campaign: consulte [esta seção](../../installation/using/configuring-campaign-options.md).
* Configurar conectores CRM: consulte [esta seção](../../platform/using/crm-connectors.md).

## No local

O Adobe Campaign pode ser implantado no local: todos os componentes do Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados, residem no local no data center do cliente. Nesse modelo de implantação, o cliente gerencia todas as atualizações de software e hardware, e um administrador de banco de dados dedicado precisa executar tarefas de manutenção e otimização para garantir o gerenciamento da instância do Campaign.

![](assets/deployment_onpremise.png)

Como cliente local, antes de começar a implantar o Campaign Classic, cuide dos seguintes pré-requisitos e recomendações:

* Leia a [Matriz de Compatibilidade](../../rn/using/compatibility-matrix.md), que lista todas as versões dos sistemas e componentes com suporte no Adobe Campaign.
* Dependendo do seu ambiente, leia os [pré-requisitos para Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) e os [pré-requisitos para Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Saiba mais sobre recomendações relacionadas aos mecanismos de banco de dados [nesta seção](../../installation/using/database.md).
* Verifique se as camadas de acesso ao banco de dados necessárias estão instaladas no servidor e acessíveis na conta do Adobe Campaign. [Saiba mais](../../installation/using/application-server.md).
* Configure suas redes, pois alguns processos precisam se comunicar com outros ou acessar a LAN e a Internet. Isso significa que algumas portas TCP precisam estar abertas para esses processos. [Saiba mais](../../installation/using/network-configuration.md) sobre os requisitos de configuração de rede.
* Leia a [lista de verificação de segurança e privacidade do Campaign](https://helpx.adobe.com/campaign/kb/acc-security.html).
* Verifique as diretrizes gerais para a estimativa dos requisitos de hardware para a implantação local [neste artigo](https://helpx.adobe.com/br/campaign/kb/hardware-sizing-guide.html).

## Híbrido

Quando implantado como um modelo híbrido, o software da solução Adobe Campaign reside no local do cliente e o gerenciamento de execução é fornecido como um serviço em nuvem pela Adobe. A instância de marketing do Adobe Campaign é instalada no firewall do cliente, portanto, as informações de identificação pessoal (PII) permanecem na empresa e somente os dados necessários para personalizar emails são enviados para a nuvem para execução de email. A instância de execução, hospedada na nuvem, recebe as solicitações da instância local para entregar emails. Essa instância personaliza todos os emails e os entrega. Nenhum tipo de dado é armazenado permanentemente na nuvem.

![](assets/deployment_hybrid.png)

Como cliente híbrido, a maioria das etapas de instalação e configuração é executada pela Adobe. Você pode acessar as seguintes seções para personalizar a implementação:

* Configurar mensagens transacionais: consulte [esta seção](../../message-center/using/transactional-messaging-architecture.md).
* Configurar URLs de rastreamento e mirror page por marca. Para mensagens transacionais, consulte [esta seção](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instalar o console do cliente: consulte [esta seção](../../installation/using/installing-the-client-console.md).
* Instalar pacotes internos: consulte [esta seção](../../installation/using/installing-campaign-standard-packages.md).
* Capacidade de entrega: configurar [regras MX](../../installation/using/email-deliverability.md#mx-configuration) e [formatos de email](../../installation/using/email-deliverability.md#managing-email-formats). Saiba mais sobre as ferramentas de entrega e as práticas recomendadas lendo a [documentação detalhada](../../delivery/using/about-deliverability.md).
* Configurar opções do Campaign: consulte [esta seção](../../installation/using/configuring-campaign-options.md).
* Configurar um banco de dados externo (Federated Data Access): consulte [esta seção](../../installation/using/about-fda.md).
* Configurando conectores CRM: consulte [esta seção](../../platform/using/crm-connectors.md).
* Para saber mais sobre os princípios de implantação mid-sourcing, consulte [esta seção](../../installation/using/mid-sourcing-deployment.md).
