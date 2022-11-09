---
product: campaign
title: Sobre as ferramentas de geração de relatórios do Adobe Campaign
description: Analise o sucesso de suas campanhas em relatórios integrados ou personalizados.
feature: Reporting
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
source-git-commit: 1635366b9e1302acd3d8997312bf07d5c1a68982
workflow-type: ht
source-wordcount: '334'
ht-degree: 100%

---

# Introdução aos relatórios {#about-adobe-campaign-reporting-tools}

![](../../assets/common.svg)

Além dos [relatórios internos](../../reporting/using/about-campaign-built-in-reports.md), o Adobe Campaign permite gerar relatórios em vários contextos para atender a diferentes necessidades. Os princípios de uso e dos modos de implementação são detalhados neste documento.

O Adobe Campaign não é uma ferramenta de relatório especializada: os relatórios criados no Adobe Campaign permitem principalmente visualizar dados agregados. Relatórios do Adobe Campaign, que são dedicados a analisar e representar dados, não foram projetados para exportações de banco de dados.

Para exportar dados do banco de dados do Adobe Campaign, é preciso criar um workflow e usar uma atividade de exportação de dados. Para obter mais informações, consulte [esta seção](../../workflow/using/about-action-activities.md).

O Adobe Campaign fornece várias ferramentas de relatório:

1. **Relatórios integrados**: o Adobe Campaign oferece um conjunto de relatórios sobre entregas, campanhas, atividades da plataforma, funcionalidades opcionais, etc. Estes relatórios estão disponíveis através das várias funcionalidades a que se referem. Eles podem ser adaptados para atender às necessidades específicas.

   Para obter mais informações, consulte [esta seção](../../reporting/using/about-campaign-built-in-reports.md).

1. **Análise de dados descritiva**: o Adobe Campaign fornece uma ferramenta visual para produzir estatísticas sobre dados no banco de dados. É possível criar relatórios de análise descritiva usando um assistente dedicado e adaptar seu conteúdo e layout dependendo das necessidades.

   Para obter mais informações, consulte [esta seção](../../reporting/using/about-descriptive-analysis.md).

1. **Relatórios personalizados**: o Adobe Campaign permite criar relatórios sobre os dados no banco de dados. Depois que eles tiverem sido criados, eles são acessíveis nos contextos apropriados.

   Dependendo da complexidade das queries, cálculos e volumes, os dados analisados nesses relatórios podem ser coletados por meio de uma query e pré-agregados em uma lista (workflow do tipo &quot;gestão de dados&quot;) ou em um Cubo (usando Marketing Analytics). Ele será exibido na forma de uma tabela dinâmica ou uma lista de grupos.

   Para obter mais informações, consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Relatórios de análise**: o Marketing Analytics permite a exploração intuitiva de dados.

   Para obter mais informações, consulte [esta seção](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>Para facilitar a exibição e a manipulação, bem como a exportação eficiente, os relatórios não devem conter mais de 1.000 linhas.
