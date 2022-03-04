---
product: campaign
title: Sobre tipologias de campanha
description: Sobre tipologias de campanha
feature: Typology Rules
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 100%

---

# Sobre tipologias de campanha{#about-campaign-typologies}

![](../../assets/common.svg)

Otimização de Campanha é o módulo do Adobe Campaign que permite controlar, filtrar e monitorar o envio de deliveries. Para evitar conflitos entre campanhas, o Adobe Campaign pode testar várias combinações aplicando regras de restrição específicas. Isso garante que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, de acordo com as políticas de comunicação da empresa.

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](#typologies-video)

>[!NOTE]
>
>Dependendo da sua oferta, a Otimização de Campanha pode estar incluída ou ser um complemento. Verifique o contrato de licença.

## Regras de tipologia {#typology-rules}

Com o Adobe Campaign, você pode criar e aplicar quatro tipos de regras de tipologia:

* Regras de **Filtro**, que permitem excluir parte do público alvo com base em critérios. Para obter mais informações, consulte [Regras de filtragem](filtering-rules.md).
* Regras de **Pressão**, que permitem controlar a fadiga da marca. Para obter mais informações, consulte [Regras de pressão](pressure-rules.md).
* Regras de **Capacidade**, que permitem limitar cargas para garantir condições de processamento ideais. Para obter mais informações, consulte [Controle de capacidade](consistency-rules.md#controlling-capacity).
* Regras de **Controle** que permitem verificar a validade das mensagens antes de serem enviadas. Para obter mais informações, consulte [Regras de controle](control-rules.md).

Depois de criadas, as regras de tipologia são agrupadas em tipologias de campanha, que são mencionadas nos deliveries. Consulte [Aplicação de tipologias](#applying-typologies).

## Tipologias {#typologies}

Uma tipologia de campanha pode conter várias [regras de tipologia](#typology-rules), mas uma entrega só pode fazer referência a uma tipologia.

A guia **[!UICONTROL Rules]** permite adicionar, excluir ou exibir as regras de tipologia a serem aplicadas.

![](assets/campaign_opt_rules_tab.png)

## Aplicação de tipologias {#applying-typologies}

As etapas para criar e aplicar uma tipologia para seus deliveries estão listadas abaixo:

1. Criar regras de tipologia.

   As regras de tipologia são encontradas no nó **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**.

   Diferentes regras disponíveis no Campaign estão descritas nas seguintes seções: [sales pressure rules](pressure-rules.md), [capacity rules](consistency-rules.md#controlling-capacity), [control rules](control-rules.md) e [filtering rules](filtering-rules.md).

1. Crie uma tipologia e faça referência às regras criadas nela.

   As tipologias são acessadas pelo nó **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**.

1. Configure seu delivery para usar a tipologia que você criou. Para obter mais informações, consulte [esta seção](applying-rules.md#applying-a-typology-to-a-delivery).
1. Teste e controle o comportamento por meio de simulações de campanha. Para saber mais sobre simulações de campanha, consulte [esta seção](campaign-simulations.md).

Durante a preparação do delivery, os recipients são excluídos quando o critério é atingido. Você pode verificar logs para monitorar exclusões. Casos de uso de exemplo das regras de tipologia de pressão estão disponíveis [nesta página](pressure-rules.md#use-cases-on-pressure-rules).

## Tutoriais em vídeo {#typologies-video}

### Como configurar o gerenciamento de fadiga usando regras de tipologia

Este vídeo explica como implementar o gerenciamento de fadiga no Adobe Campaign utilizando regras de tipologia.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Como configurar o gerenciamento de fadiga usando filtros predefinidos

O gerenciamento de fadiga controla a frequência e a quantidade de mensagens para evitar a solicitação excessiva de recipients. Se você não tiver o módulo de otimização de campanha na instância da campanha, poderá configurar um filtro predefinido que irá filtrar a população do público-alvo pelo número de mensagens recebidas
Este vídeo ensina a implementar o gerenciamento de fadiga no Adobe Campaign Classic usando filtros.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Vídeos explicativos extras sobre o Campaign estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).

**Tópicos relacionados**

* [Aplicar regras de negócios automáticas a deliveries em qualquer canal](https://helpx.adobe.com/br/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [Introdução a tipologias e gerenciamento de fadiga](pressure-rules.md)

