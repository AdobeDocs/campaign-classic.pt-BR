---
product: campaign
title: Criação de templates de importação e exportação
description: Saiba como criar templates de importação e exportação no Campaign
feature: Templates
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1180e664-5ead-4d5d-b1c3-6fe397c1f3a2
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '139'
ht-degree: 100%

---

# Criar templates de importação e exportação {#creating-import-export-templates}



Os modelos de importação e exportação são armazenados no diretório **[!UICONTROL Resources > Templates > Job templates]** da árvore do Adobe Campaign.

Por padrão, três modelos de importação e um modelo de exportação estão presentes nesse diretório. Eles não devem ser modificados.

* O modelo nativo **[!UICONTROL Import denylist]** já está configurado para importar uma lista de endereços de email que foram adicionados à lista de bloqueios.

* Os templates **[!UICONTROL New text import]** e **[!UICONTROL New text export]** permitem configurar uma importação ou exportação do zero.

![](assets/s_ncs_user_export_wizard_template_create.png)

É possível duplicar modelos existentes para criar os próprios modelos ou criar um novo por meio do menu **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**.

O processo para configurar um modelo é o mesmo apresentado nestas seções:

* [Configurar um trabalho de importação](../../platform/using/executing-import-jobs.md)
* [Configurar um trabalho de exportação](../../platform/using/executing-export-jobs.md)
