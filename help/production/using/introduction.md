---
solution: Campaign Classic
product: campaign
title: Introdução
description: Introdução
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 5639f08ad709597d5f5c9e6bbd6932cffcbde40f
workflow-type: tm+mt
source-wordcount: '191'
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

>[!CAUTION]
>
>O console do cliente deve estar na mesma compilação que a instância do servidor.

>[!NOTE]
>
>Para obter mais informações sobre os vários processos do Adobe Campaign, consulte [esta seção](../../installation/using/general-architecture.md#logical-application-layer).\
>Ao usar a arquitetura do tipo Power Booster ou Power Cluster, você deve aplicar esse processo a todos os servidores Power Booster/Cluster.

Se a nova versão envolver uma alteração na estrutura do banco de dados, recomendamos reiniciar os servidores na seguinte ordem:

1. Servidor de aplicativos (nlserver web),
1. Servidor de redirecionamento (webmdl),
1. Servidor do delivery (nlserver mta).

