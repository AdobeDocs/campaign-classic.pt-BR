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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Células{#cells}

The **[!UICONTROL Cells]** activity provides a view of the various subsets in the form of data columns. Ela facilita a manipulação de subconjunto e também foi projetada para incentivar as possibilidades de personalização.

![](assets/wf_split_cells.png)

Essa atividade pode ser configurada para inserir parâmetros específicos com base nas necessidades do usuário. By default, the detail of each subset is detailed in a dedicated window via the **[!UICONTROL Selection]** and **[!UICONTROL Advanced]** tabs. In the example below, the form has been modified: a **[!UICONTROL Data]** tab has been added to enable the association of an offer and a priority level for each subset.

![](assets/wf_split_cells_with_customization.png)

For this configuration, the following information was added to the workflow form (in the **[!UICONTROL Administration > Configurations > Input forms]** node of the Adobe Campaign tree):

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
