---
solution: Campaign Classic
product: campaign
title: Sobre a gestão de conteúdo
description: Sobre a gestão de conteúdo
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---


# Sobre a gestão de conteúdo{#about-content-management}

O módulo Adobe Campaign Content Manager é um [pacote padrão](../../installation/using/installing-campaign-standard-packages.md) do Campaign Classic específico que você pode instalar para criar informativos ou sites recorrentes. Ele pode ajudá-lo a criar, validar e publicar suas mensagens.

>[!NOTE]
>
>Esta seção se refere ao módulo Gerenciamento de conteúdo. Para obter mais informações sobre como projetar o conteúdo de deliveries de emails, consulte [esta seção](../../delivery/using/defining-the-email-content.md).

O módulo &quot;Gerenciamento de conteúdo&quot; incorpora o grupo de trabalho, o workflow e a funcionalidade de agregação de conteúdo. Isso permite que uma mensagem seja formatada automaticamente: email, correspondência, SMS, Web, etc.

O uso do gerenciador de conteúdo em um delivery permite que você ofereça campos de entrada ou de seleção aos operadores de criação de conteúdo. O layout e a exibição desse conteúdo, bem como quaisquer alterações feitas, são gerenciados automaticamente usando a folha de estilos.

![](assets/s_ncs_content_create_content_sample.png)

>[!CAUTION]
>
>Todas as alterações feitas na folha de estilos são implementadas no nível do delivery com base nos templates de conteúdo usados.

A gestão de conteúdo oferece as seguintes vantagens:

* Edição de mensagens estruturadas via interfaces de entrada,
* Separação do conteúdo de dados e como ele é apresentado (gerada no formato XML),
* Geração de documentos em vários formatos (html, txt, XML, etc.) com base nas folhas de estilos para garantir a conformidade com estatutos gráficos,
* Recuperação e agregação automática de fluxos de conteúdo externo,
* Colaboração com workflow para validação e verificação de dados.

No entanto, essa criação de conteúdo envolve algumas restrições, principalmente:

* Liberdade restrita sobre o design do documento final,
* A análise de requisitos deve ser rigorosa para que usuários finais não sejam afetados por uma função ausente.

