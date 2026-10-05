---
product: campaign
title: Sobre cubos
description: Introdução aos cubos
feature: Reporting, Monitoring
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
hide: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 100%
---
# Introdução aos cubos{#about-cubes}



## Terminologia {#terminology}

Os termos específicos do trabalho com cubos estão listados abaixo.

* **Cubo** - Um cubo é uma representação de informações multidimensionais: ele fornece estruturas projetadas para análise interativa de dados aos usuários finais.

* **Tabela/esquema de fato** - A tabela de fatos (ou esquema de fatos) contém os dados brutos ou primários nos quais as análises serão baseadas. Trata-se principalmente de tabelas de grandes volumes (possivelmente com tabelas vinculadas) com cálculos potencialmente longos. Por exemplo, uma tabela de fatos pode ser: a tabela de broadlog, a tabela de compras, etc.

* **Dimensão** - As dimensões permitem segmentar dados em grupos: uma vez criadas, as dimensões atuam como eixos de análise. Na maioria dos casos, para determinada dimensão, vários níveis serão definidos. Por exemplo, para uma dimensão temporal, os níveis serão meses, dias, horas, minutos e etc. Esse conjunto de níveis representa a hierarquia de dimensão e permite vários níveis de análise de dados.

* **Compartimentalização** - Em alguns campos, é possível definir a compartimentalização para agrupar valores e facilitar a leitura das informações. A compartimentalização é aplicada aos níveis. Recomendamos que você defina a compartimentalização quando houver a possibilidade de muitos valores diferentes.

* **Medida** - As medidas mais comuns são soma, média, máximo, mínimo, desvio padrão etc. As medidas podem ser calculadas: por exemplo, a taxa de aceitação de uma oferta é a razão do número de vezes que foi apresentada em comparação ao número de vezes que foi aceita.

## Espaço de trabalho do cubo {#cube-workspace}

Os cubos são armazenados no nó **[!UICONTROL Administration > Configuration > Cubes]**.

![](assets/s_advuser_cube_node.png)

Os principais contextos de uso para cubos são:

* É possível realizar exportações de dados diretamente em um relatório, projetado na guia **[!UICONTROL Reports]** da plataforma do Adobe Campaign.

  Para fazer isso, crie um novo relatório e selecione o cubo que deseja usar.

  ![](assets/cube_create_new.png)

  Os cubos aparecem como modelos baseados em quais relatórios são criados. Depois de escolher um modelo, clique em **[!UICONTROL Create]** para configurar e exibir o relatório correspondente.

  Você pode adaptar medidas, alterar o modo de exibição ou configurar a tabela e exibir o relatório usando o botão principal.

  ![](assets/cube_display_new.png)

* Você também pode fazer referência a um cubo na caixa **[!UICONTROL Query]** de um relatório para usar seus indicadores, conforme mostrado abaixo:

  ![](assets/s_advuser_query_using_a_cube.png)

* Você também pode inserir uma tabela dinâmica com base em um cubo em qualquer página de um relatório. Para fazer isso, faça referência ao cubo a ser usado na guia **[!UICONTROL Data]** da tabela dinâmica na página relacionada.

  ![](assets/s_advuser_cube_in_report.png)

  Para saber mais, consulte [Explorar os dados em um relatório](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
