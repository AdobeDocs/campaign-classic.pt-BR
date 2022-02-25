---
product: campaign
title: Verificar antes de enviar
description: Quando a mensagem estiver pronta, execute todas as verificações antes de enviar
feature: Deliverability
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 808f459a0b77b1787fc017c031247ab268b5aafa
workflow-type: ht
source-wordcount: '892'
ht-degree: 100%

---

# Executar todas as verificações antes de enviar {#perform-all-checks}

![](../../assets/common.svg)

Quando a mensagem estiver pronta, certifique-se de que seu conteúdo está sendo exibido corretamente, em todos os dispositivos, e de que não contém erros, como personalização incorreta ou links quebrados.

Antes de enviar a mensagem, verifique também se os parâmetros e a configuração estão consistentes com o delivery.

## Importância da validação {#validation-is-key}

Antes de enviar um delivery, você precisa garantir que seus recipients receberão a mensagem que você realmente deseja enviar. Para fazer isso é necessário validar o conteúdo da mensagem e os parâmetros do delivery.

Esta etapa permite detectar e corrigir possíveis erros antes de fazer um delivery ao público-alvo principal.

As etapas para validar um delivery são apresentadas [nesta seção](steps-validating-the-delivery.md).

## Renderização da caixa de entrada {#inbox-and-email-rendering}

A renderização da caixa de entrada permite pré-visualizar as mensagens nos principais clientes de email, verificar o conteúdo e a reputação e descobrir como os recipients estão lendo as mensagens.

**Dicas**:

* Você pode visualizar a mensagem enviada nos diferentes contextos nos quais ela pode ser recebida: webmail, serviço de mensagens, celular, etc.

* Os recursos de renderização da caixa de entrada são cruciais para identificar se suas campanhas de email terão êxito em atravessar os filtros dos principais ISPs (Provedores de serviço de internet) e serviços de webmail. Essas ferramentas enviam uma cópia de pré-impressão de um email para uma rede de caixas de entrada de teste, para que você possa ver como a mensagem será exibida ou irá renderizar nesses serviços. Elas também podem incluir relatórios e opções de correção de código que ajudam a identificar e fazer correções rapidamente que melhoram a capacidade de entrega.

Saiba mais [nesta seção](inbox-rendering.md).

## Mensagens de prova {#proof-messages}

O envio de provas permite a verificação do link de opção de não participação, a mirror page e quaisquer outros links, validação da mensagem, verificação da exibição das imagens, detecção de possíveis erros, etc. Você também pode verificar seu design e renderização em diferentes dispositivos.

Saiba mais [nesta seção](steps-validating-the-delivery.md#sending-a-proof).

## Configurar entregas de teste A/B {#a-b-testing-deliveries}

Se você tiver vários conteúdos para um delivery de email, poderá usar o teste A/B para descobrir qual versão terá o maior impacto na população direcionada.

**Dicas**:

* Envie as diferentes versões para alguns dos seus recipients

* Selecione aquela com a maior taxa de sucesso e envie-a para o restante do seu público-alvo

Saiba mais [nesta seção](get-started-a-b-testing.md).

## Verificar se a mensagem foi entregue {#make-sure-your-message-is-delivered}

Como etapa final, maximize suas chances e aproveite o potencial do Adobe Campaign Classic para garantir que sua mensagem seja de fato entregue aos recipients relevantes.

### Passar por um processo de validação

Você pode definir um processo de validação completo, envolvendo operadores e grupos do Adobe Campaign, para validar tanto o público-alvo quanto o conteúdo da mensagem. Dessa forma, será possível monitorar e controlar totalmente os diversos processos da campanha: direcionamento, conteúdo, orçamento, extração e envio de prova. Dependendo das suas permissões, os usuários serão notificados, receberão provas e poderão validar ou rejeitar a mensagem. Saiba mais [nesta seção](../../campaign/using/marketing-campaign-approval.md).

### Usar ondas

Você pode aumentar progressivamente o volume enviado usando ondas. Esse aumento evitará que sua mensagem seja marcada como spam ou pode ser usado quando você quiser restringir o número de mensagens diárias. Ao usar ondas, você pode dividir os deliveries em vários lotes, em vez de enviar grandes volumes de mensagens ao mesmo tempo. Saiba mais [nesta seção](steps-sending-the-delivery.md#sending-using-multiple-waves).

### Priorizar mensagens

Você pode definir a ordem de envio para seus deliveries, informando o nível de prioridade. Para fazer isso:

1. Edite as propriedades do delivery e selecione a guia **[!UICONTROL Delivery]**.

1. Defina o nível de prioridade do delivery em uma escala de **[!UICONTROL Very low]** a **[!UICONTROL Very high]**.

>[!NOTE]
>
>Não é possível definir a ordem de envio de mensagens a partir de um delivery.

### Configurar afinidades de IP

Para controlar melhor o tráfego SMTP de saída, é possível gerenciar afinidades definindo quais endereços IP específicos podem ser usados para cada afinidade. Isso permite a restrição do número de emails para envios específicos em máquinas ou endereços de saída. Você pode, por exemplo, usar uma afinidade por país ou subdomínio. Em seguida, é possível criar uma tipologia por país e vincular cada afinidade à tipologia correspondente.

Você pode:

* Definir as afinidades de IP no arquivo de configuração serverConf.xml. [Saiba mais](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Informar os endereços IP que podem ser usados em cada elemento IPAffinity. [Saiba mais](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Na [tipologia](../../campaign-opt/using/about-campaign-typologies.md) de sua escolha, use o campo **[!UICONTROL Managing affinities with IP addresses]** para vincular deliveries ao servidor do delivery (MTA) que gerencia essa afinidade. [Saiba mais](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* Depois que o email for enviado, verifique o cabeçalho para saber a partir de qual endereço IP o delivery foi enviado. O administrador de email deve ajudar você a obter as informações do cabeçalho.

* Para deliveries de SMS, verifique se o canal SMS tem uma afinidade dedicada limitada a **um** container do servidor de aplicativos. [Saiba mais](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>A maioria dessas etapas pode ser executada somente por um usuário especialista.

### Usar tipologias

Você pode usar as regras de tipologia para excluir parte do público-alvo com base em critérios específicos. Isso garante que as mensagens enviadas atendam melhor às necessidades e expectativas dos clientes, de acordo com as políticas de comunicação da empresa. Por exemplo, você pode filtrar os recipients menores de idade do público-alvo do seu informativo. Saiba mais [neste exemplo](../../campaign-opt/using/filtering-rules.md).

### Evitar anexos

Os anexos continuam sendo um dos vetores mais comuns para a proliferação de malware, principalmente quando enviados em massa. Inclua um link seguro no documento em vez de anexá-lo. Isso garante uma camada adicional de segurança para impedir a redistribuição não intencional e reduz amplamente a chance de a mensagem ser rejeitada em gateways de entrada de email devido ao tamanho da mensagem ou por questões de segurança.
