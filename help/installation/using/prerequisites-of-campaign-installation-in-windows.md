---
product: campaign
title: Pré-requisitos da instalação do Campaign no Windows
description: Pré-requisitos da instalação do Campaign no Windows
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# Introdução à instalação do Campaign no Windows {#prerequisites-of-campaign-installation-in-windows}



A configuração técnica e o software necessários para instalar o Adobe Campaign são apresentados na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

O processo de instalação do servidor Adobe Campaign para uso de várias instâncias é descrito abaixo em [Instalação do servidor](../../installation/using/installing-the-server.md).

As principais etapas são as seguintes:

1. Instale o servidor de aplicativos, consulte [Execução do programa de instalação](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integrar com um servidor Web (opcional, dependendo dos componentes implantados), consulte [Configuração do servidor Web IIS](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

Quando as etapas de instalação estiverem concluídas, você precisará configurar as instâncias, o banco de dados e o servidor. Para obter mais informações, consulte [Sobre a configuração inicial](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>Quando o Adobe Campaign é implantado em um ambiente Windows, os usuários com os direitos de acesso necessários podem usar a sintaxe UNC (Universal.Uniform Naming Convention, Convenção de nomenclatura universal) para caminhos de acesso durante a manipulação de arquivos na rede.
