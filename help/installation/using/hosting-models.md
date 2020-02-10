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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Modelos de hospedagem{#hosting-models}

O Adobe Campaign oferece uma escolha de três modelos de hospedagem, proporcionando flexibilidade e liberdade para escolher o melhor modelo ou modelos para atender às necessidades dos negócios.

>[!NOTE]
>
>As etapas principais de instalação e configuração só podem ser executadas pela Adobe para implantações hospedadas pela Adobe. Por exemplo, para configurar os arquivos de configuração do servidor e da instância. Para saber mais sobre as principais diferenças entre os modos de implantação, consulte [este artigo](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html). Se você tiver um modelo hospedado ou híbrido, consulte esta [seção](../../installation/using/about-hybrid-and-hosted-models.md).

* **Serviços gerenciados (hospedados)**

   O Adobe Campaign pode ser implantado como um Serviço gerenciado: todos os componentes do Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados do Campaign do cliente são totalmente hospedados pela Adobe, incluindo execução de email, páginas espelhadas, servidor de rastreamento e componentes da Web voltados para o exterior, como cancelar a inscrição da página/centro de preferências e páginas iniciais. A Adobe aloca até três instâncias na Nuvem — Desenvolvimento, Teste/Palco e Produção. As etapas de instalação e configuração deste modelo de hospedagem são apresentadas nesta [seção](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **Local**

   O Adobe Campaign pode ser implantado no local: todos os componentes do Adobe Campaign, incluindo a interface do usuário, o mecanismo de gerenciamento de execução e o banco de dados, residem no local no data center do cliente. Neste modelo de implantação, o cliente gerencia todas as atualizações e atualizações de software e hardware, e um administrador de banco de dados dedicado precisa executar tarefas de manutenção e otimização para garantir o gerenciamento da instância do Campaign.

   ![](assets/deployment_onpremise.png)

* **Híbrido**

   Quando implantado como um modelo híbrido, o software da solução Adobe Campaign fica no local do cliente e o gerenciamento de execução é fornecido como um serviço em nuvem pela Adobe. A instância de marketing do Adobe Campaign é instalada dentro do firewall de um cliente, portanto, as informações de identificação pessoal (PII) permanecem internas e somente os dados necessários para personalizar emails são enviados para a Cloud para execução de email. A instância de execução hospedada na Cloud recebe as solicitações da instância Local para fornecer emails. Esta instância personaliza todos os emails e os entrega. Nenhum dado de qualquer tipo é permanentemente armazenado na nuvem. As etapas de instalação e configuração deste modelo de hospedagem são apresentadas nesta [seção](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

