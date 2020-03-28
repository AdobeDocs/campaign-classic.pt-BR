---
title: Roteamento para um template
seo-title: Roteamento para um template
description: Roteamento para um template
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Roteamento para um template{#routing-towards-a-template}

Quando o template de mensagem é publicado na(s) instância(s) de execução, dois templates a serem vinculados a um evento em tempo real ou batch são gerados automaticamente. A etapa de roteamento consiste em vincular um evento ao template de mensagem apropriado. A vinculação é baseada no tipo de evento especificado nas propriedades do próprio evento e nas propriedades do template.

Definição do tipo de evento nas propriedades de evento:

![](assets/messagecenter_event_type_001.png)

Definição do tipo de evento nas propriedades do template de mensagem:

![](assets/messagecenter_event_type_002.png)

Por padrão, o roteamento é baseado nas seguintes informações:

* o tipo de evento,
* o canal a ser usado (por padrão: email),
* o template do delivery mais recente, com base na data da publicação.

