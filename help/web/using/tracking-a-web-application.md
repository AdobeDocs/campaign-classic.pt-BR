---
title: Rastreamento de uma aplicação web
seo-title: Rastreamento de uma aplicação web
description: Rastreamento de uma aplicação web
seo-description: null
page-status-flag: never-activated
uuid: c087b40c-fd14-440f-8f38-33f5f68120a9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 8e52f927-dadd-44c8-a51d-f717bc083eef
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# Rastreamento de aplicação 
                        web{#tracking-a-web-application}

O Adobe Campaign permite que você rastreie e avalie visitas em páginas de aplicativos da Web inserindo tags de rastreamento. Essa funcionalidade pode ser usada para todos os tipos de aplicações web (formulários, pesquisas online, páginas da Web criadas usando o DCE, etc.).

Assim, você pode definir vários caminhos de navegação e avaliar seu sucesso. Os dados recuperados estão disponíveis nos relatórios de cada aplicativo.

As principais melhorias apresentadas nessa versão são as seguintes:

* Possibilidade de inserir várias tags de controle na mesma página para facilitar a definição dos caminhos de navegação (por exemplo, compra, subscrição, retorno, etc.).
* Visualizar caminhos de navegação e tags de rastreamento das diferentes páginas no painel de aplicações web.

   ![](assets/trackers_1.png)

* Gerar um relatório de rastreamento completo.

   ![](assets/trackers_5.png)

   Os principais indicadores são os seguintes:

   * **Taxa** de conversão: número de pessoas que exibiram todas as etapas de um caminho de navegação.
   * **Taxa** de rejeição: número de pessoas que exibiram apenas o primeiro passo
   * **Túnel** de conversão: taxa de perda entre cada etapa.
   In addition, a **Sector** type chart shows the population according to its source.

## Identificação da fonte de tráfego {#identifying-the-traffic-source}

Dois modos diferentes podem ser usados para identificar de onde o visitante veio ao acessar um aplicativo da Web:

1. Envio de uma entrega específica para conceder acesso às páginas da aplicação Web: nesse caso, a fonte de tráfego é essa entrega,
1. Associando o aplicativo Web a uma fonte de tráfego dedicada: nesse caso, deve ser uma entrega externa do tipo &#39;fonte de tráfego&#39;. Ela pode ser selecionada nas propriedades da aplicação web ou no target mapping.

   ![](assets/trackers_6.png)

Para identificar a fonte de tráfego em uma aplicação web, o Adobe Campaign procura as seguintes informações sucessivamente:

1. o identificador de delivery de origem, se existir (cookie nlId),
1. o identificador do delivery externo definido nas propriedades da aplicação web, se existir,
1. o identificador do delivery externo definido no target mapping, se existir.

>[!NOTE]
>
>Lembre-se de que o tracking anônimo só é possível se a opção correspondente tiver sido ativada no assistente de implantação.
>
>For more on this, refer to the [Installation guide](../../installation/using/deploying-an-instance.md).

## Aplicações web criadas com o Editor de conteúdo digital (DCE) {#web-applications-designed-with-digital-content-editor--dce-}

When a Web application is created using the HTML content editor - **Digital Content Editor (DCE)** - tracking tags are inserted from the **[!UICONTROL Properties]** tab of the editor. Para obter mais informações sobre o Editor de conteúdo digital (DCE), consulte [esta seção](../../web/using/about-campaign-html-editor.md).

![](assets/trackers_2.png)

Ao usar a interface da Web, as tags de rastreamento devem ser inseridas nas propriedades da página.

![](assets/trackers_3.png)

The **[!UICONTROL Display blocks]** icon lets you view the number of tracking tags defined for the page.

![](assets/trackers_4.png)

