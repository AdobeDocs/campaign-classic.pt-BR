---
title: Práticas recomendadas para relatórios
seo-title: Práticas recomendadas para relatórios
description: Práticas recomendadas para relatórios
seo-description: null
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 100%

---


# Práticas recomendadas para relatórios{#best-practices-reporting}

## Análise de necessidades{#analyzing-needs}

A utilização de uma ferramenta de relatório depende do volume de dados a serem manipulados, da complexidade e do tipo de relatório a ser configurado.

Para otimizar a criação, o uso e a durabilidade de um relatório, é preciso observar as necessidades que deseja atender. Essa primeira análise permitirá identificar o tipo de relatório a ser criado e o melhor modo de criação. Para criar o relatório, siga as etapas abaixo:

1. Identificar a necessidade

   A primeira etapa é identificar claramente a necessidade: o que você deseja exibir no relatório e qual é o seu objetivo (monitoramento, análise, exportação de dados etc.).

   O Adobe Campaign oferece uma ampla variedade de capacidade de gerar relatórios. É importante analisar a necessidade de identificar a funcionalidade mais adequada.

   Por exemplo, é possível:

   * Explorar os dados no banco de dados e definir medidas (por meio [desta seção](../../reporting/using/about-cubes.md)),
   * Adicionar indicadores a um relatório existente (consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Visualizar os dados no banco de dados (por meio [desta seção](../../reporting/using/about-descriptive-analysis.md)),
   * Criar um novo relatório de delivery (consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Exportar dados do banco de dados do Adobe Campaign (por meio de um workflow, consulte [esta seção](../../workflow/using/about-workflows.md)),
   * Criar uma tabela dinâmica (consulte [esta seção](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)),
   * Explorar dados agregados (por meio [desta seção](../../reporting/using/about-cubes.md)),
   * Usar um assistente para analisar dados (por meio [desta seção](../../reporting/using/about-descriptive-analysis.md)),
   * Analisar grandes volumes de dados (consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md)) e etc.

1. Identificar a população do target

   Em seguida, você precisa descobrir quem será o alvo do relatório que deseja criar, saber o tipo de público que o exibirá e o modo de exibição do relatório (em um navegador, no Adobe Campaign, para um objeto específico, para toda a plataforma etc.).

   Você também pode criar relatórios para:

   * Todos os operadores do Adobe Campaign,
   * Operadores com os direitos de acesso somente a uma campanha de marketing,
   * Um único operador para uso temporário,
   * Todos os operadores no acesso à Web etc.

   Essas questões também precisam levar em conta os problemas vinculados aos direitos de acesso e à segurança.

1. Definição do conteúdo

   Em seguida, você precisa descobrir qual tipo de dados deseja exibir: indicadores de delivery, relatórios sobre os perfis de banco de dados etc.

   Você também precisa saber a natureza desses dados (simples, resultante de um cálculo, significativo, etc.), seu local (no Adobe Campaign, em um sistema de terceiros), sua frequência de atualização para definir o cálculo de periodicidade (diário, semanal, em tempo real), bem como seu volume.

   Os problemas vinculados aos volumes de dados e atualizações precisam ser pesquisados cuidadosamente para evitar problemas de exibição de relatórios, especialmente em termos de tempo. Portanto, recomendamos a criação de agregados para pré-calcular alguns dados fora do relatório. As tabelas com os logs do delivery e de rastreamento podem incluir milhões de registros: isso significa que os dados precisam ser agregados por meio de um workflow para ser usado em um relatório.

## Otimização da criação de relatórios{#optimizing-report-creation}

### Volume de dados {#data-volume}

Para garantir desempenho ideal, o volume de dados manipulados não deve ser muito grande.

Especificamente:

* O tempo de cálculo de um relatório nunca deve ultrapassar 5 minutos.

   Da mesma forma, durante a fase de design, com um pequeno volume de dados, se o cálculo de relatório exceder 60 segundos, os métodos de cálculo devem ser alterados.

* Ao usar o Marketing Analytics, os dados manipulados não devem exceder 10 milhões de linhas.

Também recomendamos calcular agregados à noite e usar esses dados agregados diretamente nos relatórios. Esses agregados devem ser criados por meio de workflows dedicados de Gestão de Dados (queries SQL).

Você também pode calcular relatórios durante a noite e criar um histórico automaticamente que possa ser visualizado a qualquer momento, sem sobrecarregar o banco de dados.

### Queries {#queries}

Recomendamos usar queries SQL sempre que possível e evitar o pós-processamento JavaScript. Se necessário, use uma atividade de script em um workflow e exclua os dados usados para o cálculo. Você também pode usar dados arquivados para acelerar o tempo de processamento.

Nesse caso, a seguinte sintaxe deve ser usada:

```
if(string(ctx@_historyId)!==""))
```

Queries que permitem coletar os dados exibidos nos relatórios não devem ser muito complexos, especialmente se aplicados a todos os dados no banco de dados. Para melhorar o desempenho, pode ser útil filtrar os dados antes de executar esses queries: isso significa que o cálculo só fará parte dos dados.

### Desempenho {#performances}

As recomendações acima permitem otimizar o cálculo do relatório.

Além disso, o Adobe Campaign recomenda as seguintes melhorias:

* Estude o DataModel: os campos indexados devem ser usados principalmente para melhorar as fórmulas de cálculo.

   Para localizar um campo indexado rapidamente, examine o nome da coluna na interface do Adobe Campaign: a seta de classificação está sublinhada em vermelho se o campo estiver indexado.

* Garanta que o relatório seja válido a longo prazo: o volume de dados pode aumentar significativamente ao longo do tempo.

   Da mesma forma, o volume de dados manipulados durante as fases de teste pode diferir do volume de dados real na produção. É por isso que as fases de teste são importantes.

   Finalmente, os atrasos de eliminação de dados precisam ser conhecidos e adaptados quando necessário para facilitar a manipulação de dados.

### Exportação de relatórios {#exporting-reports}

As recomendações específicas para exportar relatórios são detalhadas [nesta seção](../../reporting/using/actions-on-reports.md#exporting-a-report).
