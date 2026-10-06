---
product: campaign
title: Servidor de mensagens
description: Servidor de mensagens
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 12%
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
