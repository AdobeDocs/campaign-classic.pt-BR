---
product: campaign
title: Versão mais recente
description: Notas de versão mais recentes do Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 0d0c97213cf8b95bbadd06f4c5666213b6c6c8f1
workflow-type: tm+mt
source-wordcount: '1987'
ht-degree: 98%

---

# Versão mais recente{#latest-release}

![](../../assets/v7-only.svg)

Esta página lista novos recursos, melhorias e correções que vêm com a **versão mais recente do Campaign v7**. Cada nova build vem com um status que é materializado por uma cor. Saiba mais sobre os status de build do Campaign Classic v7 [nesta página](rn-overview.md).

## ![](assets/do-not-localize/limited_2.png) Versão 7.3.1 - Build 9352 {#release-7-3-1}

_1 de julho de 2022_

**Novidades**

<table> 
<thead>
<tr> 
<th> <strong>Notificações sensíveis ao tempo</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Com o iOS 15, a Apple adicionou uma noção de notificação relevante, que dá controle ao desenvolvedor do aplicativo para ignorar o modo de Foco quando uma notificação é considerada relevante e precisa ser entregue ao usuário em tempo real.</p>
<p>Saiba como criar uma notificação confidencial na <a href="../../delivery/using/create-notifications-ios.md">documentação detalhada</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Atualizações de compatibilidade**

* O SDK do Adobe Campaign agora é compatível com notificações por push no Android 12 e iOS 15.
* O Adobe Campaign agora é compatível com o MySQL 8.
* O Adobe Campaign agora é compatível com o Windows 11.
* O Adobe Campaign agora é compatível com o Debian 11.

