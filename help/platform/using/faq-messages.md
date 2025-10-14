---
product: campaign
title: Perguntas frequentes sobre teste e envio
description: Perguntas frequentes sobre o Campaign Classic
feature: Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 88%

---

# Validar, enviar e rastrear mensagens {#validate-send-track}



## Teste e validação {#test-and-validate-before-sending}

Saiba como executar etapas de teste e validação antes de enviar mensagens dentro do Adobe Campaign.

### O que é análise de entrega? {#what-is-the-delivery-analysis-}

A análise de entrega é a fase na qual a população de destino é calculada e o conteúdo de entrega é preparado. Uma vez concluída, a entrega estará pronta para ser enviada. Consulte os registros para verificar se tudo está certo.

Saiba mais na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/delivery-analysis.html){target="_blank"}.

### Por que devo criar provas? {#why-should-i-create-proofs-}

A Adobe recomenda criar mensagens de prova para verificar sua entrega em um grupo de aprovadores antes de enviá-la para o target principal. Em seguida, você pode validar o conteúdo da mensagem, a personalização e os parâmetros de entrega.

Saiba mais na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html){target="_blank"}.

### Como usar seed addresses no Adobe Campaign? {#how-to-use-seed-addresses-in-adobe-campaign-}

Seed addresses são usados para direcionar destinatários que não correspondem aos critérios de destino definidos. Esses destinatários são adicionados ao público-alvo: eles podem ser importados ou criados diretamente na entrega ou na campanha. Para entregas de correspondência direta, eles são adicionados durante a extração e combinados no documento de saída.

Temos assim os seguintes benefícios:

* Substituição aleatória de campos por dados de perfis de destinatários: isso permite inserir somente o endereço de e-mail, por exemplo, na seção do seed address.
* Ao usar um fluxo de trabalho com funcionalidades de gestão de dados, os dados adicionais processados nas entregas podem ser inseridos no nível do seed address para forçar valores, evitando assim a substituição de valores aleatórios.

[Clique aqui para obter mais informações sobre seed addresses](../../delivery/using/about-seed-addresses.md) .

### Como posso configurar um processo de aprovação antes de enviar mensagens? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Para detectar possíveis erros na configuração da mensagem, a Adobe recomenda configurar um ciclo de validação de entrega. Verifique se o conteúdo é aprovado com a frequência necessária enviando provas para testar os destinatários. Uma prova deve ser enviada toda vez que uma alteração for feita, para aprovar o conteúdo.

Saiba mais na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html){target="_blank"}.

### O que é uma regra de tipologia? {#what-is-a-typology-rule-}

Para evitar conflitos entre campanhas, o Adobe Campaign pode testar várias combinações aplicando regras de restrição específicas. Isso garante que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, de acordo com as políticas de comunicação da empresa.

Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=pt-BR){target="_blank"}.

## Envie suas mensagens {#send-your-messages}

Saiba como enviar mensagens em vários canais com o Adobe Campaign.

### Como posso enviar emails em ondas? {#how-can-i-send-emails-in-waves-}

Antes de enviar uma entrega a uma grande população, você pode configurar ondas para dividir as mensagens em vários lotes e equilibrar a carga. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html#sending-using-multiple-waves){target="_blank"}.

### Quais são as principais etapas para criar um email no Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Depois que a entrega do e-mail é criada e validada, é possível enviá-la. Você pode decidir enviar o email para o target principal imediatamente ou agendar a entrega para uma data posterior. Se necessário, antes disso, você também pode estimar a população de destino.

Saiba mais na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html){target="_blank"}.

### Como agendar uma entrega? {#how-to-schedule-a-delivery-}

É possível adiar a entrega de mensagens para agendar a entrega ou gerenciar as regras de pressão e evitar o excesso de solicitações em relação a uma população.

Saiba mais na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html#schedule-delivery-sending){target="_blank"}.

### Posso adicionar um anexo aos emails? {#can-i-add-an-attachment-to-emails-}

Com o Campaign Classic, você pode adicionar anexos personalizados aos seus emails.

Saiba mais sobre anexos de email na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=pt-BR){target="_blank"}.

## Acompanhe suas mensagens e avalie seu impacto {#track-your-messages-and-measure-their-impact}

Depois que as mensagens são enviadas, aprenda a controlar e medir seu impacto com o Adobe Campaign.

### Como posso configurar links rastreados em uma entrega de email? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

Para cada entrega, você pode rastrear a recepção das mensagens e a ativação dos links inseridos no conteúdo da mensagem. Isso permite rastrear o comportamento dos destinatários seguindo as ações de entrega que foram direcionadas.

Para cada URL de mensagem, você pode escolher se irá ativar o rastreamento, alterar o rótulo do link ou agrupar os links por categorias para fins de relatório, por exemplo.

[Clique aqui para saber mais](../../delivery/using/about-message-tracking.md) sobre como controlar suas mensagens no Campaign Classic.

### Onde posso acessar logs de entrega e rastreamento? {#where-can-i-access-delivery-and-tracking-logs-}

Saiba como rastrear suas entregas e entender o comportamento dos destinatários [nesta página](../../delivery/using/delivery-dashboard.md).

### Onde posso obter relatórios de entrega? {#where-can-i-get-delivery-reports-}

O Adobe Campaign vem com um conjunto de relatórios para monitorar suas entregas e rastrear suas mensagens.

[Clique aqui para saber mais sobre relatórios integrados](../../reporting/using/delivery-reports.md).

### Como o Adobe Campaign qualifica e gerencia endereços em quarentena? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

O Adobe Campaign gerencia uma lista de endereços em quarentena. Os destinatários cujo endereço está em quarentena são excluídos por padrão durante a análise de entrega e não serão direcionados. Um endereço de e-mail pode ser colocado em quarentena, por exemplo, quando a caixa de correio está cheia ou se o endereço não existe.

[Clique aqui para saber mais sobre gerenciamento de quarentena](../../delivery/using/understanding-quarantine-management.md).
