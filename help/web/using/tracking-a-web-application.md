---
product: campaign
title: Rastrear visitas em um aplicativo Web
description: Rastrear visitas em um aplicativo Web
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Web Apps, Reporting, Monitoring
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: ht
source-wordcount: '410'
ht-degree: 100%

---

# Rastrear visitas em um aplicativo Web{#tracking-a-web-application}



O Adobe Campaign permite rastrear e medir visitas em páginas de aplicativos Web inserindo tags de rastreamento. Essa funcionalidade pode ser usada para todos os tipos de aplicativos Web (formulários, páginas da Web etc.).

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

  Além disso, um gráfico de tipo **Setor** mostra a população de acordo com sua origem.

## Identificação da fonte de tráfego {#identifying-the-traffic-source}

Dois modos diferentes podem ser usados para identificar de onde o visitante veio ao acessar um aplicativo web:

1. Enviar uma entrega específica para conceder acesso às páginas do aplicativo web: nesse caso, a fonte de tráfego é essa entrega,
1. Associar a aplicação web a uma fonte de tráfego dedicada: nesse caso, ela deve ser uma entrega de tipo &quot;fonte de tráfego&quot; externo. Ela pode ser selecionada nas propriedades da aplicação web ou no target mapping.

   ![](assets/trackers_6.png)

Para identificar a fonte de tráfego em uma aplicação web, o Adobe Campaign procura as seguintes informações sucessivamente:

1. o identificador de entrega de origem, se existir (cookie nlId),
1. o identificador da entrega externa definido nas propriedades da aplicação web, se existir,
1. o identificador da entrega externa definido no target mapping, se existir.

>[!NOTE]
>
>O rastreamento anônimo só estará disponível se a opção tiver sido ativada no assistente de implantação ao instalar o Campaign.

## Aplicativos Web criados com o Editor de conteúdo digital (DCE) {#web-applications-designed-with-digital-content-editor--dce-}

Quando um aplicativo web é criado usando o editor de conteúdo HTML, o **Digital Content Editor (DCE)**, tags de rastreamento são inseridas a partir da guia **[!UICONTROL Properties]** do editor. Para obter mais informações sobre o Editor de conteúdo digital (DCE), consulte [esta seção](about-campaign-html-editor.md).

![](assets/trackers_2.png)

Ao usar a interface da Web, as tags de rastreamento devem ser inseridas nas propriedades da página.

![](assets/trackers_3.png)

O ícone **[!UICONTROL Display blocks]** permite exibir o número de tags de rastreamento definidas para a página.

![](assets/trackers_4.png)
