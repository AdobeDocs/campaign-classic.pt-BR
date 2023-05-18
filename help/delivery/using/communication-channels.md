---
product: campaign
title: Canais de comunicação
description: Criar deliveries para enviar mensagens personalizadas em diferentes canais
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '1204'
ht-degree: 100%

---

# Canais de comunicação{#communication-channels}



Com o Adobe Campaign, você pode enviar campanhas em vários canais, incluindo emails, SMS, mensagens pelo LINE, notificações por push e correspondência direta, e medir sua eficácia usando vários [relatórios](../../reporting/using/delivery-reports.md) exclusivos. Essas mensagens são projetadas e enviadas por deliveries, além disso podem ser personalizadas para cada recipient.

As funcionalidades principais incluem definição de metas, definição e personalização de mensagens, execução de comunicações e relatórios operacionais associados. O principal ponto de acesso funcional é o assistente de delivery. Esse ponto de acesso leva a vários recursos cobertos pelo Adobe Campaign.

>[!NOTE]
>
>O Adobe Campaign oferece um conjunto de ferramentas para monitorar sua capacidade de delivery e otimizar o envio de emails. Saiba mais [nesta seção](about-deliverability.md).

O envio de deliveries pode ser automatizado preparando-se um delivery e/ou enviando-o no processo de um workflow. Para obter mais informações sobre atividades do tipo delivery em workflows, consulte [esta seção](../../workflow/using/about-action-activities.md).

O Adobe Campaign oferece os seguintes canais de entrega:

