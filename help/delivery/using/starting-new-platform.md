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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 94%

---


# Início de uma nova plataforma {#starting-new-platform}

A manutenção da reputação do seu domínio e endereço IP é essencial ao configurar uma nova plataforma.

* Começar a enviar emails é uma etapa delicada, pois a plataforma não tem histórico de uso e reputação (quando os IPs de envio nunca foram usados para essa finalidade).

* Os ISPs desconfiam naturalmente dos endereços IP que nunca foram usados para enviar emails e que, de repente, começam a enviar grandes volumes de tráfego de emails. Na verdade, os remetentes de spam geralmente usam endereços IP &quot;desconhecidos&quot; (endereços que nunca foram adicionados a uma lista de bloqueios) para enviar o maior número possível de mensagens antes da detecção.

* Não se pode esperar atingir a velocidade operacional em termos de saída no início da fase de produção. Além disso, você não deve tentar enviar mensagens a essa taxa, pois isso pode levar os ISPs a bloquear os endereços de envio e comprometer seriamente o restante da fase de inicialização.

Abaixo estão listados os principais fundamentos que devem ser seguidos ao iniciar uma nova plataforma:

* Se você tiver essas informações, **importe endereços inválidos para a tabela quarentena**.
A inicialização de uma plataforma geralmente ocorre ao usar uma lista de endereços pela primeira vez e que podem não ser totalmente qualificados. Se você enviar para endereços inválidos ou para endereços armadilha, isso contribuirá para diminuir a reputação da plataforma.

   * Se você tiver uma lista de endereços inválidos, é do seu interesse importá-la para a tabela de quarentena (disponível por meio do menu **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) antes dos primeiros envios.
   * Se, mesmo assim, você quiser requalificar os endereços inválidos, é preferível fazer isso assim que a reputação da plataforma for estabelecida e pouco a pouco para &quot;diluir&quot; o uso de endereços inválidos ao longo do tempo.

   Para obter mais informações, consulte [Otimizar o delivery por meio de quarentenas](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Limite a taxa de transferência** limitando o número de mtachilds. Para obter mais informações sobre como ajustar essa configuração técnica, entre em contato com o administrador do Adobe Campaign.
* **Aumente progressivamente os volumes enviados** para evitar que sejam marcados como spam. Não direcione todo o banco de dados desde o início, mas adicione uma fração extra da lista sempre que enviar. Isso deve permitir aumentar o volume em cada etapa e reduzir a taxa geral de endereços inválidos. Para garantir o desenvolvimento perfeito da fase de início, você pode usar ondas. Para obter mais informações, consulte [Enviar usando várias ondas](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Enviar regularmente**. Em certa medida, é melhor enviar pouca coisa regularmente do que campanhas enormes esporadicamente.
* **Preste muita atenção aos relatórios do delivery**. Muito erros podem significar que uma configuração técnica está mal feita. Para obter mais informações, consulte [Monitoramento de um delivery](../../delivery/using/monitoring-a-delivery.md)

**Tópicos relacionados**:
* [Aumente sua reputação de email com o aquecimento de IP](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [Tudo sobre armadilhas de spam](https://helpx.adobe.com/campaign/kb/spam-traps.html)