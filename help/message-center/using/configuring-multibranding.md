---
title: Configuração de multimarcas
seo-title: Configuração de multimarcas
description: Configuração de multimarcas
seo-description: null
page-status-flag: never-activated
uuid: 61b4235c-da03-4da8-b14b-7ffb12c8d4c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 907d82c8-9262-4952-b8df-21144dd55824
translation-type: ht
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: ht
source-wordcount: '236'
ht-degree: 100%

---


# Configuração de multimarcas{#configuring-multibranding}

Esta seção descreve uma solução para configurar URLs de página de rastreamento e mirror page por marca, para mensagens transacionais no Adobe Campaign.

## Pré-requisitos {#prerequisites}

* Todos os hosts devem ser adicionados ao arquivo de configuração da instância (`config-<instance>.xml`).
* Cada marca deve ser atribuída a um subdomínio.
* Você deve ter um certificado HTTPS para todas as marcas se o rastreamento Web for feito em páginas HTTPS.

## Processo típico {#typical-process}

Para configurar multimarcas, você precisa configurar ambas as instâncias de execução e a instância de controle. Nas instâncias de execução, siga as etapas abaixo:

1. Crie uma conta externa por marca.

   >[!NOTE]
   >
   >A criação de uma conta externa do tipo instância de execução é apresentada na seção [Control instance](../../message-center/using/creating-a-shared-connection.md#control-instance).

1. Estenda o schema nms:extAccount para adicionar a URL de rastreamento:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >A extensão de um schema existente é apresentada na seção [Extensão de um schema](../../configuration/using/extending-a-schema.md).

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

Na instância de controle, é preciso vincular templates do delivery e contas externas. Para fazer isso, você precisa:

1. Criar uma conta externa por marca com o mesmo nome interno definido na etapa 1.
1. Criar um template do delivery padrão por marca.
1. Em **[!UICONTROL Properties]** do template do delivery, defina o roteamento para a conta externa da marca.

