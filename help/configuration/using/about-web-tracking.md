---
product: campaign
title: Sobre o rastreamento Web
feature: Configuration, Instance Settings
description: Sobre o rastreamento Web
role: User, Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 8%

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
