---
product: campaign
title: Canais de comunicação
description: Criar entregas para enviar mensagens personalizadas em diferentes canais
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: ht
source-wordcount: '1214'
ht-degree: 100%

---

# Canais de comunicação{#communication-channels}

Com o Adobe Campaign, você pode enviar campanhas em vários canais, incluindo emails, SMS, mensagens pelo LINE, notificações por push e correspondência direta, e medir sua eficácia usando vários [relatórios](../../reporting/using/delivery-reports.md) exclusivos. Essas mensagens são projetadas e enviadas em entregas, além disso podem ser personalizadas para cada destinatário.

As funcionalidades principais incluem definição de metas, definição e personalização de mensagens, execução de comunicações e relatórios operacionais associados. O principal ponto de acesso funcional é o assistente de entrega. Esse ponto de acesso leva a vários recursos cobertos pelo Adobe Campaign.

>[!NOTE]
>
>O Adobe Campaign oferece um conjunto de ferramentas para monitorar sua capacidade de entrega e otimizar o envio de emails. Saiba mais [nesta seção](about-deliverability.md).

O envio de entregas pode ser automatizado preparando-se uma entrega e/ou enviando-a no processo de um workflow. Para obter mais informações sobre atividades do tipo entrega em workflows, consulte [esta seção](../../workflow/using/about-action-activities.md).

O Adobe Campaign oferece os seguintes canais de entrega:

