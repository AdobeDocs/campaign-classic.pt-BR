---
product: campaign
title: Recomendações
description: Recomendações
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
badge-v7-prem: label="no local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 20%

---

# Recomendações{#recommendations}



O Adobe Campaign é um sistema altamente transacional (banco de dados OLTP). Isso significa que o banco de dados subjacente será atualizado com frequência, resultando em uma degradação de desempenho ao longo do tempo. Para evitar esse tipo de problema, é necessária a manutenção regular do banco de dados.

>[!IMPORTANT]
>
>Um banco de dados só terá um desempenho ideal se for mantido regularmente. A manutenção automática oferecida por alguns RDBMS não é suficiente e não substitui a manutenção aprofundada, como para qualquer sistema de gerenciamento transacional de banco de dados relacional.
>  
>Os procedimentos descritos neste documento são recomendações. Os planos de manutenção são de responsabilidade do administrador do banco de dados, que deve ser seu primeiro contato em caso de problemas.
