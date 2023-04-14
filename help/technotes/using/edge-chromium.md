---
product: campaign
title: Nota técnica - Ativação do Microsoft Edge Chromium no ambiente Campaign
description: Campanha - Chromium da borda
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 095919608e08a0bf8ad1487fa5ec0a1ddb443c7b
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 13%

---

# Como ativar o Microsoft Edge Chromium em seu ambiente {#edge-conf}

![](../../assets/v7-only.svg)


## O que mudou?

Após o fim da vida útil do Microsoft Internet Explorer 11, o mecanismo de renderização de HTML para painéis no console do cliente está usando o Edge Chromium, iniciando no Campaign Classic v7.3.

Além da instalação do tempo de execução do Microsoft Edge Webview 2, que agora está [necessário para qualquer instalação do console do cliente](../../installation/using/installing-the-client-console.md#webview), o Microsoft Edge Chromium deve ser ativado na(s) instância(s).

## Você será afetado?

Se seu ambiente tiver sido atualizado para o Campaign Classic v7.3 (ou posterior), você será afetado.

## Como atualizar?

* Como um **hospedado** cliente, o Adobe já ativou o Microsoft Edge Chromium em sua instância(s). Nenhuma ação adicional é necessária.

* Como um **no local/híbrido** cliente, é necessário ativar o Microsoft Edge Chromium em sua instância.

   Ao atualizar para o Campaign Classic v7.3 (e posterior), um novo `webView2Mode` está disponível no arquivo de configuração do servidor do Campaign `serverConf.xml`. Este atributo deve ser ativado.

   Para fazer isso, aplique as seguintes etapas em todos os seus ambientes (MKT, MID, RT):

   1. Edite o arquivo de configuração do servidor do Campaign (`serverConf.xml`)
   1. No `<web>` módulo, conjunto `webView2Mode = "1"`
   1. Execute o seguinte comando para recarregar a configuração do servidor:

      ```
      nlserver config -reload
      ```

   1. Execute o seguinte comando para reiniciar o servidor da Web:

      ```
      nlserver restart web
      ```

   1. Se o seu ambiente usar o Apache as a web server, execute o seguinte comando para reiniciar o Apache:

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
