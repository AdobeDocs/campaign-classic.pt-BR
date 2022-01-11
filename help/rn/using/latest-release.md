---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 630a62c5e5c9782c5c55fdebd651493a2d68fc54
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 30%

---

# Versão mais recente{#latest-release}

![](../../assets/v7-only.svg)

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Versão 7.2.1 – Build 9346 {#release-7-2-1}

_10 de janeiro de 2022_

**Aprimoramento de segurança**

Várias melhorias de segurança foram realizadas nas contas da FDA:

* Os drivers ODBC agora são instalados diretamente com terceiros do Adobe Campaign. As etapas manuais não são mais necessárias para instalar esses drivers.
* Ao configurar sua conta externa FDA, agora é possível fazer logon em sua conta do Snowflake usando a autenticação do par de chaves para segurança de autenticação aprimorada. [Leia mais](../../installation/using/configure-fda-snowflake.md)
* Ao configurar sua conta externa FDA, agora é possível fazer logon em sua conta do Azure synapse Analytics usando a identidade gerenciada atribuída pelo sistema. [Leia mais](../../installation/using/configure-fda-synapse.md#azure-external)
* Todas as referências à biblioteca log4j foram removidas do Campaign para garantir a segurança ideal.

**Aprimoramentos** 

* Conector do Microsoft Dynamics CRM 365

   Correções críticas foram aplicadas em relação à API da Web do Microsoft Dynamics Connector:

   * Correção de um problema durante uma importação acionada por um workflow, que fazia com que os valores nulos de campos do tipo string fossem salvos como Null em vez de valores vazios.
   * Correção de um problema que resultava no seguinte erro para importação ou exportação de dados usando chamadas de API da Web: “URI inválido: o esquema de URI é muito longo”.
   * Correção de vários problemas ao importar, a partir do Microsoft Dynamics 365, dados contendo campos de pesquisa.

* Conector FDA do Google BigQuery

   * O Google BigQuery FDA Connector agora está disponível para implantações hospedadas. [Leia mais](../../installation/using/configure-fda-google-big-query.md)
   * Adição de suporte para habilitar conexões com um servidor proxy para o conector Google BigQuery FDA. As opções de proxy necessárias podem ser definidas no campo Opções na configuração da conta externa. [Leia mais](../../installation/using/configure-fda-google-big-query.md#google-external)

**Outras alterações**

* Após a desativação, as atividades de ação Microsoft CRM, Salesforce e Oracle CRM On Demand foram removidas da interface. Para configurar a sincronização de dados entre o Adobe Campaign e um sistema CRM, você pode usar a atividade do conector CRM. [Leia mais](../../workflow/using/crm-connector.md)
* O **[!UICONTROL Encrypted identifier]** foi adicionado ao esquema do visitante (nms:visitor). Esse campo é calculado e deve ser usado para aplicativos web. Isso se aplica quando o canal Line é configurado na instância mid-sourcing.
* As fontes de dados do CRM agora podem ser usadas com o **Alterar fonte de dados** atividade .
* Uma nova opção foi adicionada na **Gerenciamento de erros** propriedades de atividades de workflow: O **Abortar no erro** a opção interromperá automaticamente o fluxo de trabalho. Não será possível reiniciá-lo posteriormente (NEO29661). [Leia mais](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Uma sequência dedicada agora é usada para gerar as chaves primárias para a tabela nmsGroup, que é usada para criar grupos estatísticos de recipients. Anteriormente, a sequência xtknownId era usada. (NEO-30832)
* Adição de suporte para operações de atualização em lote usando a atividade do conector CRM.
* Desempenho aprimorado para o tempo de processamento de mensagens transacionais. (NEO-40370)

**Correções**

* Correção de um problema ao criar um delivery que resultava em erro no **Imagens** da guia **Rastreamento e imagens** janela. Isso ocorria ao usar uma configuração de proxy automático. (NEO-33260)
* Correção de um problema que impedia o upload de um arquivo em um servidor Debian 10 (HTTPS) no modo síncrono.
* Correção de um problema que poderia impedir registros da tabela de estatísticas de deliveries (`nmsDeliveryLogStats`) de ser removido da instância mid-sourcing durante a limpeza do banco de dados depois que os deliveries relacionados foram excluídos. (NEO-31034)
* Correção de um problema que impedia o envio de notificações de aplicativos móveis no iOS ao usar a autenticação por token (NEO38640).
* Correção de um problema que poderia exibir mensagens de erro de script ao tentar criar e configurar relatórios (NEO38393).
* Correção de um problema que resultava em falha no Oracle do workflow de rastreamento devido a grandes volumes de indicadores de delivery sendo atualizados simultaneamente (NEO39653).
* Correção de um problema que impedia o envio de um delivery devido a um erro ao executar uma tipologia de controle (NEO39833).
* Correção de um problema nas páginas de aterrissagem que impedia que caracteres especiais fossem exibidos corretamente nas HTML pages das respostas de pesquisa online (NEO39438).
* Correção de um problema que impedia o funcionamento do console do Campaign Classic ao clicar com o botão direito do mouse em qualquer uma das pastas da guia Explorer (NEO3884).
* Correção de um erro ao usar um template de delivery criado anteriormente vinculado a uma conta do Web Analytics em um novo delivery no qual a configuração do Web Analytics estava ausente. (NEO-28666)
* Correção de um problema que podia impedir a pré-visualização de deliveries de dispositivos móveis que foram anexados a um fluxo de trabalho.
* Correção de um erro que impedia que URLs de rastreamento personalizadas fossem redirecionadas quando o mecanismo de assinatura do URL para links de rastreamento era ativado.
* Correção de um problema que poderia causar falhas de pós-atualização devido a um problema de gerenciamento de índice.
* Correção de um erro que ocorria ao usar tipos de dados de campo de pesquisa com o Microsoft Dynamics CRM em **Importar** ou **Exportar** atividades de workflow.
* Correção de um problema que impedia o logon no console devido a um problema de configuração de proxy. (NEO-38388)
* Correção de um problema de regressão que impedia o funcionamento correto da funcionalidade **Limpar pasta**. (NEO-37459)
* Correção de um problema que resultava em um erro de solicitação incorreta ao usar campos de dados xml com a conta do Microsoft Dynamics CRM se o xml referenciado contivesse aspas duplas.
* Correção de um problema que ocasionava o registro incorreto de complicações de tempo limite como interrupções de script, em vez de erros de rede. Esse problema ocorria no caso de solicitações HTTP que eram incluídas em atividades JavaScript. (NEO-38079)
* Correção de um problema que retornava resultados incorretos ao executar as funções HoursDiff e MinutesDiff do Amazon Redshift para tentar extrair o componente de tempo.(NEO-31673)
* Correção de um problema que impedia o **Hot Clicks** do carregamento para deliveries desde a build 9182. (NEO-28900)
* Correção de um erro que substituiu o símbolo &amp; em um URL pela referência da entidade de caractere (`&amp;`) impedindo que os usuários acessem o URL vinculado a um código QR. (NEO-28621)
* Correção de um problema que criava uma nova conta externa sempre que um usuário criava um novo workflow de campanha e uma atividade de delivery vinculada a uma conta do Web Analytics. Isso foi causado por uma ID ausente no objeto de delivery webAnalyticsAccount. (NEO-39691)
* Correção de um problema que podia impedir o funcionamento da atividade de fluxo de trabalho **Lista de leitura** quando a lista era identificada com uma ID negativa na base de dados. (NEO-39607)
* Correção de um problema com o que poderia resultar no erro **Mid-sourcing (logs do delivery)** falha no fluxo de trabalho. (NEO-39662)
* Correção de um problema que impedia a visualização de deliveries de email anexados a um workflow. (NEO-37840)
* Correção de um problema que fazia com que tabelas válidas que contivessem valores de lista fossem excluídas pelo workflow de limpeza do banco de dados. (NEO-34911)
* Correção de um problema que podia fazer com que o fluxo de trabalho de faturamento falhasse em instâncias de marketing.
