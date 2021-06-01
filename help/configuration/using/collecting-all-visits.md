---
product: campaign
title: Coleta de todas as visitas
description: Coleta de todas as visitas
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# Coleta de todas as visitas{#collecting-all-visits}

O módulo de rastreamento Web fornecido pelo Adobe Campaign permite coletar as visitas a determinadas páginas do site executadas por um recipient no contexto de rastreamento do site após um clique em uma mensagem.

No entanto, você pode configurar sua plataforma para que ela colete todas as visitas a páginas com uma tag de rastreamento Web por um usuário conhecido pela plataforma.

Um usuário conhecido pela plataforma é um recipient que já foi direcionado por um delivery e que clicou em uma mensagem recebida pelo menos uma vez. Um cookie permanente é usado para identificar esse recipient.

>[!IMPORTANT]
>
>A plataforma Adobe Campaign não se destina a ser usada como uma ferramenta de rastreamento de site além do contexto de visita ao site após um clique em uma mensagem. Quando essa opção é ativada, pode causar um alto uso dos recursos nas máquinas que hospedam seus servidores (redirecionamento, aplicativo e banco de dados). É recomendável garantir que sua arquitetura de hardware possa suportar essa carga e evitar colocar tags de rastreamento Web nas páginas visitadas com mais frequência, como a página inicial.

## Configuração do servidor {#server-configuration}

Os servidores são configurados sobrecarregando determinados elementos do arquivo **serverConf.xml**. Esses arquivos são salvos no subdiretório **conf** do diretório de instalação do Adobe Campaign.

### Redirecionar servidor {#redirection-server}

Para o servidor de redirecionamento, defina o atributo **trackWebVisitors** do elemento **redirecionamento** para **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configurar uma campanha correspondente padrão {#configuring-a-default-matching-campaign}

Para exibir informações de rastreamento por meio do console do cliente, é necessário:

* Criar um **delivery fictício** (o mapeamento de delivery deve ser idêntico ao mapeamento do schema de destino),
* Insira o **nome interno** deste delivery na opção **NmsTracking_WebTrackingDelivery**.

Todas as informações de rastreamento do site não diretamente subsequentes a um clique em um email podem ser visualizadas no delivery de teste criado.
