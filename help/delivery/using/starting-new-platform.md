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
translation-type: ht
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Início de uma nova plataforma {#starting-new-platform}

É essencial manter sua reputação de domínio e endereço IP. Você encontrará abaixo alguns conselhos para configurar uma nova plataforma.

Começar a enviar emails em uma nova plataforma é uma etapa delicada, pois a plataforma não tem histórico de uso e reputação (quando os IPs de envio nunca foram usados para essa finalidade). Os ISPs desconfiam naturalmente dos endereços IP que nunca foram usados para enviar emails e que, de repente, começam a enviar grandes volumes de tráfego de emails. Na verdade, os remetentes de spam geralmente usam endereços IP &quot;desconhecidos&quot; (ou seja, endereços que nunca foram incluídos na blacklist) para enviar o maior número possível de mensagens antes da detecção.

Não se pode esperar atingir a velocidade operacional em termos de saída no início da fase de produção. Além disso, você não deve tentar enviar mensagens a essa taxa, pois isso pode levar os ISPs a bloquear os endereços de envio e comprometer seriamente o restante da fase de inicialização.

A inicialização de uma plataforma geralmente ocorre ao usar uma lista de endereços pela primeira vez e que podem não ser totalmente qualificados. Se você enviar para endereços inválidos ou para endereços armadilha, isso contribuirá para diminuir a reputação da plataforma. Se você tiver uma lista de endereços inválidos, é do seu interesse importá-la para a tabela de quarentena (**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) antes dos primeiros envios. Se, mesmo assim, você quiser requalificar os endereços inválidos, é preferível fazer isso assim que a reputação da plataforma for estabelecida e pouco a pouco para &quot;diluir&quot; o uso de endereços inválidos ao longo do tempo.

Para resumir os princípios a serem seguidos ao iniciar:

* Importar endereços inválidos para a tabela de quarentena (se você tiver essas informações)
* Limitar a taxa de transferência (configuração técnica: limitação do número de mtachilds)
* Aumento progressivo dos volumes enviados: não direcione a todo o banco de dados desde o início, adicione uma fração extra da lista a cada envio; isso deve permitir aumentar o volume em cada etapa e reduzir a taxa geral de endereços inválidos
* Envio regular: em certa medida, é melhor enviar pouca coisa regularmente do que enormes campanhas esporadicamente
* Preste muita atenção aos relatórios do delivery: indicadores de erro elevados podem significar que uma configuração técnica está mal configurada.