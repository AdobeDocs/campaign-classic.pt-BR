---
product: campaign
title: Execução de computação agregada
description: Saiba como executar a computação agregada em consultas
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '225'
ht-degree: 100%

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

1. Em **[!UICONTROL Data to extract]**, defina uma contagem para a chave primária (como mostrado no exemplo anterior). Adicione o campo **[!UICONTROL Gender]** na coluna de saída. Marque a opção **[!UICONTROL Group]** na coluna **[!UICONTROL Gender]**. Dessa forma, os recipients serão agrupados por sexo.

   ![](assets/query_editor_nveau_27.png)

1. Na janela **[!UICONTROL Sorting]**, clique em **[!UICONTROL Next]**: nenhuma classificação é necessária aqui.
1. Configure o filtro de dados. Aqui, é possível restringir a seleção aos contatos que vivem em Londres.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Os valores diferenciam maiúsculas de minúsculas. Se o valor &quot;Londres&quot; é inserido na condição sem uma letra maiúscula e a lista de recipients contiver a palavra &quot;Londres&quot; com uma letra maiúscula, então a query falha.

1. Na janela **[!UICONTROL Data formatting]**, clique em **[!UICONTROL Next]**: nenhuma formatação é necessária para este exemplo.
1. Na janela de pré-visualização, clique em **[!UICONTROL Launch data preview]**.

   Há três valores separados para cada tipo por gênero: **2** para feminino, **1** para masculino e **0** quando o sexo é desconhecido. Neste exemplo, a lista contém 10 mulheres, 16 homens e 2 pessoas cujo gênero não é conhecido.

   ![](assets/query_editor_agregat_04.png)
