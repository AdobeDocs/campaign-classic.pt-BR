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
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 4%

---


# Objetos de aplicativo{#application-objects}

Objetos incorporados devem ser monitorados e impedir que cresçam demais é importante.

## Sequência de IDs {#sequence-of-ids}

O Adobe Campaign usa uma sequência de ID que deve ser consumida de acordo: **xtkNewId**. Se a sequência for consumida muito rapidamente (ou seja, de 100.000 por dia), você deve verificar se é consistente com as necessidades de sua empresa, como enviar milhões de emails por dia. É possível definir uma sequência dedicada para tabelas específicas. Você pode configurar um fluxo de trabalho para monitorar o uso da ID.

Quando a sequência chega a mais de 2 bilhões (2.147.483.648 é o número exato), volta a zero. Deve ser evitada e cria problemas, razão pela qual esta sequência deve ser monitorizada.

Para evitar isso com tabelas grandes, considere usar uma sequência específica. Isso pode ser feito com o atributo **pkSequence** no schema.

workflows de alta frequência que criam muitos registros consumirão muitas IDs. Portanto, é altamente recomendável evitar muitos registros e altas frequências em workflows.

Se a sequência já tiver sido cíclica, a melhor solução é alternar para IDs negativas, a partir de -2.147.483.648.

## Folders {#folders}

Deve haver menos de 1000 pastas em qualquer instância. Ter mais pastas do que isso pode causar problemas de desempenho com o cliente de Campanha. Você pode configurar um trabalho de monitoramento para contar o número de pastas, workflows, etc., e retornar ao relatório periodicamente.

Esse método também destaca os usuários que criam muitos objetos.

## Deliveries {#deliveries}

Deve haver menos de 1000 delivery na instância a qualquer momento. Ter muitos delivery consome espaço no banco de dados e gera problemas. Uma instância que cria mais de 10 delivery por dia deve ser verificada em relação aos requisitos comerciais. Considere o uso de delivery contínuos para criar menos delivery. Para obter mais informações, consulte [esta seção](../../workflow/using/continuous-delivery.md).

Delivery com mais de dois anos devem ser removidos da instância.

## Arquivos {#files}

O número de arquivos no disco do servidor de aplicativos não deve aumentar indefinidamente.

Os workflows de importação criam arquivos e, portanto, causam a expansão do disco. Isso pode ser evitado usando a atividade padrão do [File collector](../../workflow/using/file-collector.md) . O coletor de arquivos move os arquivos para uma pasta temporária e os limpa automaticamente.

Se um fluxo de trabalho importar arquivos e não fizer uso dos recursos padrão, ele precisará ser removido para manter o espaço em disco mínimo.

## Dados e registros transacionais {#transactional-data-and-logs}

Todo [fluxo de trabalho](../../workflow/using/data-life-cycle.md#work-table) que importa dados para o Adobe Campaign faz com que o tamanho do banco de dados cresça.

Verifique se os workflows de limpeza ou remoção estão em execução e removendo os registros com eficácia. Todos os dados e registros transacionais devem ser removidos. A tarefa de limpeza limpa apenas as tabelas padrão: rastreamento e logs amplos. Tabelas específicas devem ser expurgadas por workflows específicos. Consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Observe o envelhecimento dos dados transacionais verificando a data de criação mais antiga dos registros.
