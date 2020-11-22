---
solution: Campaign Classic
product: campaign
title: Rastreamento de uma aplicação web
description: Rastreamento de uma aplicação web
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 100%

---


# Rastreamento de uma aplicação web{#tracking-a-web-application}

O Adobe Campaign permite rastrear e medir visitas em páginas de aplicativos web inserindo tags de rastreamento. Essa funcionalidade pode ser usada para todos os tipos de aplicações web (formulários, pesquisas online, páginas da Web criadas usando o DCE, etc.).

Assim, você pode definir vários caminhos de navegação e avaliar seu sucesso. Os dados recuperados estão disponíveis nos relatórios de cada aplicativo.

As principais melhorias apresentadas nessa versão são as seguintes:

* Possibilidade de inserir várias tags de controle na mesma página para facilitar a definição dos caminhos de navegação (por exemplo, compra, subscrição, retorno, etc.).
* Visualizar caminhos de navegação e tags de rastreamento das diferentes páginas no painel de aplicações web.

   ![](assets/trackers_1.png)

* Gerar um relatório de rastreamento completo.

   ![](assets/trackers_5.png)

   Os principais indicadores são os seguintes:

   * **Conversion rate**: número de pessoas que exibiram todas as etapas de um caminho de navegação.
   * **Bounce rate**: número de pessoas que exibiram apenas a primeira etapa
   * **Conversion tunnel**: taxa de perda entre cada etapa.

   Além disso, um gráfico de tipo **Sector** mostra a população de acordo com sua origem.

## Identificação da fonte de tráfego {#identifying-the-traffic-source}

Dois modos diferentes podem ser usados para identificar de onde o visitante veio ao acessar um aplicativo web:

1. Enviar um delivery específico para conceder acesso às páginas do aplicativo web: nesse caso, a fonte de tráfego é esse delivery,
1. Associar a aplicação web a uma fonte de tráfego dedicada: nesse caso, ela deve ser um delivery de tipo &quot;fonte de tráfego&quot; externo. Ela pode ser selecionada nas propriedades da aplicação web ou no target mapping.

   ![](assets/trackers_6.png)

Para identificar a fonte de tráfego em uma aplicação web, o Adobe Campaign procura as seguintes informações sucessivamente:

1. o identificador de delivery de origem, se existir (cookie nlId),
1. o identificador do delivery externo definido nas propriedades da aplicação web, se existir,
1. o identificador do delivery externo definido no target mapping, se existir.

>[!NOTE]
>
>Lembre-se de que o tracking anônimo só é possível se a opção correspondente tiver sido ativada no assistente de implantação.
>
>Para obter mais informações, consulte o [Guia de instalação](../../installation/using/deploying-an-instance.md).

## Aplicações web criadas com o Editor de conteúdo digital (DCE) {#web-applications-designed-with-digital-content-editor--dce-}

Quando um aplicativo web é criado usando o editor de conteúdo HTML, o **Digital Content Editor (DCE)**, tags de rastreamento são inseridas a partir da guia **[!UICONTROL Properties]** do editor. Para obter mais informações sobre o Editor de conteúdo digital (DCE), consulte [esta seção](../../web/using/about-campaign-html-editor.md).

![](assets/trackers_2.png)

Ao usar a interface da Web, as tags de rastreamento devem ser inseridas nas propriedades da página.

![](assets/trackers_3.png)

O ícone **[!UICONTROL Display blocks]** permite exibir o número de tags de rastreamento definidas para a página.

![](assets/trackers_4.png)