Consulte a [Matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Aprimoramentos**

* Após o fim da vida útil do Internet Explorer 11, o mecanismo de renderização de HTML da Adobe Services no console passou a usar o Edge Chromium. Além disso, a instalação do Webview 2 Runtime do Microsoft Edge agora é necessária para qualquer instalação do console do cliente (a partir da versão de build 7.3 do Campaign Classic). [Leia mais](../../installation/using/installing-the-client-console.md)
* O gerenciamento de conexão de banco de dados no Adobe Campaign foi aprimorado para otimizar a estabilidade.
* A autenticação OAuth 2.0 do Microsoft Exchange Online para POP3 agora é compatível com o Campaign. [Leia mais](../../installation/using/external-accounts.md#bounce-mails-external-account)
* Correção de vários problemas ao usar uma atividade de fluxo de trabalho de enriquecimento com dados externos. (NEO-38069)
* O conector FDA do SAP HANA foi atualizado para funcionar com a versão mais recente do banco de dados SAP HANA (2.x).
* O conector FDA do Teradata foi atualizado para funcionar com a versão mais recente do Teradata (17).
* Na versão 20.2, foi introduzida a compatibilidade com autenticação baseada em token para novos deliveries e modelos de delivery do iOS. Na versão 7.2, uma correção foi adicionada à pós-atualização para aplicar a compatibilidade com a autenticação baseada em token a um máximo de 10.000 deliveries e modelos de delivery criados anteriormente. Na versão 7.3, a correção foi melhorada e o limite foi removido.

**Correções**

* Correção de um erro da build anterior que impedia os usuários de redimensionar a página de logon do IMS. (NEO-30085)
* Correção de um erro que ocorria ao instalar o pacote do gerenciador de conteúdo em uma instância existente. (NEO-32349)
* Correção de um problema no menu **Campanhas** em que a mensagem “operação em andamento” era exibida continuamente. (NEO-44904)
* Com o Adobe Analytics ativado, foi corrigido um problema que removia a BID (Broadlog ID) e a CID (ID da campanha) do URL ao enviar um email com um URL sem salvar a entrega. (NEO-38678)
* Correção de um problema que ocorria ao carregar uma imagem para a pasta Recursos públicos em uma instância com configuração específica do Centro de mensagens. A seguinte mensagem de erro era exibida: “Não foi possível carregar as imagens para os servidores de rastreamento”. (NEO-38546, NEO-45572)
* Correção de um problema que fazia com que o sistema falhasse ao regenerar uma configuração, no caso de arquivos mal configurados. (NEO-38752)
* Correção de um problema que poderia resultar na atualização incorreta dos indicadores de entrega. (NEO-44827)
* Correção de um problema que poderia levar a um erro pós-atualização ao usar consultas complexas. (NEO-43648)
* Correção de um problema que impedia o funcionamento da visualização de webApps. (NEO-43242)
* Correção de um problema que resultava na falha da preparação do delivery ao usar um arquivo de target mapping externo em um fluxo de trabalho com uma atividade de carregamento de dados (arquivo). (NEO-43691)
* Correção de um problema que poderia causar falhas e exigir uma reinicialização completa da instância. (NEO-44645)
* Correção de um problema que impedia o Workflow Heatmap de carregar qualquer resultado. (NEO-43360)
* Correção de um problema que poderia levar a problemas de conexão ao usar o conector externo FDA. (NEO-42722)
* Correção de um problema com provas ao usar substituição de endereço e exclusão de grupo de controle. (NEO-39695)
* Correção de um problema que poderia resultar em falhas de fluxo de trabalho devido a um problema no conector Snowflake. (NEO-46299)
* Correção de um problema que poderia congelar o console do cliente devido a um caractere inválido em um bloco de personalização. (NEO-45761)
* Correção de um problema que poderia levar a problemas de conexão ao criar uma conta externa para o Snowflake como um banco de dados externo. (NEO-45744)
* Correção de um problema que poderia resultar na exibição de informações de tabela protegidas por um atributo visibleIf. (NEO-37865)
* Correção de um problema que poderia exibir a mensagem de erro “$ não está definido” durante a fase de análise da entrega. (NEO-32940)
* Correção de um problema que fazia com que os deliveries fossem associados a um eventType incorreto. (NEO-45743)
* Correção de um problema que poderia resultar em falhas devido a descartes de núcleo intermitentes (NEO-30549)
* Correção de um problema que poderia resultar em falhas ao usar um código HTML incorreto em uma entrega. (NEO-40385)
* Correção de um problema que poderia impedir que usuários não administradores acessassem a guia **Análise** nas propriedades da entrega. (NEO-34025)
* Correção de um problema que impedia o upload de uma imagem no modo de partes de um servidor externo durante a preparação da mensagem. (NEO-40307)

## ![](assets/do-not-localize/green_2.png) Versão 7.2.2 - Build 9349 {#release-7-2-2}

_1º de março de 2022_

>[!NOTE]
>
> Esta build é compatível com o Console do cliente v7.2.1.

**Correções**

* Correção de um problema ao configurar a conta externa do **Web Analytics**, o que fazia com que o status de integração sempre mostrasse &quot;Integração bem-sucedida&quot; mesmo quando ocorriam erros. (NEO-36672)
* Correção de vários erros pós-atualização relacionados ao mecanismo de ID de sequência ao ter IDs negativas. (NEO-43205, NEO-42846, NEO-42845)
* Correção de um problema ao usar a conta externa do **Web Analytics** com entregas recorrentes e contínuas, o que causava a perda parcial de dados da conta externa. (NEO-38548)
* Correção de um problema que atrasava a pós-atualização ao atualizar a tabela NmsActiveContact . (NEO-43206)
* Correção de um problema de falha pós-atualização que ocorria se as pastas prontas para uso fossem movidas do nó **Administração** para qualquer outro local. (NEO-42875)
* Correção de um problema ao usar uma atividade de fluxo de trabalho **Atualizar dados**, que poderia impedir que o esquema do recipient fosse atualizado com dados do recipient de um banco de dados externo da Google Cloud. (NEO-42343)
* Correção de um problema durante a pós-atualização relacionado ao conector do Adobe Analytics. (NEO-43318, NEO-38136)
* Correção de um problema que substituía o CUID por &#39;VALUE_TO_CHANGE&#39; durante a pós-atualização. (NEO-43267)
* Correção de um problema que resultava em erros ao sincronizar as instâncias de mid-sourcing e de marketing em uma configuração multimid. (NEO-10432)
* Correção de um problema que resultava em erro ao atualizar o fluxo de trabalho da capacidade de delivery ao ter mais de 1.000 broadlogs ao mesmo tempo. (NEO-40276)
* Correção de um problema que impedia que os indicadores de delivery de taxa de abertura e de taxa de cliques fossem atualizados automaticamente. (NEO-43253)

## ![](assets/do-not-localize/limited_2.png) Versão 7.2.1 - Build 9346 {#release-7-2-1}

_10 de janeiro de 2022_

**Aprimoramento de segurança**

Várias melhorias de segurança foram realizadas nas contas FDA:

* Ao configurar sua conta externa FDA, agora é possível fazer logon em sua conta do Snowflake usando a autenticação de par de chaves, para maior segurança na autenticação. [Leia mais](../../installation/using/configure-fda-snowflake.md)
* Ao configurar sua conta externa FDA, agora é possível fazer logon em sua conta do Azure Synapse Analytics usando a identidade gerenciada atribuída pelo sistema. [Leia mais](../../installation/using/configure-fda-synapse.md#azure-external)
* Todas as referências à biblioteca log4j foram removidas do Campaign para garantir a segurança ideal.

**Atualizações de compatibilidade**

O Adobe Campaign agora é compatível com o Windows Server 2019. Consulte a [Matriz de compatibilidade do Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Aprimoramentos**

* Conector do Microsoft Dynamics CRM 365

   Correções críticas foram aplicadas em relação à API da web do Microsoft Dynamics Connector:

   * Correção de um problema durante uma importação acionada por um workflow, que fazia com que os valores nulos de campos do tipo string fossem salvos como Null em vez de valores vazios.
   * Correção de um problema que resultava no seguinte erro para importação ou exportação de dados usando chamadas de API da Web: “URI inválido: o esquema de URI é muito longo”.
   * Correção de vários problemas ao importar dados contendo campos de pesquisa a partir do Microsoft Dynamics 365.

* Conector FDA do Google BigQuery

   * O conector FDA do Google BigQuery agora está disponível para implantações hospedadas. [Leia mais](../../installation/using/configure-fda-google-big-query.md)
   * Adicionado suporte para habilitar conexões com um servidor proxy para o conector FDA do Google BigQuery. As opções de proxy necessárias podem ser definidas no campo Opções, na configuração da conta externa. [Leia mais](../../installation/using/configure-fda-google-big-query.md#google-external)

**Outras alterações**

* Após serem descontinuados, o Microsoft CRM, o Salesforce e o Oracle CRM tiveram suas atividades de ações por demanda removidas da interface. Para configurar a sincronização de dados entre o Adobe Campaign e um sistema CRM, é possível usar a atividade do conector CRM. [Leia mais](../../workflow/using/crm-connector.md)
* O campo **[!UICONTROL Encrypted identifier]** foi adicionado ao esquema de visitante (nms:visitor). Esse campo é calculado e deve ser usado para aplicativos web. Isso se aplica quando o canal Line é configurado na instância mid-sourcing.
* As fontes de dados do CRM agora podem ser usadas com a atividade **Alterar fonte de dados**.
* Uma nova opção foi adicionada nas propriedades de **Gerenciamento de erros** das atividades do fluxo de trabalho: a opção **Abort on error** interrompe automaticamente o fluxo de trabalho. Não será possível reiniciá-lo posteriormente (NEO-29661). [Leia mais](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Agora, uma sequência dedicada é usada para gerar as chaves primárias para a tabela nmsGroup, que é usada para criar grupos estatísticos de recipients. Anteriormente, a sequência xtknewId era usada. (NEO-30832)
* Adicionado suporte para operações de atualização em lote usando a atividade do conector CRM.
* Desempenho aprimorado do tempo de processamento de mensagens transacionais. (NEO-40370)

**Correções**

* Correção de um problema ao criar um delivery que resultava em erro na guia **Images** da janela **Tracking &amp; images**. Isso ocorria ao usar uma configuração de proxy automático. (NEO-33260)
* Correção de um problema que impedia o upload de arquivos em um servidor Debian 10 (HTTPS) no modo síncrono.
* Correção de um problema que poderia impedir que registros da tabela de estatísticas de deliveries (`nmsDeliveryLogStats`) fossem removidos da instância mid-sourcing durante a limpeza do banco de dados, após a exclusão dos deliveries relacionados. (NEO-31034)
* Correção de um problema que impedia o envio de notificações de aplicativos móveis no iOS ao usar a autenticação por token (NEO-38640).
* Correção de um problema que poderia exibir mensagens de erro de script ao tentar criar e configurar relatórios (NEO-38393).
* Correção de um problema que causava falha no fluxo de trabalho de rastreamento do Oracle devido a grandes volumes de indicadores de delivery sendo atualizados simultaneamente (NEO-39653).
* Correção de um problema que impedia o envio de um delivery devido a um erro ao executar uma tipologia de controle (NEO-39833).
* Correção de um problema nas páginas de aterrissagem que impedia que caracteres especiais fossem exibidos corretamente nas páginas HTML das respostas de pesquisas online (NEO-39438).
* Correção de um problema que impedia o funcionamento do console do Campaign Classic ao clicar com o botão direito do mouse em qualquer uma das pastas da guia Explorer (NEO-38884).
* Correção de um erro ao usar um template de delivery criado anteriormente e vinculado a uma conta do Web Analytics em um novo delivery, no qual a configuração do Web Analytics ficava ausente. (NEO-28666)
* Correção de um problema que podia impedir a pré-visualização de deliveries de dispositivos móveis que foram anexados a um fluxo de trabalho.
* Correção de um erro que impedia que URLs de rastreamento personalizadas fossem redirecionadas quando o mecanismo de assinatura da URL para links de rastreamento era ativado.
* Correção de um problema que poderia causar falhas após a atualização devido a um problema de gerenciamento de índice.
* Correção de um erro que ocorria ao usar tipos de dados de campo de pesquisa com o Microsoft Dynamics CRM em atividades de fluxo de trabalho de **Importação** ou **Exportação**.
* Correção de um problema que podia impedir os usuários de fazerem logon no console devido a um problema de configuração de proxy. (NEO-38388)
* Correção de um problema de regressão que impedia o funcionamento correto da funcionalidade **Limpar pasta**. (NEO-37459)
* Correção de um problema que resultava em um erro de solicitação incorreta ao usar campos de dados XML com a conta do Microsoft Dynamics CRM se o XML em questão contivesse aspas duplas.
* Correção de um problema que ocasionava o registro incorreto de problemas de tempo limite de rede como interrupções de script, em vez de erros de rede. Esse problema ocorria no caso de solicitações HTTP que eram incluídas em atividades JavaScript. (NEO-38079)
* Correção de um problema que retornava resultados incorretos ao executar as funções HoursDiff e MinutesDiff do Amazon Redshift para tentar extrair o componente de tempo.(NEO-31673)
* Correção de um problema que impedia o carregamento do relatório **Hot Clicks** em deliveries desde o build 9182. (NEO-28900)
* Correção de um erro que substituía o símbolo &amp; em um URL pela entidade de caractere de referência (`&amp;`), impedindo usuários de acessarem o URL vinculado a um código QR. (NEO-28621)
* Correção de um problema que criava uma nova conta externa sempre que um usuário criava um novo fluxo de trabalho de campanha e uma atividade de delivery vinculada a uma conta do Web Analytics. Isso era causado por uma ID ausente no objeto de delivery webAnalyticsAccount. (NEO-39691)
* Correção de um problema que podia impedir o funcionamento da atividade de fluxo de trabalho **Lista de leitura** quando a lista era identificada com uma ID negativa na base de dados. (NEO-39607)
* Correção de um problema que poderia resultar na falha do fluxo de trabalho **Mid-sourcing (logs de delivery)**. (NEO-39662)
* Correção de um problema que podia impedir a pré-visualização de deliveries de email que foram anexados a um fluxo de trabalho. (NEO-37840)
* Correção de um problema que fazia com que tabelas válidas que contivessem valores de lista fossem excluídas pelo fluxo de trabalho de limpeza do banco de dados. (NEO-34911)
* Correção de um problema que podia fazer com que o fluxo de trabalho de faturamento falhasse em instâncias de marketing.
