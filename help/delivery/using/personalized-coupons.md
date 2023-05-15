---
product: campaign
title: Cupons personalizados
description: Saiba como criar e inserir cupons personalizados
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 100%

---

# Cupons personalizados{#personalized-coupons}



A adição de cupons aos seus deliveries pode oferecer aos recipients valor aprimorado para produtos e serviços. Você pode usar o módulo de cupom do Campaign para criar um conjunto de cupons que você planeja adicionar às futuras ofertas de marketing. Quando estiver pronto para criar um delivery, atribua os cupons aplicáveis. Como os cupons são válidos para um período de seleção, um cupom atribuído é vinculado exclusivamente à sua mensagem de delivery. Além disso, o Campaign confirma que há cupons suficientes para o número de mensagens antes do envio do delivery.

>[!NOTE]
>
>A gestão de cupons é um pacote que deve ser instalado. Para confirmar se há um gerenciamento de cupom, verifique **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>Os dados de cupom podem ser importados e exportados usando formatos CSV e XML. Para obter detalhes sobre a importação e exportação, consulte [esta seção](../../platform/using/get-started-data-import-export.md).

## Criar um cupom {#creating-a-coupon}

O módulo de cupom oferece duas opções ao criar cupons:

* **Anônimo**: um cupom genérico para destinatários ou listas de destinatários selecionados.
* **Individual**: um cupom personalizado para destinatários selecionados.

Antes de seguir as etapas abaixo, verifique se você sabe o tipo de cupom que deseja criar.

