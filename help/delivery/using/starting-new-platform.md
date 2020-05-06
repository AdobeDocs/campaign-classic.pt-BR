---
title: Iniciar uma nova plataforma com o Adobe Campaign Classic
description: Saiba mais sobre como gerenciar a capacidade de delivery ao iniciar uma nova plataforma com o Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a1192bc804e752d13af869da66ba0505c077ed19
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 34%

---


# Início de uma nova plataforma {#starting-new-platform}

A manutenção da reputação do seu domínio e endereço IP é essencial ao configurar uma nova plataforma.

* Começar a enviar emails é uma etapa delicada, pois a plataforma não tem histórico de uso e, quando os IPs enviados nunca foram usados para esse fim, nenhuma reputação.

* Os ISPs desconfiam naturalmente dos endereços IP que nunca foram usados para enviar emails e que, de repente, começam a enviar grandes volumes de tráfego de emails. Na verdade, os remetentes de spam geralmente usam endereços IP &quot;desconhecidos&quot; (endereços que nunca foram incluído na blacklist) para enviar o maior número possível de mensagens antes da detecção.

* Não se pode esperar atingir a velocidade operacional em termos de saída no início da fase de produção. Além disso, você não deve tentar enviar mensagens a essa taxa, pois isso pode levar os ISPs a bloquear os endereços de envio e comprometer seriamente o restante da fase de inicialização.

Abaixo estão listados os principais princípios a serem seguidos ao iniciar uma nova plataforma:

* Se você tiver essas informações, **importe endereços inválidos para a tabela**quarentena.
A inicialização de uma plataforma geralmente ocorre ao usar uma lista de endereços pela primeira vez e que podem não ser totalmente qualificados. Se você enviar para endereços inválidos ou para endereços de correio de mel, isso contribuirá para diminuir a reputação da plataforma.

   * If you have a list of invalid addresses, it is in your best interests to import it into the quarantine table (available through the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** menu) before sending for the first times.
   * Se, mesmo assim, você quiser requalificar os endereços inválidos, é preferível fazer isso assim que a reputação da plataforma for estabelecida e pouco a pouco para &quot;diluir&quot; o uso de endereços inválidos ao longo do tempo.
   Para obter mais informações, consulte [Otimizar seu delivery pelo quarentena](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Limite a taxa** de throughput limitando o número de mtachilds. Para obter mais informações sobre como ajustar essa configuração técnica, entre em contato com o administrador do Adobe Campaign.
* **Aumente progressivamente os volumes enviados** para evitar que sejam marcados como spam. Não público alvo todo o banco de dados do próprio start, mas adicione uma fração extra da lista sempre que enviar. Isso deve permitir aumentar o volume em cada etapa e reduzir a taxa geral de endereços inválidos. Para garantir o desenvolvimento suave da fase de start, você pode usar o ondas. For more on this, see [Sending using multiple waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Enviar regularmente**. Em certa medida, é melhor enviar regularmente campanhas pequenas em vez de esporadicamente.
* **Preste muita atenção aos relatórios do delivery**. Indicadores de erro elevados podem significar que uma configuração técnica está mal configurada. Para obter mais informações, consulte [Monitoramento de um delivery](../../delivery/using/monitoring-a-delivery.md).

**Tópicos relacionados**:
* [Aumente sua reputação de email com o aquecimento de IP](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [Tudo sobre armadilhas de spam](https://helpx.adobe.com/campaign/kb/spam-traps.html)