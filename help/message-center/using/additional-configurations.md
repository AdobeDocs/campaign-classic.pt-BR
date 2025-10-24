---
product: campaign
title: Configurações adicionais
description: Saiba como definir configurações adicionais para mensagens transacionais no Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: bba3f23637dd67a1557203c5ed1b93a6cb044870
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 90%

---

# Configurações adicionais {#mc-additional-configurations}



## Monitorar limites {#monitoring-thresholds}

Você pode configurar os limites de aviso (laranja) e os limites de alerta (vermelho) dos indicadores que aparecem nos relatórios de **nível de serviço do Centro de mensagens** e **tempo de processamento do Centro de mensagens** (consulte [Acesso a mensagens transacionais](../../message-center/using/about-transactional-messaging-reports.md)).

Para fazer isso, siga as etapas abaixo:

1. Abra o assistente de implantação na **instância de execução**.

1. Acesse a página **[!UICONTROL Message Center]**.

1. Use as setas para modificar os limites.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>O número de eventos pendentes na fila é exibido na seção [Indicadores do sistema](../../production/using/monitoring-processes.md#system-indicators) da página de monitoramento do processo do Adobe Campaign. Para obter mais informações sobre o assistente de implantação, consulte [esta seção](../../installation/using/deploying-an-instance.md#deployment-assistant).

## Limpar eventos {#purging-events}

Você pode usar o [assistente de implantação](../../production/using/database-cleanup-workflow.md#deployment-assistant) para definir por quanto tempo os dados devem ser armazenados no banco de dados

A limpeza de eventos é executada automaticamente pelo [Fluxo de trabalho de limpeza de banco de dados](../../production/using/database-cleanup-workflow.md). Esse fluxo de trabalho limpa os eventos recebidos e armazenados nas instâncias de execução e eventos arquivados em uma instância de controle.

Use as setas conforme o caso para alterar as configurações de limpeza:

Configurações de limpeza de eventos em uma instância de controle:

![](assets/messagecenter_delete_events_001.png)

Configurações de limpeza de eventos em uma instância de execução:

![](assets/messagecenter_delete_events_002.png)

Para obter mais informações sobre o fluxo de trabalho de limpeza de banco de dados, consulte [esta seção](../../production/using/database-cleanup-workflow.md).


## Fluxos de trabalho técnicos {#technical-workflows}

Você deve garantir que os fluxos de trabalho técnicos na instância de controle e as diferentes instâncias de execução tenham sido criados e iniciados realmente antes de implantar qualquer modelo de mensagem transacional.

Os vários fluxos de trabalho técnicos relacionados a mensagens transacionais (Centro de Mensagens) são divididos entre a instância de controle e a(s) instância(s) de execução.

### Fluxos de trabalho da instância de controle {#control-instance-workflows}

Na instância de controle, caso tenha uma ou várias instâncias de execução registradas, é necessário criar um fluxo de trabalho de arquivamento para cada conta externa **[!UICONTROL Message Center execution instance]**. Clique no botão **[!UICONTROL Create the archiving workflow]** para criar e iniciar o fluxo de trabalho.

![](assets/messagecenter_archiving_002.png)

Os fluxos de trabalho de arquivamento podem ser acessados na pasta **Administration > Production > Message Center**. Depois de criados, os fluxos de trabalho de arquivamento são iniciados automaticamente.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### Fluxo de trabalho da instância de execução {#execution-instance-workflows}

Na(s) instância(s) de execução, os fluxos de trabalho técnicos de mensagens transacionais podem ser acessados na pasta **Administration > Production > Message Center.** Você só precisa iniciá-los. Os fluxos de trabalho na lista são:

* **[!UICONTROL Processing batch events]** (internal name: **[!UICONTROL batchEventsProcessing]** ): esse fluxo de trabalho permite dividir eventos em lote em uma fila antes que eles sejam vinculados a um modelo de mensagem.
* **[!UICONTROL Processing real time events]** (internal name: **[!UICONTROL rtEventsProcessing]** ): esse fluxo de trabalho permite dividir eventos em tempo real em uma fila antes que eles sejam vinculados a um modelo de mensagem.
* **[!UICONTROL Update event status]** (internal name: **[!UICONTROL updateEventStatus]** ): esse fluxo de trabalho permite que você atribua um status ao evento.

  Os seguintes status de evento estão disponíveis:

   * **[!UICONTROL Pending]**: o evento está na fila. Nenhum modelo de mensagem foi atribuído a ele.
   * **[!UICONTROL Pending delivery]**: o evento está na fila, um modelo de mensagem foi atribuído a ele e está sendo processado pela entrega.
   * **[!UICONTROL Sent]**: esse status é copiado dos logs da entrega. Significa que a entrega foi enviada.
   * **[!UICONTROL Ignored by the delivery]**: esse status é copiado dos logs da entrega. Ele significa que a entrega foi ignorada.
   * **[!UICONTROL Delivery failed]**: esse status é copiado dos logs da entrega. Ele significa que a entrega falhou.
   * **[!UICONTROL Event not taken into account]**: o evento não pôde ser vinculado a um modelo de mensagem. O evento não será processado.

### Cronograma do fluxo de trabalho de arquivamento

Evite modificar o cronograma do **fluxo de trabalho de arquivamento** que é executado na instância de controle. Caso contrário, alguns dados de rastreamento que estão sendo extraídos da instância de execução podem ser perdidos.

Se você modificar o cronograma do fluxo de trabalho de arquivamento, também precisará alterar o cronograma do **fluxo de trabalho de rastreamento** na instância de execução para corresponder ao cronograma do fluxo de trabalho de arquivamento na instância de controle.

## Configurar multimarcas {#configuring-multibranding}

Esta seção descreve uma solução para configurar URLs de página de rastreamento e mirror page por marca, para mensagens transacionais no Adobe Campaign.

### Nota de compatibilidade {#compatibility-note}

Essa configuração de marca herdada não é compatível com o novo modelo [marca centralizada](https://experienceleague.adobe.com/docs/campaign-web/v8/conf/branding/branding-gs.html){target="_blank"} introduzido no Campaign v8.

Se o ambiente existente usar essa configuração herdada, ele não poderá ser migrado diretamente para o novo modelo de marca centralizada. É necessária uma reimplementação completa das configurações da marca para a adoção do novo sistema.

### Pré-requisitos {#prerequisites}

* Todos os hosts devem ser adicionados ao arquivo de configuração da instância (`config-<instance>.xml`).
* Cada marca deve ser atribuída a um subdomínio.
* Você deve ter um certificado HTTPS para todas as marcas se o rastreamento Web for feito em páginas HTTPS.

Para configurar multimarcas, você precisa configurar ambas as instâncias de execução e a instância de controle.

### Instância de execução {#execution-instance}

Na(s) instância(s) de execução, siga as etapas abaixo:

1. Crie uma conta externa por marca.

   >[!NOTE]
   >
   >Saiba como criar uma conta externa do tipo instância de execução [nesta seção](../../message-center/using/configuring-instances.md#control-instance).

1. Estenda o esquema nms:extAccount para adicionar a URL de rastreamento:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Saiba como estender um esquema existente na seção [Extensão de um esquema](../../configuration/using/extending-a-schema.md).

1. Modifique o formulário nms:extAccount:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Modifique as opções NmsTracking_OpenFormula e NmsTracking_ClickFormula para usar a conta externa em vez de uma opção global.

   Para fazer isso, substitua:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   com:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Essas alterações podem gerar conflitos ao atualizar. Talvez seja necessário mesclar essas fórmulas manualmente com a nova versão.

### Instância de controle {#control-instance}

Na instância de controle, é preciso vincular modelos de entrega e contas externas.

Para fazer isso, siga as etapas abaixo:

1. Crie uma conta externa por marca com o mesmo nome interno, conforme definido na [instância de execução](#execution-instance) (etapa 1).

1. Criar um modelo de entrega por marca. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=pt-BR){target="_blank"}.

1. Em **[!UICONTROL Properties]** do modelo de entrega, defina o roteamento para a conta externa da marca.
