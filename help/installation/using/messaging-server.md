---
product: campaign
title: Servidor de mensagens
description: Servidor de mensagens
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# Servidor de mensagens{#messaging-server}

![](../../assets/v7-only.svg)

O Adobe Campaign lida com emails de saída de forma nativa, no entanto, um servidor de email tradicional é necessário para receber mensagens de entrada vinculadas a emails retornados (de daemons do remetente). As caixas de correio configuradas neste servidor serão automaticamente processadas pelo aplicativo.

Todos os servidores configurados para acesso POP3 podem ser usados para receber emails de retorno se preservarem os cabeçalhos SMTP &quot;Message-ID&quot; ao coletar o email. Por exemplo, implementações que usam Qmail, SendMail e Microsoft Exchange estão em produção no momento. No entanto, algumas instalações do Lotus Notes/domino revelaram um problema com a manutenção de cabeçalhos de &quot;ID de mensagem&quot;.

>[!CAUTION]
>
>Este servidor de e-mail pode ter que lidar com cargas pesadas: Em fases iniciais, as listas típicas podem produzir até 10% de taxas de rejeição (se você enviar 100.000 mensagens, espera receber 10.000 rejeições).
>
>É por isso que recomendamos não usar o servidor de mensagens da sua empresa para essa tarefa, pois ela pode ser fortemente afetada.
>
>É aconselhável configurar um subdomínio específico do DNS e um servidor dedicado para emails de devolução.
