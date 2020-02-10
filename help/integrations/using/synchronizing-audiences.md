---
title: Sincronia de público
seo-title: Sincronia de público
description: Sincronia de público
seo-description: null
page-status-flag: never-activated
uuid: eda67bf7-8a0a-4240-8b31-de364be5d572
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 749a084e-69ee-46b4-b09b-cb91bb1da3cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Sincronia de público{#synchronizing-audiences}

Você pode criar uma lista sofisticada usando os recursos avançados do Campaign v7 e compartilhar essa lista como um público diretamente e em tempo real com o Campaign Standard (incluindo dados adicionais) de forma contínua. O usuário do Campaign Standard pode então consumir o público no Adobe Campaign Standard.

Targets complexos envolvendo dados adicionais que não são replicados no Campaign Standard só podem ser alcançados usando o Campaign v7.

Você também pode simplesmente compartilhar listas de recipients ou dados provenientes de um conector como o Microsoft Dynamics com o Campaign Standard.

Esse caso de uso mostra como preparar o target de seu delivery no Campaign v7 e como reutilizar esse destino e seus dados adicionais em um delivery criado e enviado com o Adobe Campaign Standard.

>[!NOTE]
>
>Você também pode enriquecer dados usando agregações e coleções no Adobe Campaign Standard se todos os dados que você precisa já forem replicados.

## Pré-requisitos {#prerequisites}

Para isso, é necessário:

* Os recipients armazenados no banco de dados do Campaign v7 e sincronizados com o Campaign Standard. Consulte a seção Perfis [de](../../integrations/using/synchronizing-profiles.md) sincronização.
* Dados adicionais, como assinaturas ou transações armazenadas em tabelas relacionadas a nms:recipients no banco de dados do Campaign v7. Esses dados podem ser dos schemas de OOB ou em tabelas personalizadas do Campaign v7. Por padrão, eles não estão disponíveis no Campaign Standard, pois não são sincronizados.
* Direito para executar workflows no Campaign v7 e Campaign Standard.
* Direita para criar e executar um workflow no Campaign Standard.

## Criação de um workflow para construção do target com dados adicionais no Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Targets complexos envolvendo dados adicionais que não são replicados no Campaign Standard só podem ser alcançados usando o Campaign v7.

Quando o target e seus dados adicionais forem definidos, é possível salvá-lo como uma lista que pode ser compartilhada com o Campaign Standard.

>[!NOTE]
>
>Este é um exemplo. Dependendo dos requisitos, você pode simplesmente fazer um query de uma lista de recipients e compartilhá-la com ACS sem nenhum processamento adicional. Você também pode usar outras atividades de gestão de dados para preparar seu target final.

Para obter o público final e seus dados adicionais:

1. Crie um novo fluxo de trabalho em **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Add a **[!UICONTROL Query]** activity and select the recipients that you want to send final email to. Por exemplo, todos os recipients entre 18 e 30 anos que moram na França.

   ![](assets/acs_connect_query1.png)

1. Adicionar dados adicionais dentro do query. Para obter mais informações, consulte a seção [Adição de dados](../../workflow/using/query.md#adding-data).

   Este exemplo mostra como adicionar um agregado para contar quantos deliveries um recipient recebeu em um ano.

   No **[!UICONTROL Query]**, selecione **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Selecione **[!UICONTROL Data linked to the filtering dimension]** e clique em **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Escolha **[!UICONTROL Data linked to the filtering dimension]** , selecione o **[!UICONTROL Recipient delivery logs]** nó e clique em **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Selecione **[!UICONTROL Aggregates]** no **[!UICONTROL Data collected]** campo e clique em **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Adicione uma condição de filtragem para considerar apenas os logs criados nos últimos 365 dias e clique em **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Defina as colunas de output. Aqui, a única coluna necessária é a que conta o número de deliveries. Para fazer isso:

   * Select **[!UICONTROL Add]** on the right of the window.
   * Na **[!UICONTROL Select field]** janela, clique em **[!UICONTROL Advanced selection]**.
   * Selecione **[!UICONTROL Aggregate]**, em seguida **[!UICONTROL Count]**. Marque a **[!UICONTROL Distinct]** opção e clique em **[!UICONTROL Next]**.
   * Na lista de campos, selecione o campo usado para a função **Contagem** . Choose a field that will always be populated, for example the **[!UICONTROL Primary key]** field, and click **[!UICONTROL Finish]**.
   * Change the expression in the **[!UICONTROL Alias]** column. Esse alias permitirá recuperar facilmente a coluna adicionada no delivery final. Por exemplo, **NBdeliveries**.
   * Clique **[!UICONTROL Finish]** e salve a configuração da **[!UICONTROL Query]** atividade.
   ![](assets/acs_connect_query7.png)

1. Salve o workflow. A próxima seção demonstra como compartilhar o público com o ACS.

## Compartilhamento do target com o Campaign Standard {#share-the-target-with-campaign-standard}

Once the target population is defined, you can share it with ACS through a **[!UICONTROL List update]** activity.

1. In the workflow created previously, add a **[!UICONTROL List update]** activity and specify the list you want to update or create.

   Especifique a pasta na qual deseja salvar a lista no Campaign v7. As listas estão sujeitas ao mapeamento de pastas definido durante a implementação, que pode ter impacto em sua visibilidade uma vez compartilhado no Campaign Standard. Consulte a seção [Conversão](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) de direitos.

1. Make sure the **[!UICONTROL Share with ACS]** option is checked. Ela é marcada por padrão.

   ![](assets/acs_connect_listupdate1.png)

1. Salve e execute o workflow.

   O target e seus dados adicionais são salvos em uma lista no Campaign v7 e compartilhados imediatamente como uma lista de público no Campaign Standard. Somente os perfis replicados são compartilhados com ACS.

If an error occurs on the **[!UICONTROL List update]** activity, it means that the synchronization with Campaign Standard may have failed. To be able to see more details about what went wrong, go to **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. This folder contains synchronization workflows triggered by the **[!UICONTROL List update]** activity execution. Consulte a seção [Solução de problemas do conector](../../integrations/using/troubleshooting-the-acs-connector.md) ACS.

## Recuperação de dados no Campaign Standard e seu uso em um delivery {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Once the targeting workflow is executed in Campaign v7, you are able to find the list audience in read-only mode from the **[!UICONTROL Audiences]** menu of Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Ao criar um workflow de delivery no Campaign Standard, é possível usar esse público e os dados adicionais contidos em um delivery.

1. Create a new workflow from the **[!UICONTROL Marketing activities]** menu.
1. Add a **[!UICONTROL Read audience]** activity and select the audience you previously shared from Campaign v7.

   Essa atividade é usada para recuperar os dados do público selecionado. You can also apply an additional **[!UICONTROL Source Filtering]** if needed by using the according tab of this activity.

1. Add an **[!UICONTROL Email delivery]** activity and configure it as any other [email delivery activity](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html).
1. Abra o conteúdo do delivery.
1. Insira um campo de personalização From the popup, locate the **[!UICONTROL Additional data (targetData)]** node. Esse nó contém os dados adicionais do público calculados no workflow inicial para construção do target. Você pode usá-los como qualquer outro campo de personalização.

   Para este exemplo, os dados adicionais provenientes do workflow original para construção do target são o número de deliveries enviados a cada recipient nos últimos 365 dias. O alias NBdeliveries especificado no workflow para construção do target está visível aqui.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Salve o delivery e o workflow.

   O workflow agora está pronto para ser executado. O delivery será analisado e pronto para ser enviado.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Envio e monitoramento do delivery {#send-and-monitor-your-delivery}

Quando o delivery e seu conteúdo estiverem prontos, envie o delivery, conforme descrito com mais detalhes [nesta seção](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html):

1. Execute o workflow de delivery. Essa etapa prepara o email para envio.
1. No painel de delivery, confirme manualmente se o delivery pode ser enviado.
1. Monitore relatórios e logs de delivery:

   * **No Campaign Standard**: Acesse [relatórios](https://docs.adobe.com/content/help/en/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) e [registros](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) relacionados à entrega como qualquer entrega.
   * **no Campaign v7 e no Campaign Standard**: IDs de entrega, registros amplos de email e registros de rastreamento de email são sincronizados com o Campaign v7. Você pode obter a visão de 360° das campanhas de marketing do Campaign v7.

      As quarentenas são sincronizados automaticamente de volta ao Campaign v7. Isso possibilita que as informações não entregues sejam consideradas para o próximo target realizado no Campaign v7.

      Você pode encontrar mais informações sobre gestão de quarentena no Campaign Standard [nesta seção](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

