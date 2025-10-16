---
product: campaign
title: Cupons personalizados
description: Saiba como criar e inserir cupons personalizados
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Personalization
role: User
hide: true
hidefromtoc: true
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 0507e0372a81351adc145dafdd3cbe5d5422dc00
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 98%

---

# Cupons personalizados{#personalized-coupons}

A adição de cupons a suas entregas pode oferecer aos destinatários valor aprimorado para produtos e serviços. Você pode usar o módulo de cupom do Campaign para criar um conjunto de cupons que você planeja adicionar às futuras ofertas de marketing. Quando estiver pronto para criar uma entrega, atribua os cupons aplicáveis. Como os cupons são válidos para um período de seleção, um cupom atribuído é vinculado exclusivamente à sua mensagem de entrega. Além disso, o Campaign confirma que há cupons suficientes para o número de mensagens antes do envio da entrega.

>[!AVAILABILITY]
>
>O gerenciamento de cupons não está disponível no Campaign v8 no contexto de uma Implantação corporativa (FFDA). Saiba mais em [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"}.

O gerenciamento de cupons depende de um pacote que deve ser instalado. Para confirmar se há um gerenciamento de cupom, verifique **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**

Os dados de cupom podem ser importados e exportados usando formatos CSV e XML. [Saiba mais](../../platform/using/get-started-data-import-export.md).

## Criar um cupom {#creating-a-coupon}

O módulo de gerenciamento de cupons oferece duas opções ao criar cupons:

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

   **[!UICONTROL Anonymous coupons]** : Um cupom anônimo é idêntico para todos os destinatários. Confirme se Anônimo está selecionado no menu **Tipo de cupom** e clique em **Salvar** para gerar o cupom.

   **[!UICONTROL Individual coupons]** : Um cupom individual pode ser personalizado ainda mais com códigos de cupom adicionais. Por exemplo, um cupom individual é criado para uma venda em uma loja de equipamentos esportivos. No entanto, a lista de destinatários é longa e não compartilham a mesma paixão por um único esporte. Você pode adicionar nomes de código para o cupom individual com base em um esporte (por exemplo, futebol, futebol americano, beisebol etc.) e enviar cada código para os destinatários aplicáveis.

   1. Ao escolher Indivíduo, Cupons abre como uma nova guia na parte inferior esquerda. Acesse a guia **[!UICONTROL Coupons]** e clique em **[!UICONTROL Add]**.
   1. Insira um código exclusivo para o cupom individual quando solicitado pela janela pop-up.
   1. Clique em **[!UICONTROL Save]** para gerar o cupom.

   Para obter mais detalhes sobre a guia Cupons, consulte [Configurar cupons individuais](#configuring-individual-coupons).

   >[!NOTE]
   >
   >Os cupons individuais podem ser importados em massa. Para obter detalhes sobre a importação e exportação, consulte [esta seção](../../platform/using/get-started-data-import-export.md).

### Configurar cupons individuais {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

A guia Cupons está disponível apenas com cupons individuais. Depois que um cupom é associado a uma entrega, a guia Cupons fornece os seguintes detalhes:

* **[!UICONTROL Status]** : Disponibilidade do cupom.
* **[!UICONTROL Redeemed on]** : A data de resgate do cupom.
* **[!UICONTROL Channel]** : O canal usado para enviar o cupom.
* **[!UICONTROL Address]** : Os endereços de email dos destinatários.

Os valores de **[!UICONTROL status]**, **[!UICONTROL channel]** e **[!UICONTROL address]** são automaticamente preenchidos. No entanto, os valores de **[!UICONTROL redeemed on]** não são recuperados pelo Campaign. Eles podem ser concluídos ao importar um arquivo com os detalhes de resgate do cupom.

## Inserir um cupom em uma entrega por email {#inserting-a-coupon-into-an-email-delivery}

No exemplo abaixo, a entrega é criada a partir da Home page. Para obter instruções detalhadas sobre como criar uma entrega, consulte [esta seção](about-email-channel.md). Você também pode adicionar um cupom a uma entrega em um fluxo de trabalho.

1. Acesse **[!UICONTROL Campaigns]** e escolha **[!UICONTROL Deliveries]**.
1. Clique em **[!UICONTROL Create]**.

   ![](assets/deliv_coup_04.png)

1. Insira um nome em **[!UICONTROL Label]** e clique em **[!UICONTROL Continue]**.
1. Clique em **[!UICONTROL To]** para adicionar destinatários. 
1. Clique em **[!UICONTROL Add]** para escolher os destinatários da entrega Depois de selecionar seus destinatários, clique em **[!UICONTROL Ok]** para retornar para a entrega.

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

1. Execute um teste para confirmar o nome atribuído ao cupom. Acesse a guia **[!UICONTROL Preview]** e clique em **[!UICONTROL Test personalization]**. Escolha um destinatário para o teste.

   ![](assets/deliv_coup_13.png)

   Após o teste, o cupom deve aparecer como o nome atribuído em vez do código.

   ![](assets/deliv_coup_14.png)

1. Na barra de ferramentas, clique em **[!UICONTROL Send]**, no canto superior esquerdo, e escolha como enviar a entrega.

   ![](assets/deliv_coup_15.png)

1. Clique em **[!UICONTROL Analyze]**. Se o log de análise confirmar que há cupons suficientes para todos os destinatários, clique em **[!UICONTROL Confirm delivery]** para enviar a mensagem.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>Para obter instruções sobre como gerenciar os cupons insuficientes de uma entrega, consulte [Gerenciar cupons insuficientes](#managing-insufficient-coupons)

Para confirmar que a entrega foi bem-sucedida:

1. Vá para **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1. Clique na guia **[!UICONTROL Deliveries]**.

   ![](assets/deliv_coup_17.png)

   O status é lido como **[!UICONTROL Finished]** para uma entrega bem-sucedida.

>[!NOTE]
>
>Por padrão, o módulo de gestão de cupom usa uma tabela **nms:recipient**. [Saiba mais](../../configuration/using/about-data-model.md#default-recipient-table).
>
>Aprenda como usar uma tabela de destinatário personalizada [nesta página](../../configuration/using/about-custom-recipient-table.md).

## Gerenciar cupons insuficientes {#managing-insufficient-coupons}

A análise da entrega para se o número de cupons for menor que de mensagens. Nesse caso, você pode importar mais cupons ou restringir o número de mensagens. Siga as instruções abaixo se desejar limitar o número de mensagens.

1. Vá para a janela de entrega do email.
1. Clique em **[!UICONTROL To]**.
1. Em **[!UICONTROL Select target]**, acesse a guia **[!UICONTROL Exclusions]**.

   ![](assets/deliv_coup_18.png)

1. Na seção de configurações de exclusão, clique em **[!UICONTROL Edit]**.
1. Insira o número de mensagens que deseja enviar em **[!UICONTROL Limit delivery to...messages]** e clique em **[!UICONTROL Ok]**. Você pode enviar a entrega.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>Ao gerenciar um número limitado de cupons, um fluxo de trabalho de entrega permite dividir a entrega com base em seus critérios. É uma boa opção para enviar cupons para um população selecionada sem restringir o target.
