---
title: Monitoramento técnico
seo-title: Monitoramento técnico
description: Monitoramento técnico
seo-description: null
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 38700b79aeb19c75d10d2f5eb60c1efdb12e62e3

---


# Monitoramento técnico{#technical-monitoring}

## Relatório de monitoramento técnico da entrega {#technical-deliverability-monitoring}

O relatório técnico de monitoramento de material de entrega é atualizado diariamente e está disponível ao navegar até **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** e clicar no **[!UICONTROL Technical monitoring]** link na guia Adobe Campaign **[!UICONTROL Home]** . Ele inclui vários indicadores de qualidade de deliverability para sua plataforma.

Esses indicadores são atualizados diariamente às 9h.

>[!NOTE]
>
>Além disso, você pode receber um relatório diário por email em um endereço especificado. Informe o endereço de email solicitado por email ou pelo Adobe Campaign Extranet.

![](assets/s_tn_del_monitoring.png)

Os seguintes indicadores são usados no relatório:

* **[!UICONTROL Reverse DNS]** : O Adobe Campaign verifica se um DNS reverso é fornecido para um endereço IP e que isso seja apontado corretamente ao IP.

* **[!UICONTROL SPF]** (Estrutura de Política do Remetente): Um mecanismo de autenticação que permite aos ISPs e provedores de caixa de correio verificar se o remetente de email está autorizado no domínio de envio.

   <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->

* **[!UICONTROL DomainKeys]** : Um serviço desenvolvido pelo Yahoo e destinado a certificar a identidade de um remetente de email.

* **[!UICONTROL IP and RBL domain]** (Lista de buracos negros em tempo real): Uma lista de endereços IP e domínios que foram sinalizados por organizações de listas de bloqueios para má reputação de envio. Essas listas são mantidas por organizações dedicadas, como Spamhaus, Spamcope, SURBL/URIBL etc. Atualmente, o Adobe Campaign processa verificações contra RBLs que têm um impacto significativo na entrega. Esses RBLs refletem o envio de reputação e podem ser referenciados pelos ISPs antes de aceitarem receber seus emails.

* **[!UICONTROL SNDS]** (Serviços de dados de rede inteligente): Um serviço [antisspam do](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx)Windows Live Hotmail. O Hotmail é o único ISP que fornece esse tipo de informação. As pontuações de benchmark são um resultado de filtro verde, uma taxa de reclamação inferior a 0,1% e zero armadilhas de spam.

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->
