---
product: campaign
title: Avançado - Personalizar logs do delivery
description: Saiba como estender esquemas de log de entrega para adicionar campos personalizados no Campaign Classic v7
feature: Monitoring
role: User, Developer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
TQID: https://experienceleague.adobe.com/OXsHpEx96bDHmINu-WR7MDcwn68ZxHjQ1MsxWhbtyG0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 552
ht-degree: 69%

---

# Avançado: logs de entrega personalizados {#customize-delivery-logs}

>[!NOTE]
>
>Orientações abrangentes sobre como acessar a lista de entrega e usar o painel de entrega estão documentadas na [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-dashboard). Esse conteúdo se aplica aos usuários do Campaign Classic v7 e do Campaign v8.
>
>Esta página documenta as **personalizações avançadas específicas do Campaign Classic v7** para implantações híbridas e locais.

Para monitorar entregas na interface do Campaign, consulte a [documentação do Campaign v8 sobre como monitorar entregas na interface do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}.

## Personalizar logs do delivery {#use-case}

Para **implantações híbridas/no local do Campaign Classic v7**, você pode personalizar logs do delivery estendendo esquemas. Esta seção mostra como adicionar endereços IP dos remetentes aos logs do delivery.

>[!NOTE]
>
>Essa personalização requer recursos de extensão de esquema disponíveis em implantações locais. Os usuários do Campaign v8 Managed Cloud Services devem entrar em contato com o Atendimento ao cliente da Adobe para obter campos de log de entrega personalizados.
>
>Essa modificação é diferente se você estiver usando uma única instância ou instância mid-sourcing. Antes de fazer a modificação, verifique se você está conectado à instância de envio de email.

### Etapa 1: Estender o esquema

Para adicionar **publicID** em seus logs da entrega, primeiro é necessário estender o esquema. Você pode continuar conforme os passos a seguir.

1. Crie uma extensão de esquema, em **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   Para obter mais informações sobre extensões de esquema, consulte [esta página](../../configuration/using/extending-a-schema.md).

1. Selecione **[!UICONTROL broadLogRcp]** para estender os logs da entrega do destinatário (nms) e definir um namespace personalizado. Neste caso, será &quot;cus&quot;:

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >Se sua instância estiver no Mid-sourcing, você precisará trabalhar com o esquema broadLogMid.

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

### Etapa 2: atualizar estrutura do banco de dados

Quando as modificações forem feitas, será necessário atualizar a estrutura do banco de dados para que ela esteja alinhada à descrição lógica.

Para fazer isso, siga as etapas abaixo:

1. Clique no menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]**.

   ![](assets/update-database-structure.png)

1. Na janela **[!UICONTROL Edit tables]**, a tabela **[!UICONTROL NmsBroadLogRcp]** está marcada (ou a tabela **[!UICONTROL broadLogMid]** se estiver em um ambiente Mid-sourcing), como abaixo:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Verifique sempre se não há outra modificação, exceto a tabela **[!UICONTROL NmsBroadLoGRcp]** (ou a tabela **[!UICONTROL broadLogMid]** se estiver em um ambiente Mid-sourcing). Em caso afirmativo, desmarque as outras tabelas.

1. Clique em **[!UICONTROL Next]** para validar. A seguinte tela é exibida:

   ![](assets/update-script.png)

1. Clique em **[!UICONTROL Next]** e em **[!UICONTROL Start]** para iniciar a atualização da estrutura do banco de dados. A construção de índice está iniciando. Essa etapa pode ser longa, dependendo do número de linhas na tabela **[!UICONTROL NmsBroadLogRcp]**.

   ![](assets/start-database-update.png)

>[!NOTE]
>
>Depois que a atualização da estrutura física do banco de dados for concluída com êxito, você precisará desconectar e reconectar para que suas modificações sejam consideradas.

### Etapa 3: validar a modificação

Para confirmar se tudo funcionou corretamente, é necessário atualizar a tela de logs da entrega.

Para fazer isso, acesse os logs da entrega e adicione a coluna &quot;Identificador IP&quot;.

![](assets/list-config.png)

>[!NOTE]
>
>Para saber como configurar listas na interface do Campaign Classic, consulte [esta página](../../platform/using/adobe-campaign-workspace.md).

Abaixo está o que você deve ver na guia **[!UICONTROL Delivery]** após as modificações:

![](assets/logs-with-ip.png)

## Tópicos relacionados

* [Monitorar entregas na interface do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentação do Campaign v8)
* [Status de entrega](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (documentação do Campaign v8)
* [Noções básicas sobre falhas de entrega](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentação do Campaign v8)
* [Gerenciamento de quarentena](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentação do Campaign v8)
* [Extensão de um esquema](../../configuration/using/extending-a-schema.md) (v7 híbrido/no local)

