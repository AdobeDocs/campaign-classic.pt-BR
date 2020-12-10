---
solution: Campaign Classic
product: campaign
title: Painel de delivery
description: Saiba mais sobre como usar o painel do delivery para monitorar seus delivery.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 3c82e30cdc1057be6357d48170b959fb89c79528
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 50%

---


# Painel de delivery {#delivery-dashboard}

O **painel de delivery** é fundamental para monitorar seus deliveries e eventuais problemas encontrados durante o envio de mensagens.

Ele permite recuperar informações sobre um delivery e editá-las, se necessário. Observe que o conteúdo da guia não pode mais ser alterado depois que o delivery é enviado.

Estas são as informações que você pode monitorar usando as várias guias disponíveis no painel:

* [Resumo da entrega](#delivery-summary)
* [Relatórios de delivery](#delivery-reports)
* [Logs do delivery, mirrores page, exclusões](#delivery-logs-and-history)
* [Logs de rastreamento e histórico do delivery](#tracking-logs)
* [renderização de delivery](#delivery-rendering)
* [Auditoria de delivery](#delivery-audit-)

![](assets/s_ncs_user_del_details.png)

**Tópicos relacionados:**

* [Noções básicas sobre falhas de delivery](../../delivery/using/understanding-delivery-failures.md)
* [Noções básicas sobre gestão de quarentena](../../delivery/using/understanding-quarantine-management.md)
* [Práticas recomendadas para delivery](../../delivery/using/delivery-best-practices.md)
* [Gerenciamento da capacidade de entrega](../../delivery/using/about-deliverability.md)

## Resumo do delivery {#delivery-summary}

A guia **[!UICONTROL Summary]** contém as características do delivery: status do delivery, canal usado, informações sobre o remetente, assunto, informações relacionadas à execução.

## Relatórios de delivery {#delivery-reports}

O link **[!UICONTROL Reports]**, que pode ser acessado na guia **[!UICONTROL Summary]**, permite que você veja um conjunto de relatórios relacionados à ação do delivery: relatório geral do delivery, relatório detalhado, relatório do delivery, distribuição de mensagens com falha, taxa de abertura, cliques e transações etc.

O conteúdo dessa guia pode ser configurado de acordo com os requisitos. Para obter mais informações sobre relatórios do delivery, consulte [esta seção](../../reporting/using/delivery-reports.md).

![](assets/delivery-report.png)

## Logs do delivery, histórico e exclusões {#delivery-logs-and-history}

A guia **[!UICONTROL Delivery]** fornece um histórico das ocorrências neste delivery. Ela contém os logs de delivery, ou seja, a lista de mensagens enviadas e seus status, e as mensagens associadas.

Para um delivery, você pode exibir (por exemplo) apenas os recipients com um delivery com falha ou um endereço em quarentena. Para fazer isso, clique no botão **[!UICONTROL Filters]** e selecione **[!UICONTROL By state]**. Em seguida, selecione o estado na lista suspensa. Vários status estão listados em [esta página](../../delivery/using/delivery-statuses.md).

>[!NOTE]
>
>A lista que exibe os logs do delivery pode ser personalizada, como qualquer lista no Campaign Classic. Por exemplo, você pode adicionar uma coluna para saber qual endereço IP enviou cada email em um delivery. Para obter mais informações, consulte o caso de uso detalhado em [this section](#use-case).

![](assets/s_ncs_user_delivery_delivery_tab.png)

O link **[!UICONTROL Display the mirror page for this message...]** permite exibir a mirror page do conteúdo do delivery selecionado na lista em uma nova janela.

A mirror page só está disponível para os deliveries para as quais o conteúdo HTML foi definido. Para obter mais informações, consulte [Geração da mirror page](../../delivery/using/sending-messages.md#generating-the-mirror-page).

![](assets/s_ncs_user_wizard_miror_page_link.png)

## Logs de rastreamento de delivery e histórico {#tracking-logs}

A guia **[!UICONTROL Tracking]** lista o histórico de rastreamento desse delivery. Esta guia exibe os dados de rastreamento das mensagens enviadas, ou seja, todas as URLs sujeitas ao rastreamento por meio do Adobe Campaign. Os dados de rastreamento são atualizados de hora em hora.

>[!NOTE]
>
>Se o rastreamento não estiver ativado para um delivery, essa guia não será exibida.

A configuração de rastreamento é realizada no estágio apropriado do assistente do delivery. Consulte [Como configurar links rastreados](../../delivery/using/how-to-configure-tracked-links.md).

Os dados de **[!UICONTROL Tracking]** são interpretados nos relatórios de delivery. Consulte [esta seção](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

## Renderização da caixa de entrada {#delivery-rendering}

A guia **[!UICONTROL Inbox rendering]** permite que você pré-visualização a mensagem nos diferentes contextos em que ela pode ser recebida e verifique a compatibilidade em desktops e aplicativos principais.

Dessa forma, você pode se certificar de que sua mensagem será exibida aos recipient da maneira ideal em vários clientes da Web, emails e dispositivos.

Para obter mais informações sobre a renderização da caixa de entrada, consulte [esta página](../../delivery/using/inbox-rendering.md)

![](assets/s_tn_inbox_rendering_tokens.png)

## Auditoria de delivery {#delivery-audit-}

A guia **[!UICONTROL Audit]** contém o log de delivery e todas as mensagens relacionadas às provas.

O botão **[!UICONTROL Refresh]** permite atualizar os dados. Use o botão **[!UICONTROL Filters]** para definir um filtro nos dados.

Ícones especiais permitem identificar erros ou avisos. Consulte [Análise de delivery](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

A subguia **[!UICONTROL Proofs]** permite visualizar a lista de provas que foram enviadas.

![](assets/s_ncs_user_delivery_log_tab.png)

Você pode modificar as informações exibidas nessa janela (e das guias **[!UICONTROL Delivery]** e **[!UICONTROL Tracking]**) selecionando as colunas a serem exibidas. Para fazer isso, clique no ícone **[!UICONTROL Configure list]** localizado no canto inferior direito. Para obter mais informações sobre a configuração de exibição de listas, consulte [esta seção](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Sincronização do painel de delivery {#delivery-dashboard-synchronization}

No painel de delivery, convêm verificar as mensagens processadas e os logs de deliveries para garantir que seu delivery foi enviado com êxito.

Alguns indicadores ou status podem estar incorretos ou não atualizados, isso pode ser resolvido com as seguintes soluções:

* Se o status do delivery estiver incorreto, verifique se todas as aprovações necessárias foram feitas para esse delivery ou se os workflows **[!UICONTROL operationMgt]** e **[!UICONTROL deliveryMgt]** estão sendo executados sem erros. Isso também pode ser porque o delivery está usando uma afinidade não configurada na instância de envio.

* Se os indicadores de delivery ainda forem zero e se você estiver em uma configuração mid-sourcing, verifique o workflow técnico **[!UICONTROL Mid-sourcing (delivery counters)]**. Inicie-o se o status não for **[!UICONTROL Started]**. Você pode tentar recalcular os indicadores clicando com o botão direito do mouse no delivery relevante no gerenciador do Adobe Campaign e selecionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. Para obter mais informações sobre indicadores de rastreamento, consulte esta [seção](../../reporting/using/delivery-reports.md#tracking-indicators).

* Se o contador de delivery não corresponder ao seu delivery, tente recalcular os indicadores clicando com o botão direito do mouse no delivery relevante no explorador do Adobe Campaign e selecionando **[!UICONTROL Recompute delivery and tracking indicators]** > **[!UICONTROL Actions]** para sincronizar novamente. Para obter mais informações sobre indicadores de rastreamento, consulte esta [seção](../../reporting/using/delivery-reports.md#tracking-indicators).

* Se o seu contador de delivery não estiver atualizado para implantações de mid-sourcing, verifique se o workflow técnico **[!UICONTROL Mid-Sourcing (Delivery counters)]** está em execução. Para obter mais informações, consulte esta [página](../../installation/using/mid-sourcing-deployment.md).

Você também pode rastrear seus deliveries com relatórios diferentes através do painel de delivery. Para obter mais informações, consulte esta [seção](../../reporting/using/delivery-reports.md).

## Caso de uso: Adicionando endereços IP dos remetentes aos registros {#use-case}

Nesta seção, você aprenderá a adicionar aos logs do delivery informações relacionadas ao endereço IP que enviou cada email em um delivery.

>[!NOTE]
>
>Essa modificação é diferente se você estiver usando uma única instância ou instância mid-sourcing. Antes de fazer a modificação, verifique se você está conectado à instância de envio de email.

### Etapa 1: Estender o schema

Para adicionar **publicID** em seus logs do delivery, é necessário estender o schema primeiro. Você pode continuar como segue.

1. Crie uma extensão de schema, em **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   Para obter mais informações sobre extensões de schema, consulte [esta página](../../configuration/using/extending-a-schema.md).

1. Selecione **[!UICONTROL broadLogRcp]** para estender os logs do delivery do Recipient (nms) e definir uma Namespace personalizada. Neste caso, será &quot;cus&quot;:

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >Se sua instância estiver no Mid-sourcing, você precisará trabalhar com o schema wideLogMid.

1. Adicione o novo campo na sua extensão. Nessa amostra, é necessário substituir:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
   ```

   por:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
   <attribute desc="Outbound IP identifier" label="IP identifier"
   name="publicId" type="long"/>
   </element>
   ```

   ![](assets/edit-schema.png)

### Etapa 2: Atualizar estrutura do banco de dados

Quando as modificações forem feitas, será necessário atualizar a estrutura do banco de dados para que ela fique alinhada à descrição lógica.

Para fazer isso, siga as etapas abaixo:

1. Clique no menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]**.

   ![](assets/update-database-structure.png)

1. Na janela **[!UICONTROL Edit tables]**, a tabela **[!UICONTROL NmsBroadLogRcp]** está marcada (ou a tabela **[!UICONTROL broadLogMid]** se estiver em um ambiente Mid-sourcing), como abaixo:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Sempre verifique se não há outra modificação, exceto a tabela **[!UICONTROL NmsBroadLoGRcp]** (ou a tabela **[!UICONTROL broadLogMid]** se estiver em um ambiente Mid-sourcing). Em caso afirmativo, desmarque outras tabelas.

1. Clique em **[!UICONTROL Next]** para validar. A seguinte tela é exibida:

   ![](assets/update-script.png)

1. Clique em **[!UICONTROL Next]** e em **[!UICONTROL Start]** para atualizar o start da estrutura do banco de dados. A construção de índice está a começar. Essa etapa pode ser longa, dependendo do número de linhas na tabela **[!UICONTROL NmsBroadLogRcp]**.

   ![](assets/start-database-update.png)

>[!NOTE]
>
>Depois que a atualização da estrutura física do banco de dados for concluída com êxito, você precisará desconectar e reconectar para que suas modificações sejam consideradas.

### Etapa 3: Validar a modificação

Para confirmar se tudo funcionou corretamente, é necessário atualizar a tela logs do delivery.

Para fazer isso, acesse os logs do delivery e adicione a coluna &quot;Identificador IP&quot;.

![](assets/list-config.png)

>[!NOTE]
>
>Para saber como configurar o lista na interface do Campaign Classic, consulte [esta página](../../platform/using/adobe-campaign-workspace.md).

Abaixo está o que você deve ver na guia **[!UICONTROL Delivery]** após as modificações:

![](assets/logs-with-ip.png)