1. **Canal de email**: deliveries de email permitem enviar emails personalizados para a população do target. Consulte [Sobre o canal de email](about-email-channel.md).
1. **Canal de mala direta**: deliveries de mala direta permitem gerar um arquivo de extração que contém dados sobre a população do target. Consulte [Sobre o canal de correspondência direta](about-direct-mail-channel.md)
1. **Canal móvel**: deliveries em canais móveis permitem enviar mensagens SMS ou por LINE personalizadas para a população do target. Consulte [Canal de SMS](sms-channel.md).
1. **Canal de aplicativo móvel**: os deliveries por aplicativo móvel permitem enviar as notificações para sistemas iOs e Android. Consulte o capítulo [Canal de aplicativo móvel](about-mobile-app-channel.md).

   Outros canais são descritos [nesta página](steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >O número de canais disponíveis depende do seu contrato. Verifique o contrato de licença.

Os deliveries podem ser realizados **online** (via email, um dos canais móveis e notificações por push) e **offline** (canal de mala direta).

Dependendo do canal, os modos de delivery poderão ser:

* Delivery direta em massa via Adobe Campaign (modo padrão para canal de email).
* Delivery externo por meio de um operador especialista que recebe o arquivo de saída gerado pelo assistente de delivery (modo padrão para o canal de mala direta).

As contas externas são configuradas por meio do nó **[!UICONTROL Administration > Platform > External accounts]**. Essa configuração deve ser executada somente por usuários avançados.

## Entregas de email {#email-deliveries}

O [Canal de email](about-email-channel.md) é um dos canais principais do Adobe Campaign, permitindo agendar e enviar emails personalizados para targets específicos.

Você pode enviar diferentes tipos de emails:

* Emails de envio único: emails que você pode enviar uma vez para um target definido. Normalmente, eles são usados para promover um conteúdo específico que seria preparado e enviado apenas uma vez (boletim informativo, email promocional etc.).
* Emails recorrentes: em uma campanha, envie o mesmo email regularmente e agregue cada envio e seus relatórios periodicamente. O mesmo email é enviado, mas geralmente para um target diferente, com base no target qualificado do dia do envio. Um exemplo comum é um email de aniversário. Para obter mais informações, consulte [Deliveires recorrentes](../../workflow/using/recurring-delivery.md).
* Emails transacionais: emails unitários que são acionados com base no comportamento dos clientes. Consulte [Mensagens transacionais](../../message-center/using/about-transactional-messaging.md).

Para saber mais sobre o uso de delivery e recomendações, consulte [Práticas recomendadas de Delivery](delivery-best-practices.md) de campanha .

Para obter mais informações sobre tipos diferentes de entrega, consulte [esta página](#types-of-deliveries).

## Entregas por dispositivos móveis {#mobile-deliveries}

O Adobe Campaign permite que você faça deliveires de mensagens por [SMS](sms-channel.md) e [LINE](line-channel.md) em celulares.

Para mensagens SMS, você poderá criar, modificar e personalizar mensagens somente no formato de texto. Você também poderá visualizar suas mensagens SMS antes de enviá-las.

Para mensagens por LINE, você poderá enviar texto ou imagens e links.

Para fazer delivery de mensagens SMS ou LINE a um celular, você vai precisar de:

* Uma conta externa configurada no canal **[!UICONTROL Mobile (SMS)]** ou no canal **[!UICONTROL LINE]**.
* Um modelo de entrega por SMS ou LINE que esteja vinculado corretamente a essa conta externa.

## Notificações por push {#push-notifications}

O Adobe Campaign permite enviar [notificações por push](about-mobile-app-channel.md) personalizadas e segmentadas em dispositivos móveis iOS e Android, por meio de aplicativos dedicados. Depois que as etapas de configuração e integração forem executadas, os deliveries do iOS e do Android poderão ser criados e enviados. Você também poderá criar notificações avançadas com imagens ou vídeos.

## Correspondência direta {#direct-mail}

A [mala direta](about-direct-mail-channel.md) é um canal offline que permite personalizar e gerar o arquivo exigido por provedores de mala direta. Ela oferece a possibilidade de misturar canais online e offline nas jornadas do cliente.

Os canais online permitem que você crie mensagens (email, SMS, delivery de aplicativo móvel, etc.) e envie-as para seu público diretamente do Adobe Campaign. Com canais offline, é diferente. Quando você prepara um delivery direto de correspondência direta, o Adobe Campaign gera um arquivo incluindo todos os perfis do target e as informações de contato escolhidas (endereço postal por exemplo). Você poderá enviar esse arquivo para seu provedor de correspondência direta que irá cuidar realmente do envio.

## Outros canais {#other-channels}

O modelo de entrega do Adobe Campaign oferece o Telephone, usado para criar entregas externas. A utilização desse canal implica que você configure metodologias específicas para processar arquivos de output. As etapas de configuração são as mesmas do [Canal de correspondência direta](about-direct-mail-channel.md).

>[!NOTE]
>
>O canal Telephone não está disponível prontamente. A implementação requer o envolvimento da Adobe Consulting ou de um Parceiro da Adobe. Entre em contato com seu representante da Adobe para obter mais informações.

Além disso, os deliveries do tipo &quot;Outros&quot; usam um template técnico específico que não executa um processo: isso permite gerenciar ações de marketing executadas fora da plataforma Adobe Campaign.

Este canal não tem nenhum mecanismo específico. É um canal genérico que tem sua própria opção de roteamento de conta externa, tipo de template do delivery e atividade de workflow de campanha, como qualquer outro canal de comunicação disponível no Adobe Campaign.

Esse canal foi projetado apenas para fins descritivos, por exemplo, para definir deliveries para os quais você deseja manter um rastreamento do público-alvo de uma campanha executada em uma ferramenta diferente do Adobe Campaign.

## Tipos de entregas{#types-of-deliveries}

Existem três tipos de objetos de entrega no Campaign:

### Entrega única {#single-delivery}

Um **delivery** é um objeto de delivery independente executado uma vez. Ele pode ser duplicado, preparado novamente, mas, desde que esteja no seu estado final (cancelado, interrompido, concluído), não poderá ser reutilizado.

Os deliveries podem ser criados a partir da lista de deliveries ou em um fluxo de trabalho através de uma atividade de [Delivery](../../workflow/using/delivery.md) .

Os workflows também fornecem atividades de delivery específicas de acordo com o tipo de canal que você deseja usar. Para obter mais informações sobre essas atividades, consulte [esta seção](../../workflow/using/cross-channel-deliveries.md).

### Entrega recorrente {#recurring-delivery}

Um **delivery recorrente** permite criar um novo delivery sempre que a atividade for executada. Isso evita que você crie um novo delivery para tarefas recorrentes.

Como exemplo, se você executar esse tipo de atividade uma vez por mês, acabará com 12 deliveries após um ano.

Os deliveries recorrentes são criados em workflows através da [atividade Recurring delivery.](../../workflow/using/recurring-delivery.md) Um exemplo dessa atividade que está sendo usada é apresentado nesta seção: [Criação de um delivery recorrente em um workflow de direcionamento](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Entrega contínua {#continuous-delivery}

Um **delivery contínuo** permite que você adicione novos recipients a um delivery existente, o que evita a necessidade de criar um novo delivery a cada execução.

Se uma informação no delivery for alterado (conteúdo, nome, etc.), um novo objeto de delivery será criado na execução do delivery. Se nenhuma informação for alterada, o mesmo objeto do delivery será reutilizado e os logs de delivery e rastreamento serão adicionados no mesmo objeto.

Como exemplo, se você executar esse tipo de atividade uma vez por mês, acabará com um único delivery após um ano (desde que não tenha feito nenhuma alteração no delivery).

Os deliveries contínuos são criados em workflows através da [atividade Continuous delivery](../../workflow/using/continuous-delivery.md).
