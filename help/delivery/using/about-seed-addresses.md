---
product: campaign
title: Sobre seed addresses
description: Introdução a seed addresses
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Seed Address
role: User
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
TQID: https://experienceleague.adobe.com/ZFeQSj9pGtKzG-wBsm5Go39ja7jvZ0pVi8h3xKOYR8c
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 388
ht-degree: 100%

---

# Sobre seed addresses{#about-seed-addresses}

Seed addresses são usados para direcionar destinatários que não correspondem aos critérios de destino definidos. Dessa forma, os destinatários que estiverem fora do escopo de entrega podem recebê-lo, como qualquer outro destinatário target receberia.

Uma vez que a principal razão para utilizá-los é **sua proteção da lista de endereçamento**. Inserir seed addresses em sua lista de mala direta permite que você seja notado, se ela estiver sendo usada por um terceiro, pois esses seed addresses receberão as entregas enviadas à sua lista de mala direta.

Além disso, os seed addresses permitem **pré-visualizar e testar a personalização e renderização de entregas** antes do envio, enviando provas (consulte [Usar seed addresses como prova](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Conheça este recurso no vídeo](steps-defining-the-target-population.md#seeds-and-proofs-video)

O recurso de seed addresses tem os seguintes benefícios:

* Substituição aleatória de campos com dados obtidos de perfis de destinatários: permite inserir somente o endereço de email, por exemplo, na seção seed address e permite que o Campaign preencha automaticamente os outros campos no formulário do perfil (consulte [Caso de uso: configuração a substituição do campo](use-case-configuring-the-field-substitution.md)).
* Ao usar um fluxo de trabalho com funcionalidades de gestão de dados, os dados adicionais processados nas entregas podem ser inseridos no nível do seed address para forçar valores, evitando assim a substituição de valores aleatórios.
* Os seed addresses são excluídos automaticamente dos relatórios nas seguintes estatísticas da entrega: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Esses seed addresses são adicionados ao target das entregas ao serem importados ou criados diretamente na entrega ou na campanha.

>[!NOTE]
>
>Os seed addresses não pertencem à tabela de destinatários, pois são criados em uma tabela separada. Se a tabela de destinatários é estendida com novos dados, a tabela de seed addresses também deverá ser ampliada, assim como os mesmos dados. Caso contrário, os campos estendidos não são considerados para seed addresses.
>
>Um exemplo de como estender a tabela de seed addresses é apresentado nesta seção: [Caso de uso: seleção de seed addresses em critérios](use-case-selecting-seed-addresses-on-criteria.md).

Para entregas de correspondência direta, os seed addresses são adicionados durante a extração e combinados no documento de saída.

>[!IMPORTANT]
>
>Para entregas de correspondência direta, o formato do arquivo de extração deve estar em conformidade com as seguintes limitações:
>
>* Não deve usar a opção **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Se as coleções de elemento forem extraídas, esses campos têm um valor vazio para os seed addresses, a menos que a opção **[!UICONTROL Single row (expert user)]** esteja selecionada. Para obter mais informações, consulte [esta seção](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>
