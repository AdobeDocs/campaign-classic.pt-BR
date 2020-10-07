---
title: Modo de rastreamento Web
seo-title: Modo de rastreamento Web
description: Modo de rastreamento Web
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 1%

---


# Modo de rastreamento Web{#web-tracking-mode}

O Adobe Campaign permite que você selecione um modo de rastreamento da Web que define a forma como os logs de rastreamento são processados no aplicativo.

Há três modos de Rastreamento web disponíveis: **&quot;Rastreamento de sessão&quot;**,**&quot;Rastreamento permanente&quot;** e **&quot;Tracking anônimo&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Cada modo tem características específicas. O modo de Rastreamento web &quot;permanente&quot; inclui as características do modo de Rastreamento web &quot;sessão&quot;, enquanto o modo &quot;anônimo&quot; inclui as características dos modos &quot;permanente&quot; e &quot;sessão&quot;.

>[!IMPORTANT]
>
>O modo de Rastreamento web &quot;anônimo&quot; é ativado por padrão se o pacote &quot;Clientes potenciais&quot; estiver ativado. Em todos os outros casos, o modo de Rastreamento web &quot;sessão&quot; é ativado por padrão.
>
>A qualquer momento, o modo padrão pode ser alterado no assistente de implantação da instância.

Observe que se você estiver usando o modo de rastreamento **permanente da Web** ou **anônimo** , é necessário adicionar um índice à coluna &quot;sourceID&quot; (uuid230) nas tabelas de rastreamento (trackingLogXXX):

1. Identificar as tabelas de rastreamento afetadas pelo rastreamento permanente.
1. Estenda os schemas que correspondem a essas tabelas adicionando as seguintes linhas:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Os modos de Rastreamento web permanente** e **anônimo** incluem duas opções: **Delivery** forçado e **último delivery**.

A opção delivery **** forçado permite especificar o identificador do delivery (@jobid) durante o rastreamento.

A opção **Último delivery** permite vincular o log de rastreamento atual ao último delivery rastreado.

**Características do Rastreamento web da sessão:**

Este modo cria um log de rastreamento para pessoas com um cookie de sessão. Essas são pessoas que clicaram em um URL em um email enviado pela Adobe Campaign, permitindo que rastreássemos as seguintes informações:

* ID do delivery
* ID do contato
* Registro de delivery
* cookie permanente (uuid230)
* URL de rastreamento
* data do registro de rastreamento

Com esse modo de Rastreamento web, se parte das informações estiver ausente, nenhum registro de rastreamento será criado no aplicativo.

Esse modo é econômico em termos de volume (número limitado de registros na tabela trackingLog) e cálculo (sem reconciliação).

**Características do modo de Rastreamento web permanente:**

Esse modo de Rastreamento web permite criar um log de rastreamento com base na presença do cookie uid230 permanente. Se um visitante fechar sua sessão, a Adobe Campaign usará o cookie permanente para recuperar informações sobre ele de logs de rastreamento anteriores. A Adobe Campaign insere novamente um log de rastreamento se o uuid230 da sessão atual tiver o mesmo valor que um uuid230 já armazenado na tabela de rastreamento.

Isso significa que o visitante precisa ter sido identificado anteriormente no Adobe Campaign (por meio de um delivery) para permitir a reconciliação nos valores do uid230.

Por padrão, as pesquisas em logs de rastreamento anteriores são executadas na tabela &quot;trackingLog&quot;. Se o pacote Leads estiver ativado, antes de pesquisar a tabela &quot;trackingLog&quot;, a Adobe Campaign pesquisará na tabela &quot;incomingLead&quot; os registros de log de rastreamento anteriores.

Esse modo é caro em termos de cálculo durante a reconciliação do log.

**Características do modo de Rastreamento web anônimo:**

Esse modo de Rastreamento web permite recuperar um log de rastreamento vinculado à navegação anônima no Adobe Campaign. Um log de rastreamento é criado automaticamente para cada clique em um URL rastreado. Este log tem apenas o valor do uuid230. Durante uma campanha de marketing, um log de rastreamento é criado automaticamente com todas as informações de identificação (consulte o rastreamento de sessão). A Adobe Campaign pesquisará automaticamente os registros anteriores em busca de um valor &quot;uid230&quot; igual ao valor do log de rastreamento desta campanha de marketing. Se forem encontrados valores idênticos, todos os logs de rastreamento anteriores serão inseridos com todas as informações do log de rastreamento da campanha de marketing.

Esse modo é o mais caro em termos de cálculo e volume.

>[!NOTE]
>
>Se o **[!UICONTROL Leads]** pacote estiver instalado, é necessário fazer o mesmo para a tabela de atividade (**crm:incomingLead**)

O schema a seguir resume as funcionalidades dos três modos de Rastreamento web:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Exemplo de rastreamento permanente da Web com base no último delivery:**

Florence recebe um delivery, abre o email, clica no link, navega no site de varejo, mas não faz compras. No dia seguinte, Florence volta ao site de varejo, navega e faz uma compra. Como o rastreamento permanente da Web (último delivery) está ativado, todos os logs de sua segunda visita serão vinculados ao delivery que foi enviado a ela no dia anterior.
