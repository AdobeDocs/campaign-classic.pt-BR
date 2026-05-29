---
product: campaign
title: Definir um conteúdo condicional
description: Definir um conteúdo condicional
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Reporting, Monitoring
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
TQID: https://experienceleague.adobe.com/LSZh-7Q3HKx0rIWHJRRvMo4q-HWSxrK38QCV7Sz-LT0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 100%

---

# Definir um conteúdo condicional{#defining-a-conditional-content}



É possível documentar a exibição de itens ou páginas de relatório específicos.

Para tornar itens específicos condicionais, adapte suas configurações de visibilidade. Para obter mais informações, consulte [Exibição do item de condição](#conditioning-item-display).

Para exibir uma ou mais páginas condicionais, use uma atividade do tipo **[!UICONTROL Test]**. Para obter mais informações, consulte [Exibição da página de condição](#conditioning-page-display).

## Exibição do item de condição {#conditioning-item-display}

Para exibir parte de um relatório condicional, é preciso definir suas condições de visibilidade: se elas não forem atendidas, os itens não serão exibidos.

As condições de visibilidade podem depender do status do operador, nos itens selecionados ou inseridos na página do relatório.

Exemplos mostrando a exibição condicional de itens em uma página são fornecidos [nesta seção](../../web/using/form-rendering.md#defining-fields-conditional-display).

No exemplo a seguir, a condição de exibição depende do idioma:

![](assets/reporting_display_condition.png)

## Exibição de página de condição {#conditioning-page-display}

No gráfico de um relatório, a atividade **[!UICONTROL Test]** permite alterar a sequência de páginas dependendo de uma ou mais condições.

Essa atividade baseia-se no seguinte princípio operacional:

1. Coloque um **[!UICONTROL Test]** em um gráfico e faça a edição dele.
1. Clique no botão **[!UICONTROL Add]** para criar os vários casos possíveis.

   ![](assets/reporting_test_sample.png)

   Para cada caso, uma transição de saída é adicionada à atividade **[!UICONTROL Test]**.

   ![](assets/reporting_test_transitions.png)

1. Selecione **[!UICONTROL Enable default transition]** para adicionar uma transição, caso uma das condições configuradas não seja atendida.

   Para obter mais informações, consulte [esta seção](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

Uma atividade **[!UICONTROL Test]** pode ser colocada no início do gráfico para condicionar a exibição, dependendo do contexto ou do perfil do operador, por exemplo.
