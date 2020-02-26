---
title: Sobre seed addresses
seo-title: Sobre seed addresses
description: Sobre seed addresses
seo-description: null
page-status-flag: never-activated
uuid: 80ab5abc-3ae0-484d-88c0-be039aac360d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: b49acfd0-b601-4694-88e3-cc0a169cb866
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3641e438784d40aa097f8c89ca19bdbb52f4bc7d

---


# Sobre seed addresses{#about-seed-addresses}

Seed addresses são usados para direcionar destinatários que não correspondem aos critérios de destino definidos. Dessa forma, os recipients que estiverem fora do escopo de delivery podem recebê-lo, como qualquer outro recipient target receberia.

Uma vez que a principal razão para utilizá-los é **sua proteção da lista de endereçamento**. Inserir seed addresses na sua lista de endereçamento permite que você seja notado se estiver sendo usado por um terceiro, pois esses seeds addresses receberão os deliveries enviados à sua lista de endereçamento.

Moreover, seed addresses let you **preview and test the deliveries personalization and rendering** before their sending, by sending them proofs (see [Using seed addresses as proof](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

Os recursos dos seed addresses tem os seguintes benefícios:

* Random substitution of fields with data taken from recipient profiles: this lets you enter only the email address, for instance in the seed address section, and let Campaign automatically fill in the other fields form the profile (see [Use case: configuring the field substitution](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Ao usar um workflow com funcionalidades de gestão de dados, os dados adicionais processados nos deliveries podem ser inseridos no nível do seed address para forçar valores, evitando assim a substituição de valores aleatórios.
* Os seed addresses são excluídos automaticamente dos relatórios nas seguintes estatísticas do delivery: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Esses seed addresses são adicionados ao target por serem importados ou criados diretamente no delivery ou na campanha.

>[!NOTE]
>
>Os seed addresses não pertencem a tabela de recipients, pois são criados em uma tabela separada. Se a tabela de recipients é estendida com novos dados, a tabela de seed addresses também deverá ser ampliada, assim como os mesmos dados. Caso contrário, os campos estendidos não são considerados para seed addresses.
>
>Um exemplo de como estender a tabela de endereços semente é apresentado nesta seção: Caso de [uso: seleção de endereços semente em critérios](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

Para deliveries de mala direta, os seed addresses são adicionados durante a extração e combinados no documento de saída.

>[!CAUTION]
>
>Para deliveries de mala direta, o formato do arquivo de extração deve estar em conformidade com as seguintes limitações:
>
>* Não deve usar essa opção **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* If element collections are extracted, these fields will have an empty value for the seed addresses, unless the **[!UICONTROL Single row (expert user)]** option is selected. Para obter mais informações, consulte [esta seção](../../platform/using/exporting-data.md#step-7---data-formatting).
>


