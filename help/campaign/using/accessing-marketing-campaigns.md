---
product: campaign
title: Acessar campanhas de marketing
description: Acessar campanhas de marketing
role: User
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 100%

---

# Acesso às campanhas de marketing{#accessing-marketing-campaigns}

O Adobe Campaign permite criar, configurar, executar e analisar campanhas de marketing. Todas as campanhas de marketing podem ser gerenciadas a partir de um centro de controle unificado.

## Noções básicas do Workspace {#workspace-basics}

### Home page {#home-page}

Depois de se conectar ao Adobe Campaign, é possível navegar pelos vários recursos usando os links da barra de navegação.


![](assets/campaign_global_view.png)


Os elementos de campanha são encontrados na guia **[!UICONTROL Campaigns]**: aqui você pode ter uma visão geral dos programas e campanhas de marketing, bem como de seus subconjuntos. Um programa de marketing é composto por campanhas, que são compostas por entregas, tarefas, recursos vinculados etc. No contexto de gerenciamento de campanhas de marketing que utilizam o Campaign, as informações relacionadas a entregas, orçamentos, revisores e documentos vinculados são encontradas nas campanhas.

O bloco **[!UICONTROL Browsing]** da guia **[!UICONTROL Campaigns]** oferece várias entradas, dependendo dos módulos instalados na instância. Como exemplo, você pode acessar:

