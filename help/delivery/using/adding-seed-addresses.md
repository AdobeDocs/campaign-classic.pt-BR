---
title: Adição de seed addresses
seo-title: Adição de seed addresses
description: Adição de seed addresses
seo-description: null
page-status-flag: never-activated
uuid: e94ddd46-bed6-4505-91b7-7e17abb0e9c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 0b9b53bf-4dd2-416c-894e-393aded489f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Adição de seed addresses{#adding-seed-addresses}

## Seed addresses em um delivery {#seed-addresses-in-a-delivery}

To add specific seed addresses for a delivery, click the **[!UICONTROL To]** link, then select the **[!UICONTROL Seed addresses]** tab.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Há três modos de inserção possíveis:

1. Inserir seed addresses individuais.

   To do this, click the **[!UICONTROL Add]** button and define the content of the address fields. Repita para cada endereço. Para obter mais informações, consulte [esta seção](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Importação de templates de endereços e adaptando-os de acordo com suas necessidades.

   To do this, click the **[!UICONTROL Import seed templates...]** link and select the folder which contains the address templates. Para obter mais informações, consulte [Criação de modelos](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates)de endereço semente.

   If necessary, once they are added, you can doucle-click them or click the **[!UICONTROL Detail...]** button to adapt the content of each address.

1. Criação de uma condição para selecionar dinamicamente os endereços de controle a serem inseridos.

   To do this, click the **[!UICONTROL Edit the dynamic condition...]** link, then enter the seed address selection parameters. Por exemplo, você pode incluir todos os seed addresses contidos em uma pasta específica, ou seed addresses que pertencem a um departamento específico da sua organização.

   Um exemplo disso é apresentado nesta seção: Caso de [uso: seleção de endereços semente em critérios](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>This option is used when the recipient table used is not the default **nms:recipient** table and you are using the Inbox Rendering functionality provided with Adobe Campaign&#39;s **[!UICONTROL Deliverability]** module.
>
>Para obter mais informações, consulte [Uso de uma tabela](../../delivery/using/using-an-external-recipient-table.md) de destinatários externos e a documentação sobre renderização [da](../../delivery/using/inbox-rendering.md)Caixa de entrada.

Para deliveries, você também pode personalizar a maneira como os endereços são inseridos no arquivo de extração. Por padrão, eles são inseridos na ordem de classificação do arquivo de saída, mas você pode optar por inseri-los no final ou no início do arquivo, ou aleatoriamente entre os recipients do target principal.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Seed addresses em uma campanha {#seed-addresses-in-a-campaign}

To add seed addresses to a target for a campaign, select the operation and click the **[!UICONTROL Edit]** tab.

Clique no **[!UICONTROL Advanced campaign settings...]** link e na **[!UICONTROL Seed addresses]** guia, como mostrado abaixo:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Os seed addresses inseridos a partir da campanha serão adicionados ao target de cada delivery na campanha.
