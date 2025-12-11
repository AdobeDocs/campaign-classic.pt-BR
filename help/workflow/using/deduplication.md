---
product: campaign
title: Desduplicação
description: Saiba mais sobre a atividade de fluxo de trabalho de desduplicação
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: 38add4fe-6238-45de-863e-895ebca189b7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: ht
source-wordcount: '1114'
ht-degree: 100%

---

# Desduplicação{#deduplication}



A desduplicação exclui duplicados dos resultados das atividades de entrada. A desduplicação pode ser executada no endereço de e-mail, número de telefone ou outro campo.

A atividade **[!UICONTROL Deduplication]** é usada para remover linhas duplicadas de um conjunto de dados. Por exemplo, os registros abaixo podem ser considerados duplicados, pois têm o mesmo endereço de email e o mesmo celular e/ou telefone residencial.

| Data da última modificação | Nome | Sobrenome | Email | Telefone celular | Telefone |
|-----|------------|-----------|-------|--------------|------|
| 03/02/2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |
| 19/05/2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 22/07/2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

A atividade **[!UICONTROL Deduplication]** tem a capacidade de manter uma linha inteira como o registro exclusivo após a identificação de duplicados. Por exemplo, no caso de uso acima, se a atividade estiver configurada para manter somente o registro com o **[!UICONTROL Date]** mais antigo, o resultado será:

| Data | Nome | Sobrenome | Email | Telefone celular | Telefone |
|-----|----------|------------|-------|--------------|------|
| 03/02/2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

O registro principal selecionado transportará os dados sem mesclar os dados de campo com outros dados relevantes nas linhas duplicadas.

Complemento:

| Data | Nome | Sobrenome | Email | Telefone celular | Telefone |
|-----|------------|-----------|-------|--------------|------|
| 19/05/2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 22/07/2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

## Práticas recomendadas {#best-practices}

Durante a desduplicação, os fluxos de entrada são processados separadamente. Se por exemplo, o destinatário A for encontrado no resultado da query 1, bem como no resultado da query 2, eles não serão desduplicados.

Esse problema precisa ser resolvido da seguinte maneira:

* Crie uma atividade **União** para unificar cada fluxo de entrada.
* Crie uma atividade **Desduplicação** após a atividade **União**.

![](assets/dedup_bonnepratique.png)

## Configuração {#configuration}

Para configurar uma desduplicação, insira o rótulo, o método e os critérios de desduplicação e as opções referentes ao resultado.

1. Clique no link **[!UICONTROL Edit configuration...]** para definir o modo de desduplicação.

   ![](assets/s_user_segmentation_dedup_param.png)

1. Selecione o tipo de target para essa atividade (por padrão, a desduplicação está vinculada aos destinatários) e o critério a ser usado, isto é, o campo cujos valores idênticos permitem identificar duplicados.

   >[!NOTE]
   >
   >Se os dados externos estiverem sendo usados como entrada, por exemplo, de um arquivo externo, selecione a opção **[!UICONTROL Temporary schema]**.
   >
   >Na próxima etapa, a opção **[!UICONTROL Other]** permite selecionar o critério ou os critérios a serem usados:

   ![](assets/s_user_segmentation_dedup_param2.png)

1. Na próxima etapa, a opção **[!UICONTROL Other]** permite selecionar o critério ou os critérios a serem usados em caso de valores idênticos.

   ![](assets/s_user_segmentation_dedup_param3.png)

