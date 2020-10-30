---
title: Delivery outline
seo-title: Delivery outline
description: Delivery outline
seo-description: null
page-status-flag: never-activated
uuid: 2b924cc6-6b71-481e-acab-2d035bbc2852
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: a2a65f97-425b-44b2-8cf4-beea850423bc
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '263'
ht-degree: 100%

---


# Delivery outline{#delivery-outline}

O delivery outline permite usar um outline em um workflow de campanha. O outline deve ter sido criado antecipadamente na campanha.

Para obter mais informações sobre delivery outlines no Adobe Campaign, consulte esta [seção](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Para configurar a atividade, basta marcar outline desejado e a data de contato planejada. É possível adicionar regras do filtro adicionando tipologias ou regras de tipologia.

## Exemplo: Inserção de uma oferta por meio de um esboço de entrega.{#example--inserting-an-offer-via-a-delivery-outline}

A atividade delivery outline, disponível nos workflows da campanha, permite apresentar ofertas mencionadas em um delivery outline na campanha atual em andamento.

>[!NOTE]
>
>O pacote de **Interaction** deve ser instalado.

1. Em um workflow, adicione uma atividade de delivery outline antes de adicionar uma atividade de delivery.
1. Na atividade de delivery outline, especifique o outline que deseja usar.

   Para obter mais informações sobre especificar delivery outlines, consulte esta [seção](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Preencha os campos disponíveis de acordo com seu delivery.
1. Há dois casos possíveis:

   * Se desejar chamar o mecanismo de oferta, marque a caixa **[!UICONTROL Restrict the number of propositions selected]**. Especifique o espaço de oferta e o número de propostas que serão apresentadas no delivery.

      Os pesos da oferta e as regras de qualificação serão considerados pelo mecanismo de oferta.

   * Se não marcar a caixa, todas as ofertas no delivery outline serão apresentadas sem chamar o mecanismo de oferta.

   A pré-visualização leva em conta o número de ofertas especificadas no delivery. Ao executar um workflow, é o número especificado no delivery outline que é levado em conta.

   ![](assets/int_compo_offre_wf1.png)

