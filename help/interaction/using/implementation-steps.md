---
title: Etapas de implementação
seo-title: Etapas de implementação
description: Etapas de implementação
seo-description: null
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '286'
ht-degree: 100%

---


# Etapas de implementação{#implementation-steps}

## Configuração da interação {#configuring-interaction}

>[!NOTE]
>
>As etapas a seguir devem ser executadas por um perfil **Administrador** e apenas em ambientes de design.

1. Criar perfis de usuário. Para obter mais informações, consulte [Perfis de operador](../../interaction/using/operator-profiles.md).
1. Criar um ambiente de oferta pelo direcionamento da dimensão. Para obter mais informações, consulte [Criação de um ambiente de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Criar regras de tipologia para cada ambiente. Para obter mais informações, consulte [Criação e referência de uma regra de apresentação de oferta](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Criar espaços de oferta para cada ambiente e configurar funções de renderização. Para obter mais informações, consulte [Criação de espaços de oferta](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Se o espaço for definido por um canal unitário no modo identificado, você deverá especificar os parâmetros avançados para esse espaço.

1. Configurar o mecanismo de oferta para interações de entrada para apresentar e atualizar uma ou várias ofertas.

   Os vários modos de integração são detalhados em [Sobre canais de entrada](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Quando um espaço é criado no canal de entrada da Web, também é necessária uma configuração no site em que a oferta será exibida.

## Gerenciar o catálogo de ofertas {#managing-the-offer-catalog-}

>[!NOTE]
>
>As etapas a seguir devem ser executadas por um **Gerente de ofertas**.

1. Criando categorias de ofertas em ambientes de design. Para obter mais informações, consulte [Criação de categorias de oferta](../../interaction/using/creating-offer-categories.md).
1. Criação de ofertas em ambientes de design. Para obter mais informações, consulte [Criação de uma oferta](../../interaction/using/creating-an-offer.md).
1. Aprovação e publicação de ofertas em um ou vários espaços para torná-las disponíveis em ambientes dinâmicos para o gerente de delivery. Para obter mais informações, consulte [Aprovação e ativação de uma oferta](../../interaction/using/approving-and-activating-an-offer.md).

## Utilização do catálogo de ofertas {#using-the-offer-catalog-}

>[!NOTE]
>
>As etapas a seguir devem ser executadas por um perfil de **Gerente de delivery** . Eles só podem editar ofertas em ambientes dinâmicos.

1. Criação de uma campanha.
1. Consulta de uma oferta em uma campanha ou uma delivery de campanha. Para obter mais informações, consulte [Sobre canais de saída](../../interaction/using/about-outbound-channels.md).

