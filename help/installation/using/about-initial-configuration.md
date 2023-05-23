---
product: campaign
title: Sobre a configuração inicial
description: Sobre a configuração inicial
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 8%

---

# Etapas principais para configurar e implantar sua instância{#about-initial-configuration}



Quando a instalação do Adobe Campaign estiver concluída, você precisará configurá-lo para garantir que ele opere com eficiência com suas restrições e arquitetura técnica. As etapas para configurar uma instância do Adobe Campaign estão detalhadas neste capítulo, na seguinte sequência:

1. Crie a instância e a conexão relacionada, consulte [Criação de uma instância e fazer logon](../../installation/using/creating-an-instance-and-logging-on.md).
1. Crie e configure o banco de dados, consulte [Criação e configuração do banco de dados](../../installation/using/creating-and-configuring-the-database.md).
1. Configure o servidor Adobe Campaign, consulte [Configuração do servidor do Campaign](../../installation/using/configuring-campaign-server.md).
1. Implante a instância, consulte [Implantação de uma instância](../../installation/using/deploying-an-instance.md).

A configuração da instância implica ativar processos (web, mta, wfserver etc.) para ser iniciado no servidor e configurar os módulos para enviar email, rastreamento, etc. Para cada instância, os processos do Adobe Campaign são ativados no servidor. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#enabling-processes).

Configurações adicionais podem ser necessárias para cada instância (dependendo dos módulos usados, da arquitetura e das necessidades) para otimizar a operação do Adobe Campaign.
