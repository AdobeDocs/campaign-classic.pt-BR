---
product: campaign
title: Configurações adicionais
description: Saiba como definir configurações adicionais para mensagens transacionais no Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
TQID: 'https://experienceleague.adobe.com/TJ5R6T1pu5JQU5SaGoWRgZLG2m29TWWPVB8nniorRUg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: cce1f22c34cbd13d063850a7ca636a3b0dfc62f6
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 91%
---
# Configurações adicionais {#mc-additional-configurations}

Esta página aborda configurações adicionais para mensagens transacionais no Campaign Classic v7.

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8. Para saber mais sobre a limpeza de eventos de mensagens transacionais e workflows técnicos, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}

## Monitorar limites {#monitoring-thresholds}

Você pode configurar os limites de aviso (laranja) e os limites de alerta (vermelho) dos indicadores que aparecem nos relatórios de **nível de serviço** e de **tempo de processamento** do Centro de mensagens (consulte [Acessar relatórios de mensagens transacionais](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} na documentação do Campaign v8).

Para fazer isso, siga as etapas abaixo:

1. Abra o assistente de implantação na **instância de execução**.

1. Acesse a página **[!UICONTROL Message Center]**.

1. Use as setas para modificar os limites.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>O número de eventos pendentes na fila é exibido na seção [Indicadores do sistema](../../production/using/monitoring-processes.md#system-indicators) da página de monitoramento do processo do Adobe Campaign. Para obter mais informações sobre o assistente de implantação, consulte [esta seção](../../installation/using/deploying-an-instance.md#deployment-assistant).

## Fluxos de trabalho técnicos {#technical-workflows}

Você deve garantir que os fluxos de trabalho técnicos na instância de controle e as diferentes instâncias de execução tenham sido criados e iniciados realmente antes de implantar qualquer modelo de mensagem transacional.

### Cronograma do fluxo de trabalho de arquivamento

Evite modificar o cronograma do **fluxo de trabalho de arquivamento** que é executado na instância de controle. Caso contrário, alguns dados de rastreamento que estão sendo extraídos da instância de execução podem ser perdidos.

Se você modificar o cronograma do fluxo de trabalho de arquivamento, também precisará alterar o cronograma do **fluxo de trabalho de rastreamento** na instância de execução para corresponder ao cronograma do fluxo de trabalho de arquivamento na instância de controle.

## Configurar multimarcas {#configuring-multibranding}

Esta seção descreve uma solução para configurar URLs de página de rastreamento e mirror page por marca, para mensagens transacionais no Adobe Campaign.

### Nota de compatibilidade {#compatibility-note}

Essa configuração de identidade visual legada não é compatível com o novo modelo de [identidade visual centralizada](https://experienceleague.adobe.com/docs/campaign-web/v8/conf/branding/branding-gs.html?lang=pt-BR){target="_blank"} introduzido no Campaign v8.

Se o ambiente existente usar essa configuração legada, ele não poderá ser migrado diretamente para o novo modelo de identidade visual centralizada. É necessária uma reimplementação completa das configurações de identidade visual para a adoção do novo sistema.

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
   >Saiba como estender um esquema na seção [Extensão de um esquema](../../configuration/using/extending-a-schema.md).

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

1. Crie um modelo de entrega por marca. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=pt-BR){target="_blank"}.

1. Em **[!UICONTROL Properties]** do modelo de entrega, defina o roteamento para a conta externa da marca.
