---
product: campaign
title: Perguntas frequentes sobre teste e envio
description: Perguntas frequentes sobre o Campaign Classic
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
source-git-commit: 6d53ba957fb567a9a921544418a73a9bde37c97b
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 98%

---

# Validar, enviar e rastrear mensagens {#validate-send-track}

![](../../assets/v7-only.svg)

## Teste e validação {#test-and-validate-before-sending}

Saiba como executar etapas de teste e validação antes de enviar mensagens dentro do Adobe Campaign.

### O que é análise de entrega? {#what-is-the-delivery-analysis-}

A análise de entrega é a fase na qual a população de destino é calculada e o conteúdo de entrega é preparado. Uma vez concluída, a entrega estará pronta para ser enviada. Consulte os registros para verificar se tudo está certo.

[Clique aqui para saber mais](../../delivery/using/steps-validating-the-delivery.md).

### Por que devo criar provas? {#why-should-i-create-proofs-}

A Adobe recomenda criar mensagens de prova para verificar seu delivery em um grupo de aprovadores antes de enviá-lo para o target principal. Em seguida, você pode validar o conteúdo da mensagem, a personalização e os parâmetros de entrega.

[Clique aqui para saber mais](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Como usar seed addresses no Adobe Campaign? {#how-to-use-seed-addresses-in-adobe-campaign-}

Seed addresses são usados para direcionar destinatários que não correspondem aos critérios de destino definidos. Esses destinatários são adicionados ao público-alvo: eles podem ser importados ou criados diretamente na entrega ou na campanha. Para entregas de mala direta, eles são adicionados durante a extração e combinados no documento de saída.

Temos assim os seguintes benefícios:

* Substituição aleatória de campos por dados de perfis de destinatários: isso permite inserir somente o endereço de e-mail, por exemplo, na seção do seed address.
* Ao usar um fluxo de trabalho com funcionalidades de gestão de dados, os dados adicionais processados nas entregas podem ser inseridos no nível do seed address para forçar valores, evitando assim a substituição de valores aleatórios.

[Clique aqui para obter mais informações sobre seed addresses](../../delivery/using/about-seed-addresses.md) .

### Como posso configurar um processo de aprovação antes de enviar mensagens? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Para detectar possíveis erros na configuração da mensagem, a Adobe recomenda configurar um ciclo de validação de delivery. Verifique se o conteúdo é aprovado com a frequência necessária enviando provas para testar os destinatários. Uma prova deve ser enviada toda vez que uma alteração for feita, para aprovar o conteúdo.

[Clique aqui para saber mais](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### O que é uma regra de tipologia? {#what-is-a-typology-rule-}

Para evitar conflitos entre campanhas, o Adobe Campaign pode testar várias combinações aplicando regras de restrição específicas. Isso garante que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, de acordo com as políticas de comunicação da empresa.

[Clique aqui para saber mais](../../campaign-opt/using/about-campaign-typologies.md).

## Envie suas mensagens {#send-your-messages}

Saiba como enviar mensagens em vários canais com o Adobe Campaign.

### Como posso enviar emails em ondas? {#how-can-i-send-emails-in-waves-}

Antes de enviar uma entrega a uma grande população, você pode [configurar ondas](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) para dividir as mensagens em vários lotes e equilibrar a carga.

### Quais são as principais etapas para criar um email no Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Depois que a entrega do e-mail é criada e validada, é possível enviá-la. Você pode decidir enviar o email para o target principal imediatamente ou agendar o delivery para uma data posterior. Se necessário, antes disso, você também pode estimar o público-alvo.

[Clique aqui para saber mais](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Como agendar uma entrega? {#how-to-schedule-a-delivery-}

É possível adiar o envio de mensagens para agendar a entrega ou gerenciar a pressão de vendas e evitar o excesso de solicitações sobre uma população.

[Clique aqui para saber mais](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### Posso adicionar um anexo aos emails? {#can-i-add-an-attachment-to-emails-}

Com o Campaign Classic, você pode adicionar anexos personalizados aos seus emails.

[Clique aqui para saber mais sobre anexos de email](../../delivery/using/attaching-files.md).

## Acompanhe suas mensagens e avalie seu impacto {#track-your-messages-and-measure-their-impact}

Depois que as mensagens são enviadas, aprenda a controlar e medir seu impacto com o Adobe Campaign.

### Como posso configurar links rastreados em uma entrega de email? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

Para cada entrega, você pode rastrear a recepção das mensagens e a ativação dos links inseridos no conteúdo da mensagem. Isso permite rastrear o comportamento dos destinatários seguindo as ações de entrega que foram direcionadas.

Para cada URL de mensagem, você pode escolher se irá ativar o rastreamento, alterar o rótulo do link ou agrupar os links por categorias para fins de relatório, por exemplo.

[Clique aqui para saber mais](../../delivery/using/about-message-tracking.md) sobre como controlar suas mensagens no Campaign Classic.

### Onde posso acessar logs de entrega e rastreamento? {#where-can-i-access-delivery-and-tracking-logs-}

Saiba como controlar suas entregas e entender o comportamento dos destinatários [nesta página](../../delivery/using/delivery-dashboard.md).

### Onde posso obter relatórios de entrega? {#where-can-i-get-delivery-reports-}

O Adobe Campaign vem com um conjunto de relatórios para monitorar suas entregas e rastrear suas mensagens.

[Clique aqui para saber mais sobre relatórios internos](../../reporting/using/delivery-reports.md).

### Como o Adobe Campaign qualifica e gerencia endereços em quarentena? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

O Adobe Campaign gerencia uma lista de endereços em quarentena. Os destinatários cujo endereço está em quarentena são excluídos por padrão durante a análise de entrega e não serão direcionados. Um endereço de e-mail pode ser colocado em quarentena, por exemplo, quando a caixa de correio está cheia ou se o endereço não existe.

[Clique aqui para saber mais sobre gerenciamento de quarentena](../../delivery/using/understanding-quarantine-management.md).
