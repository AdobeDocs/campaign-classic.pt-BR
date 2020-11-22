---
solution: Campaign Classic
product: campaign
title: Introdução
description: Introdução
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 1%

---


# Introdução{#introduction}

Esta seção apresenta o procedimento a ser aplicado para atualizar o Adobe Campaign, o lado do cliente e o lado do servidor, e descreve a alternância para o Unicode de uma instância existente.

>[!NOTE]
>
>Para instâncias hospedadas, é necessário coordenar com o administrador do Adobe.\
>Para instâncias locais, você pode obter assistência dos consultores Adobe.

A atualização deve ser aplicada a todos os servidores nos quais o Adobe Campaign está instalado.

1. Migre os servidores de redirecionamento e rastreamento (Apache/IIS).
1. Migre os servidores do Power Booster/Cluster.
1. Migre o servidor de marketing.

A Adobe Campaign se baseia em vários processos executados no lado do servidor que serão necessários para manipular durante as atualizações, em particular:

* Servidor de aplicativos (nlserver web)
* Servidor de delivery (nlserver mta)
* Servidor de redirecionamento (webmdl)

>[!NOTE]
>
>For more on the various Adobe Campaign processes, refer to [this section](../../installation/using/general-architecture.md#logical-application-layer).\
>Ao usar a arquitetura do tipo Power Booster ou Power Cluster, você deve aplicar esse processo a todos os servidores Power Booster/Cluster.

Se a nova versão envolver uma alteração na estrutura do banco de dados, recomendamos reiniciar os servidores na seguinte ordem:

1. Servidor de aplicativos (nlserver web),
1. Servidor de redirecionamento (webmdl),
1. Servidor do delivery (nlserver mta).

