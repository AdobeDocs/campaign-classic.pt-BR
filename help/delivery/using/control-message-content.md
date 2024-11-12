---
product: campaign
title: Sobre a capacidade de entrega do Adobe Campaign Classic
description: Saiba mais sobre como gerenciar a capacidade de entrega no Adobe Campaign
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 98%

---

# Controlar conteúdo da mensagem{#control-message-content}

Para garantir que seus emails cheguem aos destinatários e melhorem a taxa de capacidade de entrega de email, eles devem respeitar várias regras. Caso contrário, o conteúdo de determinadas mensagens pode ser detectado como spam. O Adobe Campaign fornece várias ferramentas para fazer com que o conteúdo esteja em conformidade com essas regras.

Siga os princípios listados abaixo ao criar o conteúdo da mensagem:

* [Endereço do remetente](#sender-address): o endereço deve identificar explicitamente o remetente. O domínio deve ser de propriedade do remetente e registrado por ele. O registro de domínio não deve ser privatizado.
* [Personalização](#personalization): personalizar o conteúdo e definir um tempo de envio por destinatário aumenta as chances de sua mensagem ser aberta.
* Imagens e texto: respeitar uma proporção adequada de texto/imagem (por exemplo, 60% de texto e 40% de imagens).
* [Link de unsubscription ](#opt-out) e landing page: o link de unsubscription é essencial. Deve ser visível e válido e o formulário deve ser funcional.
* Pré-visualização: use as ferramentas oferecidas pelo Adobe Campaign para verificar e otimizar o conteúdo do seu email ([renderização de caixa de entrada](#message-responsiveness), [SpamAssassin](#spamassassin)).

Para obter dicas adicionais para otimizar a capacidade de entrega ao projetar conteúdo, consulte o [Manual de práticas recomendadas de capacidade de entrega da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html?lang=pt-BR).

>[!NOTE]
>
>Para obter mais informações sobre edição de conteúdo de email, consulte [Definir o conteúdo do email](defining-the-email-content.md).

## Endereço do remetente {#sender-address}

Determinados ISPs verificam a validade do endereço do remetente (**[!UICONTROL From]**) antes de aceitar mensagens. Um endereço formado incorretamente pode resultar na rejeição pelo servidor de recebimento.

Verifique se um endereço correto é fornecido no nível da instância (menu **[!UICONTROL Tools > Advanced > deployment wizard...]**) ou nos cenários usados com mais frequência.

Para obter mais informações, consulte [esta página](defining-the-email-content.md).

## Personalização {#personalization}

Para melhorar a experiência dos destinatários e fazer com que eles abram seu email, o Adobe Campaign permite personalizar as mensagens.

Para obter mais informações sobre o uso de campos de personalização no Adobe Campaign, consulte [esta seção](personalization-fields.md).

## Formulário e link para opção de não participação {#opt-out}

Por padrão, quando a mensagem é analisada, uma [regra de tipologia](steps-validating-the-delivery.md#validation-process-with-typologies) verifica se um link para opção de não participação foi incluído e gera um aviso caso ele esteja ausente. É possível alterar essa regra para gerar um erro ao invés de um simples aviso e, assim, impedir que uma entrega saia sem esse link.

Você deve verificar se o link de opt-out funciona corretamente antes de cada vez que enviar. Por exemplo, ao enviar a prova, verifique se o link é válido, se o formulário está online e se a validação altera o valor do campo **[!UICONTROL No longer contact this recipient]** para **[!UICONTROL Yes]**. Você deve fazer essa verificação sistematicamente, pois sempre é possível que ocorra um erro humano ao inserir o link ou ao alterar o formulário.

Saiba como inserir um link para opção de não participação [nesta seção](personalization-blocks.md#personalization-blocks-example)

Se for detectado um problema de cancelamento de subscrição após o início da entrega, ainda será possível realizar um cancelamento de subscrição manualmente (usando a função de atualização em massa, por exemplo) para os destinatários que clicam no link de opt-out, mesmo que não tenham conseguido confirmar sua escolha.

Como regra geral, não tente impedir os destinatários que desejam fazer o opt-out exigindo que eles preencham campos como endereço de email ou nome, por exemplo. O formulário deve ter apenas um botão de validação, e a reconciliação deve ser executada somente no identificador criptografado.

Solicitar confirmação adicional não é confiável: um usuário pode ter dois endereços de email redirecionados para a mesma caixa (por exemplo: firstname.lastname@club.com e firstname.lastname@internet-club.com). Se o destinatário conseguir lembrar somente o primeiro endereço e desejar cancelar a subscrição por meio de uma mensagem enviada para o outro, o formulário recusará essa ação, pois o identificador criptografado e o endereço de email digitado não corresponderão.

## Renderização da caixa de entrada {#message-responsiveness}

Antes de enviar a mensagem, você pode testar a capacidade de resposta dela verificando como a mensagem será exibida em diferentes dispositivos. Isso é para garantir que ela seja exibida de maneira ideal em uma variedade de clientes web, emails da web e dispositivos.

Para permitir isso, o Adobe Campaign captura a renderização e a disponibiliza em um relatório dedicado. Assim, você pré-visualiza a mensagem enviada nos diferentes contextos nos quais ela pode ser recebida.

Para obter mais informações, consulte [Renderização da caixa de entrada](inbox-rendering.md).

## SpamAssassin {#spamassassin}

O Adobe Campaign pode ser configurado para funcionar com o SpamAssassin. Isso permite que você marque emails para determinar se uma mensagem corre o risco de ser considerada spam pelas ferramentas anti-spam usadas no recebimento.

Antes de iniciar uma entrega, a guia **[!UICONTROL Preview]** permite avaliar os riscos. Uma mensagem de aviso dará o resultado do teste.

Saiba mais nesta [seção](spamassassin.md).
