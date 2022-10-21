---
product: campaign
title: Princípios fundamentais
description: Princípios fundamentais
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: c929557ee9f5467f9c3b8eb1ed25fae5399820ba
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 93%

---

# Princípios fundamentais{#fundamental-principles}

![](../../assets/v7-only.svg)

## Implantação de ambientes {#deploying-environments}

Há dois ambientes para cada targeting dimension usada ao gerenciar ofertas:

* Um ambiente de design no qual o gerente de ofertas cuida da criação e categorização de ofertas, como editá-las e do início do processo de aprovação para que elas possam ser usadas. As regras para cada categoria, os espaços de oferta nos quais as ofertas podem ser apresentadas, e os filtros predefinidos usados para definir a elegibilidade de uma oferta também são definidos neste ambiente.

   As categorias também podem ser publicadas manualmente no ambiente online.

   O processo de aprovação de ofertas está detalhado na seção [Aprovação e ativação de uma oferta](../../interaction/using/approving-and-activating-an-offer.md).

* Um ambiente dinâmico no qual podem ser encontradas ofertas aprovadas do ambiente de design, bem como os vários espaços de oferta, filtros, categorias e regras configurados no ambiente de design. Durante uma chamada para o mecanismo de oferta, o mecanismo sempre usará ofertas do ambiente dinâmico.

Uma oferta só é implantada nos espaços de oferta selecionados durante o processo de aprovação. Portanto, uma oferta pode estar ativa, mas inutilizável em um espaço de oferta que também está ativo.

![](assets/architecture_interaction1.png)

## Tipos de interação e métodos de contato {#interaction-types-and-contact-methods}

Há dois tipos possíveis de interações: interações de entrada (iniciadas por um contato) e interações de saída (iniciadas pelo designer de ofertas).

Esses dois tipos de interações podem ser realizadas no modo unitário (a oferta é calculada para um único contato), ou em modo de lote (a oferta é calculada para um conjunto de contatos). Geralmente, as interações de entrada são realizadas no modo unitário e as interações de saída são executadas em modo de lote. No entanto, pode haver certas exceções, como mensagens transacionais, por exemplo, pois a interação de saída é executada no modo unitário (consulte [esta seção](../../message-center/using/about-transactional-messaging.md)).

Assim que uma oferta puder ou deve ser apresentada (de acordo com as configurações realizadas), o motor de oferta reproduzirá a função intermediária: ele calcula automaticamente a melhor oferta possível para um contato dentre as disponíveis ao combinar dados recebidos sobre o contato e as diferentes regras que podem ser aplicadas conforme especificado na aplicação.

![](assets/architecture_interaction2.png)
