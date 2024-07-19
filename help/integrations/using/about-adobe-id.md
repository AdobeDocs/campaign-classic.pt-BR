---
product: campaign
title: Usar sua Adobe ID para se conectar ao Adobe Campaign
description: Saiba mais sobre a implementação do Adobe IMS no Adobe Campaign
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: ffab91fc9fa7e60973fdda930239f5836671a341
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 100%

---

# Sobre a Adobe ID {#about-adobe-id}

O Sistema de gerenciamento de identidades (IMS) da Adobe ajuda os administradores a criar e gerenciar o acesso do usuário a aplicativos e serviços. Para obter mais informações sobre tipos diferentes de Adobe IDs, consulte [esta página](https://helpx.adobe.com/br/enterprise/using/identity.html).

Os usuários do Campaign podem se conectar ao console do Adobe Campaign usando a Adobe ID, em vez da [autenticação nativa de usuário/senha](../../platform/using/access-management-operators.md). Esta implementação oferece as seguintes vantagens:

* A mesma ID pode ser usada para todas as soluções Experience Cloud.
* A conexão é mantida ao usar o Adobe Campaign com diferentes integrações.
* Política de gerenciamento de senha mais segura do que login/senha nativos.
* Uso de contas de Federated ID (provedor de ID externo).

>[!IMPORTANT]
>
> Observe que no Campaign v8, a conexão com usuário/senha (também conhecida como autenticação nativa) não é permitida. **A Adobe recomenda executar essa migração a partir do Campaign v7.3.5 para facilitar a migração para o Campaign v8.**
>
>Saiba como migrar para o Adobe IMS [nesta seção](../../technotes/using/ac-ims.md).
>


<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## Mais recursos

| Páginas úteis | Recursos adicionais |
|---|---|
| [Configuração de IMS](../../integrations/using/configuring-ims.md) | [Perguntas frequentes sobre a Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=pt-BR) |
| [Implementação de IMS](../../integrations/using/implementing-ims.md) | [Gerenciamento de acesso](../../platform/using/access-management.md) |
| [Solução de problemas com o IMS](../../integrations/using/ims-troubleshooting.md) | [Instalação de pacotes do Campaign](../../installation/using/installing-campaign-standard-packages.md) |