1. Na árvore do Campaign, acesse **[!UICONTROL Resources > Campaign management > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. Clique no botão **[!UICONTROL New]**.
1. Insira o nome do cupom no campo **[!UICONTROL Label]**. Um código exclusivo foi inserido automaticamente no **[!UICONTROL Coupon code]**. Você pode manter o código ou inserir um novo.

   ![](assets/deliv_coup_02.png)

1. Escolha **[!UICONTROL Start date]** e **[!UICONTROL End date]** para definir o período de validade do cupom.
1. Em **[!UICONTROL Coupon type]**, escolha Anônimo ou Individual.

   **[!UICONTROL Anonymous coupons]** : Um cupom anônimo é idêntico para todos os recipients. Confirme se Anônimo está selecionado no menu **Tipo de cupom** e clique em **Salvar** para gerar o cupom.

   **[!UICONTROL Individual coupons]** : Um cupom individual pode ser personalizado ainda mais com códigos de cupom adicionais. Por exemplo, um cupom individual é criado para uma venda em uma loja de equipamentos esportivos. No entanto, a lista de recipients é longa e não compartilham a mesma paixão por um único esporte. Você pode adicionar nomes de código para o cupom individual com base em um esporte (por exemplo, futebol, futebol americano, beisebol etc.) e enviar cada código para os recipients aplicáveis.

   1. Ao escolher Indivíduo, Cupons abre como uma nova guia na parte inferior esquerda. Acesse a guia **[!UICONTROL Coupons]** e clique em **[!UICONTROL Add]**.
   1. Insira um código exclusivo para o cupom individual quando solicitado pela janela pop-up.
   1. Clique em **[!UICONTROL Save]** para gerar o cupom.

   Para obter mais detalhes sobre a guia Cupons, consulte [Configurar cupons individuais](#configuring-individual-coupons).

   >[!NOTE]
   >
   >Os cupons individuais podem ser importados em massa. Para obter detalhes sobre a importação e exportação, consulte [esta seção](../../platform/using/get-started-data-import-export.md).

### Configurar cupons individuais {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

A guia Cupons está disponível apenas com cupons individuais. Depois que um cupom é associado a um delivery, a guia Cupons fornece os seguintes detalhes:

* **[!UICONTROL Status]** : Disponibilidade do cupom.
* **[!UICONTROL Redeemed on]** : A data de resgate do cupom.
* **[!UICONTROL Channel]** : O canal usado para enviar o cupom.
* **[!UICONTROL Address]** : Os endereços de email dos recipients.

Os valores de **[!UICONTROL status]**, **[!UICONTROL channel]** e **[!UICONTROL address]** são automaticamente preenchidos. No entanto, os valores de **[!UICONTROL redeemed on]** não são recuperados pelo Campaign. Eles podem ser concluídos ao importar um arquivo com os detalhes de resgate do cupom.

## Inserir um cupom em um delivery por email {#inserting-a-coupon-into-an-email-delivery}

No exemplo abaixo, o delivery é criado a partir da Home page. Para obter instruções detalhadas sobre como criar um delivery, consulte [esta seção](about-email-channel.md). Você também pode adicionar um cupom a um delivery em um workflow.

1. Acesse **[!UICONTROL Campaigns]** e escolha **[!UICONTROL Deliveries]**.
1. Clique em **[!UICONTROL Create]**.

   ![](assets/deliv_coup_04.png)

1. Insira um nome em **[!UICONTROL Label]** e clique em **[!UICONTROL Continue]**.
1. Clique em **[!UICONTROL To]** para adicionar recipients. 
1. Clique em **[!UICONTROL Add]** para escolher os destinatários do delivery Depois de selecionar seus destinatários, clique em **[!UICONTROL Ok]** para retornar para o delivery.

   ![](assets/deliv_coup_05.png)

1. Insira um assunto e adicione conteúdo à mensagem.

   ![](assets/deliv_coup_06.png)

1. Na barra de ferramentas, clique em **[!UICONTROL Properties]** e escolha a guia **[!UICONTROL Advanced]**.
1. Clique no ícone de pasta para **[!UICONTROL Coupon management]**.

   ![](assets/deliv_coup_07.png)

1. Escolha o cupom e clique em **[!UICONTROL Ok]**. Clique novamente em **[!UICONTROL Ok]**.

   ![](assets/deliv_coup_08.png)

1. Clique na mensagem para escolher onde deseja colocar o cupom.

   ![](assets/deliv_coup_09.png)

1. Clique no ícone de personalização para fazer a escolha baseada no tipo de cupom:

   * Cupom anônimo: **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * Cupom individual: **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      O cupom é inserido na mensagem como código em vez do nome que você atribuiu. O código é usado no modelo padrão de dados do Campaign.
   ![](assets/deliv_coup_12.png)

1. Execute um teste para confirmar o nome atribuído ao cupom. Acesse a guia **[!UICONTROL Preview]** e clique em **[!UICONTROL Test personalization]**. Escolha um recipient para o teste.

   ![](assets/deliv_coup_13.png)

   Após o teste, o cupom deve aparecer como o nome atribuído em vez do código.

   ![](assets/deliv_coup_14.png)

1. Na barra de ferramentas, clique em **[!UICONTROL Send]**, no canto superior esquerdo, e escolha como enviar o delivery.

   ![](assets/deliv_coup_15.png)

1. Clique em **[!UICONTROL Analyze]**. Se o log de análise confirmar que há cupons suficientes para todos os destinatários, clique em **[!UICONTROL Confirm delivery]** para enviar a mensagem.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>Para obter instruções sobre como gerenciar os cupons insuficientes de um delivery, consulte [Gerenciar cupons insuficientes](#managing-insufficient-coupons)

Para confirmar que o delivery foi bem-sucedido:

1. Vá para **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1. Clique na guia **[!UICONTROL Deliveries]**.

   ![](assets/deliv_coup_17.png)

   O status é lido como **[!UICONTROL Finished]** para um delivery bem-sucedido.

>[!NOTE]
>
>Por padrão, o módulo de gestão de cupom usa uma tabela **nms:recipient**. [Saiba mais](../../configuration/using/about-data-model.md#default-recipient-table).
>
>Aprenda como usar uma tabela de recipient personalizada [nesta página](../../configuration/using/about-custom-recipient-table.md).

## Gerenciar cupons insuficientes {#managing-insufficient-coupons}

A análise do delivery para se o número de cupons for menor que de mensagens. Nesse caso, você pode importar mais cupons ou restringir o número de mensagens. Siga as instruções abaixo se desejar limitar o número de mensagens.

1. Vá para a janela de delivery do email.
1. Clique em **[!UICONTROL To]**.
1. Em **[!UICONTROL Select target]**, acesse a guia **[!UICONTROL Exclusions]**.

   ![](assets/deliv_coup_18.png)

1. Na seção de configurações de exclusão, clique em **[!UICONTROL Edit]**.
1. Insira o número de mensagens que deseja enviar em **[!UICONTROL Limit delivery to...messages]** e clique em **[!UICONTROL Ok]**. Você pode enviar o delivery.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>Ao gerenciar um número limitado de cupons, um workflow de delivery permite dividir o delivery com base em seus critérios. É uma boa opção para enviar cupons para um público selecionado sem restringir o target.
