---
product: campaign
title: Sobre a capacidade de delivery do Adobe Campaign Classic
description: Saiba mais sobre como gerenciar a capacidade de delivery no Adobe Campaign
feature: Deliverability
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 100%

---

# Controlar conteúdo da mensagem{#control-message-content}

![](../../assets/common.svg)

Para garantir que seus emails cheguem aos recipients e melhorem a taxa de capacidade de delivery de email, eles devem respeitar várias regras. Caso contrário, o conteúdo de determinadas mensagens pode ser detectado como spam. O Adobe Campaign fornece várias ferramentas para fazer com que o conteúdo esteja em conformidade com essas regras.

Siga os princípios listados abaixo ao criar o conteúdo da mensagem:

* [Endereço do remetente](#sender-address): o endereço deve identificar explicitamente o remetente. O domínio deve ser de propriedade do remetente e registrado por ele. O registro de domínio não deve ser privatizado.
* [Personalização](#personalization): personalizar o conteúdo e definir um tempo de envio por recipient aumenta as chances de sua mensagem ser aberta.
* Imagens e texto: respeitar uma proporção adequada de texto/imagem (por exemplo, 60% de texto e 40% de imagens).
* [Link de unsubscription ](#opt-out) e landing page: o link de unsubscription é essencial. Deve ser visível e válido e o formulário deve ser funcional.
* Pré-visualização: use as ferramentas oferecidas pelo Adobe Campaign para verificar e otimizar o conteúdo do seu email ([renderização de caixa de entrada](#message-responsiveness), [SpamAssassin](#spamassassin)).

Para obter dicas adicionais para otimizar a capacidade de delivery ao projetar conteúdo, consulte o [Manual de práticas recomendadas de capacidade de delivery da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html?lang=pt-BR).

>[!NOTE]
>
>Para obter mais informações sobre edição de conteúdo de email, consulte [Definir o conteúdo do email](defining-the-email-content.md) e [Criar conteúdo personalizado](design-and-personalize.md).

## Endereço do remetente {#sender-address}

Determinados ISPs verificam a validade do endereço do remetente (**[!UICONTROL From]**) antes de aceitar mensagens. Um endereço formado incorretamente pode resultar na rejeição pelo servidor de recebimento.

Verifique se um endereço correto é fornecido no nível da instância (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) ou nos cenários usados com mais frequência.

Para obter mais informações, consulte [esta página](defining-the-email-content.md).

## Personalização {#personalization}

Para melhorar a experiência dos recipients e fazer com que eles abram seu email, o Adobe Campaign permite personalizar as mensagens.

Para obter mais informações sobre o uso de campos de personalização no Adobe Campaign, consulte [esta seção](personalization-fields.md).

Algumas dicas para otimizar a personalização ao criar o conteúdo são apresentadas [nesta seção](design-and-personalize.md#optimize-personalization).

## Formulário e link para opção de não participação {#opt-out}

Por padrão, quando a mensagem é analisada, uma [regra de tipologia](steps-validating-the-delivery.md#validation-process-with-typologies) verifica se um link para opção de não participação foi incluído e gera um aviso caso ele esteja ausente. É possível alterar essa regra para gerar um erro ao invés de um simples aviso e, assim, impedir que um delivery saia sem esse link.

Você deve verificar se o link de opt-out funciona corretamente antes de cada vez que enviar. Por exemplo, ao enviar a prova, verifique se o link é válido, se o formulário está online e se a validação altera o valor do campo **[!UICONTROL No longer contact this recipient]** para **[!UICONTROL Yes]**. Você deve fazer essa verificação sistematicamente, pois sempre é possível que ocorra um erro humano ao inserir o link ou ao alterar o formulário.

Saiba como inserir um link para opção de não participação [nesta seção](personalization-blocks.md#personalization-blocks-example)

Se for detectado um problema de cancelamento de subscrição após o início do delivery, ainda será possível realizar um cancelamento de subscrição manualmente (usando a função de atualização em massa, por exemplo) para os recipients que clicam no link de opt-out, mesmo que não tenham conseguido confirmar sua escolha.

Como regra geral, não tente impedir os recipients que desejam fazer o opt-out exigindo que eles preencham campos como endereço de email ou nome, por exemplo. O formulário deve ter apenas um botão de validação, e a reconciliação deve ser executada somente no identificador criptografado.

Solicitar confirmação adicional não é confiável: um usuário pode ter dois endereços de email redirecionados para a mesma caixa (por exemplo: firstname.lastname@club.com e firstname.lastname@internet-club.com). Se o recipient conseguir lembrar somente o primeiro endereço e desejar cancelar a subscrição por meio de uma mensagem enviada para o outro, o formulário recusará essa ação, pois o identificador criptografado e o endereço de email digitado não corresponderão.

## Renderização da caixa de entrada {#message-responsiveness}

Antes de enviar a mensagem, você pode testar a capacidade de resposta dela verificando como a mensagem será exibida em diferentes dispositivos. Isso é para garantir que ela seja exibida de maneira ideal em uma variedade de clientes web, emails da web e dispositivos.

Para permitir isso, o Adobe Campaign captura a renderização e a disponibiliza em um relatório dedicado. Assim, você pré-visualiza a mensagem enviada nos diferentes contextos nos quais ela pode ser recebida.

Para obter mais informações, consulte [Renderização da caixa de entrada](inbox-rendering.md).

## SpamAssassin {#spamassassin}

O Adobe Campaign pode ser configurado para funcionar com o SpamAssassin. Isso permite que você marque emails para determinar se uma mensagem corre o risco de ser considerada spam pelas ferramentas anti-spam usadas no recebimento.

Antes de iniciar um delivery, a guia **[!UICONTROL Preview]** permite avaliar os riscos. Uma mensagem de aviso dará o resultado do teste.

Saiba mais nesta [seção](spamassassin.md).
