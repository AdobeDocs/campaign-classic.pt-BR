---
solution: Campaign Classic
product: campaign
title: Servidor de mensagens
description: Servidor de mensagens
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---


# Servidor de mensagens{#messaging-server}

A Adobe Campaign lida com emails de saída nativamente, no entanto, um servidor de email tradicional é necessário para receber mensagens de entrada vinculadas ao email retornado (de maileres daemon). As caixas de correio configuradas neste servidor serão automaticamente processadas pelo aplicativo.

Todos os servidores configurados para acesso POP3 podem ser usados para receber e-mails de retorno se preservarem os cabeçalhos SMTP &quot;ID da mensagem&quot; ao coletar os e-mails. Por exemplo, as implementações que usam o Qmail, o SendMail e o Microsoft Exchange estão em produção no momento. No entanto, algumas instalações do Lotus Notes/domino revelaram um problema com a manutenção dos cabeçalhos &quot;Message-Id&quot;.

>[!CAUTION]
>
>Este servidor de correio pode ter que lidar com cargas pesadas: Em fases iniciais, as listas típicas podem produzir até 10% de taxas de rejeição (se você enviar 100.000 mensagens, espera receber 10.000 rejeições).
>
>É por isso que recomendamos não usar seu servidor de mensagens de empresa para essa tarefa, pois ela pode ser fortemente afetada.
>
>É aconselhável configurar um subdomínio específico do DNS e um servidor dedicado para o envio de e-mails.
