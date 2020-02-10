---
title: Interações anônimas
seo-title: Interações anônimas
description: Interações anônimas
seo-description: null
page-status-flag: never-activated
uuid: 6e28e8a4-8d2f-4747-8dd0-680fbf02b25d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 3fd7a1ef-b0e2-4a7e-9e36-044d997db785
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8e37be4f764feadb49c70a9d598f8f3b8f864380

---


# Interações anônimas{#anonymous-interactions}

Assista a este [vídeo](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&ref=helpx.adobe.com) para obter uma visão geral de como as ofertas são fornecidas para alvos identificados e anônimos.

## Direcionamento e armazenamento de um ambiente para interações anônimas {#targeting-and-storing-an-environment-for-anonymous-interactions}

Por padrão, o Interaction vem com um ambiente pré-configurado para direcionar à tabela de recipients (ofertas identificadas). Se quiser direcionar a outra tabela (tabela de visitantes para ofertas anônimas ou uma tabela de recipients específica), é preciso usar o assistente de target mapping para criar o ambiente. Para obter mais informações, consulte [Criação de um ambiente](../../interaction/using/live-design-environments.md#creating-an-offer-environment)de ofertas.

When you create an anonymous environment via the mapping creation wizard, the **[!UICONTROL Environment dedicated to incoming anonymous interactions]** box is automatically checked in the environment&#39;s **[!UICONTROL General]** tab.

A conclusão **[!UICONTROL Targeting dimension]** é automática. Por padrão, ele vincula à tabela do visitante.

O **[!UICONTROL Visitor folder]** campo é exibido. It is automatically completed to link to the **[!UICONTROL Visitors]** folder. Este campo permite escolher onde armazenar os perfis de visitantes.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>If you want to filter several types of visitors, for instance in the case of anonymous offers presented for one or more brands, you need to create an environment for each brand, and a **[!UICONTROL Visitors]** type folder for each environment.

## Catálogo de ofertas para interações anônimas {#offer-catalog-for-anonymous-interactions}

Assim como as interações de saída, as interações de entrada são organizadas em um catálogo de ofertas que é composto por categorias e ofertas.

Para criar categorias e espaços, aplique o mesmo processo que para os visitantes identificados (consulte [Criar categorias](../../interaction/using/creating-offer-categories.md) de ofertas e [Criar um ambiente](../../interaction/using/live-design-environments.md#creating-an-offer-environment)de ofertas).

## Visitantes anônimos {#anonymous-visitors}

Os visitantes anônimos podem ser submetidos a um processo de identificação por cookies quando se conectam. Esse reconhecimento implícito baseia-se no histórico do navegador do visitante.

Durante essa etapa, uma comparação é feita entre os dados recuperados pelos cookies e aqueles no banco de dados. Em alguns casos, o visitante é reconhecido (ele é então identificado implicitamente), em outros casos, não é reconhecido (e, portanto, permanece anônimo).

Para executar essa análise, para o espaço da oferta, marque a **[!UICONTROL Implicitly identify the individual based on their browser history]** opção.

![](assets/identification_anonymous_visitors.png)

## Processamento de visitantes anônimos não identificados {#processing-unidentified-anonymous-visitors}

Após a análise, se um visitante anônimo não for identificado, é possível armazenar seus dados em um determinado espaço. Isso permitirá sugerir ofertas especificamente destinadas a este tipo de visitante, correspondendo às regras específicas da tipologia.

Se não houver elemento que permitam identificar um contato ou se não quiser sugerir uma oferta identificada para um contato que possa ser identificado implicitamente, é possível optar por realizar um fallback em um ambiente anônimo.

Para fazer isso, marque o e, em seguida, especifique o ambiente dedicado a esses visitantes não identificados no **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]****[!UICONTROL Linked anonymous space]** ao especificar um espaço de oferta.

![](assets/anonymous_to_anonymous_environment.png)

