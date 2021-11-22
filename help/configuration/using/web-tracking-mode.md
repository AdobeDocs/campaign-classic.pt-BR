---
product: campaign
title: Modo de rastreamento Web
description: Modo de rastreamento Web
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---

# Modo de rastreamento Web{#web-tracking-mode}

![](../../assets/v7-only.svg)

O Adobe Campaign permite selecionar um modo de rastreamento Web que define como os logs de rastreamento são processados no aplicativo.

Há três modos de rastreamento Web disponíveis: **&quot;Rastreamento de sessão&quot;**,**&quot;Rastreamento permanente&quot;** e **&quot;Rastreamento anônimo&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Cada modo tem características específicas. O modo de rastreamento web &quot;permanente&quot; inclui as características do modo de rastreamento web &quot;sessão&quot;, enquanto o modo &quot;anônimo&quot; inclui as características dos modos &quot;permanente&quot; e &quot;sessão&quot;.

>[!IMPORTANT]
>
>O modo de rastreamento Web &quot;anonymous&quot; é ativado por padrão se o pacote &quot;Leads&quot; estiver ativado. Em todos os outros casos, o modo de rastreamento Web &quot;sessão&quot; é ativado por padrão.
>
>A qualquer momento, o modo padrão pode ser alterado no assistente de implantação da instância.

Observe que, se você estiver usando a variável **web permanente** ou **anonymous** no modo de rastreamento, você deve adicionar um índice à coluna &quot;sourceID&quot; (uuid230) nas tabelas de rastreamento (trackingLogXXX):

1. Identifique as tabelas de rastreamento relacionadas ao rastreamento permanente.
1. Estenda os esquemas que correspondem a essas tabelas adicionando as seguintes linhas:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Permanente** e **Anônimo** Os modos de rastreamento web incluem duas opções: **Entrega forçada** e **Última entrega**.

O **Entrega forçada** permite especificar o identificador do delivery (@jobid) durante o rastreamento.

O **Última entrega** permite vincular o log de rastreamento atual ao último delivery rastreado.

**Características do rastreamento Web da sessão:**

Esse modo cria um log de rastreamento para pessoas com um cookie de sessão. Essas são pessoas que clicaram em um URL em um email enviado pelo Adobe Campaign, permitindo rastrear as seguintes informações:

* ID de entrega
* ID de contato
* log de delivery
* cookie permanente (uuid230)
* URL de rastreamento
* data do log de rastreamento

Com esse modo de rastreamento Web, se parte das informações estiver ausente, nenhum log de rastreamento será criado no aplicativo.

Esse modo é econômico em termos de volume (número limitado de registros na tabela trackingLog) e cálculo (sem reconciliação).

**Características do modo permanente de rastreamento web:**

Este modo de rastreamento Web permite criar um log de rastreamento com base na presença do cookie uuid230 permanente. Se um visitante fechar sua sessão, o Adobe Campaign usará o cookie permanente para recuperar informações sobre ele de logs de rastreamento anteriores. O Adobe Campaign insere novamente um log de rastreamento se o uuid230 da sessão atual tiver o mesmo valor que um uuid230 já armazenado na tabela de rastreamento.

Isso significa que o visitante precisa ter sido identificado anteriormente no Adobe Campaign (por meio de um delivery) para permitir a reconciliação nos valores uuid230.

Por padrão, as pesquisas nos logs de rastreamento anteriores são realizadas na tabela &quot;trackingLog&quot;. Se o pacote Leads estiver ativado, antes de pesquisar a tabela &quot;trackingLog&quot;, o Adobe Campaign pesquisará na tabela &quot;incomingLead&quot; por registros de log de rastreamento anteriores.

Esse modo custa caro em termos de cálculo durante a reconciliação do log.

**Características do modo de rastreamento Web anônimo:**

Esse modo de rastreamento Web permite recuperar um log de rastreamento vinculado à navegação anônima no Adobe Campaign. Um log de rastreamento é criado automaticamente para cada clique em um URL rastreado. Este log tem apenas o valor do uuid230. Durante uma campanha de marketing, um log de rastreamento é criado automaticamente com todas as informações de identificação (consulte rastreamento de sessão). O Adobe Campaign pesquisará automaticamente registros anteriores em busca de um valor &quot;uuid230&quot; igual ao valor do log de rastreamento dessa campanha de marketing. Se valores idênticos forem encontrados, todos os logs de rastreamento anteriores serão inseridos com todas as informações do log de rastreamento da campanha de marketing.

Esse modo é o mais dispendioso em termos de cálculo e volume.

>[!NOTE]
>
>Se a variável **[!UICONTROL Leads]** estiver instalado, você precisa fazer o mesmo para a tabela de atividades (**crm:incomingLead**)

O schema a seguir resume as funcionalidades de todos os três modos de rastreamento Web:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Exemplo de rastreamento Web permanente com base no último delivery:**

Florence recebe um delivery, abre o email, clica no link, navega no site de varejo, mas não faz compras. No dia seguinte, Florence volta ao site de varejo, navega e faz uma compra. Como o rastreamento web permanente (última delivery) está ativado, todos os logs para sua segunda visita serão vinculados ao delivery que foi enviado a ela no dia anterior.
