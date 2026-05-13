---
product: campaign
title: Sobre a configuração inicial
description: Sobre a configuração inicial
feature: Installation, Configuration
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
TQID: https://experienceleague.adobe.com/rQT-wcpjGzyYfEV3thGlY0WD7Po-A08yD0pGMr13p7s
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 197
ht-degree: 19%

---

# Etapas principais para configurar e implantar sua instância{#about-initial-configuration}



Quando a instalação do Adobe Campaign estiver concluída, você precisará configurá-lo para garantir que ele opere com eficiência com suas restrições e arquitetura técnica. As etapas para configurar uma instância do Adobe Campaign estão detalhadas neste capítulo, na seguinte sequência:

1. Para criar a instância e a conexão relacionada, consulte [Criação de uma instância e logon](../../installation/using/creating-an-instance-and-logging-on.md).
1. Crie e configure o banco de dados; consulte [Criação e configuração do banco de dados](../../installation/using/creating-and-configuring-the-database.md).
1. Configure o servidor do Adobe Campaign, consulte [Configuração do servidor do Campaign](../../installation/using/configuring-campaign-server.md).
1. Implante a instância, consulte [Implantando uma instância](../../installation/using/deploying-an-instance.md).

A configuração da instância implica ativar processos (web, mta, wfserver etc.) para ser iniciado no servidor e configurar os módulos para enviar email, rastreamento, etc. Para cada instância, os processos do Adobe Campaign são ativados no servidor. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#enabling-processes).

Configurações adicionais podem ser necessárias para cada instância (dependendo dos módulos usados, da arquitetura e das necessidades) para otimizar a operação do Adobe Campaign.
