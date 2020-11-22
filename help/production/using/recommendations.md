---
solution: Campaign Classic
product: campaign
title: Recomendações
description: Recomendações
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---


# Recomendações{#recommendations}

A Adobe Campaign é um sistema altamente transacional (banco de dados OLTP). Isso significa que o banco de dados subjacente será atualizado com frequência, resultando em uma degradação do desempenho ao longo do tempo. Para evitar esse tipo de problema, é necessária a manutenção regular do banco de dados.

>[!IMPORTANT]
>
>Um banco de dados só terá um desempenho ótimo se for mantido regularmente. A manutenção automática oferecida por alguns RDBMS não é suficiente e não substitui a manutenção aprofundada, como acontece com qualquer sistema de gestão transacional de base de dados relacional.
>  
>Os procedimentos descritos neste documento são recomendações. Os planos de manutenção são da responsabilidade do administrador do banco de dados, que deve ser seu primeiro contato em caso de problemas.