* **Calendário da campanha**: calendário de planos, programas de marketing, entregas e campanhas. Consulte [Calendário da campanha](#campaign-calendar).
* **Campanhas**: acesso às campanhas contidas em todos os programas de marketing.
* **Remessas**: acesso às remessas vinculadas às campanhas.
* **Aplicativos Web**: acesso a aplicativos Web (formulários, landing pages etc.).

>[!NOTE]
>
>Para saber mais sobre a ergonomia geral do Adobe Campaign, as permissões e o gerenciamento de perfis, consulte [esta seção](../../platform/using/adobe-campaign-workspace.md).
>
>Todas as funcionalidades relacionadas a canais e entregas são detalhadas [nesta seção](../../delivery/using/steps-about-delivery-creation-steps.md).

### Calendário da campanha {#campaign-calendar}

Cada campanha pertence a um programa que, por sua vez, pertence a um plano. Os planos, programas e campanhas são acessados por meio do menu **[!UICONTROL Campaign calendar]** na guia **Campanhas**.

Para editar um plano, programa, campanha ou entrega, clique no nome no calendário e clique em **[!UICONTROL Open...]**. Eles são exibidos em uma nova guia, conforme mostrado abaixo:

![](assets/d_ncs_user_interface_hierar.png)

Você pode filtrar as informações exibidas no calendário da campanha; para isso, clique no link **[!UICONTROL Filter]** e selecione o critério de filtragem.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>Quando você filtrar em uma data, todas as campanhas com uma data de início posterior à data especificada e/ou com uma data final anterior à data especificada serão exibidas. Selecione datas usando os calendários à direita de cada campo.

Também é possível usar o campo **[!UICONTROL Search]** para filtrar os itens exibidos.

Os ícones vinculados a cada item permitem visualizar o status: concluído, em andamento, sendo editado etc.

### Navegação em um programa de marketing {#browsing-in-a-marketing-program}

O Campaign permite gerenciar um conjunto de programas feitos de várias campanhas de marketing. Cada campanha contém entregas e processos e recursos associados.

#### Procurar um programa {#browsing-a-program}

Ao editar um programa, use as guias descritas abaixo para procurar e configurar.

* A guia **Programação** exibe o calendário de programas de um mês, semana ou dia, dependendo da guia que você selecionar no cabeçalho do calendário.

  Se necessário, você pode criar uma campanha, um programa ou uma tarefa por esta página.

  ![](assets/s_ncs_user_interface_campaign02.png)

* A guia **Editar** permite personalizar o programa: nome, datas de início e término, orçamento, documentos vinculados etc.

  ![](assets/s_ncs_user_interface_campaign05.png)

#### Procurar campanhas {#browsing-campaigns}

As campanhas podem ser acessadas por meio do calendário da campanha, da guia **[!UICONTROL Schedule]** do programa ou da lista de campanhas.

1. Através do calendário da campanha, selecione a campanha que deseja exibir e clique em **[!UICONTROL Open]**.

   ![](assets/campaign_planning_edit_op.png)

   A campanha é editada em uma nova guia, conforme mostrado abaixo:

   ![](assets/campaign_op_edit.png)

1. Na guia **[!UICONTROL Schedule]** do programa, o modo de edição é igual ao que pode ser acessado pelo calendário da campanha.
1. Por meio do link **[!UICONTROL Campaigns]** da guia **[!UICONTROL Campaigns]**, clique no nome da campanha que deseja editar.

   ![](assets/campaign_edit_from_list.png)

### Controlar uma campanha {#controlling-a-campaign}

#### Painel {#dashboard}

Cada campanha, tarefa, recurso e entrega é centralizada em uma única tela - o painel- que permite gerenciar ações de marketing em colaboração com outras pessoas.

O painel de controle de uma campanha é usado como interface de controle. Ele acessa os estágios principais de criação e gerenciamento de campanha diretamente: entregas, arquivos de extração, notificações, orçamentos etc.

![](assets/s_ncs_user_op_board_start_del.png)

Com o Adobe Campaign você pode configurar processos colaborativos para a criação e aprovação dos vários estágios de campanhas de marketing e comunicação: aprovação do orçamento, destino, conteúdo etc.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>A configuração dos modelos de campanha é apresentada em [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Programação {#schedule}

Uma campanha centraliza um conjunto de entregas. Para cada campanha, a programação oferece uma visão global de todos os componentes, permitindo exibir as tarefas e entregas e acessá-los com facilidade.

![](assets/campaign_planning_tab.png)

#### Fórum {#forum}

Para cada campanha, os operadores podem trocar mensagens por meio de um fórum dedicado.

Saiba mais em [Fóruns de discussão](../../mrm/using/discussion-forums.md).

#### Relatórios {#reports}

O link **[!UICONTROL Reports]** permite acessar os relatórios da campanha.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>Os relatórios são detalhados [nesta seção](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Configuração {#configuration}

As campanhas são criadas por meio de templates de campanha. É possível configurar templates reutilizáveis para os quais algumas opções estão selecionadas e outras configurações já estão salvas. Para cada campanha, a seguinte funcionalidade é oferecida:

* Referência de [documentos e recursos](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents): é possível associar documentos a uma campanha (resumo, relatório, imagens etc.). Todos os formatos de documento são compatíveis.
* Definir custos: para cada campanha, o Adobe Campaign permite definir [entradas de custo e estruturas de cálculo de custo](../../campaign/using/providers-stocks-and-budgets.md#defining-cost-categories) que podem ser usadas ao criar a campanha de marketing. Por exemplo: custos de impressão, uso de uma agência externa, aluguel de sala. 
* Definir objetivos: é possível definir objetivos quantificáveis para uma campanha, por exemplo, número de inscritos, volume de negócios etc. Essas informações são usadas posteriormente nos relatórios de campanha.
* Gerenciar [seed addresses](../../delivery/using/about-seed-addresses.md) e [grupos de controle](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).
* Gerenciar aprovações: é possível selecionar os tratamentos a serem aprovados e, se necessário, selecionar os operadores de revisão ou grupos de operadores. [Saiba mais](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>Para acessar as configurações da campanha e fazer alterações, clique no link **[!UICONTROL Advanced campaign parameters...]** na guia **[!UICONTROL Edit]**. 

## Utilização da interface da web {#using-the-web-interface-}

Você pode acessar as telas do console do Adobe Campaign por meio de um navegador da Internet para exibir todas as campanhas e remessas, bem como relatórios e informações dos perfis em seu banco de dados. Este acesso não habilita a criação de registros. Dependendo dos direitos do operador, você pode visualizar e/ou agir nos dados do banco de dados. Por exemplo, você pode aprovar conteúdo de campanha e segmentação, reiniciar ou parar uma entrega etc.

1. Faça logon como de costume via https://`<your instance>:<port>/view/home`.
1. Use os menus para acessar as exibições.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Além de navegar entre campanhas e visualizá-las, é possível executar esses tipos de tarefas:

* Monitorar atividade em uma instância
* Participar de processos de validação como, por exemplo, aprovar ou rejeitar o conteúdo de uma entrega
* Executar outras ações rápidas como, por exemplo, pausar um fluxo de trabalho
* Acessar todos os recursos de relatório
* Participar das discussões do fórum

Esta tabela resume as ações que você pode realizar nas campanhas a partir de um navegador:

| Página  | Ação |
| --- | --- |
| Lista de campanhas, entregas, ofertas, etc. | Excluir um item da lista |
| Campanha | Cancelar uma campanha |
| Entrega | Aprovar o conteúdo e o target da entrega<br/>Enviar o conteúdo da entrega<br/>Confirmar uma entrega<br/>Pausar e parar uma entrega |
| Aplicativo web | Criar um aplicativo web<br/>Editar o conteúdo e as propriedades do aplicativo<br/>Salvar o conteúdo do aplicativo como um modelo<br/>Publicar o aplicativo |
| Oferta | Aprovar o conteúdo e a elegibilidade da oferta<br/>Desabilitar uma oferta online |
| Tarefa | Concluir uma tarefa<br/>Cancelar uma tarefa |
| Recursos de marketing | Aprovar um recurso<br/>Bloquear e desbloquear um recurso |
| Pacotes da campanha | Enviar um pacote para aprovação<br/>Aprovar ou rejeitar um pacote<br/>Cancelar um pacote |
| Pedidos da campanha | Criar um pedido<br/>Aceitar ou rejeitar um pedido <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| Estoque | Excluir uma linha do estoque |
| Simulação de oferta | Iniciar e parar uma simulação |
| Fluxo de trabalho de direcionamento | Iniciar, pausar e parar um fluxo de trabalho |
| Relatórios | Salvar os dados atuais no histórico do relatório |
| Fórum | Adicionar uma discussão<br/>Responder a uma mensagem em uma discussão<br/>Seguir uma discussão e cancelar a inscrição nela |

### Aprovações

Aprovações (de um público-alvo ou conteúdo de entrega, por exemplo) podem ser realizadas via acesso web.

![](assets/campaign_web_interface_validation.png)

Você também pode usar o link contido nas mensagens de notificação. Para obter mais informações, consulte [Verificação e aprovação de entregas](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
