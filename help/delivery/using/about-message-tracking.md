---
solution: Campaign Classic
product: campaign
title: Introdução ao rastreamento
description: Saiba mais sobre as diretrizes gerais para rastreamento no Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: e52d1963b72593c5dab8ced9e459d25b05044022
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 24%

---


# Introdução ao rastreamento de mensagens {#get-started-tracking}

Graças às suas funcionalidades de rastreamento, o Adobe Campaign permite rastrear as mensagens enviadas e verificar o comportamento dos recipients: abrir, clicar em links, cancelar assinatura etc.

Essas informações são recuperadas na guia **[!UICONTROL Tracking]** do perfil de cada recipient do delivery. Esta guia apresenta todos os links de URL rastreados e clicados pelo recipient selecionado na lista. Esse é o acúmulo de todos os URLs rastreados nas remessas que ainda estão na tela de envio. A lista pode ser configurada e normalmente contém: o URL clicado, a data e a hora do clique e o documento no qual o URL foi localizado. Para obter mais informações, consulte [esta seção](../../platform/using/editing-a-profile.md#tracking-tab).

O **painel de delivery** também é fundamental para monitorar seus deliveries e eventuais problemas encontrados durante o envio de mensagens. Para obter mais informações, consulte [esta seção](../../delivery/using/delivery-dashboard.md).

O diagrama a seguir mostra os estágios da caixa de diálogo entre o usuário e os vários servidores.

![](assets/tracking-diagram.png)

## Configurar o rastreamento {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Princípio operacional**

Antes de usar o rastreamento, é necessário primeiro configurá-lo para sua instância. [Saiba mais](../../installation/using/deploying-an-instance.md#operating-principle)

**Servidor de rastreamento**

Para configurar o rastreamento, sua instância deve ser declarada e registrada com os servidores de rastreamento. [Saiba mais](../../installation/using/deploying-an-instance.md#tracking-server)

**Salvar o rastreamento**

Depois que o rastreamento é configurado e seus URLs são preenchidos, o servidor de rastreamento deve ser registrado. [Saiba mais](../../installation/using/deploying-an-instance.md#saving-tracking)

## Rastreamento de mensagens {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Links rastreados**

Você pode rastrear a recepção das mensagens e a ativação dos links inseridos no conteúdo da mensagem para entender melhor o comportamento dos recipients. [Saiba mais](../../delivery/using/how-to-configure-tracked-links.md)

**Rastreamento de URL**

As opções de rastreamento podem ser configuradas ativando ou desativando URLs rastreadas. [Saiba mais](../../delivery/using/personalizing-url-tracking.md)

**Personalização de link rastreado**

Os recursos de rastreamento do Campaign Classic permitem adicionar links em emails que podem ser personalizados e que oferecem suporte ao rastreamento. [Saiba mais](../../delivery/using/tracking-personalized-links.md)

**Logs de rastreamento**

O workflow técnico Tracking recupera os dados de rastreamento depois que o delivery é enviado e o rastreamento é ativado. Esses dados podem ser encontrados na guia Tracking do delivery. [Saiba mais](../../delivery/using/accessing-the-tracking-logs.md)

**Testar o rastreamento**

Antes de enviar suas mensagens com o rastreamento, você pode testar o rastreamento na sua mirror page, registros de email e links. [Saiba mais](../../delivery/using/testing-tracking.md)

## Acompanhamento da aplicação web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Rastreamento de uma aplicação web**

Também é possível rastrear e medir visitas em páginas de aplicativos web com tags de rastreamento. Essa funcionalidade pode ser usada para todos os tipos de aplicações web, como formulários e pesquisas online. [Saiba mais](../../web/using/tracking-a-web-application.md)

**Opt out de rastreamento da aplicação web**

A recusa de rastreamento da aplicação web permite interromper o rastreamento de comportamentos da web de usuários finais que recusam o rastreamento comportamental. Você pode incluir a capacidade de exibir um banner em aplicações web ou landing pages para permitir que os usuários optem por não participar. [Saiba mais](../../web/using/web-application-tracking-opt-out.md)

## Relatórios de rastreamento {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Estatísticas de rastreamento**

Este relatório fornece estatísticas sobre aberturas, cliques e transações e permite rastrear o impacto de marketing do delivery. [Saiba mais](../../reporting/using/delivery-reports.md#tracking-statistics)

**Fluxos de clique e URLs**

Este relatório mostra a lista de páginas visitadas após um delivery. [Saiba mais](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Pessoa/pessoas e recipients**

Entenda melhor a diferença de rastreamento entre uma pessoa/pessoas e um recipient no Adobe Campaign com este exemplo. [Saiba mais](../../reporting/using/person-people-recipients.md)

**Indicadores de rastreamento**

Este relatório combina os indicadores principais para rastrear o comportamento dos recipients ao receber o delivery, como taxas de abertura, click-through e fluxos de clique. [Saiba mais](../../reporting/using/delivery-reports.md#tracking-indicators)

**Cálculo do indicador**

As diferentes tabelas fornecem a lista de indicadores usados nos diferentes relatórios e suas fórmulas de cálculo, dependendo do tipo de delivery. [Saiba mais](../../reporting/using/indicator-calculation.md)

## Rastreamento da solução de problemas {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

As seguintes dicas de solução de problemas ajudarão você a resolver os problemas mais comuns que ocorrem ao usar o rastreamento no Adobe Campaign Classic. Para obter uma solução de problemas mais avançada, consulte [esta seção](../../delivery/using/tracking-troubleshooting.md).

* Verifique se o processo trackinglogd está em execução

   Esse processo lê a memória compartilhada do IIS/Servidor da Web e grava os logs de redirecionamento.

   Você pode acessá-lo na Página inicial selecionando a guia Monitoring na instância. Você também pode executar o seguinte comando na instância: `<user>@<instance>:~$ nlserver pdump`

   Se o processo trackinglogd não aparecer na lista, inicie-o com o seguinte comando na instância: `<user>@<instance>:~$ nlserver start trackinglogd`

* Verifique se o workflow técnico Tracking foi executado recentemente.

   Você pode localizar o workflow técnico Tracking nas pastas Administration > Production > Technical workflows.