1. Na lista suspensa, selecione o método de desduplicação a ser usado e insira o número de duplicados a serem mantidos.

   ![](assets/s_user_segmentation_dedup_param4.png)

   Os métodos seguintes estão disponíveis:

   * **[!UICONTROL Choose for me]**: seleciona aleatoriamente o registro que será mantido fora dos duplicados.
   * **[!UICONTROL Following a list of values]**: permite definir uma prioridade de valor para um ou mais campos. Para definir os valores, selecione um campo ou crie uma expressão e adicione o(s) valor(es) à tabela apropriada. Para definir um novo campo, clique no botão **[!UICONTROL Add]** localizado acima da lista de valores.

     ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**: permite manter registros para os quais o valor da expressão selecionada não está vazio como uma prioridade.

     ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**: permite manter registros com o valor mais baixo (ou mais alto) da expressão fornecida.

     ![](assets/s_user_segmentation_dedup_param7.png)

   >[!NOTE]
   >
   >A funcionalidade **[!UICONTROL Merge]**, acessível por meio do link **[!UICONTROL Advanced parameters]**, permite configurar um conjunto de regras para mesclar um campo ou grupo de campos em um único registro de dados resultante. Para obter mais informações, consulte [Mesclar campos em um único registro](#merging-fields-into-single-record).

1. Clique em **[!UICONTROL Finish]** para aprovar o método de desduplicação selecionado.

   A seção intermediária da janela resume a configuração definida.

   Na seção inferior da janela do editor de atividades, é possível modificar o rótulo da transição de saída do objeto gráfico e inserir um código de segmento que será associado ao resultado da atividade. Esse código pode ser usado posteriormente como um critério de direcionamento.

   ![](assets/s_user_segmentation_dedup_param8.png)

1. Marque a opção **[!UICONTROL Generate complement]** se desejar explorar a população restante. O complemento consiste de todos os duplicados. Uma transição adicional será adicionada à atividade, da seguinte maneira:

   ![](assets/s_user_segmentation_dedup_param9.png)

## Exemplo: identificar os duplicados antes de uma entrega {#example--identify-the-duplicates-before-a-delivery}

No exemplo a seguir, a desduplicação lida com a união entre três queries.

O objetivo do fluxo de trabalho é definir o target de uma entrega excluindo duplicados para evitar o envio para o mesmo destinatário várias vezes.

Os duplicados identificados também serão integrados em uma lista de duplicados dedicada que podem ser reutilizados se necessário.

![](assets/deduplication_example.png)

1. Adicione e vincule as várias atividades necessárias para que o fluxo de trabalho funcione conforme mostrado acima.

   A atividade União é usada aqui para &quot;unificar&quot; as três consultas em uma única transição. Assim, a desduplicação não funcionará para cada query individualmente, mas para toda a query. Para obter mais informações sobre este assunto, consulte [Melhores práticas](#best-practices).

1. Abra a atividade de desduplicação e clique no link **[!UICONTROL Edit configuration...]** para definir o modo de desduplicação.
1. Na nova janela, selecione **[!UICONTROL Database schema]**.
1. Selecione **Recipients** como dimensões de filtragem e direcionamento.
1. Selecione o campo de ID para os duplicados de **[!UICONTROL Email]** a fim de enviar a entrega somente uma vez para cada endereço de email, depois clique em **[!UICONTROL Next]**. 

   Se desejar basear as IDs duplicadas em um campo específico, selecione **[!UICONTROL Other]** para acessar a lista de campos disponíveis.

1. Escolha manter apenas uma entrada quando o mesmo endereço de email for identificado para vários destinatários.
1. Selecione o modo de desduplicação **[!UICONTROL Choose for me]** para que os registros salvos no caso de duplicados identificados sejam escolhidos aleatoriamente, depois clique em **[!UICONTROL Finish]**.

Ao executar o fluxo de trabalho, todos os destinatários identificados como duplicados são excluídos do resultado (e, portanto, da entrega) e adicionada à lista de duplicados. Essa lista pode ser usada novamente em vez de ter que tornar a identificar os duplicados.

## Mesclar campos em um único registro de dados {#merging-fields-into-single-record}

A funcionalidade **[!UICONTROL Merge]** permite configurar um conjunto de regras para que a desduplicação defina um campo ou grupo de campos a serem mesclados em um único registro de dados resultante.

Por exemplo, com um conjunto de registros duplicados, você pode optar por manter o número de telefone mais antigo ou o nome mais recente.

Um caso de uso que utiliza esse recurso está disponível [nesta seção](deduplication-merge.md).

Para fazer isso, siga estes passos:

1. Na etapa de seleção **[!UICONTROL Deduplication method]**, clique no link **[!UICONTROL Advanced Parameters]**.

   ![](assets/dedup1.png)

1. Selecione a opção **[!UICONTROL Merge records]** para ativar a funcionalidade.

   Se desejar agrupar vários campos de dados em cada condição de mesclagem, ative a opção **[!UICONTROL Use several record merging criteria]**.

   ![](assets/dedup2.png)

1. Depois de ativar a funcionalidade, uma guia **[!UICONTROL Merge]** é adicionada à atividade **[!UICONTROL Deduplication]**. Isso permite que você defina grupos de campos a serem mesclados e suas regras associadas.

   Para obter mais informações, consulte o caso de uso detalhado disponível [nesta seção](deduplication-merge.md).

   ![](assets/dedup3.png)

## Parâmetros de entrada {#input-parameters}

* tableName
* esquema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

## Parâmetros de saída {#output-parameters}

* tableName
* esquema
* recCount

Esse conjunto de três valores identifica o target resultante da desduplicação. **[!UICONTROL tableName]** é o nome da tabela que salva os identificadores de destino, **[!UICONTROL schema]**&#x200B;é o schema da população (geralmente nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.

A transição associada ao complemento tem os mesmos parâmetros.
