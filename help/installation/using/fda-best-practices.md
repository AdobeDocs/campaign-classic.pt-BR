---
product: campaign
title: Práticas recomendadas e limitações do FDA do Campaign
description: Saiba mais sobre as práticas recomendadas e limitações ao trabalhar com um banco de dados externo (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 23%

---

# Práticas recomendadas e limitações



## Otimizar a personalização de email com dados externos {#optimizing-email-personalization-with-external-data}

Você pode pré-processar a personalização da mensagem em um fluxo de trabalho dedicado. Para fazer isso, use a opção **[!UICONTROL Prepare the personalization data with a workflow]**, disponível na guia **[!UICONTROL Analysis]** das propriedades de entrega.

Durante a análise de delivery, essa opção cria e executa automaticamente um workflow que armazena todos os dados vinculados ao target em uma tabela temporária, incluindo dados de tabelas vinculadas em um banco de dados externo.

Essa opção melhora significativamente o desempenho ao executar a etapa de personalização.

## Usar dados de um banco de dados externo em um workflow {#using-data-from-an-external-database-in-a-workflow}

Em várias atividades de workflow do Adobe Campaign, é possível usar os dados armazenados em um banco de dados externo.

* **Filtrar dados externos** - A atividade Query permite adicionar dados externos e usá-los nas configurações de filtro definidas. Para obter mais informações, consulte a [documentação do Campaign v8]https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}.

* **Criar subconjuntos** - A atividade Split permite criar subconjuntos. Você pode usar dados externos para definir os critérios de filtragem a serem usados. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}.

* **Carregar banco de dados externo** - Você pode usar os dados externos na atividade de carregamento de dados (RDBMS). Saiba mais na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-rdbms.html){target="_blank"}.

* **Adicionando informações e links** - A atividade de Enriquecimento permite adicionar dados à tabela de trabalho do fluxo de trabalho e links a uma tabela externa. Nesse contexto, ele pode usar dados de um banco de dados externo. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}.

## Medidas de proteção e limitações {#fda-limitations}

A opção FDA foi projetada para manipular os dados em bancos de dados externos em modo de lote em workflows. Para evitar problemas de desempenho, não é recomendável usar o módulo FDA no contexto de operações unitárias, como: personalização, interação, mensagens em tempo real etc.

Não há suporte para direcionamento de dados de um banco de dados e filtragem de resultados usando uma dimensão de filtro que pertence a outro banco de dados. Não é possível unir tabelas que estão em diferentes fontes de dados em uma consulta. Você pode superar essa limitação usando outras atividades de workflow, como Alterar dimensão.

Evite o máximo possível as operações que precisam usar o banco de dados tanto do Adobe Campaign quanto externo. A prática recomendada é:

* Exportar o banco de dados do Adobe Campaign para o banco de dados externo e executar as operações somente do banco de dados externo antes de importar novamente os resultados para o Adobe Campaign.

* Coletar os dados do banco de dados externo do Adobe Campaign e executar as operações no local.

Se você quiser realizar a personalização de entregas usando dados do banco de dados externo, colete os dados para usar em um fluxo de trabalho para torná-lo disponível em uma tabela temporária. Em seguida, use os dados da tabela temporária para personalizar sua entrega.

A opção FDA está sujeita às limitações do sistema de banco de dados externo que você usa.
