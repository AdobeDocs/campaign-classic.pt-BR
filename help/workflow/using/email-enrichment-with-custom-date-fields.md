---
title: Enriquecimento de e-mail com campos de data personalizados
description: Saiba como enriquecer emails com campos de data personalizados
page-status-flag: never-activated
uuid: 6dd240b1-f995-4e12-90a5-55aeb584bcdc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9cb3be65-6652-47fa-b8a4-e088530aab4a
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 98%

---


# Enriquecimento de e-mail com campos de data personalizados{#email-enrichment-with-custom-date-fields}

Neste exemplo, queremos enviar um e-mail com campos de dados personalizados para os recipients que celebram seus aniversários nesse mês. O e-mail incluirá um cupom válido por uma semana antes e depois de seus aniversários.

Precisamos direcionar os recipients de uma lista que celebram os aniversariantes deste mês com uma atividade **[!UICONTROL Split]**. Em seguida, usando a atividade **[!UICONTROL Enrichment]**, o campo de dados personalizado atuará como as datas de validade no email para a oferta especial do cliente.

![](assets/uc_enrichment.png)

Para criar este exemplo, aplique as seguintes etapas:

1. Na guia **[!UICONTROL Targeting and workflows]** da campanha, arraste e solte uma atividade **[!UICONTROL Read list]** para direcionar a lista de recipients.
1. A lista a ser processada pode ser especificada explicitamente, calculada por um script ou localizada dinamicamente, de acordo com as opções selecionadas e parâmetros definidos aqui.

   ![](assets/uc_enrichment_1.png)

1. Adicione uma atividade **[!UICONTROL Split]** para diferenciar os recipients que farão aniversário neste mês dos outros recipients.
1. Para dividir a lista, na categoria **[!UICONTROL Filtering of selected records]**, selecione **[!UICONTROL Add a filtering condition on the inbound population]**. Em seguida, clique em **[!UICONTROL Edit]**.

   ![](assets/uc_enrichment_2.png)

1. Selecione **[!UICONTROL Filtering conditions]** e clique no botão **[!UICONTROL Edit expression]** para filtrar o mês de aniversário do recipient.

   ![](assets/uc_enrichment_3.png)

1. Clique em **[!UICONTROL Advanced Selection]**, em **[!UICONTROL Edit the formula using an expression]** e adicione a seguinte expressão: Month(@birthDate).
1. Na coluna **[!UICONTROL Operator]**, selecione **[!UICONTROL equal to]**.
1. Filtre ainda mais sua condição, adicionando o mês **[!UICONTROL Value]** da data atual: Month(GetDate()).

   Isso consultará os recipients cujo mês de aniversário corresponde ao mês atual.

   ![](assets/uc_enrichment_4.png)

1. Clique em **[!UICONTROL Finish]**. Em seguida, na guia **[!UICONTROL General]** da sua atividade **[!UICONTROL Split]**, clique em **[!UICONTROL Generate complement]**, na categoria **[!UICONTROL Results]**.

   Com o resultado **[!UICONTROL Complement]**, é possível adicionar uma atividade de delivery ou atualizar uma lista. Aqui, adicionamos uma atividade **[!UICONTROL End]**.

   ![](assets/uc_enrichment_6.png)

Agora, é necessário configurar a atividade **[!UICONTROL Enrichment]**:

1. Adicione uma atividade **[!UICONTROL Enrichment]** depois do subconjunto para adicionar campos de data personalizados.

   ![](assets/uc_enrichment_7.png)

1. Abra a atividade **[!UICONTROL Enrichment]**. Na categoria **[!UICONTROL Complementary information]**, clique em **[!UICONTROL Add data]**.

   ![](assets/uc_enrichment_8.png)

1. Selecione **[!UICONTROL Data linked to the filtering dimension]** e, em seguida, **[!UICONTROL Data of the filtering dimension]**.
1. Clique no botão **[!UICONTROL Add]**.

   ![](assets/uc_enrichment_9.png)

1. Adicione um **[!UICONTROL Label]**. Em seguida, na coluna **[!UICONTROL Expression]**, clique em **[!UICONTROL Edit expression]**.

   ![](assets/uc_enrichment_10.png)

1. Primeiro, precisamos direcionar a semana antes da data de nascimento como a **Validity start date** com a seguinte **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Depois, para criar o campo personalizado **Validity end date** que direciona a semana após a data de nascimento, é necessário adicionar a **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`.

   É possível adicionar um rótulo à expressão.

   ![](assets/uc_enrichment_12.png)

1. Clique em **[!UICONTROL Ok]**. Agora o enriquecimento está pronto.

Após a atividade **[!UICONTROL Enrichment]**, você pode adicionar um delivery. Nesse caso, adicionamos um delivery de email para enviar uma oferta especial com datas de validade para celebrar os aniversários dos clientes no mês atual.

1. Arraste e solte uma atividade **[!UICONTROL Email delivery]** após a atividade **[!UICONTROL Enrichment]**.

   ![](assets/uc_enrichment_15.png)

1. Clique duas vezes na atividade **[!UICONTROL Email delivery]** para começar a personalizar o delivery.
1. Adicione um **[!UICONTROL Label]** ao delivery e clique em **[!UICONTROL Continue]**.
1. Clique em **[!UICONTROL Save]** para criar o delivery de email.
1. Verifique na **[!UICONTROL Approval]** guia do delivery de e-mail **[!UICONTROL Properties]** se a opção **[!UICONTROL Confirm delivery before sending option]** está marcada.

   Em seguida, inicie o workflow para enriquecer a transição de saída com as informações de direcionamento.

   ![](assets/uc_enrichment_18.png)

Agora é possível começar a projetar o delivery de email com os campos de data personalizados criados na atividade **[!UICONTROL Enrichment]**.

1. Clique duas vezes na atividade **[!UICONTROL Email delivery]**.
1. Adicione suas extensões do target ao email. Elas devem estar dentro da seguinte expressão para configurar o formato de suas datas de validade:

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Clique em ![](assets/uc_enrichment_16.png) . Selecione **[!UICONTROL Target extension]** e então as datas de validade personalizadas criadas anteriormente com a atividade **[!UICONTROL Enrichment]** para adicionar a extensão à expressão formatDate.

   ![](assets/uc_enrichment_19.png)

1. Configure seu conteúdo de e-mail conforme necessário.

   ![](assets/uc_enrichment_17.png)

1. Visualize seu e-mail para verificar se os campos de data personalizados foram corretamente configurados.

   ![](assets/uc_enrichment_20.png)

Seu e-mail está pronto. É possível começar a enviar as provas e confirmar o delivery para enviar os e-mails de aniversário.
