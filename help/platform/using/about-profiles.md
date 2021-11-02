---
product: campaign
title: Sobre perfis
description: Sobre perfis
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: ed43a632a962747c9402ff8d5f0ce442c2cc6490
workflow-type: ht
source-wordcount: '836'
ht-degree: 100%

---

# Introdução a perfis{#about-profiles}

![](../../assets/common.svg)

Os perfis são centralizados no banco de dados do Adobe Campaign. Há vários mecanismos possíveis para obter perfis e criar esse banco de dados: coleta online via formulários Web, importação manual ou automática de arquivos de texto, replicação com bancos de dados corporativos ou outros sistemas de informações. Com o Adobe Campaign, você pode incorporar o histórico de marketing, informações de compras, preferências, dados de CRM e quaisquer dados de PI relevantes em uma exibição consolidada para analisar e tomar decisões.

“**Perfil**” significa um registro de informações (por exemplo: um registro na tabela nmsRecipient ou uma tabela externa contendo uma ID de cookie, uma ID do cliente, um identificador móvel ou outras informações relevantes para um canal específico) representando um cliente final, um prospecto ou um cliente potencial.

No Adobe Campaign, os recipients são os perfis padrão direcionados para envio de deliveries (emails, SMS etc.). Os dados do recipient armazenados no banco de dados permitem filtrar o target que receberá qualquer delivery e adicionar dados de personalização ao conteúdo de delivery. Existem outros tipos de perfis no banco de dados. Esses perfis foram projetados para diferentes usos. Por exemplo, perfis iniciais são feitos para testar seus deliveries antes que sejam enviados ao público-alvo final.

![](assets/do-not-localize/how-to-video.png) [Compreender o conceito de perfis em vídeo](#create-profiles-video)

## Tipos de perfil {#profile-types}

O Adobe Campaign permite gerenciar perfis em todo o ciclo de vida: criação, importação, direcionamento, rastreamento de ações, atualizações, etc.

Cada perfil corresponde a uma entrada do banco de dados. Eles contêm todas as informações necessárias para direcionamento, qualificação e acompanhamento de indivíduos.

Os perfis podem ser identificados com base no espaço de armazenamento. Isso significa que um perfil pode corresponder a: um recipient, um visitante, um operador, um assinante, um prospecto, etc.

## Perfis de recipient {#recipient-profiles}

Os recipients do delivery são armazenados no banco de dados como perfis que contêm as informações vinculadas a eles: sobrenome, nome, endereço, assinaturas, deliveries, etc. Ao criar campanhas, é possível definir o direcionamento dos deliveries a uma seleção de perfis da base de acordo com critérios simples ou avançados.

Também é possível criar campanhas direcionadas a destinatários cujos perfis estão armazenados em arquivos, em vez de em banco de dados. Elas são conhecidas como deliveries “externos”. Para obter mais informações sobre esse tipo de delivery, consulte [esta página](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

Os principais métodos para criar perfis de destinatários são os seguintes:

* entrada direta nas telas da interface gráfica;
* importação de listas de destinatários;
* coleta on-line via formulários web.

>[!NOTE]
>
>Para saber como arquivos e formulários web são importados, consulte [Importações e exportações genéricas](../../platform/using/get-started-data-import-export.md).

## Perfis e targets {#profiles-and-targets}

O link **[!UICONTROL Profiles and targets]** permite exibir os recipients armazenados no banco de dados do Adobe Campaign. É possível criar um novo destinatário, editar um destinatário existente e acessar o perfil dele. Para obter mais informações, consulte [esta página](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Ele também dá acesso a:

* listas - [Saiba mais](../../platform/using/creating-and-managing-lists.md)
* serviços de assinatura - [Saiba mais](../../delivery/using/managing-subscriptions.md)
* aplicativos Web - [Saiba mais](../../web/using/about-web-applications.md)
* importações e exportações (tarefas) - [Saiba mais](../../platform/using/about-generic-imports-exports.md)
* workflows para construção do target - [Saiba mais](../../workflow/using/building-a-workflow.md#implementation-steps-)

A página de destinatários permite executar operações frequentes em perfis: edições, atualizações, adições, exclusões e classificações.

Para manipulações de perfil mais avançadas, é necessário editar a árvore do Adobe Campaign. Para fazer isso, clique no link **[!UICONTROL Explorer]** na página inicial do Adobe Campaign.

Por padrão, os recipients são armazenados no nó **[!UICONTROL Profiles and Targets > Recipients]** da árvore. É possível criar recipients nesta visualização, bem como:

* classificar e filtrar os perfis do banco de dados - [Saiba mais](../../platform/using/filtering-options.md)
* mover, copiar ou excluir perfis do banco de dados - [Saiba mais](../../platform/using/managing-profiles.md),
* atualizar perfis - [Saiba mais](../../platform/using/updating-data.md)
* exportar recipients - [Saiba mais](../../platform/using/exporting-and-importing-profiles.md)
* criar grupos de recipients - [Saiba mais](../../platform/using/creating-and-managing-lists.md)

Para acessar funcionalidades e configurações avançadas, clique no ícone **[!UICONTROL Explorer]**.

![](assets/d_ncs_user_interface01.png)

O layout geral do explorador do Adobe Campaign é apresentado [nesta página](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>Também é possível exibir uma visualização avançada dessa lista na árvore do Adobe Campaign clicando no link **[!UICONTROL Profiles and targets > Recipients]**. A exibição da lista pode ser configurada para atender às suas necessidades. É possível adicionar ou excluir colunas, definir a ordem das colunas, classificar dados etc. A configuração de exibição de lista é descrita [nesta página](../../platform/using/adobe-campaign-ui-lists.md).
>
>Também é possível definir as visualizações de recipients. Para obter mais informações sobre esta funcionalidade, consulte [esta seção](../../platform/using/access-management-folders.md).

## Perfis ativos {#active-profiles}

Os perfis ativos são aqueles que são contados para fins de faturamento.

A cobrança só afeta perfis que estão **ativos**. Um perfil é considerado ativo quando ele é visado ou recebe comunicação nos últimos 12 meses por meio de qualquer canal.

Um perfil que se tornou alvo de vários deliveries é contado apenas uma vez.

>[!NOTE]
>
>Os canais Facebook e Twitter não são considerados.

A contagem de perfis ativos está disponível somente para **Instâncias de marketing**. Não está disponível para Instâncias de execução, ou seja, instâncias de MID (mid-sourcing) e RT (Centro de mensagens/Mensagens em tempo real).

>[!NOTE]
>
>Você também pode monitorar o número de perfis ativos em sua instância diretamente do Painel de controle do Campaign. Para obter mais informações, consulte a [documentação do Painel de controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=pt-BR).

## Tutorial em vídeo {#create-profiles-video}

Saiba como acessar os dados do perfil, classificar e filtrar perfis, além de criar e gerenciar perfis manualmente.

Este vídeo também explica a conformidade da Adobe Campaign Classic com os Regulamentos Gerais de Proteção de Dados.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).

**Consulte também**

* [Gerenciamento da privacidade no Campaign](https://helpx.adobe.com/br/campaign/kb/acc-privacy.html)

* [Definir a população do target](../../delivery/using/define-the-right-audience.md)

* [Criar queries e dados de segmento em workflows](../../workflow/using/targeting-data.md)

* [Selecionar target mapping](../../delivery/using/selecting-a-target-mapping.md)

* [Definir o público - práticas recomendadas](../../delivery/using/define-the-right-audience.md)
