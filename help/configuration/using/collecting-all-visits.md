---
title: Coleta de todas as visitas
seo-title: Coleta de todas as visitas
description: Coleta de todas as visitas
seo-description: null
page-status-flag: never-activated
uuid: c2869b3d-33bb-4a22-a8e6-ac037f0665d9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 7f841368-3867-4d6e-9720-c038d9bea0ce
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Coleta de todas as visitas{#collecting-all-visits}

O módulo de rastreamento da Web fornecido pelo Adobe Campaign permite que você colete as visitas a determinadas páginas do site executadas por um destinatário no contexto do rastreamento do site após um clique em uma mensagem.

No entanto, você pode configurar sua plataforma para que ela colete todas as visitas a páginas com uma tag de rastreamento da Web por um usuário conhecido da plataforma.

Um usuário conhecido pela plataforma é um destinatário que já foi alvo de uma entrega e que clicou em uma mensagem recebida pelo menos uma vez. Um cookie permanente é usado para identificar esse destinatário.

>[!IMPORTANT]
>
>A plataforma do Adobe Campaign não se destina ao uso como uma ferramenta de rastreamento de site além do contexto de visita ao site após um clique em uma mensagem. Quando esta opção está ativada, pode causar um uso muito alto dos recursos nas máquinas que hospedam seus servidores (redirecionamento, aplicativo e banco de dados). É recomendável garantir que a sua arquitetura de hardware suporte essa carga e evitar colocar tags de rastreamento da Web nas páginas visitadas com mais frequência, como a página inicial.

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

Para exibir informações de rastreamento pelo console do cliente, você deve:

* Criar uma entrega **** simulada (o mapeamento da entrega deve ser idêntico ao mapeamento do esquema de destino),
* Digite o nome **** interno dessa entrega na opção **NmsTracking_WebTrackingDelivery** .

Todas as informações de rastreamento do site não diretamente subsequentes a um clique em um email podem ser visualizadas na entrega do teste criada.
