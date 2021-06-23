---
product: campaign
title: Configuração da integração com o Adobe Target
description: Configuração da integração com o Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 94e609f3df94c553e2ec84ee427887a767b9af21
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 89%

---

# Configuração da integração com o Adobe Target{#configuring-the-integration-with-adobe-target}

## Pré-requisitos {#prerequisites}

Para usar a integração entre o Adobe Campaign e o Adobe Target, você deve ter:

* Organizações do Adobe Experience Cloud e Adobe Target
* Um rawbox do Adobe Target especificado para estabelecer a conexão com o Adobe Campaign

## Configuração do Adobe Campaign {#configuring-adobe-campaign}

Para configurar o Adobe Campaign:

1. Instale o pacote padrão **[!UICONTROL Integration with the Adobe Experience Cloud]**. A instalação de um pacote de integração é a mesma instalação de um pacote padrão, que é detalhado na seção [Importação de pacotes. ](../../platform/using/working-with-data-packages.md#importing-packages) Isso dá acesso aos ativos compartilhados por meio do Digital Asset Manager.
1. Ative a conexão pelo IMS (serviço de conexão da Adobe ID) para usar imagens compartilhadas pela Adobe Experience Cloud em seus emails. Consulte a seção sobre [IMS](../../integrations/using/about-adobe-id.md).
1. Em **[!UICONTROL Administration > Platform > Options]**, configure as opções do servidor e da organização (locatário) para o Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** : O servidor Adobe Target usado para a integração. Essa opção é selecionada por padrão. Esse valor corresponde ao **[!UICONTROL Domain Server]** do Adobe Target, seguido pelo valor **/m2**. Por exemplo: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nome da organização do Adobe Target. Esse valor corresponde ao nome do **[!UICONTROL Client]** do Adobe Target.

   ![](assets/tar_options.png)

>[!CAUTION]
>
>Para arquiteturas híbridas e hospedadas, essas opções devem ser definidas em todos os servidores, incluindo o [servidor mid-sourcing](../../installation/using/mid-sourcing-server.md) e a [instância de execução](../../message-center/using/configuring-instances.md#execution-instance).