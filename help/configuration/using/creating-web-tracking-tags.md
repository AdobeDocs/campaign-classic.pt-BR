---
solution: Campaign Classic
product: campaign
title: Criação de tags de rastreamento Web
description: Criação de tags de rastreamento Web
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 4%

---


# Criação de tags de rastreamento Web{#creating-web-tracking-tags}

Cada página do site que você deseja rastrear deve ser referenciada na sua plataforma Adobe Campaign. Essa referência pode ser executada de duas maneiras:

1. Definição manual dos URLs a rastrear,
1. Criação imediata de URLs a serem rastreados.

## Definição dos URLs a serem rastreados no aplicativo {#defining-the-urls-to-be-tracked-in-the-application}

Esse método permite que você defina manualmente as páginas a serem rastreadas e gere um exemplo do tag de rastreamento da Web associado. Essa operação é definida no **[!UICONTROL Campaign execution>Resources>Web tracking tags]** nó do console do cliente.

![](assets/d_ncs_integration_webtracking_screen.png)

Para gerar o código HTML a ser inserido na página:

* Digite o rótulo da tag: será mostrada nos logs de rastreamento,
* Indique o URL de origem: este campo é para fins informativos e permite que você indique a página rastreada (opcional),
* Se necessário, insira um período de validade,
* Clique em código **[!UICONTROL Generate]** HTML.

Em seguida, copie o código gerado e cole-o na página a ser rastreada.

## Criação imediata de URLs a serem rastreados {#on-the-fly-creation-of-urls-to-be-tracked}

Você pode criar URLs de rastreamento da Web dinamicamente adicionando informações ao valor do parâmetro **tagid** :

* Tipo de página rastreada: &#39;w&#39; para WEB ou &#39;t&#39; para TRANSAÇÃO,
* O nome interno da pasta onde o URL deve ser criado.

Estas duas informações devem ser concatenadas com o identificador da página rastreada, adicionando o caractere &#39;|&#39;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Lembre-se de codificar o valor do parâmetro **tagid** quando ele for usado como um parâmetro de URL.

**Exemplo**: criação de um URL de rastreamento da Web de tipo de transação.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
