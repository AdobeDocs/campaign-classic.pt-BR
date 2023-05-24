---
product: campaign
title: Coleta de todas as visitas
description: Coleta de todas as visitas
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# Coleta de todas as visitas{#collecting-all-visits}

O módulo de rastreamento Web fornecido pela Adobe Campaign permite coletar as visitas a determinadas páginas do site executadas por um recipient no contexto do rastreamento do site após um clique em uma mensagem.

No entanto, você pode configurar sua plataforma para que ela colete todas as visitas a páginas com uma tag de rastreamento Web por um usuário conhecido na plataforma.

Um usuário conhecido da plataforma é um recipient que já foi direcionado por um delivery e que clicou em uma mensagem recebida pelo menos uma vez. Um cookie permanente é usado para identificar esse recipient.

>[!IMPORTANT]
>
>A plataforma do Adobe Campaign não deve ser usada como uma ferramenta de rastreamento de sites além do contexto de visitar o site após um clique em uma mensagem. Quando essa opção é habilitada, ela pode causar um alto uso de recursos nas máquinas que hospedam seus servidores (redirecionamento, aplicativo e banco de dados). É recomendável garantir que sua arquitetura de hardware possa suportar essa carga e evitar a inserção de tags de rastreamento Web nas páginas visitadas com mais frequência, como a página inicial.

## Configuração do servidor {#server-configuration}

Os servidores são configurados sobrecarregando determinados elementos do **serverConf.xml** arquivo. Esses arquivos são salvos na variável **conf** subdiretório do diretório de instalação do Adobe Campaign.

### Servidor de redirecionamento {#redirection-server}

Para o servidor de redirecionamento, defina o **trackWebVisitors** atributo de **redirecionamento** elemento para **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configurar uma campanha de correspondência padrão {#configuring-a-default-matching-campaign}

Para exibir informações de rastreamento por meio do console do cliente, você deve:

* Criar um **entrega fictícia** (o mapeamento do delivery deve ser idêntico ao mapeamento do schema de destino),
* Insira o **nome interno** desta entrega no **NmsTracking_WebTrackingDelivery** opção.

Todas as informações de rastreamento do site não diretamente subsequentes a um clique em um email podem ser visualizadas no delivery fictício criado.
