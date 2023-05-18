---
product: campaign
title: Alterar dimensão
description: Alterar dimensão
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '370'
ht-degree: 100%

---

# Alterar dimensão{#change-dimension}



A atividade Change dimension permite alterar o targeting dimension durante o ciclo de construção do target. O deslocamento do eixo depende do template de dados e da dimensão de entrada. Isso permite alternar da dimensão &quot;contratos&quot; para a dimensão &quot;clientes&quot;, por exemplo.

Também é possível usar essa atividade para definir as colunas adicionais do novo target.

É possível definir os critérios de desduplicação de dados.

## Modo de configuração {#configuration-mode}

Para configurar a atividade de alteração de dimensão, aplique as seguintes etapas:

1. Selecione a nova dimensão do target por meio do campo **[!UICONTROL Change dimension]**.

   ![](assets/s_user_change_dimension_param1.png)

1. Durante a mudança de dimensão, é possível manter todos os elementos ou selecioná-los para serem mantidos na saída. No exemplo a seguir, o número máximo de duplicatas é definido como 2.

   ![](assets/s_user_change_dimension_limit.png)

   Quando você escolhe manter apenas um registro, uma coleção é exibida no schema de trabalho: essa coleção representa todos os registros que não serão direcionados ao resultado final (já que apenas um registro é mantido). Como todas as outras coleções, esta é a que permite calcular agregações ou recuperar informações em colunas.

   Por exemplo, se alterar a dimensão **[!UICONTROL Customers]** para a dimensão **[!UICONTROL Recipients]**, será possível selecionar os clientes de uma loja específica, ao mesmo tempo em que adiciona o número de compras feitas.

1. Se optar por não manter todas essas informações, poderá configurar o modo de gerenciamento duplicatas.

   ![](assets/s_user_change_dimension_param2.png)

   As setas azuis permitem definir a prioridade de processamento duplicatas.

   No exemplo acima, os recipient serão desduplicados em seu endereço de e-mail primeiro e, em seguida, em seu número de conta, se necessário.

1. A guia **[!UICONTROL Result]** permite adicionar mais informações.

   Por exemplo, é possível recuperar o município baseado no código postal utilizando uma função do tipo **Substring**. Para fazer isso:

   * Clique no link **[!UICONTROL Add data...]** e selecione **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >Para obter mais informações sobre como criar e gerenciar colunas adicionais, consulte [Adição de dados](query.md#adding-data).

   * Selecione a dimensão do target anterior (antes da troca de eixo) e selecione **[!UICONTROL Zip Code]** na árvore secundária **[!UICONTROL Location]** do recipient e clique em **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * Clique em **[!UICONTROL Advanced selection]** e escolha **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Use as funções oferecidas na lista e especifique o cálculo a ser executado.

      ![](assets/wf_change-dimension_sample_04.png)

   * Finalmente, insira o rótulo da coluna que acabou de criar.

      ![](assets/wf_change-dimension_sample_05.png)

1. Execute o workflow para exibir o resultado dessa configuração. Compare os dados nas tabelas antes e depois da atividade de alteração de dimensão e compare a estrutura das tabelas do workflow, conforme mostrado nos exemplos a seguir:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
