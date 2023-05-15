---
product: campaign
title: Objetos de aplicativo
description: Objetos de aplicativo
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---

# Objetos de aplicativo{#application-objects}



Os objetos incorporados devem ser monitorizados e é importante evitar que cresçam demasiado.

## Sequência de IDs {#sequence-of-ids}

O Adobe Campaign usa uma sequência de ID que deve ser consumida adequadamente: **xtkNewId**. Se a sequência for consumida muito rapidamente (ou seja, de 100.000 por dia), você deve verificar se é consistente com as necessidades da sua empresa, como enviar milhões de emails por dia. É possível definir uma sequência dedicada para tabelas específicas. Você pode configurar um fluxo de trabalho para monitorar o uso da ID.

Quando a sequência atinge mais de 2 bilhões (2.147.483.648 é o número exato), volta a zero. Deve ser evitado e cria questões, razão pela qual esta sequência deve ser monitorizada.

Para evitar isso com tabelas grandes, considere usar uma sequência específica. Isso pode ser feito com o **pkSequence** no schema.

Os workflows de alta frequência que criam muitos logs consumirão muitas IDs. Portanto, é altamente recomendável evitar muitos logs e altas frequências em workflows.

Se a sequência já tiver sido cíclica, a melhor solução é alternar para IDs negativas, a partir de -2.147.483.648.

## Pastas {#folders}

Deve haver menos de 1000 pastas em qualquer instância. Ter mais pastas do que isso pode causar problemas de desempenho com o cliente do Campaign. Você pode configurar um trabalho de monitoramento para contar o número de pastas, fluxos de trabalho, etc., e gerar relatórios periodicamente.

Esse método também destaca os usuários que criam muitos objetos.

## Entregas {#deliveries}

Deve haver menos de 1000 deliveries na instância a qualquer momento. Ter muitos deliveries consome espaço no banco de dados e cria problemas. Uma instância que cria mais de 10 deliveries por dia deve ser verificada em relação às necessidades comerciais. Considere o uso de deliveries contínuos para criar menos deliveries. Para obter mais informações, consulte [esta seção](../../workflow/using/continuous-delivery.md).

Os deliveries com mais de dois anos devem ser removidos da instância.

## Arquivos {#files}

O número de arquivos no disco do servidor de aplicativos não deve aumentar indefinidamente.

Os workflows de importação criam arquivos e, portanto, causam expansão de disco. Isso pode ser evitado usando o padrão [File collector](../../workflow/using/file-collector.md) atividade . O coletor de arquivos move os arquivos para uma pasta temporária e os limpa automaticamente.

Se um workflow importar arquivos e não fizer uso dos recursos padrão, ele precisará ser removido para manter o espaço em disco mínimo.

## Dados e registros transacionais {#transactional-data-and-logs}

Cada [workflow](../../workflow/using/data-life-cycle.md#work-table) que importa dados para o Adobe Campaign faz com que o tamanho do banco de dados aumente.

Verifique se os workflows de limpeza ou limpeza estão em execução e excluindo registros com eficácia. Todos os dados e logs transacionais devem ser limpos. A tarefa de limpeza limpa apenas as tabelas padrão: rastreamento e logs amplos. Tabelas específicas devem ser removidas por workflows específicos. Consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Fique atento ao envelhecimento dos dados transacionais, verificando a data de criação mais antiga dos registros.
