---
title: Sobre o rastreamento Web
seo-title: Sobre o rastreamento Web
description: Sobre o rastreamento Web
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 6%

---


# Sobre o rastreamento Web{#about-web-tracking}

Além do rastreamento padrão que mostra o comportamento de um usuário da Internet clicar em um link em uma mensagem de email, a plataforma Adobe Campaign permite coletar informações sobre como os usuários da Internet navegam em seu site. Essa coleta de dados é realizada pelo módulo de rastreamento da Web.

Quando um usuário de Internet clica em um link rastreado em um email de um determinado delivery, o servidor de redirecionamento contactado deposita um cookie de sessão que contém o identificador de catálogo (BroadlogId) e o identificador do delivery (deliveryId).

O cliente da Web envia esse cookie para o servidor sempre que o usuário visita uma página que contém um tag de rastreamento da Web. Isso continua durante toda a sessão, ou seja, até que o cliente da Web seja fechado.

O servidor de redirecionamento coleta os seguintes dados dessa forma:

* URL da página visualizada, por meio de um identificador enviado como parâmetro,
* o delivery do qual a página da Web foi visitada, por meio do cookie da sessão,
* identificador do utilizador da Internet que clicou, através do cookie da sessão,
* informações adicionais, como o volume de negócios gerado.

O diagrama a seguir mostra os estágios da caixa de diálogo entre o cliente e os vários servidores.

![](assets/d_ncs_integration_webtracking_structure1.png)

