---
solution: Campaign Classic
product: campaign
title: Sobre perfis
description: Sobre perfis
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 99%

---


# Sobre perfis{#about-profiles}

Os perfis (clientes, clientes potenciais, assinantes de boletim informativo etc.) são centralizados no banco de dados do Adobe Campaign. Há vários mecanismos possíveis para obter perfis e criar esse banco de dados: coleta online via formulários Web, importação manual ou automática de arquivos de texto, replicação com bancos de dados corporativos ou outros sistemas de informações. Com o Adobe Campaign, você pode incorporar o histórico de marketing, informações de compras, preferências, dados de CRM e quaisquer dados de PI relevantes em uma exibição consolidada para analisar e tomar decisões.

No Adobe Campaign, os recipients são os perfis padrão direcionados para envio de deliveries (emails, SMS, etc.). Graças aos dados dos recipients que são armazenados no banco de dados, você poderá filtrar o recipient que receberá qualquer delivery e adicionar dados de personalização ao seu conteúdo de delivery. Existem outros tipos de perfis no banco de dados. Esses perfis foram projetados para diferentes usos. Por exemplo, perfis iniciais são feitos para testar seus deliveries antes que sejam enviados ao público-alvo final.

![](assets/do-not-localize/how-to-video.png) [Compreender o conceito de perfis em vídeo](#create-profiles-video)

## Tipos de perfil {#profile-types}

O Adobe Campaign permite gerenciar perfis em todo o ciclo de vida: criação, importação, direcionamento, rastreamento de ações, atualizações, etc.

Cada perfil corresponde a uma entrada do banco de dados. Eles contêm todas as informações necessárias para direcionamento, qualificação e acompanhamento de indivíduos.

Os perfis podem ser identificados com base no espaço de armazenamento. Isso significa que um perfil pode corresponder a: um recipient, um visitante, um operador, um assinante, um prospecto, etc.

## Perfis de destinatário {#recipient-profiles}

Os recipients do delivery são armazenados no banco de dados como perfis que contêm as informações vinculadas a eles: sobrenome, nome, endereço, assinaturas, deliveries, etc. Ao criar campanhas, é possível definir o direcionamento dos deliveries a uma seleção de perfis da base de acordo com critérios simples ou avançados.

Também é possível criar campanhas direcionadas a destinatários cujos perfis estão armazenados em arquivos, em vez de em banco de dados. Elas são conhecidas como deliveries “externos”. Para obter mais informações sobre esse tipo de delivery, consulte [esta página](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

Os principais métodos para criar perfis de destinatários são os seguintes:

* entrada direta nas telas da interface gráfica;
* importação de listas de destinatários;
* coleta on-line via formulários web.

>[!NOTE]
>
>Para saber como arquivos e formulários web são importados, consulte [Importações e exportações genéricas](../../platform/using/generic-imports-and-exports.md).

## Profiles and targets {#profiles-and-targets}

O link **[!UICONTROL Profiles and targets]** permite exibir os recipients armazenados no banco de dados do Adobe Campaign. É possível criar um novo destinatário, editar um destinatário existente e acessar o perfil dele. Para obter mais informações, consulte [esta página](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Ele também dá acesso a:

* listas; consulte [Criação e gerenciamento de listas](../../platform/using/creating-and-managing-lists.md),
* serviços de assinatura; consulte [esta página](../../delivery/using/managing-subscriptions.md);
* aplicativos web; consulte [esta página](../../web/using/about-web-applications.md);
* importações e exportações (tarefas); consulte [Importações e exportações genéricas](../../platform/using/generic-imports-and-exports.md),
* fluxos de trabalho de direcionamento; consulte [esta página](../../workflow/using/building-a-workflow.md#implementation-steps-).

A página de destinatários permite executar operações frequentes em perfis: edições, atualizações, adições, exclusões e classificações.

Para manipulações de perfil mais avançadas, é necessário editar a árvore do Adobe Campaign. Para fazer isso, clique no link **[!UICONTROL Explorer]** na página inicial do Adobe Campaign.

Por padrão, os recipients são armazenados no nó **[!UICONTROL Profiles and Targets > Recipients]** da árvore. É possível criar destinatários nesta tela, bem como:

* classificar e filtrar os perfis do banco de dados; consulte [Opções de filtragem](../../platform/using/filtering-options.md),
* mover, copiar ou excluir perfis do banco de dados; consulte [Gerenciamento de perfis](../../platform/using/managing-profiles.md),
* atualizar perfis; consulte [Atualização de dados](../../platform/using/updating-data.md),
* destinatários da exportação; consulte [Exportação e importação de perfis](../../platform/using/exporting-and-importing-profiles.md),
* criar grupos de recipients; consulte [Criação e gerenciamento de listas](../../platform/using/creating-and-managing-lists.md).

Para acessar funcionalidades e configurações avançadas, clique no ícone **[!UICONTROL Explorer]**.

![](assets/d_ncs_user_interface01.png)

O layout geral do Adobe Campaign Explorer é apresentado em [Uso do Adobe Campaign Explorer](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).

>[!NOTE]
>
>Também é possível exibir uma visualização avançada dessa lista na árvore do Adobe Campaign clicando no link **[!UICONTROL Profiles and targets > Recipients]**. A exibição da lista pode ser configurada para atender às suas necessidades. É possível adicionar ou excluir colunas, definir a ordem das colunas, classificar dados etc. A configuração de exibição de lista é descrita em [Uso do Adobe Campaign Explorer](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).
>
>Também é possível definir as visualizações de destinatários. Para obter mais informações sobre essa funcionalidade, consulte [Pastas e exibições](../../platform/using/access-management.md#folders-and-views).

## Perfis ativos {#active-profiles}

Os perfis ativos são aqueles que são contados para fins de cobrança.

>[!NOTE]
>
>Se você estiver hospedado no AWS usando o Campaign Classic a partir da build 8931, também poderá monitorar o número de perfis ativos usados em suas instâncias diretamente do Painel de controle do Campaign. Para obter mais informações, consulte a [documentação do Painel de controle do Campaign](https://docs.adobe.com/content/help/pt-BR/control-panel/using/performance-monitoring/active-profiles-monitoring.html).
>
>Observe que a contagem de perfis ativos está disponível somente para **Instâncias de marketing**. Não está disponível para instância de execução, ou seja, instâncias de MID (mid-sourcing) e RT (Centro de mensagens/Mensagens em tempo real).

“**Perfil**” significa um registro de informações (por exemplo: um registro na tabela nmsRecipient ou uma tabela externa contendo uma ID de cookie, ID do cliente, identificador móvel ou outras informações relevantes para um canal específico) representando um cliente final, um prospecto ou um cliente potencial.

A cobrança só afeta perfis que estão **ativos**. Um perfil é considerado ativo quando ele é visado ou recebe comunicação nos últimos 12 meses por meio de qualquer canal.

Os perfis excluídos durante a preparação do delivery (regras de tipologia, quarentenas) não são levados em consideração. Um perfil que foi direcionado por vários deliveries será contado apenas uma vez.

>[!NOTE]
>
>Os canais Facebook e Twitter não são considerados.

Você pode ter uma visão geral do **[!UICONTROL Number of active profiles]** a partir do menu **[!UICONTROL Administration > Campaign Management > Customer metrics]** do Campaign Standard. A contagem real é executada pelo **[!UICONTROL Number of active billing profiles]** [workflow técnico](../../workflow/using/deliveries.md) (**[!UICONTROL billingActiveContactCount]**), que é executado diariamente e adiciona os novos dados ao relatório existente para o período atual no menu **[!UICONTROL Customer metrics]**. Cada período dura 12 meses.

## Como criar e gerenciar perfis {#create-profiles-video}

Saiba como acessar os dados do perfil, classificar e filtrar perfis, além de criar e gerenciar perfis manualmente.

Este vídeo também explica a conformidade da Adobe Campaign Classic com os Regulamentos Gerais de Proteção de Dados.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

**Consulte também**

* [Gerenciamento de privacidade na Campanhas](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html)

* [Definir a população de público-alvo](../../delivery/using/define-the-right-audience.md)

* [Criar query e dados de segmento em workflows](../../workflow/using/targeting-data.md)

* [Selecionar target mapping](../../delivery/using/selecting-a-target-mapping.md)

* [Definir o público-alvo – práticas recomendadas](../../delivery/using/define-the-right-audience.md)
