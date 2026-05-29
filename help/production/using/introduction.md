---
product: campaign
title: Introdução
description: Introdução
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
TQID: https://experienceleague.adobe.com/L6Ais2NSt-Z29b7Jgz25a6uYInel9V-Hb5kv0u6oSLo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 1%

---

# Introdução{#introduction}



Esta seção apresenta o procedimento a ser aplicado para atualizar o Adobe Campaign, o lado do cliente e o lado do servidor, e descreve a alternância para Unicode de uma instância existente.

>[!NOTE]
>
>Para instâncias de serviços hospedados/gerenciados, você deve entrar em contato com o administrador do Adobe.\
>Para instâncias no local, você pode obter assistência dos consultores da Adobe.

A atualização deve ser aplicada a todos os servidores nos quais o Adobe Campaign está instalado.

1. Migrar os servidores de redirecionamento e rastreamento (Apache/IIS).
1. Migre os servidores Power Boster/Cluster.
1. Migrar o servidor de marketing.

O Adobe Campaign se baseia em vários processos executados no lado do servidor que você precisará manipular durante atualizações, especificamente:

* Servidor de aplicativos (nlserver web)
* Servidor de entrega (nlserver mta)
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
1. Servidor de entrega (nlserver mta).
