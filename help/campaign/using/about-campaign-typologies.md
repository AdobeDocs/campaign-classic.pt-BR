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
translation-type: tm+mt
source-git-commit: 44d8ba19f2e79d30229239312e6a5148d247fb28

---


# Sobre tipologias de campanha{#about-campaign-typologies}

A Otimização de campanha é o módulo do Adobe Campaign que permite controlar, filtrar e monitorar o envio de entregas. Para evitar conflitos entre campanhas, o Adobe Campaign pode testar várias combinações aplicando regras de restrição específicas. Isso garante que as mensagens enviadas atendam às necessidades e expectativas dos clientes e às políticas de comunicação da empresa.

>[!NOTE]
>
>Dependendo da sua oferta, a Otimização de Campanha pode estar incluída ou ser um complemento. Verifique o contrato de licença.

## Regras de tipologia {#typology-rules}

Com o Adobe Campaign, você pode criar e aplicar quatro tipos de regras de tipologia:

1. Regras de **Filtro**, que permitem excluir parte do público alvo com base em critérios. For more on this, refer to [Filtering rules](../../campaign/using/filtering-rules.md).
1. Regras de **Pressão**, que permitem controlar a fadiga da marca. For more on this, refer to [Pressure rules](../../campaign/using/pressure-rules.md).
1. Regras de **Capacidade**, que permitem limitar cargas para garantir condições de processamento ideais. For more on this, refer to [Controlling capacity](../../campaign/using/consistency-rules.md#controlling-capacity).
1. Regras de **Controle** que permitem verificar a validade das mensagens antes de serem enviadas. For more on this, refer to [Control rules](../../campaign/using/control-rules.md).

Depois de criadas, as regras de tipologia são agrupadas em tipologias de campanha, que são mencionadas nos deliveries. Consulte [Aplicação de tipologias](#applying-typologies).

## Tipologias {#typologies}

Uma tipologia de campanha pode conter várias [regras de tipologia](#typology-rules), mas um delivery só pode fazer referência a uma tipologia.

The **[!UICONTROL Rules]** tab lets you add, delete or view the typology rules to apply.

![](assets/campaign_opt_rules_tab.png)

## Aplicação de tipologias {#applying-typologies}

As etapas para criar e aplicar uma tipologia para seus deliveries estão listadas abaixo:

1. Criar regras de tipologia.

   As regras de tipologia são encontradas no **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** nó.

   Diferentes regras disponíveis no Campaign estão descritas nas seguintes seções: Regras [de pressão de](../../campaign/using/pressure-rules.md)vendas, regras [de](../../campaign/using/consistency-rules.md#controlling-capacity)capacidade, regras [de](../../campaign/using/control-rules.md) controle e regras [de](../../campaign/using/filtering-rules.md)filtragem.

1. Crie uma tipologia e faça referência às regras criadas nela.

   As tipologias são acessadas pelo nó **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** .

1. Configure seu delivery para usar a tipologia que você criou. Para obter mais informações, consulte [esta seção](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Teste e controle o comportamento por meio de simulações de campanha. Para saber mais sobre simulações de campanha, consulte [esta seção](../../campaign/using/campaign-simulations.md).

Durante a preparação do delivery, os recipients são excluídos quando o critério é atingido. Você pode verificar logs para monitorar exclusões. Casos de uso de exemplo das regras de tipologia de pressão estão disponíveis [nesta página](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

**Tópico relacionado**

* [Aplicar regras de negócios automáticas a entregas em qualquer canal](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)