1. **Canal de email**: entregas de email permitem enviar emails personalizados para a população do target. Consulte [Sobre o canal de email](about-email-channel.md).
1. **Canal de mala direta**: entregas de mala direta permitem gerar um arquivo de extração que contém dados sobre a população do target. Consulte [Sobre o canal de correspondência direta](about-direct-mail-channel.md)
1. **Canal móvel**: entregas em canais móveis permitem enviar mensagens SMS ou por LINE personalizadas para a população do target. Consulte [Canal de SMS](sms-channel.md).
1. **Canal de aplicativo móvel**: as entregas por aplicativo móvel permitem enviar as notificações para sistemas iOs e Android. Consulte o capítulo [Canal de aplicativo móvel](about-mobile-app-channel.md).

   Outros canais são descritos [nesta página](#other-channels).

   >[!NOTE]
   >
   >O número de canais disponíveis depende do seu contrato. Verifique o contrato de licença.

As entregas podem ser realizadas **online** (via email, um dos canais móveis e notificações por push) e **offline** (canal de mala direta).

Dependendo do canal, os modos de entrega poderão ser:

* Entrega direta em massa via Adobe Campaign (modo padrão para canal de email).
* Entrega externa por meio de um operador especializado que recebe o arquivo de saída gerado pelo assistente de entrega (modo padrão para o canal de correspondência direta).

As contas externas são configuradas por meio do nó **[!UICONTROL Administration > Platform > External accounts]**. Essa configuração deve ser executada somente por usuários avançados.

## Entregas de email {#email-deliveries}

O [Canal de email](about-email-channel.md) é um dos canais principais do Adobe Campaign, permitindo agendar e enviar emails personalizados para targets específicos.

Você pode enviar diferentes tipos de emails:

* Emails de envio único: emails que você pode enviar uma vez para um target definido. Normalmente, eles são usados para promover um conteúdo específico que seria preparado e enviado apenas uma vez (boletim informativo, email promocional etc.).
* Emails recorrentes: em uma campanha, envie o mesmo email regularmente e agregue cada envio e seus relatórios periodicamente. O mesmo email é enviado, mas geralmente para um target diferente, com base no target qualificado do dia do envio. Um exemplo comum é um email de aniversário. Para obter mais informações, consulte [Entregas recorrentes](../../workflow/using/recurring-delivery.md).
* Emails transacionais: emails unitários que são acionados com base no comportamento dos clientes. Consulte [Mensagens transacionais](../../message-center/using/about-transactional-messaging.md).

Para saber mais sobre o uso de entrega e recomendações, consulte [Práticas recomendadas de entrega](delivery-best-practices.md) de campanha.

Para obter mais informações sobre tipos diferentes de entrega, consulte [esta página](#types-of-deliveries).

## Entregas por dispositivos móveis {#mobile-deliveries}

O Adobe Campaign permite que você faça entrega de mensagens por [SMS](sms-channel.md) e [LINE](line-channel.md) em celulares.

Para mensagens SMS, você poderá criar, modificar e personalizar mensagens somente no formato de texto. Você também poderá visualizar suas mensagens SMS antes de enviá-las.

Para mensagens por LINE, você poderá enviar texto ou imagens e links.

Para fazer entrega de mensagens SMS ou LINE a um celular, você vai precisar de:

* Uma conta externa configurada no canal **[!UICONTROL Mobile (SMS)]** ou no canal **[!UICONTROL LINE]**.
* Um modelo de entrega por SMS ou LINE que esteja vinculado corretamente a essa conta externa.

## Notificações por push {#push-notifications}

O Adobe Campaign permite enviar [notificações por push](about-mobile-app-channel.md) personalizadas e segmentadas em dispositivos móveis iOS e Android, por meio de aplicativos dedicados. Depois que as etapas de configuração e integração forem executadas, as entregas do iOS e do Android poderão ser criadas e enviadas. Você também poderá criar notificações avançadas com imagens ou vídeos.

## Correspondência direta {#direct-mail}

A [mala direta](about-direct-mail-channel.md) é um canal offline que permite personalizar e gerar o arquivo exigido por provedores de mala direta. Ela oferece a possibilidade de misturar canais online e offline nas jornadas do cliente.

Os canais online permitem que você crie mensagens (email, SMS, entrega de aplicativo móvel, etc.) e envie-as para seu público diretamente do Adobe Campaign. Com canais offline, é diferente. Quando você prepara uma entrega de correspondência direta, o Adobe Campaign gera um arquivo incluindo todos os perfis do target e as informações de contato escolhidas (endereço postal por exemplo). Você poderá enviar esse arquivo para seu provedor de correspondência direta que irá cuidar realmente do envio.

## Outros canais {#other-channels}

O modelo de entrega do Adobe Campaign oferece o Telephone, usado para criar entregas externas. A utilização desse canal implica que você configure metodologias específicas para processar arquivos de output. As etapas de configuração são as mesmas do [Canal de correspondência direta](about-direct-mail-channel.md).

>[!NOTE]
>
>O canal Telephone não está disponível prontamente. A implementação requer o envolvimento da Adobe Consulting ou de um Parceiro da Adobe. Entre em contato com seu representante da Adobe para obter mais informações.

Além disso, as entregas do tipo &quot;Outros&quot; usam um template técnico específico que não executa um processo: isso permite gerenciar ações de marketing executadas fora da plataforma Adobe Campaign.

Este canal não tem nenhum mecanismo específico. É um canal genérico que tem sua própria opção de roteamento de conta externa, tipo de template da entrega e atividade de workflow de campanha, como qualquer outro canal de comunicação disponível no Adobe Campaign.

Esse canal foi projetado apenas para fins descritivos, por exemplo, para definir entregas para as quais você deseja manter um rastreamento do público-alvo de uma campanha executada em uma ferramenta diferente do Adobe Campaign.

## Tipos de entregas{#types-of-deliveries}

Existem três tipos de objetos de entrega no Campaign:

### Entrega única {#single-delivery}

Uma **entrega** é um objeto de entrega independente executado uma vez. Ele pode ser duplicado, preparado novamente, mas, desde que esteja no seu estado final (cancelado, interrompido, concluído), não poderá ser reutilizado.

As entregas podem ser criadas a partir da lista de entregas ou em um fluxo de trabalho através de uma atividade de [Entrega](../../workflow/using/delivery.md) .

Os workflows também fornecem atividades de entrega específicas de acordo com o tipo de canal que você deseja usar. Para obter mais informações sobre essas atividades, consulte [esta seção](../../workflow/using/cross-channel-deliveries.md).

### Entrega recorrente {#recurring-delivery}

Uma **entrega recorrente** permite criar uma nova entrega sempre que a atividade for executada. Isso evita que você crie uma nova entrega para tarefas recorrentes.

Como exemplo, se você executar esse tipo de atividade uma vez por mês, acabará com 12 entregas após um ano.

As entregas recorrentes são criadas em workflows através da [atividade Entrega recorrente.](../../workflow/using/recurring-delivery.md) Um exemplo dessa atividade que está sendo usada é apresentado nesta seção: [Criação de uma entrega recorrente em um workflow de direcionamento](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Entrega contínua {#continuous-delivery}

Uma **entrega contínua** permite que você adicione novos destinatários a uma entrega existente, o que evita a necessidade de criar uma nova entrega a cada execução.

Se uma informação na entrega for alterado (conteúdo, nome, etc.), um novo objeto de entrega será criado na execução da entrega. Se nenhuma informação for alterada, o mesmo objeto da entrega será reutilizado e os logs de entrega e rastreamento serão adicionados no mesmo objeto.

Como exemplo, se você executar esse tipo de atividade uma vez por mês, acabará com uma única entrega após um ano (desde que não tenha feito nenhuma alteração na entrega).

As entregas contínuas são criadas em workflows através da [atividade Entrega contínua](../../workflow/using/continuous-delivery.md).
