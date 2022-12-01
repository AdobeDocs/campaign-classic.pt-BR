---
product: campaign
title: Criar solicitações de privacidade
description: Saiba como criar e gerenciar solicitações de privacidade
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 73b90d79-88b6-4aaf-8103-4564de5e06be
source-git-commit: 42b420d7dae7d38e9f4df442146d3b484c25e831
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 100%

---

# Criar e gerenciar solicitações de privacidade {#privacy-request-ui}

![](../../assets/v7-only.svg)

Esta seção descreve como criar solicitações de Acesso e Exclusão e como elas são processadas pelo Adobe Campaign.

## Criar uma solicitação de privacidade {#create-privacy-request-ui}

A **interface do Adobe Campaign** permite criar solicitações de privacidade e acompanhar a evolução. Para criar uma nova solicitação de privacidade, siga estas instruções:

1. Acesse a pasta solicitação de privacidade em **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Privacy Requests]**.

   ![](assets/privacy-requests-folder.png)

1. Essa tela permite a visualização de todas as solicitações de privacidade atuais, bem como os respectivos status e logs. Clique em **[!UICONTROL New]** para criar uma solicitação de privacidade.

   ![](assets/privacy-request-new.png)

1. Selecione o **[!UICONTROL Regulation]** (GDPR, CCPA, PDPA ou LGPD), **[!UICONTROL Request type]** (Acessar ou Excluir), selecione um **[!UICONTROL Namespace]** e insira o **[!UICONTROL Reconciliation value]**. Se estiver usando o email como namespace, digite o email do Titular dos dados.

   ![](assets/privacy-request-properties.png)

Os workflows técnicos de privacidade são executados uma vez por dia e processam cada nova solicitação:

* Solicitação de exclusão: esse fluxo de trabalho exclui os dados do destinatário armazenados no Adobe Campaign.
* Solicitações de acesso: os dados do destinatário armazenados no Adobe Campaign são gerados e disponibilizados como um arquivo XML na parte esquerda da tela de solicitação.

![](assets/privacy-request-download.png)

## Lista de tabelas {#list-of-tables}

Ao executar uma solicitação de privacidade de exclusão ou acesso, o Adobe Campaign pesquisa todos os dados do Titular dos dados com base em **[!UICONTROL Reconciliation value]** em todas as tabelas que tenham um link para a tabela do recipient (tipo próprio). 

Esta é a lista de recursos prontos para utilização que são considerados ao executar solicitações de privacidade:

* Recipients (recipient)
* Log de delivery de recipient (broadLogRcp)
* Log de rastreamento de recipient (trackingLogRcp)
* Log de delivery de evento arquivado (broadLogEventHisto)
* Conteúdo da lista de recipient (rcpGrpRel)
* Apresentação da oferta do visitante (propositionVisitor)
* Visitantes (visitante)
* Histórico de inscrições (subHisto)
* Inscrições (inscrição)
* Apresentação da oferta do recipient (propositionRcp)

Se você criou tabelas personalizadas que tenham um link para a tabela do recipient (tipo próprio), elas também serão consideradas. Por exemplo, se você tiver uma tabela de transações vinculada à tabela do recipient e uma tabela de detalhes da transação vinculada à tabela de transações, ambas serão consideradas.

>[!IMPORTANT]
>
>Se você executar solicitações de privacidade em lote usando workflows de exclusão de perfis, considere as seguintes observações:
>* A exclusão de perfis por meio de workflows não processa tabelas secundárias.
>* Você precisa lidar com a exclusão de todas as tabelas secundárias.
>* A Adobe recomenda a criação de um workflow ETL que adicione as linhas que serão excluídas na tabela Acesso de privacidade e permita que o workflow **[!UICONTROL Delete privacy requests data]** execute a exclusão. Por motivos de desempenho, sugerimos que sejam limitadas a 200 perfis por dia.


## Status de solicitação de privacidade {#privacy-request-statuses}

Estes são os diferentes status de solicitações de acesso a dados pessoais:

* **[!UICONTROL New]** / **[!UICONTROL Retry pending]**: em andamento, o workflow ainda não processou a solicitação.
* **[!UICONTROL Processing]** / **[!UICONTROL Retry in progress]**: o workflow está processando a solicitação.
* **[!UICONTROL Delete pending]**: o workflow identificou todos os dados do recipient que serão excluídos.
* **[!UICONTROL Delete in progress]**: o workflow está processando a exclusão.
* **[!UICONTROL Delete Confirmation Pending]** (Solicitação de exclusão no modo de processo de duas etapas): o workflow processou a solicitação de acesso. A confirmação manual é solicitada para executar a exclusão. O botão está disponível por 15 dias.
* **[!UICONTROL Complete]**: o processamento da solicitação foi concluído sem erros.
* **[!UICONTROL Error]**: o workflow encontrou um erro. O motivo aparece na lista de solicitações de privacidade na coluna **[!UICONTROL Request status]**. Por exemplo, **[!UICONTROL Error data not found]** significa que nenhum dado de recipient correspondente a **[!UICONTROL Reconciliation value]** do Titular dos dados foi encontrado no banco de dados.

