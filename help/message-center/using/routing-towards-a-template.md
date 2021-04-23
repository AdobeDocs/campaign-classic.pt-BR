---
solution: Campaign Classic
product: campaign
title: Roteamento para um template
description: Roteamento para um template
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 2c18c557-f49b-4af8-8795-3d59bd78e63f
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '121'
ht-degree: 100%

---

# Roteamento para um template{#routing-towards-a-template}

Quando o template de mensagem é publicado na(s) instância(s) de execução, dois templates a serem vinculados a um evento em tempo real ou batch são gerados automaticamente. A etapa de roteamento consiste em vincular um evento ao template de mensagem apropriado. A vinculação é baseada no tipo de evento especificado nas propriedades do próprio evento e nas propriedades do template.

Definição do tipo de evento nas propriedades de evento:

![](assets/messagecenter_event_type_001.png)

Definição do tipo de evento nas propriedades do template de mensagem:

![](assets/messagecenter_event_type_002.png)

Por padrão, o roteamento é baseado nas seguintes informações:

* O tipo de evento
* O canal a ser usado (por padrão: email)
* O template do delivery mais recente, com base na data da publicação
