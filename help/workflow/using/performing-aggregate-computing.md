---
title: Execução de computação agregada
description: Saiba como executar a computação agregada em consultas
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 86%

---


# Execução de computação agregada {#performing-aggregate-computing}

Neste exemplo, devemos contar o número de recipients que vivem em Londres, de acordo com o sexo.

* Qual tabela precisa ser selecionada?

   A tabela de recipient (**nms:recipient**)

* Quais campos devem ser selecionados na coluna de saída?

   Primary key (with count) e Gender

* Quais condições são usadas para filtrar as informações?

   Com base nos recipients que vivem em Londres.

Para criar este exemplo, aplique as seguintes etapas:

1. Em **[!UICONTROL Data to extract]**, defina uma contagem para a chave primária (como mostrado no exemplo anterior). Adicione o campo **[!UICONTROL Gender]** na coluna de saída. Marque a opção **[!UICONTROL Group]** na **[!UICONTROL Gender]** coluna. Dessa forma, os recipients serão agrupados por sexo.

   ![](assets/query_editor_nveau_27.png)

1. In the **[!UICONTROL Sorting]** window, click **[!UICONTROL Next]**: no sorting is necessary here.
1. Configure o filtro de dados. Aqui, é possível restringir a seleção aos contatos que vivem em Londres.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Os valores diferenciam maiúsculas de minúsculas. Se o valor &quot;Londres&quot; é inserido na condição sem uma letra maiúscula e a lista de recipients contiver a palavra &quot;Londres&quot; com uma letra maiúscula, então a query falha.

1. In the **[!UICONTROL Data formatting]** window, click **[!UICONTROL Next]**: no formatting is required for this example.
1. In the preview window, click **[!UICONTROL Launch data preview]**.

   Há três valores separados para cada tipo por gênero: **2** para feminino, **1** para masculino e **0** quando o sexo é desconhecido. Neste exemplo, a lista contém 10 mulheres, 16 homens e 2 pessoas cujo gênero não é conhecido.

   ![](assets/query_editor_agregat_04.png)
