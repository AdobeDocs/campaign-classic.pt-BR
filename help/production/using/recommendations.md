---
title: Recomendações
seo-title: Recomendações
description: Recomendações
seo-description: null
page-status-flag: never-activated
uuid: d898fe6d-7627-405f-b2bc-b17bf1dc9e96
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: a31c5c9f-503f-4b55-8409-34d4addbd581
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Recomendações{#recommendations}

O Adobe Campaign é um sistema altamente transacional (banco de dados OLTP). Isso significa que o banco de dados subjacente será atualizado com frequência, resultando em uma degradação do desempenho ao longo do tempo. Para evitar esse tipo de problema, é necessária a manutenção regular do banco de dados.

>[!CAUTION]
>
>Um banco de dados só terá um desempenho ótimo se for mantido regularmente. A manutenção automática oferecida por alguns RDBMS não é suficiente e não substitui a manutenção aprofundada, como acontece com qualquer sistema de gestão transacional de base de dados relacional.
>  
>Os procedimentos descritos neste documento são recomendações. Os planos de manutenção são da responsabilidade do administrador do banco de dados, que deve ser seu primeiro contato em caso de problemas.

