---
title: Sobre a deliverability do Adobe Campaign Classic
description: Saiba mais sobre como gerenciar a deliverability no Adobe Campaign Classic.
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
source-wordcount: '437'
ht-degree: 95%

---


# Controle do conteúdo da sua mensagem{#control-message-content}

Para melhorar a taxa de delivery de email e garantir que seus emails cheguem aos recipients, o email deve respeitar um determinado número de regras detalhadas abaixo.

## Endereço do remetente {#sender-address}

Determinados ISPs verificam a validade do endereço do remetente (From) antes de aceitar mensagens. Um endereço mal formado pode resultar na rejeição pelo servidor de recebimento. You must make sure a correct address is given at the instance level (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) or in the most frequently-used scenarios.

## Link e formulário de opt-out {#opt-out}

Por padrão, quando a mensagem é analisada, uma regra de tipologia verifica se há um link de opt-out e gera um aviso se estiver faltando. É possível alterar essa regra para gerar um erro ao invés de um simples aviso e, assim, impedir que um delivery saia sem esse link.

Você deve verificar se o link de opt-out funciona corretamente antes de cada vez que enviar. Por exemplo, ao enviar a prova, verifique se o link é válido, se o formulário está online e se a validação altera o valor do campo **[!UICONTROL No longer contact this recipient]** para **[!UICONTROL Yes]**. Você deve fazer essa verificação sistematicamente, pois sempre é possível que ocorra um erro humano ao inserir o link ou ao alterar o formulário.

Se for detectado um problema de cancelamento de subscrição após o início do delivery, ainda será possível realizar um cancelamento de subscrição manualmente (usando a função de atualização em massa, por exemplo) para os recipients que clicam no link de opt-out, mesmo que não tenham conseguido confirmar sua escolha.

Como regra geral, não tente impedir os recipients que desejam fazer o opt-out exigindo que eles preencham campos como endereço de email ou nome, por exemplo. O formulário deve ter apenas um botão de validação e a reconciliação deve ser executada somente no identificador criptografado. Solicitar confirmação adicional não é confiável: um usuário pode ter dois endereços de email redirecionados para a mesma caixa (por exemplo: firstname.lastname@club.com e firstname.lastname@internet-club.com). Se o recipient conseguir lembrar somente o primeiro endereço e desejar cancelar a subscrição por meio de uma mensagem enviada para o outro, o formulário recusará essa ação, pois o identificador criptografado e o endereço de email digitado não corresponderão.

## SpamAssassin {#spamassassin}

O Adobe Campaign pode ser configurado para funcionar com o SpamAssassin. Isso permite que você marque emails para determinar se uma mensagem corre o risco de ser considerada spam pelas ferramentas anti-spam usadas no recebimento.

Antes de iniciar um delivery, a guia Preview permite que você avalie os riscos. Uma mensagem de aviso dará o resultado do teste.

Saiba mais nesta [seção](../../delivery/using/spamassassin.md).