---
product: campaign
title: Execução de computação agregada
description: Saiba como executar a computação agregada em consultas
feature: Workflows
hide: true
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
TQID: https://experienceleague.adobe.com/hr3jxs4JCrcPXdGBGN8I9edBG4FIg1AakOmWaN-Zplk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 231
ht-degree: 98%

---

# Execução de computação agregada {#performing-aggregate-computing}



Neste exemplo, devemos contar o número de destinatários que vivem em Londres, de acordo com o gênero.

* Qual tabela precisa ser selecionada?

  A tabela de destinatários (**nms:recipient**)

* Quais campos devem ser selecionados na coluna de saída?

  Primary key (with count) e Gender

* Quais condições são usadas para filtrar as informações?

  Com base nos destinatários que vivem em Londres.

Para criar este exemplo, aplique as seguintes etapas:

1. Em **[!UICONTROL Data to extract]**, defina uma contagem para a chave primária (como mostrado no exemplo anterior). Adicione o campo **[!UICONTROL Gender]** na coluna de saída. Marque a opção **[!UICONTROL Group]** na coluna **[!UICONTROL Gender]**. Dessa forma, os destinatários serão agrupados por gênero.

   ![](assets/query_editor_nveau_27.png)

1. Na janela **[!UICONTROL Sorting]**, clique em **[!UICONTROL Next]**: nenhuma classificação é necessária aqui.
1. Configure o filtro de dados. Aqui, é possível restringir a seleção aos contatos que vivem em Londres.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Os valores diferenciam maiúsculas de minúsculas. Se o valor &quot;Londres&quot; é inserido na condição sem uma letra maiúscula e a lista de destinatários contiver a palavra &quot;Londres&quot; com uma letra maiúscula, então a consulta falha.

1. Na janela **[!UICONTROL Data formatting]**, clique em **[!UICONTROL Next]**: nenhuma formatação é necessária para este exemplo.
1. Na janela de pré-visualização, clique em **[!UICONTROL Launch data preview]**.

   Há três valores separados para cada tipo por gênero: **2** para feminino, **1** para masculino e **0** quando o sexo é desconhecido. Neste exemplo, a lista contém 10 mulheres, 16 homens e 2 pessoas cujo gênero não é conhecido.

   ![](assets/query_editor_agregat_04.png)
