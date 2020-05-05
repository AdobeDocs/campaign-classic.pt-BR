---
title: Tipos de deliveries
seo-title: Tipos de deliveries
description: Tipos de deliveries
seo-description: null
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# Tipos de deliveries{#types-of-deliveries}

Existem três tipos de objetos de delivery no Campaign:

## Delivery unitário {#single-delivery}

Um **delivery** é um objeto de delivery independente executado uma vez. Ele pode ser duplicado, preparado novamente, mas, desde que esteja no seu estado final (cancelado, interrompido, concluído), não poderá ser reutilizado.

Os deliveries podem ser criados a partir da lista de deliveries ou em um fluxo de trabalho através de uma atividade de [Delivery](../../workflow/using/delivery.md) .

Os workflows também fornecem atividades de delivery específicas de acordo com o tipo de canal que você deseja usar. Para obter mais informações sobre essas atividades, consulte [esta seção](../../workflow/using/cross-channel-deliveries.md).

## Delivery recorrente {#recurring-delivery}

Um **delivery recorrente** permite criar um novo delivery sempre que a atividade for executada. Isso evita que você crie um novo delivery para tarefas recorrentes.

Como exemplo, se você executar esse tipo de atividade uma vez por mês, acabará com 12 deliveries após um ano.

Os deliveries recorrentes são criados em workflows através da [atividade Recurring delivery.](../../workflow/using/recurring-delivery.md) Um exemplo dessa atividade que está sendo usada é apresentado nesta seção: [Criação de um delivery recorrente em um workflow de direcionamento](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Delivery contínuo {#continuous-delivery}

Um **delivery contínuo** permite que você adicione novos recipients a um delivery existente, o que evita a necessidade de criar um novo delivery a cada execução.

Se uma informação no delivery for alterado (conteúdo, nome, etc.), um novo objeto de delivery será criado na execução do delivery. Se nenhuma informação for alterada, o mesmo objeto do delivery será reutilizado e os logs de delivery e rastreamento serão adicionados no mesmo objeto.

Como exemplo, se você executar esse tipo de atividade uma vez por mês, acabará com um único delivery após um ano (desde que não tenha feito nenhuma alteração no delivery).

Os deliveries contínuos são criados em workflows através da [atividade Continuous delivery](../../workflow/using/continuous-delivery.md).
