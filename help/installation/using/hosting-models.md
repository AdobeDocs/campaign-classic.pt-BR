---
title: Modelos de hospedagem
seo-title: Modelos de hospedagem
description: Modelos de hospedagem
seo-description: null
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 3%

---


# Modelos de hospedagem{#hosting-models}

A Adobe Campaign oferta uma escolha de três modelos de hospedagem, proporcionando flexibilidade e liberdade para escolher o melhor modelo ou modelos para atender às necessidades da empresa.

>[!NOTE]
>
>As etapas principais de instalação e configuração só podem ser executadas por Adobe para implantações hospedadas por Adobe. Por exemplo, para configurar os arquivos de configuração do servidor e da instância. Para saber mais sobre as principais diferenças entre os modos de implantação, consulte [este artigo](https://helpx.adobe.com/br/campaign/kb/acc-on-prem-vs-hosted.html). Se você tiver um modelo hospedado ou híbrido, consulte esta [seção](../../installation/using/about-hybrid-and-hosted-models.md).

* **Managed Services (hospedado)**

   A Adobe Campaign pode ser implantada como um serviço gerenciado: todos os componentes do Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados de Campanha do cliente são totalmente hospedados pela Adobe, incluindo execução de e-mail, mirrores page, servidor de rastreamento e componentes da Web externos, como página/centro de preferências e landings page de cancelamento de inscrição. O Adobe aloca até três instâncias na nuvem — Desenvolvimento, Teste/Palco e Produção. As etapas de instalação e configuração deste modelo de hospedagem são apresentadas nesta [seção](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **Local**

   A Adobe Campaign pode ser implantada no local: todos os componentes da Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados, residem no local no data center do cliente. Neste modelo de implantação, o cliente gerencia todas as atualizações e atualizações de software e hardware, e um administrador de banco de dados dedicado precisa executar tarefas de manutenção e otimização para garantir o gerenciamento de instâncias de Campanha.

   ![](assets/deployment_onpremise.png)

* **Híbrido**

   Quando implantado como um modelo híbrido, o software da solução Adobe Campaign reside no local do cliente e o gerenciamento da execução é fornecido como um serviço em nuvem pela Adobe. A instância de marketing da Adobe Campaign é instalada dentro do firewall de um cliente, portanto, as informações pessoais identificáveis (PII) permanecem internas e somente os dados necessários para personalizar e-mails são enviados para a Cloud para execução de e-mails. A instância de execução, hospedada na Cloud, recebe as solicitações da instância Local para fornecer emails. Esta instância personaliza todos os emails e os entrega. Nenhum dado de qualquer tipo é permanentemente armazenado na nuvem. As etapas de instalação e configuração deste modelo de hospedagem são apresentadas nesta [seção](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

