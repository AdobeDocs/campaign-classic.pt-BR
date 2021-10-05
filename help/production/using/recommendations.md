---
product: campaign
title: Recomendações
description: Recomendações
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# Recomendações{#recommendations}

![](../../assets/v7-only.svg)

O Adobe Campaign é um sistema altamente transacional (banco de dados OLTP). Isso significa que o banco de dados subjacente será atualizado com frequência, levando a uma degradação do desempenho ao longo do tempo. Para evitar esse tipo de problema, é necessária a manutenção regular do banco de dados.

>[!IMPORTANT]
>
>Um banco de dados só terá um desempenho ideal se for mantido regularmente. A manutenção automática oferecida por alguns RDBMS não é suficiente e não substitui a manutenção aprofundada, como acontece com qualquer sistema de gestão transacional de base de dados relacional.
>  
>Os procedimentos descritos neste documento são recomendações. Os planos de manutenção são da responsabilidade do administrador do banco de dados, que deve ser o primeiro contato em caso de problemas.
