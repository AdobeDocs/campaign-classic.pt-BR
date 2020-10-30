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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '379'
ht-degree: 100%

---


# Sobre seed addresses{#about-seed-addresses}

Seed addresses são usados para direcionar destinatários que não correspondem aos critérios de destino definidos. Dessa forma, os recipients que estiverem fora do escopo de delivery podem recebê-lo, como qualquer outro recipient target receberia.

Uma vez que a principal razão para utilizá-los é **sua proteção da lista de endereçamento**. Inserir seed addresses na sua lista de endereçamento permite que você seja notado se estiver sendo usado por um terceiro, pois esses seeds addresses receberão os deliveries enviados à sua lista de endereçamento.

Além disso, os seed addresses permitem **visualizar e testar a personalização e renderização dos deliveries** antes de serem enviados ao enviar provas (consulte [Uso de seed addresses como prova](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof).

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

Os recursos dos seed addresses tem os seguintes benefícios:

* Substituição aleatória de campos com dados obtidos de perfis de recipients: permite inserir somente o endereço de email, por exemplo, na seção seed address e permite que o Campaign preencha automaticamente os outros campos no formulário do perfil (consulte [Caso de uso: configuração do campo de substituição](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Ao usar um workflow com funcionalidades de gestão de dados, os dados adicionais processados nos deliveries podem ser inseridos no nível do seed address para forçar valores, evitando assim a substituição de valores aleatórios.
* Os seed addresses são excluídos automaticamente dos relatórios nas seguintes estatísticas do delivery: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Esses seed addresses são adicionados ao target por serem importados ou criados diretamente no delivery ou na campanha.

>[!NOTE]
>
>Os seed addresses não pertencem a tabela de recipients, pois são criados em uma tabela separada. Se a tabela de recipients é estendida com novos dados, a tabela de seed addresses também deverá ser ampliada, assim como os mesmos dados. Caso contrário, os campos estendidos não são considerados para seed addresses.
>
>Um exemplo de como estender a tabela de seed addresses é apresentado nesta seção: [Caso de uso: seleção de seed addresses em critérios](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

Para deliveries de mala direta, os seed addresses são adicionados durante a extração e combinados no documento de saída.

>[!IMPORTANT]
>
>Para deliveries de mala direta, o formato do arquivo de extração deve estar em conformidade com as seguintes limitações:
>
>* Não deve usar a opção **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Se as coleções de elemento forem extraídas, esses campos têm um valor vazio para os seed addresses, a menos que a opção **[!UICONTROL Single row (expert user)]** esteja selecionada. Para obter mais informações, consulte [esta seção](../../platform/using/exporting-data.md#step-7---data-formatting).

>


