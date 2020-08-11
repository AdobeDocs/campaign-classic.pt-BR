---
title: Verificar antes de enviar
seo-title: Verificar antes de enviar
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 36%

---


# Executar todas as verificações antes de enviar {#perform-all-checks}

Quando a mensagem estiver pronta, certifique-se de que seu conteúdo está sendo exibido corretamente, em todos os dispositivos, e de que não contém erros, como personalização incorreta ou links quebrados.

Antes de enviar sua mensagem, verifique também se os parâmetros e a configuração estão consistentes na entrega.

## Por que a validação é chave {#validation-is-key}

Antes de enviar uma entrega, você precisa garantir que seus destinatários receberão a mensagem que você realmente deseja enviar. Para fazer isso, é necessário validar o conteúdo da mensagem e os parâmetros do delivery.

Esta etapa permite que você detecte possíveis erros e os corrija antes de entregar para o público alvo principal.

As etapas para validar um delivery são apresentadas [nesta seção](../../delivery/using/steps-validating-the-delivery.md).

## Renderização da caixa de entrada {#inbox-and-email-rendering}

A renderização da caixa de entrada permite que você pré-visualização suas mensagens nos principais clientes de email, verifique o conteúdo e a reputação, descubra como os recipient estão lendo as mensagens.

**Dicas**:

* Você pode visualização a mensagem enviada nos diferentes contextos nos quais ela pode ser recebida: webmail, serviço de mensagens, celular etc.

* Os recursos de renderização da caixa de entrada são cruciais para identificar se suas campanhas de email ultrapassam com êxito os filtros dos principais ISPs (Provedores de serviço da Internet) e serviços de email. Essas ferramentas enviam uma cópia de pré-impressão de um email para uma rede de caixas de entrada de teste, para que você possa ver como a mensagem será exibida ou irá renderizar nesses serviços. Elas também podem incluir relatórios e opções de correção de código que ajudam a identificar e fazer correções rapidamente que melhoram o deliverability.

Learn more [in this section](../../delivery/using/inbox-rendering.md).

## Mensagens de prova {#proof-messages}

O envio de provas permite que você verifique o link de opção de não participação, o mirror page e quaisquer outros links, valide a mensagem, verifique se as imagens são exibidas, detecte possíveis erros etc. Você também pode verificar seu design e renderização em diferentes dispositivos.

Learn more [in this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Configurar delivery de teste A/B {#a-b-testing-deliveries}

Se você tiver vários conteúdos para um delivery de email, poderá usar o teste A/B para descobrir qual versão terá o maior impacto na população-alvo.

**Dicas**:

* Envie as diferentes versões para alguns dos seus destinatários

* Selecione aquele com a maior taxa de sucesso e envie-o para o restante do seu público alvo

Learn more [in this section](../../workflow/using/a-b-testing.md).

## Certifique-se de que sua mensagem foi entregue {#make-sure-your-message-is-delivered}

Como etapa final, maximize suas chances e aproveite o poder do Adobe Campaign Classic para garantir que sua mensagem seja de fato entregue aos destinatários relevantes.

### Passe por um processo de validação

Você pode definir um processo de validação completo, envolvendo operadores e grupos do Adobe Campaign, para validar tanto o destino quanto o conteúdo da mensagem. Isso garantirá o monitoramento e o controle completos dos vários processos da campanha: definição de metas, conteúdo, orçamento, extração e envio de uma prova. Dependendo de suas permissões, os usuários serão notificados, receberão provas e poderão validar ou rejeitar a mensagem. Learn more [in this section](../../campaign/using/marketing-campaign-approval.md#approval-process).

### Usar ondas

Você pode aumentar progressivamente o volume enviado usando o ondas. Isso evitará que suas mensagens sejam marcadas como spam ou quando você quiser restringir o número de mensagens por dia. Ao usar ondas, você pode dividir as entregas em vários lotes, em vez de enviar grandes volumes de mensagens ao mesmo tempo. Learn more [in this section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Priorizar mensagens

Você pode definir a ordem de envio para seus delivery declarando o nível de prioridade. Para fazer isso:

1. Edite as propriedades do delivery e selecione a **[!UICONTROL Delivery]** guia.

1. Defina o nível de prioridade do delivery em uma escala de **[!UICONTROL Very low]** para **[!UICONTROL Very high]**.

>[!NOTE]
>
>Não é possível definir a ordem de envio de mensagens a partir de um delivery.

### Configurar Afinidades IP

Para controlar melhor o tráfego SMTP de saída, é possível gerenciar afinidades definindo quais endereços IP específicos podem ser usados para cada afinidade. Isso permite a restrição do número de emails para envios específicas em máquinas ou endereços de saída. Por exemplo, você pode usar uma afinidade por país ou subdomínio. Em seguida, é possível criar uma tipologia por país e vincular cada afinidade à tipologia correspondente.

Você pode:

* Defina as afinidades IP no arquivo de configuração serverConf.xml. [Saiba mais](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Para cada elemento IPAffinity, declare os endereços IP que podem ser usados. [Saiba mais](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Na [tipologia](../../campaign/using/about-campaign-typologies.md) de sua escolha, use o **[!UICONTROL Managing affinities with IP addresses]** campo para vincular delivery ao servidor do delivery (MTA) que gerencia a afinidade. [Saiba mais](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Depois que o email for enviado, verifique o cabeçalho para verificar de qual endereço IP o delivery foi enviado. O administrador de e-mail deve ajudá-lo a obter as informações do cabeçalho.

>[!NOTE]
>
>A maioria dessas etapas só pode ser executada por um usuário especialista.

### Usar tipologias

Você pode usar o regra de tipologia para excluir parte do público alvo com base em critérios específicos. Isso garante que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, de acordo com as políticas de comunicação da empresa. Por exemplo, você pode filtrar os destinatários menores de idade do público-alvo do seu boletim informativo. Saiba mais [neste exemplo](../../campaign/using/filtering-rules.md).

### Evitar anexos

Os anexos continuam sendo um dos vetores mais comuns para a proliferação de malware, principalmente quando enviados em massa. Inclua um link seguro no documento em vez de anexá-lo. Isso garante uma camada adicional de segurança para impedir a redistribuição não intencional e reduz consideravelmente as chances de a mensagem ser rejeitada em gateways de entrada de email por motivos de tamanho de mensagem ou de segurança.
