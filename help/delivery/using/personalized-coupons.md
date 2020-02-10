---
title: Cupons personalizados
seo-title: Cupons personalizados
description: Cupons personalizados
seo-description: null
page-status-flag: never-activated
uuid: c840e2de-f0ef-478b-af9f-82e1b6534933
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: f324afa5-304c-470e-a592-290f76a11ccb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Cupons personalizados{#personalized-coupons}

A adição de cupons aos seus deliveries pode oferecer aos recipients valor aprimorado para produtos e serviços. Você pode usar o módulo de cupom do Campaign para criar um conjunto de cupons que você planeja adicionar às futuras ofertas de marketing. Quando estiver pronto para criar um delivery, atribua os cupons aplicáveis. Como os cupons são válidos para um período de seleção, um cupom atribuído é vinculado exclusivamente à sua mensagem de delivery. Além disso, o Campaign confirma que há cupons suficientes para o número de mensagens antes do envio do delivery.

>[!NOTE]
>
>A gestão de cupons é um pacote que deve ser instalado. To confirm that you have Coupon management, check **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>Os dados de cupom podem ser importados e exportados usando formatos CSV e XML. Para obter detalhes sobre a importação e exportação, consulte [esta seção](../../platform/using/generic-imports-and-exports.md).

## Criação de um cupom {#creating-a-coupon}

O módulo de cupom oferece duas opções ao criar cupons:

* **Anônimo**: Um cupom genérico para destinatários selecionados ou listas de destinatários.
* **Individual**: Um cupom personalizado para destinatários selecionados.

Antes de seguir as etapas abaixo, verifique se você sabe o tipo de cupom que deseja criar.

1. In the Campaign tree, go to **[!UICONTROL Resources > Campaign management > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. Clique no botão **[!UICONTROL New]**.
1. Enter the name of the coupon in **[!UICONTROL Label]** field. A unique code has been automatically entered in **[!UICONTROL Coupon code]**. Você pode manter o código ou inserir um novo.

   ![](assets/deliv_coup_02.png)

1. Choose **[!UICONTROL Start date]** and **[!UICONTROL End date]** to set the period in which the coupon is valid.
1. In **[!UICONTROL Coupon type]**, choose Anonymous or Individual.

   **[!UICONTROL Anonymous coupons]** : Um cupom anônimo é idêntico para todos os recipients. Confirme se Anônimo está selecionado no menu **Tipo de cupom** e clique em **Salvar** para gerar o cupom.

   **[!UICONTROL Individual coupons]** : Um cupom individual pode ser personalizado ainda mais com códigos de cupom adicionais. Por exemplo, um cupom individual é criado para uma venda em uma loja de equipamentos esportivos. No entanto, a lista de recipients é longa e não compartilham a mesma paixão por um único esporte. Você pode adicionar nomes de código para o cupom individual com base em um esporte (por exemplo, futebol, futebol americano, beisebol etc.) e enviar cada código para os recipients aplicáveis.

   1. Ao escolher Indivíduo, Cupons abre como uma nova guia na parte inferior esquerda. Vá para a **[!UICONTROL Coupons]** guia e clique em **[!UICONTROL Add]**.
   1. Insira um código exclusivo para o cupom individual quando solicitado pela janela pop-up.
   1. Click **[!UICONTROL Save]** to generate the coupon.
   Para obter mais detalhes sobre a guia Cupons, consulte [Configuração de cupons](#configuring-individual-coupons)individuais.

   >[!NOTE]
   >
   >Os cupons individuais podem ser importados em massa. Para obter detalhes sobre a importação e exportação, consulte [esta seção](../../platform/using/generic-imports-and-exports.md).

### Configuração de cupons individuais {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

A guia Cupons está disponível apenas com cupons individuais. Depois que um cupom é associado a um delivery, a guia Cupons fornece os seguintes detalhes:

* **[!UICONTROL Status]** : Disponibilidade do cupom.
* **[!UICONTROL Redeemed on]** : A data de resgate do cupom.
* **[!UICONTROL Channel]** : O canal usado para enviar o cupom.
* **[!UICONTROL Address]** : Os endereços de email dos recipients.

Os valores para **[!UICONTROL status]**, **[!UICONTROL channel]** e **[!UICONTROL address]** são automaticamente concluídos. However, the values for **[!UICONTROL redeemed on]** are not recovered by Campaign. Eles podem ser concluídos ao importar um arquivo com os detalhes de resgate do cupom.

## Inserir um cupom em um delivery de email {#inserting-a-coupon-into-an-email-delivery}

No exemplo abaixo, o delivery é criado a partir da Home page. Para obter instruções detalhadas sobre como criar um delivery, consulte [esta seção](../../delivery/using/about-email-channel.md). Você também pode adicionar um cupom a um delivery em um workflow.

1. Vá até **[!UICONTROL Campaigns]** e escolha **[!UICONTROL Deliveries]**.
1. Clique em **[!UICONTROL Create]**.

   ![](assets/deliv_coup_04.png)

1. Enter a name in **[!UICONTROL Label]** and click **[!UICONTROL Continue]**.
1. Click **[!UICONTROL To]** to add recipients.
1. Click **[!UICONTROL Add]** to choose recipients for the delivery. Once you have selected your recipients, click **[!UICONTROL Ok]** to return to the delivery.

   ![](assets/deliv_coup_05.png)

1. Insira um assunto e adicione conteúdo à mensagem.

   ![](assets/deliv_coup_06.png)

1. In the toolbar, click **[!UICONTROL Properties]** and choose the **[!UICONTROL Advanced]** tab.
1. Click the folder icon for **[!UICONTROL Coupon management]**.

   ![](assets/deliv_coup_07.png)

1. Choose the coupon and click **[!UICONTROL Ok]**. Clique **[!UICONTROL Ok]** novamente.

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

1. Execute um teste para confirmar o nome atribuído ao cupom. Vá para a **[!UICONTROL Preview]** guia e clique em **[!UICONTROL Test personalization]**. Escolha um recipient para o teste.

   ![](assets/deliv_coup_13.png)

   Após o teste, o cupom deve aparecer como o nome atribuído em vez do código.

   ![](assets/deliv_coup_14.png)

1. In the toolbar, click **[!UICONTROL Send]** (upper left) and choose how you want to send the delivery.

   ![](assets/deliv_coup_15.png)

1. Clique em **[!UICONTROL Analyze]**. If the analysis log confirms that there are enough coupons for all recipients, click **[!UICONTROL Confirm delivery]** to send it.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>For instructions on how to manage insufficient coupons for a delivery, see [Managing insufficient coupons](#managing-insufficient-coupons)

Para confirmar que o delivery foi bem-sucedido:

1. Vá para **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1.  Clique na **[!UICONTROL Deliveries]** guia.

   ![](assets/deliv_coup_17.png)

   The status reads as **[!UICONTROL Finished]** for a successful delivery.

>[!NOTE]
>
>Por padrão, o módulo de gestão de cupom usa uma tabela **nms:recipient**. Para obter instruções sobre como usar outras tabelas, consulte [Edição de schemas](../../configuration/using/data-schemas.md).

## Gestão de cupons insuficientes {#managing-insufficient-coupons}

A análise do delivery para se o número de cupons for menor que de mensagens. Nesse caso, você pode importar mais cupons ou restringir o número de mensagens. Siga as instruções abaixo se desejar limitar o número de mensagens.

1. Vá para a janela de delivery do email.
1. Clique em **[!UICONTROL To]**.
1. Em **[!UICONTROL Select target]**, vá para a **[!UICONTROL Exclusions]** guia.

   ![](assets/deliv_coup_18.png)

1. In the exclusion settings section, click **[!UICONTROL Edit]**.
1. Enter the number of messages you want to send in **[!UICONTROL Limit delivery to...messages]** and click **[!UICONTROL Ok]**. Você pode enviar o delivery.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>Ao gerenciar um número limitado de cupons, um workflow de delivery permite dividir o delivery com base em seus critérios. É uma boa opção para enviar cupons para um público selecionado sem restringir o target.
