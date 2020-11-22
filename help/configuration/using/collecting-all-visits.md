---
solution: Campaign Classic
product: campaign
title: Coleta de todas as visitas
description: Coleta de todas as visitas
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---


# Coleta de todas as visitas{#collecting-all-visits}

O módulo de rastreamento da Web fornecido pela Adobe Campaign permite coletar as visitas a determinadas páginas do site executadas por um recipient no contexto do rastreamento do site após um clique em uma mensagem.

No entanto, você pode configurar sua plataforma para que ela colete todas as visitas a páginas com um tag de rastreamento da Web por um usuário conhecido pela plataforma.

Um usuário conhecido pela plataforma é um recipient que já foi alvo de um delivery e que clicou em uma mensagem recebida pelo menos uma vez. Um cookie permanente é usado para identificar esse recipient.

>[!IMPORTANT]
>
>A plataforma Adobe Campaign não se destina ao uso como uma ferramenta de rastreamento de site além do contexto de visita ao site após um clique em uma mensagem. Quando esta opção está ativada, pode causar um uso muito alto dos recursos nas máquinas que hospedam seus servidores (redirecionamento, aplicativo e banco de dados). É recomendável garantir que sua arquitetura de hardware suporte essa carga e evitar colocar tag de rastreamento da Web nas páginas visitadas com mais frequência, como o home page.

## Configuração do servidor {#server-configuration}

Os servidores são configurados sobrecarregando certos elementos do arquivo **serverConf.xml** . Esses arquivos são salvos no subdiretório **conf** do diretório de instalação do Adobe Campaign.

### Servidor de redirecionamento {#redirection-server}

Para o servidor de redirecionamento, defina o atributo **trackWebVisitors** do elemento de **redirecionamento** como **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configurar uma campanha de correspondência padrão {#configuring-a-default-matching-campaign}

Para visualização de informações de rastreamento por meio do console do cliente, é necessário:

* Criar um delivery **** simulado (o mapeamento do delivery deve ser idêntico ao mapeamento do schema do público alvo),
* Digite o nome **** interno desse delivery na opção **NmsTracking_WebTrackingDelivery** .

Todas as informações de rastreamento de site não diretamente subsequentes a um clique em um email podem ser visualizadas no delivery de teste criado.
