---
title: Objetos de aplicativo
seo-title: Objetos de aplicativo
description: Objetos de aplicativo
seo-description: null
page-status-flag: never-activated
uuid: 84fbad0f-872d-4aca-8ea9-007577be076d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 24d4875b-81fa-4bf3-8cf0-e6998bec4949
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# Objetos de aplicativo{#application-objects}

Objetos incorporados devem ser monitorados e impedir que cresçam demais é importante.

## Sequência de IDs {#sequence-of-ids}

O Adobe Campaign usa uma sequência de ID que deve ser consumida de acordo: **xtkNewId**. Se a sequência for consumida muito rapidamente (ou seja, de 100.000 por dia), você deve verificar se é consistente com as necessidades de sua empresa, como enviar milhões de emails por dia. É possível definir uma sequência dedicada para tabelas específicas. Você pode configurar um fluxo de trabalho para monitorar o uso da ID.

Quando a sequência chega a mais de 2 bilhões (2.147.483.648 é o número exato), volta a zero. Deve ser evitada e cria problemas, razão pela qual esta sequência deve ser monitorizada.

Para evitar isso com tabelas grandes, considere usar uma sequência específica. Isso pode ser feito com o atributo **pkSequence** no esquema.

Fluxos de trabalho de alta frequência que criam muitos logs consumirão muitas IDs. Portanto, é altamente recomendável evitar muitos registros e altas frequências nos fluxos de trabalho.

Se a sequência já tiver sido cíclica, a melhor solução é alternar para IDs negativas, a partir de -2.147.483.648.

## Pastas {#folders}

Deve haver menos de 1000 pastas em qualquer instância. Ter mais pastas do que isso pode causar problemas de desempenho com o cliente Campaign. Você pode configurar um trabalho de monitoramento para contar o número de pastas, fluxos de trabalho etc. e retornar o relatório periodicamente.

Esse método também destaca os usuários que criam muitos objetos.

## Entregas {#deliveries}

Deve haver menos de 1000 entregas na instância a qualquer momento. Muitas entregas consomem espaço no banco de dados e geram problemas. Uma instância que cria mais de 10 entregas por dia deve ser verificada em relação às necessidades comerciais. Considere o uso de entregas contínuas para criar menos entregas. Para obter mais informações, consulte [esta seção](../../workflow/using/continuous-delivery.md).

Entregas com mais de dois anos devem ser removidas da instância.

## Arquivos {#files}

O número de arquivos no disco do servidor de aplicativos não deve aumentar indefinidamente.

Os fluxos de trabalho de importação criam arquivos e, portanto, causam a expansão do disco. Isso pode ser evitado usando a atividade padrão do coletor [de](../../workflow/using/file-collector.md) arquivos. O coletor de arquivos move os arquivos para uma pasta temporária e os limpa automaticamente.

Se um fluxo de trabalho importar arquivos e não fizer uso dos recursos padrão, ele precisará ser removido para manter o espaço em disco mínimo.

## Dados e registros transacionais {#transactional-data-and-logs}

Todo [fluxo de trabalho](../../workflow/using/executing-a-workflow.md#work-table) que importa dados para o Adobe Campaign faz com que o tamanho do banco de dados cresça.

Verifique se os fluxos de trabalho de limpeza ou expurgação estão em execução e expurgando os registros com eficácia. Todos os dados e registros transacionais devem ser removidos. A tarefa de limpeza limpa apenas as tabelas padrão: rastreamento e logs amplos. Tabelas específicas devem ser expurgadas por fluxos de trabalho específicos. Consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Observe o envelhecimento dos dados transacionais verificando a data de criação mais antiga dos registros.