## Processo em duas etapas {#two-step-process}

O **processo de duas etapas** é ativado por padrão. Ao criar uma nova solicitação de exclusão usando esse modo, o Adobe Campaign sempre executa uma solicitação de acesso primeiro. Isso permite que você verifique os dados antes de confirmar a exclusão.

Você pode alterar esse modo da tela de edição de solicitação de privacidade. Clique em **[!UICONTROL Advanced settings]**.

![](assets/privacy-request-advanced-settings.png)

Com o modo de 2 etapas ativado, o status de uma nova solicitação de exclusão muda para **[!UICONTROL Confirm Delete Pending]**. Baixe o arquivo XML gerado na tela de solicitação de privacidade e verifique os dados. Para confirmar o cancelamento dos dados, clique no botão **[!UICONTROL Confirm delete data]**.

![](assets/privacy-request-delete-data.png)

## URL JSSP {#jspp-url}

Ao processar solicitações do Access, o Adobe Campaign gera um JSSP que recupera os dados do recipient do banco de dados e os exporta para um arquivo XML armazenado no computador local. O URL JSSP é definido conforme indicação abaixo:

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

onde @id é a ID da solicitação de privacidade.

Esse URL é armazenado no campo **[!UICONTROL "File location" (@urlFile)]** do esquema **[!UICONTROL Privacy Requests (gdprRequest)]**.

As informações ficam disponíveis no banco de dados por 90 dias. Depois que a solicitação é limpa pelo workflow técnico, as informações são removidas do banco de dados e o URL torna-se obsoleto. Verifique se o URL ainda é válido antes de baixar os dados de uma página da web.

Exemplo de um arquivo de dados de um titular de dados:

![](assets/do-not-localize/privacy-access-file.png)

Os controladores de dados podem criar facilmente um aplicativo da web, incluindo o URL JSSP correspondente, para disponibilizar o arquivo de dados do titular dos dados de uma página da web.

![](assets/privacy-gdpr-jssp.png)

Este é um trecho de código que você pode usar como exemplo na atividade **[!UICONTROL Page]** do aplicativo da web.

![](assets/privacy-page-activity.png)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv="Content-Language" content="en"> <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> <link rel="stylesheet" type="text/css" href="/nl/webForms/landingPage.css"/> <title>Clickthrough</title> <style type="text/css" media="all"> /* override formulary area */ .formulary { top: 200px; position: absolute; left: 0; } </style> </head> <body style="" class="">
<center>
<div id="wrap">
<div id="header"><img class="nlui-widget" alt="placeholder_header" src="/nms/img/contentModels/placeholder_header.png" unselectable="on" />
<div class="header-title center-title">DOWNLOAD GDPR DATA</div>
<div class="formulary center-formulary"><form>
<div class="button large-button"><a href=[SERVER_URL]/nms/gdpr.jssp?id=13000" data-nl-type="externalLink">CLICK TO DOWNLOAD</a></div>
</form></div>
</div>
<div id="content">
<div class="row">
<div class="info">
<div class="desc">
<div class="title">EFFICIENCY</div>
<div class="desc">Our service is guaranteed to improve your efficiency. Increase performance and use our high-technology service to implement even the most ambitious of projects.</div>
</div>
</div>
</div>
</div>
<div id="footer">
<div style="text-align: center;">
<div style="float: left;"><a href="#">Contact us</a></div>
<div style="float: right;">&copy; Copyrights</div>
<div><a href="#"><img title="facebook" class="nlui-widget" alt="facebook" src="/xtk/img/facebook.png" unselectable="on" /></a> <a href="#"><img title="Twitter" class="nlui-widget" alt="twitter" src="/xtk/img/twitter.png" unselectable="on" /></a> <a href="#"><img title="Google" class="nlui-widget" alt="google_plus" src="/xtk/img/google_plus.png" unselectable="on" /></a> <a href="#"><img title="Linkedin" class="nlui-widget" alt="Linkedin" src="/xtk/img/linkedin.png" unselectable="on" /></a></div>
</div>
</div>
</div>
</center>
</body> </html>
```

Como o acesso ao arquivo de dados do titular de dados é restrito, o acesso anônimo à página da web deve ser desativado. Somente o operador com o direito nomeado **[!UICONTROL Privacy Data Right]** pode fazer logon na página e baixar os dados.
