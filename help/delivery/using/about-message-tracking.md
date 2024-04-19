---
product: campaign
title: Introdução ao rastreamento
description: Saiba mais sobre as diretrizes gerais para rastreamento no Adobe Campaign
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '692'
ht-degree: 100%

---

# Introdução ao rastreamento de mensagens {#get-started-tracking}



Graças às funcionalidades de rastreamento, o Adobe Campaign permite que você rastreie as mensagens enviadas e verifique o comportamento dos destinatárioes: abrir, clicar em links, cancelamento de subscrição, etc.

Essas informações são recuperadas na guia **[!UICONTROL Tracking]** do perfil de cada destinatário da entrega. Esta guia apresenta todos os links de URL rastreados e clicados pelo destinatário selecionado na lista. Esse é o acúmulo de todos os URLs rastreados nas entregas que ainda estão na tela de envio. A lista pode ser configurada e normalmente contém: o URL clicado, a data e a hora do clique e o documento no qual o URL foi localizado. Para obter mais informações, consulte [esta seção](../../platform/using/editing-a-profile.md#tracking-tab).

O **painel de entrega** também é fundamental para monitorar suas entregas e eventuais problemas encontrados durante o envio de mensagens. Para obter mais informações, consulte [esta seção](delivery-dashboard.md).

O diagrama a seguir mostra os estágios da caixa de diálogo entre o usuário e os vários servidores.

![](assets/tracking-diagram.png)

## Configurar rastreamento {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Princípio operacional**

Antes de usar o rastreamento, é necessário configurá-lo para a sua instância. [Saiba mais](../../installation/using/deploying-an-instance.md#operating-principle)

**Servidor de rastreamento**

Para configurar o rastreamento, sua instância deve ser declarada e registrada nos servidores de rastreamento. [Saiba mais](../../installation/using/deploying-an-instance.md#tracking-server)

**Salvar o rastreamento**

Depois que o rastreamento é configurado e os URLs são preenchidos, o servidor de rastreamento deve ser registrado. [Saiba mais](../../installation/using/deploying-an-instance.md#saving-tracking)

## Rastreamento de mensagens {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Links rastreados**

Você pode rastrear a recepção de mensagens e a ativação dos links inseridos no conteúdo da mensagem para entender melhor o comportamento dos destinatários. [Saiba mais](how-to-configure-tracked-links.md)

**Rastreamento de URL**

As opções de rastreamento podem ser configuradas por meio da ativação ou desativação de URLs rastreados. [Saiba mais](personalizing-url-tracking.md)

**Personalização do link rastreado**

Os recursos de rastreamento de Campaign Classic permitem que você adicione links em emails que podem ser personalizados e que oferecem suporte ao rastreamento. [Saiba mais](tracking-personalized-links.md)

**Logs de rastreamento**

O fluxo de trabalho técnico de rastreamento recupera os dados de rastreamento depois que a entrega é enviada e o rastreamento ativado. Esses dados podem ser encontrados na guia Rastreamento da sua entrega. [Saiba mais](accessing-the-tracking-logs.md)

**Testar o rastreamento**

Antes de enviar as mensagens com o rastreamento, você pode testar o rastreamento na mirror page, em logs de email e em links. [Saiba mais](testing-tracking.md)

## Rastreamento de aplicativo web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Rastreamento de uma aplicação web**

Também é possível rastrear e medir visitas em páginas de aplicação web com tags de rastreamento. Essa funcionalidade pode ser usada para todos os tipos de aplicativo Web, como formulários e landing pages. [Saiba mais](../../web/using/tracking-a-web-application.md)

**Recusar rastreamento da aplicação web**

A opção de recusar o rastreamento de aplicações web permite que você interrompa o rastreamento dos comportamentos da Web de usuários finais que recusam o rastreamento comportamental. Você pode incluir a capacidade de exibir um banner em aplicações web ou landing pages para permitir que os usuários recusem. [Saiba mais](../../web/using/web-application-tracking-opt-out.md)

## Rastreamento de relatórios {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Estatísticas de rastreamento**

Este relatório fornece estatísticas sobre aberturas, cliques e transações e permite rastrear o impacto de marketing da entrega. [Saiba mais](../../reporting/using/delivery-reports.md#tracking-statistics)

**Fluxos de clique e URLs**

Este relatório mostra a lista de páginas visitadas após uma entrega. [Saiba mais](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Pessoa/pessoas e destinatários**

Entenda melhor a diferença de rastreamento entre uma pessoa/pessoas e um destinatário no Adobe Campaign com este exemplo. [Saiba mais](../../reporting/using/person-people-recipients.md)

**Indicadores de rastreamento**

Este relatório combina os principais indicadores para rastrear o comportamento dos destinatários ao receber a entrega, como abertura, taxas de click-through e fluxos de cliques. [Saiba mais](../../reporting/using/delivery-reports.md#tracking-indicators)

**Cálculo do indicador**

As diferentes tabelas fornecem a lista de indicadores usados nos diferentes relatórios e suas fórmulas de cálculo, dependendo do tipo de entrega. [Saiba mais](../../reporting/using/indicator-calculation.md)

## Solução de problemas de rastreamento {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

As seguintes dicas de solução de problemas ajudarão você a resolver os problemas mais comuns que ocorrem ao usar o rastreamento no Adobe Campaign Classic. Para obter uma solução de problemas mais avançada, consulte [esta seção](tracking-troubleshooting.md).

* Verifique se o processo trackinglogd está em execução

  Esse processo lê a memória compartilhada do IIS/Servidor Web e grava os logs de redirecionamento.

  Você pode acessá-la na Página inicial selecionando a guia Monitoramento na sua instância. Você também pode executar o seguinte comando na instância: `<user>@<instance>:~$ nlserver pdump`

  Se o processo trackinglogd não aparecer na lista, inicie-o com o seguinte comando na instância: `<user>@<instance>:~$ nlserver start trackinglogd`

* Verifique se o fluxo de trabalho técnico de Rastreamento foi executado recentemente.

  Você pode localizar o fluxo de trabalho técnico de Rastreamento nas pastas de workflows técnicos da > Produção > de Administração.
