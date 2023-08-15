---
product: campaign
title: Servidor de mensagens
description: Servidor de mensagens
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
badge-v7-prem: label="no local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 15%

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
