---
title: Introdução
seo-title: Introdução
description: Introdução
seo-description: null
page-status-flag: never-activated
uuid: 4192a74e-1d4f-4784-80e3-53aaefa9141e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 772992bf-588f-42bd-a72a-986a88815264
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Introdução{#introduction}

Esta seção apresenta o procedimento a ser aplicado para atualizar o Adobe Campaign, o lado do cliente e o lado do servidor, e descreve a alternância para o Unicode de uma instância existente.

>[!NOTE]
>
>Para instâncias hospedadas, é necessário coordenar com o administrador da Adobe.\
>Para instâncias locais, você pode obter assistência dos consultores da Adobe.

A atualização deve ser aplicada a todos os servidores nos quais o Adobe Campaign está instalado.

1. Migre os servidores de redirecionamento e rastreamento (Apache/IIS).
1. Migre os servidores do Power Booster/Cluster.
1. Migre o servidor de marketing.

O Adobe Campaign se baseia em vários processos executados no lado do servidor que você precisará manipular durante as atualizações, em particular:

* Servidor de aplicativos (nlserver web)
* Servidor de entrega (nlserver mta)
* Servidor de redirecionamento (webmdl)

>[!NOTE]
>
>For more on the various Adobe Campaign processes, refer to [this section](../../installation/using/general-architecture.md#logical-application-layer).\
>Ao usar a arquitetura do tipo Power Booster ou Power Cluster, você deve aplicar esse processo a todos os servidores Power Booster/Cluster.

Se a nova versão envolver uma alteração na estrutura do banco de dados, recomendamos reiniciar os servidores na seguinte ordem:

1. Servidor de aplicativos (nlserver web),
1. Servidor de redirecionamento (webmdl),
1. Servidor de entrega (nlserver mta).

