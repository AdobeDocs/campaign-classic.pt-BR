---
title: Servidor de mensagens
seo-title: Servidor de mensagens
description: Servidor de mensagens
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Servidor de mensagens{#messaging-server}

O Adobe Campaign lida com email de saída de forma nativa, no entanto, um servidor de email tradicional é necessário para receber mensagens de entrada vinculadas a email retornado (de daemons de correio). As caixas de correio configuradas neste servidor serão automaticamente processadas pelo aplicativo.

Todos os servidores configurados para acesso POP3 podem ser usados para receber e-mails de retorno se preservarem os cabeçalhos SMTP &quot;ID da mensagem&quot; ao coletar os e-mails. Por exemplo, as implementações que usam o Qmail, o SendMail e o Microsoft Exchange estão em produção no momento. No entanto, algumas instalações do Lotus Notes/domino revelaram um problema com a manutenção dos cabeçalhos &quot;Message-Id&quot;.

>[!CAUTION]
>
>Este servidor de correio pode ter que lidar com cargas pesadas: Em fases iniciais, as listas típicas podem produzir até 10% de taxas de rejeição (se você enviar 100.000 mensagens, espera receber 10.000 rejeições).
>
>É por isso que recomendamos não usar o servidor de mensagens da sua empresa para essa tarefa, pois ela pode ser fortemente afetada.
>
>É aconselhável configurar um subdomínio específico do DNS e um servidor dedicado para o envio de e-mails.
