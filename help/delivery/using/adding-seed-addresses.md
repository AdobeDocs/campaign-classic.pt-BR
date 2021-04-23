---
solution: Campaign Classic
product: campaign
title: Adição de seed addresses
description: Adição de seed addresses
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '335'
ht-degree: 100%

---

# Adicionar seed addresses{#adding-seed-addresses}

## Seed addresses em um delivery {#seed-addresses-in-a-delivery}

Para adicionar seed addresses específicos em um delivery, clique no link **[!UICONTROL To]** e selecione a guia **[!UICONTROL Seed addresses]** Seed addresses.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Há três modos de inserção possíveis:

1. Inserir seed addresses individuais.

   Para fazer isso, clique no botão **[!UICONTROL Add]** e defina o conteúdo dos campos de endereço. Repita para cada endereço. Para obter mais informações, consulte [esta seção](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Importação de templates de endereços e adaptando-os de acordo com suas necessidades.

   Para fazer isso, clique no link **[!UICONTROL Import seed templates...]** e selecione a pasta que contém os templates de endereço. Para obter mais informações, consulte [esta seção](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates).

   Se necessário, depois da execução, clique duas vezes neles ou no botão **[!UICONTROL Detail...]** para adaptar o conteúdo de cada endereço.

1. Criação de uma condição para selecionar dinamicamente os endereços de controle a serem inseridos.

   Para fazer isso, clique no link **[!UICONTROL Edit the dynamic condition...]** e insira os parâmetros de seleção do seed address. Por exemplo, você pode incluir todos os seed addresses contidos em uma pasta específica ou seed addresses que pertencem a um departamento específico da sua organização.

   Um exemplo é apresentado nesta seção: [Caso de uso: seleção de seed addresses por critérios](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Essa opção é usada quando a tabela do recipient usada não é a tabela padrão **nms:recipient** e você está usando a funcionalidade de Renderização da caixa de entrada disponibilizada com o módulo **[!UICONTROL Deliverability]** do Adobe Campaign.
>
>Para obter mais informações, consulte [Usar uma tabela de recipient externa](../../delivery/using/using-an-external-recipient-table.md) e a documentação sobre [Renderização de caixa de entrada](../../delivery/using/inbox-rendering.md).

Para deliveries, você também pode personalizar a maneira como os endereços são inseridos no arquivo de extração. Por padrão, eles são inseridos na ordem de classificação do arquivo de saída, mas você pode optar por inseri-los no final ou no início do arquivo, ou aleatoriamente entre os recipients do target principal.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Seed addresses em uma campanha {#seed-addresses-in-a-campaign}

Para adicionar seed addresses a um target para uma campanha, selecione a operação e clique na guia **[!UICONTROL Edit]**.

Clique no link **[!UICONTROL Advanced campaign settings...]** e, em seguida, na guia **[!UICONTROL Seed addresses]**, conforme mostrado abaixo:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Os seed addresses inseridos a partir da campanha serão adicionados ao target de cada delivery na campanha.
