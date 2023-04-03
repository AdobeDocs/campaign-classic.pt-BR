---
product: campaign
title: Nota técnica - Ativação do Microsoft Edge Chromium no ambiente Campaign
description: Campanha - Chromium da borda
hide: true
hidefromtoc: true
source-git-commit: d9f57d4e5b6f880907040344ece40546456a2321
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 14%

---


# Como ativar o Microsoft Edge Chromium em seu ambiente {#edge-conf}

![](../../assets/v7-only.svg)


## O que mudou?

Após o fim da vida útil do Microsoft Internet Explorer 11, o mecanismo de renderização de HTML para Adobe Services (página de logon) no console do cliente agora usa o Microsoft Edge Chromium, a partir do Campaign Classic v7.3.

Além da instalação do tempo de execução do Microsoft Edge Webview 2, que agora está [necessário para qualquer instalação do console do cliente](../../installation/using/installing-the-client-console.md#webview), o Microsoft Edge Chromium deve ser ativado na(s) instância(s).

## Você será afetado?

Se seu ambiente tiver sido atualizado para o Campaign Classic v7.3 (ou posterior), você será afetado.

## Como atualizar?

* Como um **hospedado** cliente, o Adobe já ativou o Microsoft Edge Chromium em sua instância(s).

* Como um **no local/híbrido** cliente, é necessário ativar o Microsoft Edge Chromium em sua instância.

   Ao atualizar para o Campaign Classic v7.3 (e posterior), um novo `webView2Mode` está disponível no arquivo de configuração do servidor do Campaign `serverConf.xml`. Este atributo deve ser ativado.

   Para fazer isso, aplique as seguintes etapas em todos os seus ambientes (MKT, MID, RT):

   1. Edite o arquivo de configuração do servidor do Campaign (`serverConf.xml`)
   1. No `<web>` módulo, conjunto `webView2Mode = "1"`
   1. Recarregar a configuração do servidor

      ```
      nlserver config -reload
      ```

   1. Reiniciar o servidor Web

      ```
      nlserver restart web
      ```

   1. Se o ambiente for executado no Apache, reinicie o Apache

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Tópicos relacionados

* [Atualizar seu ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Instalar o console do cliente do Campaign](../../installation/using/installing-the-client-console.md)

