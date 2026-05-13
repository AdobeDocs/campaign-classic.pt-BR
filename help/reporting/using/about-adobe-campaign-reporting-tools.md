---
product: campaign
title: Sobre as ferramentas de geração de relatórios do Adobe Campaign
description: Analise o sucesso de suas campanhas em relatórios integrados ou personalizados
feature: Reporting, Monitoring
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
TQID: https://experienceleague.adobe.com/4D-bCeMQakNjr7OXhiZ1u0Sfp5MZWwzZzHtykBfFzZ8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 362
ht-degree: 91%

---

# Introdução aos relatórios {#about-adobe-campaign-reporting-tools}



Além dos [relatórios integrados](../../reporting/using/about-campaign-built-in-reports.md), o Adobe Campaign permite gerar relatórios em vários contextos para atender a diferentes necessidades. Os princípios de uso e dos modos de implementação são detalhados neste documento.

O Adobe Campaign não é uma ferramenta de relatório especializada: os relatórios criados no Adobe Campaign permitem principalmente visualizar dados agregados. Relatórios do Adobe Campaign, que são dedicados a analisar e representar dados, não foram projetados para exportações de banco de dados.

Para exportar dados do banco de dados do Adobe Campaign, é preciso criar um fluxo de trabalho e usar uma atividade de exportação de dados. Para mais informações, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities){target="_blank"}.

O Adobe Campaign fornece várias ferramentas de relatório:

1. **Relatórios internos**: o Adobe Campaign oferece um conjunto de relatórios sobre entregas, campanhas, atividades da plataforma, funcionalidades opcionais, etc. Estes relatórios estão disponíveis através das várias funcionalidades a que se referem. Eles podem ser adaptados para atender às necessidades específicas.

   Para obter mais informações, consulte [esta seção](../../reporting/using/about-campaign-built-in-reports.md).

1. **Análise de dados descritiva**: o Adobe Campaign fornece uma ferramenta visual para produzir estatísticas sobre dados no banco de dados. É possível criar relatórios de análise descritiva com um assistente dedicado e adaptar seu conteúdo e layout de acordo com as necessidades.

   Para obter mais informações, consulte [esta seção](../../reporting/using/about-descriptive-analysis.md).

1. **Relatórios personalizados**: o Adobe Campaign permite criar relatórios sobre os dados no banco de dados. Depois que eles tiverem sido criados, eles são acessíveis nos contextos apropriados.

   Dependendo da complexidade das consultas, cálculos e volumes, os dados analisados nesses relatórios podem ser coletados por meio de uma consulta e pré-agregados em uma lista (fluxo de trabalho do tipo &quot;gestão de dados&quot;) ou em um Cubo (usando Marketing Analytics). Ele será exibido na forma de uma tabela dinâmica ou uma lista de grupos.

   Para obter mais informações, consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Relatórios de análise**: o Marketing Analytics permite a exploração intuitiva de dados.

   Para obter mais informações, consulte [esta seção](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>Para facilitar a exibição e a manipulação, bem como a exportação eficiente, os relatórios não devem conter mais de 1.000 linhas.
