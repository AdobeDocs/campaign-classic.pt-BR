---
product: campaign
title: Introdução
description: Introdução
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

---

# Introdução{#introduction}

![](../../assets/v7-only.svg)

Esta seção apresenta o procedimento a ser aplicado para atualizar o Adobe Campaign, o lado do cliente e o lado do servidor e descreve a alternância para Unicode de uma instância existente.

>[!NOTE]
>
>Para instâncias hospedadas, você deve coordenar com o Administrador do Adobe.\
>Para instâncias locais, você pode obter assistência de consultores Adobe.

A atualização deve ser aplicada a todos os servidores onde o Adobe Campaign estiver instalado.

1. Migre os servidores de redirecionamento e rastreamento (Apache/IIS).
1. Migre os servidores Power Boster/Cluster.
1. Migre o servidor de marketing.

O Adobe Campaign é baseado em vários processos executados no lado do servidor, que serão necessários para manipular durante as atualizações, em particular:

* Servidor de aplicativos (nlserver web)
* Servidor de delivery (nlserver mta)
* Servidor de redirecionamento (webmdl)

>[!CAUTION]
>
>O console do cliente deve estar na mesma build que a instância do servidor.

>[!NOTE]
>
>Para obter mais informações sobre os vários processos do Adobe Campaign, consulte [esta seção](../../installation/using/general-architecture.md#logical-application-layer).\
>Ao usar a arquitetura do tipo Power Boster ou Power Cluster, você deve aplicar esse processo a todos os servidores Power Boster/Cluster.

Se a nova versão envolver uma alteração na estrutura do banco de dados, recomendamos reiniciar os servidores na seguinte ordem:

1. Servidor de aplicativos (nlserver web),
1. Servidor de redirecionamento (webmdl),
1. Servidor de delivery (nlserver mta).
