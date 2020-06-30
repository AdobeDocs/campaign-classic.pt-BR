---
title: Sobre tipologias de campanha
seo-title: Sobre tipologias de campanha
description: Sobre tipologias de campanha
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: e97183256ef6d3f2068dd0fbc8eb3c3f32e0bae0
workflow-type: ht
source-wordcount: '367'
ht-degree: 100%

---


# Sobre tipologias de campanha{#about-campaign-typologies}

Otimização de Campanha é o módulo do Adobe Campaign que permite controlar, filtrar e monitorar o envio de deliveries. Para evitar conflitos entre campanhas, o Adobe Campaign pode testar várias combinações aplicando regras de restrição específicas. Isso garante que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, de acordo com as políticas de comunicação da empresa.

>[!NOTE]
>
>Dependendo da sua oferta, a Otimização de Campanha pode estar incluída ou ser um complemento. Verifique o contrato de licença.

## Regras de tipologia {#typology-rules}

Com o Adobe Campaign, você pode criar e aplicar quatro tipos de regras de tipologia:

* Regras de **Filtro**, que permitem excluir parte do público alvo com base em critérios. Para obter mais informações, consulte [Regras de filtragem](../../campaign/using/filtering-rules.md).
* Regras de **Pressão**, que permitem controlar a fadiga da marca. Para obter mais informações, consulte [Regras de pressão](../../campaign/using/pressure-rules.md).
* Regras de **Capacidade**, que permitem limitar cargas para garantir condições de processamento ideais. Para obter mais informações, consulte [Controle de capacidade](../../campaign/using/consistency-rules.md#controlling-capacity).
* Regras de **Controle** que permitem verificar a validade das mensagens antes de serem enviadas. Para obter mais informações, consulte [Regras de controle](../../campaign/using/control-rules.md).

Depois de criadas, as regras de tipologia são agrupadas em tipologias de campanha, que são mencionadas nos deliveries. Consulte [Aplicação de tipologias](#applying-typologies).

## Tipologias {#typologies}

Uma tipologia de campanha pode conter várias [regras de tipologia](#typology-rules), mas um delivery só pode fazer referência a uma tipologia.

A guia **[!UICONTROL Rules]** permite adicionar, excluir ou exibir as regras de tipologia a serem aplicadas.

![](assets/campaign_opt_rules_tab.png)

## Aplicação de tipologias {#applying-typologies}

As etapas para criar e aplicar uma tipologia para seus deliveries estão listadas abaixo:

1. Criar regras de tipologia.

   As regras de tipologia são encontradas no nó **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**.

   Diferentes regras disponíveis no Campaign estão descritas nas seguintes seções: [sales pressure rules](../../campaign/using/pressure-rules.md), [capacity rules](../../campaign/using/consistency-rules.md#controlling-capacity), [control rules](../../campaign/using/control-rules.md) e [filtering rules](../../campaign/using/filtering-rules.md).

1. Crie uma tipologia e faça referência às regras criadas nela.

   As tipologias são acessadas pelo nó **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**.

1. Configure seu delivery para usar a tipologia que você criou. Para obter mais informações, consulte [esta seção](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Teste e controle o comportamento por meio de simulações de campanha. Para saber mais sobre simulações de campanha, consulte [esta seção](../../campaign/using/campaign-simulations.md).

Durante a preparação do delivery, os recipients são excluídos quando o critério é atingido. Você pode verificar logs para monitorar exclusões. Casos de uso de exemplo das regras de tipologia de pressão estão disponíveis [nesta página](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

**Tópicos relacionados**

* [Aplicar regras de negócios automáticas a deliveries em qualquer canal](https://helpx.adobe.com/br/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)