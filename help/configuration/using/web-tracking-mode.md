---
product: campaign
title: Modo de rastreamento Web
description: Saiba como selecionar o modo de rastreamento web
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 1%

---

# Modo de rastreamento Web{#web-tracking-mode}



O Adobe Campaign permite selecionar um modo de rastreamento Web que define como os logs de rastreamento são processados no aplicativo.

Há três modos de rastreamento Web disponíveis: **&quot;Rastreamento de sessão&quot;**,**&quot;Rastreamento permanente&quot;** e **&quot;Rastreamento anônimo&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Cada modo tem características específicas. O modo de rastreamento web &quot;permanente&quot; inclui as características do modo de rastreamento web &quot;sessão&quot;, enquanto o modo &quot;anônimo&quot; inclui as características dos modos &quot;permanente&quot; e &quot;sessão&quot;.

>[!IMPORTANT]
>
>O modo de rastreamento web &quot;anônimo&quot; é ativado por padrão se o pacote &quot;Clientes potenciais&quot; estiver ativado. Em todos os outros casos, o modo de rastreamento web &quot;session&quot; é ativado por padrão.
>
>A qualquer momento, o modo padrão pode ser alterado no assistente de implantação da instância.

Observe que se estiver usando o método **web permanente** ou **anônimo** modo de rastreamento, você deve adicionar um índice à coluna &quot;sourceID&quot; (uuid230) nas tabelas de rastreamento (trackingLogXXX):

1. Identifique as tabelas de rastreamento relacionadas ao rastreamento permanente.
1. Estenda os schemas que correspondem a essas tabelas adicionando as seguintes linhas:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Permanente** e **Anônimo** Os modos de rastreamento web incluem duas opções: **Entrega forçada** e **Última entrega**.

A variável **Entrega forçada** option permite especificar o identificador do delivery (@jobid) durante o rastreamento.

A variável **Última entrega** permite vincular o log de rastreamento atual ao último delivery rastreado.

**Características do rastreamento web da sessão:**

Este modo cria um log de rastreamento para pessoas com um cookie de sessão. São pessoas que clicaram em um URL em um email enviado pelo Adobe Campaign, permitindo rastrear as seguintes informações:

* ID de entrega
* ID de contato
* log de entrega
* cookie permanente (uuid230)
* URL de rastreamento
* data do log de rastreamento

Com esse modo de rastreamento web, se parte das informações estiver ausente, nenhum log de rastreamento será criado no aplicativo.

Esse modo é econômico em termos de volume (número limitado de registros na tabela trackingLog) e cálculo (sem reconciliação).

**Características do modo de rastreamento web permanente:**

Esse modo de rastreamento web permite criar um log de rastreamento com base na presença do cookie uuid230 permanente. Se um visitante fechar a sessão, o Adobe Campaign usará o cookie permanente para recuperar as informações sobre ele nos logs de rastreamento anteriores. O Adobe Campaign insere novamente um log de rastreamento se o uuid230 da sessão atual tiver o mesmo valor que um uuid230 já armazenado na tabela de rastreamento.

Isso significa que o visitante precisa ter sido identificado anteriormente no Adobe Campaign (por meio de uma entrega) para ativar a reconciliação nos valores uuid230.

Por padrão, as pesquisas em logs de rastreamento anteriores são executadas na tabela &quot;trackingLog&quot;. Se o pacote de clientes potenciais estiver ativado, antes de pesquisar a tabela &quot;trackingLog&quot;, o Adobe Campaign pesquisará a tabela &quot;incomingLead&quot; em busca de registros anteriores de log de rastreamento.

Esse modo custa caro em termos de cálculo durante a reconciliação do log.

**Características do modo de rastreamento web anônimo:**

Esse modo de rastreamento web permite recuperar um log de rastreamento vinculado à navegação anônima no Adobe Campaign. Um log de rastreamento é criado automaticamente para cada clique em um URL rastreado. Este log tem apenas o valor de uuid230. Durante uma campanha de marketing, um log de rastreamento é criado automaticamente com todas as informações de identificação (consulte Rastreamento de sessão). O Adobe Campaign pesquisará automaticamente nos logs anteriores por um valor &quot;uuid230&quot; igual ao valor do log de rastreamento para esta campanha de marketing. Se valores idênticos forem encontrados, todos os logs de rastreamento anteriores serão inseridos com todas as informações do log de rastreamento da campanha de marketing.

Esse modo é o mais caro em termos de cálculo e volume.

>[!NOTE]
>
>Se a variável **[!UICONTROL Leads]** for instalado, você precisará fazer o mesmo para a tabela de atividades (**crm:incomingLead**)

O schema a seguir soma as funcionalidades dos três modos de rastreamento Web:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Exemplo de rastreamento web permanente com base no último delivery:**

Florence recebe um delivery, abre o email, clica no link, navega no site de varejo, mas não faz compras. No dia seguinte, Florence retorna ao site de varejo, navega e faz uma compra. Como o rastreamento web permanente (último delivery) está ativado, todos os logs de sua segunda visita serão vinculados ao delivery que foi enviado a ela no dia anterior.
