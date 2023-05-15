---
product: campaign
title: Pré-requisitos da instalação do Campaign no Windows
description: Pré-requisitos da instalação do Campaign no Windows
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# Introdução à instalação do Campaign no Windows {#prerequisites-of-campaign-installation-in-windows}



A configuração técnica e o software necessários para instalar o Adobe Campaign são apresentados na seção [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

O processo de instalação do servidor Adobe Campaign para uso de várias instâncias é descrito abaixo em [Instalação do servidor](../../installation/using/installing-the-server.md).

As principais etapas são as seguintes:

1. Instale o servidor de aplicativos, consulte [Execução do programa de instalação](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integrar com um servidor da Web (opcional, dependendo dos componentes implantados), consulte [Configuração do servidor Web IIS](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

Depois que as etapas de instalação forem concluídas, será necessário configurar as instâncias, o banco de dados e o servidor. Para obter mais informações, consulte [Sobre a configuração inicial](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>Quando o Adobe Campaign é implantado em um ambiente Windows, os usuários com os direitos de acesso necessários podem usar a sintaxe UNC (Universal.Uniform Naming Agreement) para acessar caminhos durante a manipulação de arquivos na rede.
