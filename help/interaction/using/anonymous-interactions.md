---
product: campaign
title: Interações anônimas
description: Interações anônimas
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: ht
source-wordcount: '407'
ht-degree: 100%

---

# Interações anônimas{#anonymous-interactions}



![](assets/do-not-localize/how-to-video.png) Assista a este [vídeo](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) para obter uma visão geral de como as ofertas são entregues para alvos identificados e anônimos.

## Direcionamento e armazenamento de um ambiente para interações anônimas {#targeting-and-storing-an-environment-for-anonymous-interactions}

Por padrão, o Interaction vem com um ambiente pré-configurado para direcionar a tabela de destinatários (ofertas identificadas). Se quiser direcionar outra tabela (tabela de visitantes para ofertas anônimas ou uma tabela de destinatários específica), é necessário usar o assistente de target mapping para criar o ambiente. Para obter mais informações, consulte [Criação de um ambiente de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

Ao criar um ambiente anônimo por meio do assistente de criação de mapeamento, a caixa **[!UICONTROL Environment dedicated to incoming anonymous interactions]** é automaticamente marcada na guia **[!UICONTROL General]** do ambiente.

O **[!UICONTROL Targeting dimension]** é automaticamente concluído. Por padrão, ele vincula à tabela do visitante.

O campo **[!UICONTROL Visitor folder]** é exibido. Ele é automaticamente preenchido para vincular à pasta **[!UICONTROL Visitors]**. Este campo permite escolher onde armazenar os perfis de visitantes.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Para filtrar vários tipos de visitantes, por exemplo, no caso de ofertas anônimas apresentadas para uma ou mais marcas, é necessário criar um ambiente para cada marca e uma pasta do tipo **[!UICONTROL Visitors]** para cada ambiente.

## Catálogo de ofertas para interações anônimas {#offer-catalog-for-anonymous-interactions}

Assim como as interações de saída, as interações de entrada são organizadas em um catálogo de ofertas que é composto por categorias e ofertas.

Para criar categorias e espaços, aplique o mesmo processo que os visitantes identificados (consulte [Criação categorias de ofertas](../../interaction/using/creating-offer-categories.md) e [Criação de um ambiente de ofertas)](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

## Visitantes anônimos {#anonymous-visitors}

Os visitantes anônimos podem ser submetidos a um processo de identificação por cookies quando se conectam. Esse reconhecimento implícito baseia-se no histórico do navegador do visitante.

Durante essa etapa, uma comparação é feita entre os dados recuperados pelos cookies e aqueles no banco de dados. Em alguns casos, os visitantes são reconhecidos (são então identificados implicitamente), em outros casos, eles não são reconhecidos (e, portanto, permanecem anônimos).

Para executar essa análise, para o espaço de ofertas, marque a opção **[!UICONTROL Implicitly identify the individual based on their browser history]**.

![](assets/identification_anonymous_visitors.png)

## Processamento de visitantes anônimos não identificados {#processing-unidentified-anonymous-visitors}

Após a análise, se um visitante anônimo não for identificado, é possível armazenar seus dados em um determinado espaço. Isso permitirá sugerir ofertas especificamente destinadas a este tipo de visitante, correspondendo às regras específicas da tipologia.

Se não houver elemento que permitam identificar um contato ou se não quiser sugerir uma oferta identificada para um contato que possa ser identificado implicitamente, é possível optar por realizar um fallback em um ambiente anônimo.

Para fazer isso, marque a opção **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** e, em seguida, especifique o ambiente dedicado para esses visitantes não identificados em **[!UICONTROL Linked anonymous space]** quando especificar um espaço de oferta.

![](assets/anonymous_to_anonymous_environment.png)
