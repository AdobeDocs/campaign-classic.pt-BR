---
product: campaign
title: Inserir código de barras em um email
description: Inserir código de barras em um email
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 100%

---


# Inserir código de barras em um email{#insert-a-barcode-in-an-email}

![](../../assets/common.svg)

O módulo de geração de código de barras permite criar vários tipos de códigos de barras que estão em conformidade com muitos padrões comuns, incluindo códigos de barras 2D.

É possível gerar um código de barras de forma dinâmica como um bitmap usando um valor definido por meio de critérios do cliente. Os códigos de barra personalizados podem ser incluídos em campanhas de email. O recipient pode imprimir a mensagem e mostrá-la à empresa emissora para exame (ao verificar, por exemplo).

Para inserir um código de barras em um email, coloque o cursor no conteúdo onde deseja exibi-lo e clique no botão de personalização. Selecione **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Em seguida, configure os seguintes elementos para atender às suas necessidades:

1. Selecione o tipo de código de barras.

   * Para o formato 1D, os seguintes tipos estão disponíveis no Adobe Campaign: Codabar, Code 128, GS1-128 (antigo EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 de 5, POSTNET e Royal Mail (RM4SCC).

      Exemplo de um código de barras 1D:

      ![](assets/barcode_insert_08.png)

   * Os tipos DataMatrix e PDF417 correspondem ao formato 2D.

      Exemplo de um código de barras 2D:

      ![](assets/barcode_insert_09.png)

   * Para inserir um código QR, selecione esse tipo e digite a taxa de correção de erro a ser aplicada. Essa taxa define a quantidade de informações repetidas e a tolerância à deterioração.

      ![](assets/barcode_insert_06.png)

      Exemplo de código QR:

      ![](assets/barcode_insert_12.png)

1. Insira o tamanho do código de barras que deseja inserir no email: a configuração da escala permite aumentar ou reduzir o tamanho do código de barras, de x1 a x10.
1. O campo **[!UICONTROL Value]** permite definir o valor do código de barras. Um valor pode corresponder a uma oferta especial e pode ser a função de um critério, ele pode ser o valor de um campo de banco de dados vinculado aos clientes.

   Este exemplo mostra um código de barras do tipo EAN-8, ao qual foi adicionado o número da conta de um recipient. Para adicionar esse número de conta, clique no botão de personalização à direita do campo **[!UICONTROL Value]** e selecione **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. O campo **[!UICONTROL Height]** permite configurar a altura do código de barras sem alterar sua largura, alterando a quantidade do espaço entre cada barra.

   Não há controle de entrada restritivo dependendo do tipo de código de barras. Se um valor de código de barras estiver incorreto, ele só será visível no modo de **Pré-visualização**, onde o código de barras estará riscado em vermelho.

   >[!NOTE]
   >
   >O valor atribuído a um código de barras depende do seu tipo. Por exemplo, um tipo EAN-8 deve ter exatamente 8 números.
   >
   >O botão de personalização à direita do campo **[!UICONTROL Value]** também permite adicionar dados, além do valor. Isso enriquece o código de barras, desde que o padrão do código de barras o aceite.
   >
   >Por exemplo, se estiver usando um código de barras do tipo GS1-128 e quiser inserir o número da conta de um recipient, além do valor, clique no botão de personalização e selecione **[!UICONTROL Recipient > Account number]**. Se o número da conta do recipient selecionado for inserido corretamente, ele será considerado pelo código de barras.

Após configurar estes elementos, você pode finalizar seu email e enviá-lo. Para evitar erros, sempre verifique se o conteúdo é exibido corretamente antes de executar um delivery clicando na guia **[!UICONTROL Preview]**.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Se o valor de um código de barras estiver incorreto, seu bitmap é exibido riscado em vermelho.

![](assets/barcode_insert_11.png)
