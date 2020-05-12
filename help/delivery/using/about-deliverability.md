---
title: Sobre a deliverability do Adobe Campaign Classic
description: Saiba mais sobre como gerenciar a deliverability no Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e6617614ae22b73c6783f9775f441e5e25ae19e3
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 90%

---


# Sobre a entregabilidade{#about-deliverability}

**A capacidade de delivery consiste em medir o sucesso das campanhas em chegar à caixa de entrada dos recipients sem rejeição ou sem serem marcadas como spam.**

O Adobe Campaign oferece ferramentas para acompanhar o desempenho de deliverability da sua plataforma. Esta seção também destaca os principais princípios que você deve ter em mente ao gerenciar e otimizar a deliverability.

## Configuração {#configuration}

Esse recurso está disponível por meio de um pacote dedicado no Adobe Campaign. Para usá-lo, esse pacote deve ser instalado. Depois de concluído, reinicie o servidor para que o pacote seja considerado.
* Para clientes hospedados e híbridos, a opção **Deliverability monitoring** é configurada em sua instância pelo suporte técnico e consultores da Adobe. Para obter mais informações, entre em contato com o executivo da sua conta Adobe.

* For on-premise installations, you must install the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. Para obter mais informações, consulte [Instalação de pacotes padrão do Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

In Adobe Campaign Classic, **Deliverability monitoring** is managed by the **[!UICONTROL Refresh for deliverability]** workflow. Ele é instalado por padrão em todas as instâncias e permite inicializar a lista de regras de qualificação de email de devolução, a lista de domínios e a lista de MXs. Once the **[!UICONTROL Deliverability monitoring (Email Deliverability)]** package is installed, this workflow runs nightly to regularly update the list of rules and enables you to actively manage platform deliverability.

## Histórico {#background}

A capacidade de fornecimento de email apresenta um grande desafio para os profissionais de marketing - estejam eles enviando alguns milhares ou vários bilhões de mensagens. Uma em cinco mensagens nunca alcança a caixa de entrada ou o recipient pretendido.

Uma vez relegado como um &quot;problema técnico&quot; para o departamento de TI, a capacidade de fornecimento de email continua aumentando de importância na agenda do marketing. Isso porque os profissionais de marketing experientes reconhecem que, embora muitos de seus elementos sejam técnicos, o deliverability é, em última instância, um problema comercial com implicações significativas de receita.

Considere o funil de marketing por email. O deliverability determina o número de mensagens recebidas, o que, por sua vez, afeta cada estágio subsequente do funil. Menos emails recebidos resulta em menos aberturas, menos cliques e menos conversões. **Para empresas com um banco de dados grande, a diferença entre o deliverability médio e excelente poderia literalmente significar centenas de milhares de dólares em receita.**

![](assets/deliverability_overview_1.png)

Ao estabelecer o deliverability médio (80%), os profissionais de marketing estão deixando de ganhar conversões significativas e dólares.

O que exatamente é a capacidade de fornecimento de email? E como os profissionais de marketing podem melhorar as taxas de deliverability para alargar a boca do funil e obter mais resultados de suas campanhas de email?

A capacidade de fornecimento de email refere-se ao conjunto de características que determinam a capacidade de uma mensagem de alcançar seu destino por meio de um endereço de email pessoal, dentro de um curto período e com a qualidade esperada em termos de conteúdo e formato. Essas características estão em quatro categorias principais: qualidade de dados, mensagem e conteúdo, infraestrutura de envio e reputação. Juntos, elas formam a base de um programa bem-sucedido de capacidade de fornecimento de email. Essa visão geral destaca os quatro princípios básicos de sucesso da capacidade de fornecimento de email e oferece práticas recomendadas para alcançar a caixa de entrada e gerar receitas maiores dos programas de marketing por email.

<!--![](assets/deliverability_overview_2.png)-->
