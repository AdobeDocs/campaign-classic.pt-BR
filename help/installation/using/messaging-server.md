---
product: campaign
title: Servidor de mensagens
description: Servidor de mensagens
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# Servidor de mensagens{#messaging-server}



O Adobe Campaign lida com emails de saída nativamente, no entanto, um servidor de email tradicional é necessário para receber mensagens de entrada vinculadas a emails retornados (de daemons do mailer). As caixas de correio configuradas neste servidor serão processadas automaticamente pelo aplicativo.

Todos os servidores configurados para acesso POP3 podem ser usados para receber emails de retorno se preservarem os cabeçalhos SMTP &quot;Message-ID&quot; ao pegar o email. Por exemplo, implementações que usam Qmail, SendMail e Microsoft Exchange estão atualmente em produção. No entanto, algumas instalações do Lotus Notes/domino revelaram um problema com a manutenção de cabeçalhos &quot;Message-Id&quot;.

>[!CAUTION]
>
>Esse servidor de email pode ter que lidar com cargas pesadas: nas fases iniciais, as listas típicas podem produzir até 10% de taxas de rejeição (se você enviar 100.000 mensagens, esperar receber 10.000 rejeições).
>
>É por isso que recomendamos não usar o servidor de mensagens da sua empresa para essa tarefa, pois ela pode ser bastante afetada.
>
>É aconselhável configurar um subdomínio específico do DNS e um servidor dedicado para emails devolvidos.
