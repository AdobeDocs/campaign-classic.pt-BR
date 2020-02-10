---
title: Eliminação de duplicação
seo-title: Eliminação de duplicação
description: Eliminação de duplicação
seo-description: null
page-status-flag: never-activated
uuid: 90dee589-ac45-442e-89ef-1c14bb22200d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 83b915bd-7e23-41b5-9f9a-f7eb72026376
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Eliminação de duplicação{#deduplication}

A desduplicação exclui duplicatas dos resultados das atividades de entrada. A desduplicação pode ser executada no endereço de e-mail, número de telefone ou outro campo.

## Práticas recomendadas {#best-practices}

Durante a desduplicação, os fluxos de entrada são processados separadamente. Se por exemplo, o recipient A for encontrado no resultado da query 1, bem como no resultado da query 2, eles não serão desduplicados.

Esse problema precisa ser resolvido da seguinte maneira:

* Crie uma atividade **Union** para unificar cada fluxo de entrada.
* Crie uma atividade **Deduplication** após a atividade **Union**.

![](assets/dedup_bonnepratique.png)

## Configuração {#configuration}

Para configurar uma desduplicação, insira o rótulo, o método e os critérios de desduplicação e as opções referentes ao resultado.

Click the **[!UICONTROL Edit configuration...]** link to define the deduplication mode.

![](assets/s_user_segmentation_dedup_param.png)

1. Seleção do target

   Selecione o tipo de target para esta atividade (por padrão, desduplicação lidam com recipients) e o critério a ser usado, ou seja, o campo para o qual os valores idênticos permitem identificar duplicatas: endereço de e-mail, número de celular ou endereço de mala direta.

   ![](assets/s_user_segmentation_dedup_param2.png)

   In the next step, the **[!UICONTROL Other]** option lets you select the criterion or criteria to be used:

   ![](assets/s_user_segmentation_dedup_param3.png)

1. Métodos de desduplicação

   Na lista suspensa, selecione o método de desduplicação a ser usado e insira o número de duplicatas a serem mantidas.

   ![](assets/s_user_segmentation_dedup_param4.png)

   Os métodos seguintes estão disponíveis:

   * **[!UICONTROL Choose for me]**: seleciona aleatoriamente o registro a ser mantido fora das duplicatas.
   * **[!UICONTROL Following a list of values]**: permite definir uma prioridade de valor para um ou mais campos. Para definir os valores, selecione um campo ou crie uma expressão e adicione o(s) valor(s) à tabela apropriada. To define a new field, click the **[!UICONTROL Add]** button located above the list of values.

      ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**: isso permite manter registros para os quais o valor da expressão selecionada não está vazio como prioridade.

      ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**: permite manter registros com o valor mais baixo (ou mais alto) da expressão.

      ![](assets/s_user_segmentation_dedup_param7.png)
   Click **[!UICONTROL Finish]** to approve the selected deduplication method.

   A seção intermediária da janela resume a configuração definida.

   Na seção inferior da janela do editor de atividades, é possível modificar o rótulo da transição de saída do objeto gráfico e inserir um código de segmento que será associado ao resultado da atividade. Esse código pode ser usado posteriormente como um critério de target.

   ![](assets/s_user_segmentation_dedup_param8.png)

   Check the **[!UICONTROL Generate complement]** option if you wish to exploit the remaining population. O complemento consiste de todas as duplicatas. Uma transição adicional será adicionada à atividade, da seguinte maneira:

   ![](assets/s_user_segmentation_dedup_param9.png)

## Example: Identify the duplicates before a delivery {#example--identify-the-duplicates-before-a-delivery}

No exemplo a seguir, a desduplicação lida com a união entre três queries.

O objetivo do workflow é definir o target de uma delivery excluindo duplicatas para evitar o envio para o mesmo recipient várias vezes.

As duplicatas identificadas também serão integradas em uma lista de duplicatas dedicada que podem ser reutilizadas se necessário.

![](assets/deduplication_example.png)

1. Adicione e vincule as várias atividades necessárias para que o workflow funcione conforme mostrado acima.

   A atividade Union é usada aqui para &quot;unificar&quot; as três queries em uma única transição. Assim, a desduplicação não funcionará para cada query individualmente, mas para toda a query. For more on this subject, refer to [Best practices](#best-practices).

1. Open the deduplication activity then click the **[!UICONTROL Edit configuration...]** link to define the deduplication mode.
1. Na nova janela, selecione **[!UICONTROL Database schema]**.
1. Selecione **Recipientes** como e dimensão do filtro e target.
1. Select the ID field for the **[!UICONTROL Email]** duplicates, to send the delivery only once to every email address, then click **[!UICONTROL Next]**.

   If you wish to base the duplicate IDs on a specific field, select **[!UICONTROL Other]** to access the list of available fields.

1. Escolha manter apenas uma entrada quando o mesmo endereço de e-mail for identificado para vários recipients.
1. Select the **[!UICONTROL Choose for me]** deduplication mode so that the records saved in case of identified duplicates are randomly chosen, then click **[!UICONTROL Finish]**.

Ao executar o workflow, todos os recipients identificados como duplicatas são excluídos do resultado (e, portanto, da delivery) e adicionada à lista de duplicatas. Essa lista pode ser usada novamente em vez de ter que reidentificar as duplicatas.

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o target resultante da desduplicação. **[!UICONTROL tableName]** é o nome da tabela que salva identificadores de metas, **[!UICONTROL schema]** é o esquema da população (normalmente nms:receipt) e **[!UICONTROL recCount]** é o número de elementos na tabela.

A transição associada ao complemento tem os mesmos parâmetros.
