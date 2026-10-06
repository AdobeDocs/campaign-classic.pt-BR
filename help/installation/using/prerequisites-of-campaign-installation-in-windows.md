---
product: campaign
title: Pré-requisitos da instalação do Campaign no Windows
description: Pré-requisitos da instalação do Campaign no Windows
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
TQID: 'https://experienceleague.adobe.com/vECxz7-bt6DMteRM-N4BtD6Uo5qonHrkgQQeEOkTSt0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 11%
---
# Introdução à instalação do Campaign no Windows {#prerequisites-of-campaign-installation-in-windows}



A configuração técnica e o software necessários para instalar o Adobe Campaign são apresentados na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

O processo de instalação do servidor Adobe Campaign para uso de várias instâncias está descrito abaixo em [Instalando o servidor](../../installation/using/installing-the-server.md).

As principais etapas são as seguintes:

1. Instale o servidor de aplicativos, consulte [Executando o programa de instalação](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integrar com um servidor Web (opcional, dependendo dos componentes implantados), consulte [Configuração do servidor Web IIS](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

Quando as etapas de instalação estiverem concluídas, você precisará configurar as instâncias, o banco de dados e o servidor. Para obter mais informações, consulte [Sobre a configuração inicial](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>Quando o Adobe Campaign é implantado em um ambiente Windows, os usuários com os direitos de acesso necessários podem usar a sintaxe UNC (Universal.Uniform Naming Convention, Convenção de nomenclatura universal) para caminhos de acesso durante a manipulação de arquivos na rede.
