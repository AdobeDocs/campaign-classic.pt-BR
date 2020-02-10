---
title: Sobre a capacidade de entrega no Adobe Campaign Classic
description: Saiba mais sobre como gerenciar a capacidade de entrega no Adobe Campaign Classic.
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
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Controle do conteúdo da sua mensagem{#control-message-content}

Para melhorar a taxa de entrega de email e garantir que seus emails cheguem aos destinatários, o email deve respeitar um certo número de regras detalhadas abaixo.

## Endereço do remetente {#sender-address}

Determinados ISPs verificam a validade do endereço do remetente (De) antes de aceitar mensagens. Um endereço mal formado pode resultar na sua rejeição pelo servidor de recebimento. É necessário garantir que um endereço correto seja fornecido no nível da instância (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) ou nos cenários mais usados.

## Link e formulário de recusa {#opt-out}

Por padrão, quando a mensagem é analisada, uma regra de tipologia verifica se um link de opção de não participação foi incluído e gera um aviso se estiver faltando. É possível alterar essa regra para que um erro seja gerado, em vez de um simples aviso, e impedir que uma entrega saia sem esse link.

Você deve verificar se o link para opção de não participação funciona corretamente antes de cada vez que enviar. Por exemplo, ao enviar a prova, verifique se o link é válido, se o formulário está on-line e se a validação altera o valor do **[!UICONTROL No longer contact this recipient]** campo para **[!UICONTROL Yes]**. Você deve fazer essa verificação sistematicamente, pois o erro humano é sempre possível ao inserir o link ou ao alterar o formulário.

Se for detectado um problema de cancelamento de assinatura após a entrega ser iniciada, ainda será possível realizar uma cancelamento de assinatura manualmente (usando a função de atualização em massa, por exemplo) para os destinatários que clicam no link para opção de não participação, mesmo que não tenham conseguido confirmar sua escolha.

Como regra geral, não tente impedir os destinatários que desejam recusar exigindo que eles preencham campos como seu endereço de email ou nome, por exemplo. O formulário deve ter apenas um botão de validação e a reconciliação deve ser executada somente no identificador criptografado. Solicitar confirmação adicional não é confiável: um usuário pode ter dois endereços de email redirecionados para a mesma caixa (por exemplo: firstname.lastname@club.com e firstname.lastname@internet-club.com). Se o destinatário conseguir lembrar somente o primeiro endereço e desejar cancelar a inscrição por meio de uma mensagem enviada para o outro, o formulário recusará isso, pois o identificador criptografado e o endereço de email digitado não corresponderão.

## SpamAssassin {#spamassassin}

O Adobe Campaign pode ser configurado para funcionar com o SpamAssassin. Isso possibilita a pontuação de emails para determinar se uma mensagem corre o risco de ser considerada spam pelas ferramentas antisspam usadas no recebimento.

Antes de iniciar uma entrega, a guia Visualizar permite que você avalie os riscos. Uma mensagem de aviso dará o resultado do teste.

Learn more in this [section](../../delivery/using/spamassassin.md).