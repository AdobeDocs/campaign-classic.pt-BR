---
title: Aplicar regras
seo-title: Aplicar regras
description: Aplicar regras
seo-description: null
page-status-flag: never-activated
uuid: 4472fc0d-d717-4603-8472-bdaf2835a02a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: a0e76d27-bedd-4f81-b4d2-1221444e670e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Aplicar regras{#applying-rules}

## Aplicar uma tipologia a um delivery {#applying-a-typology-to-a-delivery}

Para aplicar as regras de tipologia criadas, é necessário associá-las a uma tipologia e depois fazer referência a essa tipologia no delivery. Para fazer isso:

1. Crie uma tipologia de campanha.

   As tipologias são acessadas pelo nó **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** .

1. Go to the **[!UICONTROL Rules]** tab, click the **[!UICONTROL Add]** button and select the rules to apply with this typology.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Salve a tipologia: ela será adicionada à lista de tipologias existentes.
1. Abra o delivery para o qual deseja aplicar as regras.
1. Open the delivery properties and access the **[!UICONTROL Typology]** tab.
1. Selecione a tipologia na lista suspensa.

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >A tipologia poderá ser definida no template de delivery para ser aplicada automaticamente a todos os deliveries criados usando esse template.

## Definindo as condições de aplicação {#defining-application-conditions}

Você poderá restringir o campo de aplicação de uma regra de acordo com suas necessidades (exceto para regras de controle).

É possível configurar regras de tipologia para que elas se apliquem apenas a certos deliveries aos quais estajam vinculadas ou a certos recipients entre os alvos de um delivery.

Para definir as condições do aplicativo de uma regra, clique no **[!UICONTROL Edit the rule application conditions...]** link na **[!UICONTROL General]** guia.

Em seguida, use o editor de query para definir as condições de filtragem. No exemplo a seguir, a regra de capacidade apresenta apenas os deliveries com a palavra &#39;oferta&#39; em seu rótulo ou deliveries criados antes de 1º de abril de 2013.

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>Nas regras de filtragem, é possível selecionar a condição do aplicativo de critérios de filtragem: eles podem depender do delivery ou do delivery outline. Para obter mais informações, consulte [Condicionar uma regra](../../campaign/using/filtering-rules.md#conditioning-a-filtering-rule)de filtragem.

## Ajustar a frequência de cálculo {#adjusting-calculation-frequency}

As arbitragens são reexecutadas automaticamente todas as noites através do workflow de limpeza de banco de dados. No entanto, os valores podem ser salvos além desse período.

De fato, alguns cálculos usam valores que não são alterados diariamente. Portanto, seria irrelevante para os dados recalcular todos os dias e sobrecarregar o banco de dados para nada. Por exemplo, se um processo enriquece o banco de dados de marketing com pontuações do cliente e informações de compra em uma base semanal, os dados baseados nesses valores não precisarão serem recalculados todos os dias.

To do this, the **[!UICONTROL Frequency]** field of the **[!UICONTROL General]** tab lets you define a maximum period during which targeting is saved. Por padrão, o valor **0** indica que o cálculo permanece válido até a próxima execução de uma nova arbitragem diária.

To save the results beyond this period, enter a value greater than 12 in the **[!UICONTROL Frequency]** field: once this period expires, all rules are re-applied.

The **[!UICONTROL Re-apply the rule at the start of personalization]** option lets you apply the rule automatically during the personalization phase, including if the period stated in the **[!UICONTROL Frequency]** field is still valid.

## Selecionar a fase da aplicação da regra {#selecting-the-rule-application-phase}

As regras de tipologia são aplicadas em uma sequência específica durante as fases de direcionamento, análise e personalização dos envios.

### Ordem de execução {#execution-order}

No modo de operação padrão, as regras são aplicadas na seguinte sequência:

1. Regras de controle, se elas forem aplicadas no início do direcionamento.
1. Regras de filtragem:

   * Regras de aplicações nativas para qualificação de endereço: endereço definido / endereço não verificado / endereço incluído na blacklist / endereço em quarentena / qualidade do endereço.
   * Filtrar regras definidas pelo usuário.
   * Regra de desduplicação no endereço ou identificador (aplicado se necessário).

1. Regras de pressão.
1. Regras de capacidade.
1. Regras de controle, se elas forem aplicadas no final do direcionamento.
1. Regras de controle, se elas forem aplicadas ao início da personalização. Se as regras dos usuários (filtragem/pressão/capacitive) expiram e precisam de recálculo, elas serão aplicadas durante esta etapa.
1. Regras de controle, se elas forem aplicadas ao final da personalização.

>[!NOTE]
>
>Ao trabalhar com o módulo Campaign Interaction, regras de elegibilidade de oferta são aplicadas ao mesmo tempo que as regras de filtragem (para ofertas encontradas em delivery outlines) ou durante a fase de personalização, durante a chamada para o mecanismo de oferta.

You can adapt the execution sequence of rules which have the same type using the appropriate field in the **[!UICONTROL General]** tab of the rule. When several rules are executed during the same message processing phase, you can configure their execution sequence in the **[!UICONTROL Execution sequence]** field.

Por exemplo, uma regra de pressão com uma ordem de execução de 20 é executada antes de uma regra de pressão com uma ordem de execução de 30.

### Regras de controle {#control-rules}

For **[!UICONTROL Control]** rules, you can decide at which point of the delivery life cycle the rule will be applied (before or after targeting, at the start of personalization, at the end of the analysis). Select the value to apply in the drop-down list of the **[!UICONTROL Phase]** field, in the **[!UICONTROL General]** tab of the typology rule.

![](assets/campaign_opt_define_control_phase.png)

Os valores possíveis são:

* **[!UICONTROL At the start of targeting]**

   Para evitar que a etapa de personalização seja executada no caso de erros, é possível aplicar a regra de controle aqui.

* **[!UICONTROL After targeting]**

   Se é necessário saber o target para aplicar a regra de controle, selecione essa fase.

   For example, the **[!UICONTROL Check proof size]** control rule applies after each targeting stage: this rule prevents message personalization if there are too many proof recipients.

* **[!UICONTROL At the start of personalization]**

   Essa fase deve ser selecionada se o controle envolver a aprovação da personalização da mensagem. A personalização da mensagem é realizada durante a fase de análise.

* **[!UICONTROL At the end of the analysis]**

   Quando uma verificação exige a personalização da mensagem para ser concluída, selecione essa fase.

## Configurações adicionais {#additional-configurations}

### Controle o tráfego SMTP de saída {#control-outgoing-smtp-traffic}

As an option, you can use the **[!UICONTROL Managing affinities with IP addresses]** field to link deliveries to the delivery server (MTA) this affinity. Isso permite a restrição do número de emails para envios específicas em máquinas ou endereços de saída.

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>Affinity management does not apply for **[!UICONTROL Filtering]** typologies.\
>As afinidades são definidas no arquivo de configuração de instância, no servidor do Adobe Campaign. Para obter mais informações, consulte [esta seção](../../installation/using/about-initial-configuration.md).

### Otimização de Campanha e Marketing Distribuído {#campaign-optimization-and-distributed-marketing}

The **[!UICONTROL Distributed Marketing]** tab lets you define the re-mapping of typologies and/or rules which applies when a shared campaign is ordered and/or reserved. As tipologias/regras definidas para uma entidade local (vinculada àqueles definidos para a entidade central) substituem as regras/tipologias vinculadas à entidade central. O remapeamento permite adaptar regras da entidade central às entidades locais que solicitam a campanha.

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>In typologies and typology rules, the **[!UICONTROL Distributed Marketing]** tab is added if your license includes this option: please check you license agreement.\
>Para obter mais informações sobre Marketing distribuído, consulte [Sobre marketing](../../campaign/using/about-distributed-marketing.md)distribuído.

