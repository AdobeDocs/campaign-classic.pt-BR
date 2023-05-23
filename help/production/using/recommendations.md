---
product: campaign
title: Recomendações
description: Recomendações
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# Recomendações{#recommendations}



O Adobe Campaign é um sistema altamente transacional (banco de dados OLTP). Isso significa que o banco de dados subjacente será atualizado com frequência, resultando em uma degradação de desempenho ao longo do tempo. Para evitar esse tipo de problema, é necessária a manutenção regular do banco de dados.

>[!IMPORTANT]
>
>Um banco de dados só terá um desempenho ideal se for mantido regularmente. A manutenção automática oferecida por alguns RDBMS não é suficiente e não substitui a manutenção aprofundada, como para qualquer sistema de gerenciamento transacional de banco de dados relacional.
>  
>Os procedimentos descritos neste documento são recomendações. Os planos de manutenção são de responsabilidade do administrador do banco de dados, que deve ser seu primeiro contato em caso de problemas.
