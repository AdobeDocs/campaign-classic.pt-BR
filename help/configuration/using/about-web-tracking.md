---
solution: Campaign Classic
product: campaign
title: Sobre o rastreamento Web
description: Sobre o rastreamento Web
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

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

