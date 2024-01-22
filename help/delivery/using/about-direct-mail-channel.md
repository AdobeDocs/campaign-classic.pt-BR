---
product: campaign
title: Sobre o canal de correspondência direta
description: Sobre o canal de correspondência direta
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Direct Mail
role: User
exl-id: 6474cf2e-c4db-4430-b001-18bf4911b0ea
source-git-commit: ba542c0811141e707589568706d44c73c280c0d3
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 47%

---

# Sobre o canal de correspondência direta{#about-direct-mail-channel}


O Adobe Campaign permite produzir arquivos para fazer entregas em massa de cartas personalizadas. Os perfis de recipients devem conter pelo menos seus nomes e endereços postais.

>[!NOTE]
>
>Os endereços postais são campos calculados. Um endereço pode conter até seis linhas por padrão: a primeira contém o nome e sobrenome, as próximas linhas contêm o endereço postal (rua etc.) e a última linha contém o CEP e a cidade. A definição do campo postalAddress calculado padrão pode ser revisada no esquema nms:recipient.
>
>Um endereço é considerado completo se o nome, o campo CEP e os campos do município/cidade não estiverem vazios. Quaisquer recipients com endereços incompletos serão excluídos dos deliveries de correspondência direta.

As seções abaixo fornecem informações específicas para o canal de mala direta. Para obter informações globais sobre como criar e enviar uma entrega, consulte [esta seção](steps-about-delivery-creation-steps.md).
