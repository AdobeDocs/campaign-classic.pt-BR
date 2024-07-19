---
product: campaign
title: Nota técnica - Ativação do Microsoft Edge Chromium no ambiente do Campaign
description: Campaign — Edge Chromium
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 8734e6ef26a7342042a5242d54854b7d3a5e6244
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 7%

---

# Como ativar o Microsoft Edge Chromium no seu ambiente {#edge-conf}

## O que mudou?

Após o fim da vida útil do Microsoft Internet Explorer 11, o mecanismo de renderização de HTML para painéis no console do cliente estará usando o Edge Chromium, iniciando o Campaign Classic v7.3.

Além da instalação do Microsoft Edge Webview 2 runtime, que agora é [necessária para qualquer instalação do console do cliente](../../installation/using/installing-the-client-console.md#webview), o Microsoft Edge Chromium deve ser habilitado em sua(s) instância(s).

>[!NOTE]
>
>Depois de habilitar o Microsoft Edge Chromium, o atalho `Ctrl+F` (Windows) ou `Command+F` (Mac) para abrir a caixa de diálogo de pesquisa do navegador não funcionará mais.

## Você será afetado?

Se seu ambiente foi atualizado para o Campaign Classic v7.3 (ou posterior), você será afetado.

## Como atualizar?

* Como cliente **hospedado**, o Adobe já habilitou o Microsoft Edge Chromium em sua(s) instância(s). Nenhuma ação adicional é necessária.

* Como cliente do **no local/híbrido**, você precisa habilitar o Microsoft Edge Chromium nas suas instâncias.

  Ao atualizar para o Campaign Classic v7.3 (e posterior), um novo atributo `webView2Mode` está disponível no arquivo de configuração do servidor do Campaign `serverConf.xml`. Este atributo deve ser habilitado.

  Para fazer isso, aplique as seguintes etapas em todos os seus ambientes (MKT, MID, RT):

   1. Editar o arquivo de configuração do servidor do Campaign (`serverConf.xml`)
   1. No módulo `<web>`, defina `webView2Mode = "1"`
   1. Execute o seguinte comando para recarregar a configuração do servidor:

      ```
      nlserver config -reload
      ```

   1. Execute o seguinte comando para reiniciar o servidor Web:

      ```
      nlserver restart web
      ```

   1. Se o ambiente usar o Apache como um servidor Web, execute o seguinte comando para reiniciar o Apache:

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Tópicos relacionados

* [Atualizar o ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Instalar o console do cliente do Campaign](../../installation/using/installing-the-client-console.md)
