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

O módulo de rastreamento Web fornecido pelo Adobe Campaign permite coletar as visitas a determinadas páginas do site executadas por um recipient no contexto de rastreamento do site após um clique em uma mensagem.

No entanto, você pode configurar sua plataforma para que ela colete todas as visitas a páginas com uma tag de rastreamento Web por um usuário conhecido pela plataforma.

Um usuário conhecido pela plataforma é um recipient que já foi direcionado por um delivery e que clicou em uma mensagem recebida pelo menos uma vez. Um cookie permanente é usado para identificar esse recipient.

>[!IMPORTANT]
>
>A plataforma Adobe Campaign não se destina a ser usada como uma ferramenta de rastreamento de site além do contexto de visita ao site após um clique em uma mensagem. Quando essa opção é ativada, pode causar um alto uso dos recursos nas máquinas que hospedam seus servidores (redirecionamento, aplicativo e banco de dados). É recomendável garantir que sua arquitetura de hardware possa suportar essa carga e evitar colocar tags de rastreamento Web nas páginas visitadas com mais frequência, como a página inicial.

## Configuração do servidor {#server-configuration}

Os servidores são configurados ao sobrecarregar determinados elementos da variável **serverConf.xml** arquivo. Esses arquivos são salvos no **conf** subdiretório do diretório de instalação do Adobe Campaign.

### Redirecionar servidor {#redirection-server}

Para o servidor de redirecionamento, defina a variável **trackWebVisitors** do **redirecionamento** elemento para **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configuração de uma campanha correspondente padrão {#configuring-a-default-matching-campaign}

Para exibir informações de rastreamento por meio do console do cliente, é necessário:

* Crie um **entrega de testes** (o mapeamento do delivery deve ser idêntico ao mapeamento do schema do target),
* Insira o **nome interno** do delivery no **NmsTracking_WebTrackingDelivery** opção.

Todas as informações de rastreamento do site não diretamente subsequentes a um clique em um email podem ser visualizadas no delivery de teste criado.
