---
product: campaign
title: Criar tags de rastreamento Web
description: Saiba como criar tags de rastreamento Web
feature: Application Settings
role: Developer
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Criar tags de rastreamento Web{#creating-web-tracking-tags}

Cada página do site que você deseja rastrear deve ser referenciada na plataforma Adobe Campaign. Essa referência pode ser executada de duas maneiras:

1. Definição manual de URLs a serem rastreados,
1. Criação instantânea de URLs a serem rastreados.

## Definição dos URLs a serem rastreados no aplicativo {#defining-the-urls-to-be-tracked-in-the-application}

Esse método permite definir manualmente as páginas que serão rastreadas e gerar um exemplo da tag de rastreamento Web associada. Esta operação é definida no nó **[!UICONTROL Campaign execution>Resources>Web tracking tags]** do console do cliente.

![](assets/d_ncs_integration_webtracking_screen.png)

Para gerar o código HTML a ser inserido na página:

* Insira o rótulo da tag: ele será mostrado nos logs de rastreamento,
* Indicar o URL de origem: este campo é para fins de informação e permite indicar a página rastreada (opcional),
* Se necessário, insira um período de validade,
* Clique em **[!UICONTROL Generate]** código HTML.

Em seguida, copie o código gerado e cole-o na página a ser rastreada.

## Criação instantânea de URLs a serem rastreados {#on-the-fly-creation-of-urls-to-be-tracked}

Você pode criar as URLs de rastreamento web instantaneamente adicionando informações ao valor do parâmetro **tagid**:

* Tipo de página rastreada: &quot;w&quot; para WEB ou &quot;t&quot; para TRANSAÇÃO,
* O nome interno da pasta onde o URL deve ser criado.

Essas duas informações devem ser concatenadas com o identificador da página rastreada adicionando o caractere &#39;|&#39;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Lembre-se de codificar o valor do parâmetro **tagid** quando ele for usado como um parâmetro de URL.

**Exemplo**: criação de uma URL de rastreamento Web do tipo transação.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
