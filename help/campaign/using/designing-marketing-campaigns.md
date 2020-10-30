---
title: Criar campanhas de marketing
seo-title: Criar campanhas de marketing
description: Defina, otimize, execute e analise campanhas de marketing.
seo-description: null
page-status-flag: never-activated
uuid: e0fd5df6-7516-4ca6-bbdf-243a264d0283
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
discoiquuid: a9eb6627-2e51-42d0-9b29-5b798bdf5b33
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '420'
ht-degree: 100%

---


# Criar campanhas de marketing{#designing-marketing-campaigns}

O Adobe Campaign permite que você defina, otimize, execute e analise campanhas de comunicação e marketing. O Adobe Campaign atua como uma central de execução e pedido unificada para estratégias de marketing. Para obter mais informações, consulte [Accessing campaigns](../../campaign/using/accessing-campaigns.md) and [Setting up marketing campaigns](../../campaign/using/setting-up-marketing-campaigns.md).

Além disso, o módulo **GMarketing Resource Management (MRM)** permite controlar ações de marketing em um modo colaborativo fornecendo gerenciamento completo e rastreamento em tempo real das tarefas, orçamentos e recursos de marketing envolvidos. O Gerenciamento de recursos de marketing permite otimizar e regular o gerenciamento de processos internos e externos, recursos e campanhas de marketing, bem como relações de terceiros (agências, impressoras etc.). Para obter mais informações, consulte [esta seção](../../campaign/using/about-marketing-resource-management.md).

>[!NOTE]
>
>Para saber mais sobre as funcionalidades principais do Adobe Campaign, consulte a seção [Introdução](../../platform/using/about-adobe-campaign-classic.md) .\
>Os recursos relacionados à definição de metas de população, personalização de mensagens e delivery de mensagens nos diversos canais são detalhados [nesta seção](../../delivery/using/steps-about-delivery-creation-steps.md).

## Conceitos principais {#core-concepts}

Os seguintes conceitos precisam ser conhecidos no contexto do Campaign:

* **Campanha**

   Uma campanha centraliza todos os elementos relacionados a uma campanha de marketing: remessas, regras de definição de metas, custos, arquivos de exportação, documentos relacionados etc. Cada campanha é anexada a um programa.

   Para obter mais informações, consulte [Adicionar uma campanha](../../campaign/using/setting-up-marketing-campaigns.md#adding-a-campaign).

* **Programa**

   Um programa permite definir ações de marketing para um período de calendário: iniciar, prospecção, fidelização etc. Cada programa contém campanhas vinculadas a um calendário, que fornece uma visualização geral.

* **Plano**

   O plano de marketing pode conter vários programas. Ele está vinculado a um período de calendário, tem um orçamento alocado e também pode ser vinculado a documentos e objetivos.

   Para obter mais informações, consulte [Calendário da campanha](../../campaign/using/accessing-marketing-campaigns.md#campaign-calendar).

* **Workflow**

   Um workflow de campanha contém as mesmas atividades que para todos os workflows, mas é específico da campanha. Ele permite que você crie e configure fornecimentos para todos os canais disponíveis.

   Para obter mais informações, consulte [esta seção](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

* **Objetivos**

   Dentro da campanha, programa ou plano, você pode declarar uma lista de objetivos. Esses valores são quantificados para serem alcançados. No final da campanha, do programa ou do plano, o módulo MRM permite que você compare os objetivos e os resultados em relatórios dedicados.

* **Delivery outline**

   Um delivery outline é uma descrição estruturada de um delivery. Cada delivery pode se referir a um delivery outline que contenha, por exemplo, as ofertas relacionadas, documentos a serem anexados ou um link para lojas. Uma oferta pode ser referida no delivery de acordo com o delivery outline selecionado.

   Para obter mais informações, consulte [Associando e estruturando recursos vinculados por um outline de delivery](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

