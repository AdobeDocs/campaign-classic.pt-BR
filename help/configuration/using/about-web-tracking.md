---
product: campaign
title: Sobre o rastreamento Web
feature: Configuration, Instance Settings
description: Sobre o rastreamento Web
role: User, Developer
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
TQID: 'https://experienceleague.adobe.com/FfA6FEH5WP2JJGVR4BhpjO19Yj4mt8irvyJLwuzCThs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%
---
# Sobre o rastreamento Web{#about-web-tracking}

Além do rastreamento padrão, que mostra o comportamento de um usuário da Internet ao clicar em um link em uma mensagem de email, a plataforma do Adobe Campaign permite coletar informações sobre como os usuários da Internet navegam em seu site. Essa coleta de dados é executada pelo módulo de rastreamento web.

Quando um usuário da Internet clica em um link rastreado em um email de um determinado delivery, o servidor de redirecionamento contatado deposita um cookie de sessão contendo o identificador de broadlog (broadlogId) e o identificador de delivery (deliveryId).

O cliente Web envia esse cookie ao servidor sempre que o usuário visita uma página contendo uma tag de rastreamento Web. Isso continua durante toda a sessão, ou seja, até que o cliente da Web seja fechado.

O servidor de redirecionamento coleta os seguintes dados dessa maneira:

* URL da página visualizada, por meio de um identificador enviado como um parâmetro,
* o delivery do qual a página da Web foi visitada, por meio do cookie de sessão,
* identificador do usuário da Internet que clicou, por meio do cookie de sessão,
* informações adicionais, como o volume de negócios gerado.

O diagrama a seguir mostra os estágios da caixa de diálogo entre o cliente e os vários servidores.

![](assets/d_ncs_integration_webtracking_structure1.png)
