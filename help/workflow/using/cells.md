---
title: Células
seo-title: Células
description: Células
seo-description: null
page-status-flag: never-activated
uuid: 1b18928f-04e1-4268-ab8e-ff74d78599de
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: f7187d42-56e9-4681-b172-22abd43ecd29
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '128'
ht-degree: 100%

---


# Células{#cells}

A atividade **[!UICONTROL Cells]** fornece uma visualização dos vários subconjuntos de colunas de dados. Ela facilita a manipulação de subconjunto e também foi projetada para incentivar as possibilidades de personalização.

![](assets/wf_split_cells.png)

Essa atividade pode ser configurada para inserir parâmetros específicos com base nas necessidades do usuário. Por padrão, os detalhes de cada subconjunto são detalhados em uma janela dedicada por meio das guias **[!UICONTROL Selection]** e **[!UICONTROL Advanced]**. No exemplo abaixo, o formulário foi modificado: uma guia **[!UICONTROL Data]** foi adicionada para habilitar a associação de uma oferta e um nível de prioridade para cada subconjunto.

![](assets/wf_split_cells_with_customization.png)

Para essa configuração, as seguintes informações foram adicionadas ao formulário do fluxo de trabalho (no nó **[!UICONTROL Administration > Configurations > Input forms]** da árvore do Adobe Campaign):

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

A personalização do formulário de entrada no Adobe Campaign é reservada para usuários especialistas. Para obter mais informações, consulte esta [seção](../../configuration/using/identifying-a-form.md).
