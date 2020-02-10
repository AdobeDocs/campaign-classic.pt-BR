---
title: Teste A/B
seo-title: Teste A/B
description: Teste A/B
seo-description: null
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Teste A/B{#a-b-testing}

Se houver vários conteúdos para uma delivery de e-mail e quiser descobrir qual versão terá maior impacto na população direcionada, poderá enviar as diferentes versões para alguns dos recipients e, em seguida, selecionar aquela com a maior taxa de sucesso e enviá-la ao resto dos recipients.

Nesse caso de uso, vamos comparar dois conteúdos de delivery de e-mail por meio de um workflow para construção do target. A mensagem e o texto são idênticos nas duas remessas: apenas o layout é alterado.

A população direcionada é dividida em três grupos: dois grupos de teste e a população restante. Uma versão diferente da delivery é enviada para cada grupo de teste. Após a delivery, um período de espera de 5 dias é configurado antes de coletar os resultados das melhores taxas aberturas. O conteúdo da delivery com a pontuação mais alta é então recuperado por um script e enviado à população que não foi usada como um grupo de teste.

Observe que os critérios que decide qual delivery é o melhor pode ser alterado para atender às suas necessidades. Pode ser a taxa de abertura, a taxa de cliques, a taxa de subscrição, o reatividade, etc.

Além disso, o teste detalhado neste caso de uso aborda apenas duas deliveries, mas é possível testar quantas versões forem necessárias. Basta adicionar atividades ao workflow.

Para criar o teste A/B, aplique as seguintes etapas:

* [Etapa 1: Criação de um fluxo de trabalho de definição de metas](#step-1--creating-a-targeting-workflow)
* [Etapa 2: Configuração de amostras de população](#step-2--configuring-population-samples)
* [Etapa 3: Criação de dois modelos de entrega](#step-3--creating-two-delivery-templates)
* [Etapa 4: Configurar as entregas no fluxo de trabalho](#step-4--configuring-the-deliveries-in-the-workflow)
* [Etapa 5: Criação do script](#step-5--creating-the-script)
* [Etapa 7: Iniciar o fluxo de trabalho](#step-7--starting-the-workflow)
* [Etapa 8: Analisando o resultado](#step-8--analyzing-the-result).

## Step 1: Creating a targeting workflow {#step-1--creating-a-targeting-workflow}

You need to create your workflow in the **[!UICONTROL Targeting and Workflows]** tab of a campaign. É composto de uma **[!UICONTROL Query]** atividade, uma **[!UICONTROL Split]** atividade ligada a duas **[!UICONTROL Email delivery]** atividades, uma **[!UICONTROL Wait]** , uma **[!UICONTROL JavaScript code]** atividade e uma **[!UICONTROL Delivery]** atividade.

1. Se ainda não tiver feito isso, crie uma campanha (para saber mais sobre isso, consulte esta [seção](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Vá para a **[!UICONTROL Targeting and Workflows]** guia.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Change the label of the existing workflow or click **[!UICONTROL Add]** to create a new one (for more on this, refer to this [section](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Use o mouse para arrastar e soltar atividades no diagrama do fluxo de trabalho, incluindo uma **[!UICONTROL Query]** (guia), uma **[!UICONTROL Target]** (guia **[!UICONTROL Split]** ), duas **[!UICONTROL Target]** (guia **[!UICONTROL Email deliveries]** ), uma **[!UICONTROL Deliveries]** atividade (guia **[!UICONTROL Wait]** ), uma **[!UICONTROL Flow Control]** atividade (guia **[!UICONTROL JavaScript code]****[!UICONTROL Actions]** **[!UICONTROL Delivery]****[!UICONTROL Actions]** ) e uma atividade  (guia ).

![](assets/use_case_abtesting_targetwkfl_004.png)

## Etapa 2: Configuração de amostras de população {#step-2--configuring-population-samples}

### Configurando a atividade de Consulta {#configuring-the-query-activity}

* Clique duas vezes na **[!UICONTROL Query]** atividade.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Click the **[!UICONTROL Edit query]** link and select the recipients you want to target.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Vincule a **[!UICONTROL Query]** atividade à **[!UICONTROL Split]** atividade.

   ![](assets/use_case_abtesting_createrecipients_003.png)

### Configuração da atividade Split {#configuring-the-split-activity}

Esta atividade permite criar várias populações: a que recebe a delivery A, aquela que recebe a delivery B e a população restante. A utilização de seleção aleatória permite atingir apenas parte da população de cada delivery.

1. Criação da população A:

   * Clique duas vezes na **[!UICONTROL Split]** atividade.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * Na guia existente, altere o rótulo para a população A.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Selecione a **[!UICONTROL Limit the selected records]** opção.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Clique no **[!UICONTROL Edit]** link, selecione **[!UICONTROL Activate random sampling]** e clique em **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Set the threshold to 10%, then click **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Criação da população B:

   * Click **[!UICONTROL Add]** to create a new tab for population B.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limite a população para 10% como anteriormente.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Criação da população restante:

   * Vá para a **[!UICONTROL General]** guia.

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Select **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Change the label to specify that this population includes neither A nor B, and click **[!UICONTROL OK]** to close the activity.

      ![](assets/use_case_abtesting_createrecipients_013.png)

## Step 3: Creating two delivery templates {#step-3--creating-two-delivery-templates}

Agora devemos criar dois templates de delivery. Each template will be referenced in an **[!UICONTROL Email delivery]** activity linked to the **[!UICONTROL Split]** activity. Para obter mais informações, consulte esta [seção](../../delivery/using/about-templates.md).

1. Vá para a **[!UICONTROL Resources > Delivery template]** pasta.
1. Duplique o modelo de **[!UICONTROL Email]** entrega.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Crie o conteúdo a ser usado para a delivery A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Repita esse processo para criar um modelo para a delivery B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

## Step 4: Configuring the deliveries in the workflow {#step-4--configuring-the-deliveries-in-the-workflow}

A próxima etapa é configurar as deliveries. Estão destinados às três populações criadas na fase anterior: [Etapa 2: Configuração de amostras](#step-2--configuring-population-samples)de população. As duas primeiras deliverys permitem enviar conteúdo diferente para a população A e B. A terceiro delivery é destinada à população que não recebeu A nem B. O conteúdo será calculado por um script e será idêntico a A ou ao B, dependendo de qual deles obteve a maior taxa de abertura. We need to configure a wait period for the third delivery, to find out the outcome of deliveries A and B. This is why the third delivery includes a **[!UICONTROL Wait]** activity.

1. Go to the **[!UICONTROL Split]** activity and link the transition destined for population A to one of the email deliveries already in the workflow.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Clique duas vezes na delivery para abri-la.
1. Usando a lista suspensa, selecione o template para a delivery A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Click **[!UICONTROL Continue]** to view the delivery, then save it.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Link the transition of the **[!UICONTROL Split]** activity destined for population B to the second email delivery.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Abra delivery e selecione o template na delivery B e, em seguida, salve a delivery.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Link the transition destined for the remaining population to the **[!UICONTROL Wait]** activity.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Open the **[!UICONTROL Wait]** activity and configure a 5-day waiting period.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Vincule a **[!UICONTROL Wait]** atividade à **[!UICONTROL JavaScript code]** atividade.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

## Etapa 5: Criação do script {#step-5--creating-the-script}

A escolha do conteúdo de delivery destinado à população restante é calculada por um script. Este script recupera as informações relacionadas à delivery com a mais alta taxa de abertura e copia o conteúdo para a delivery final.

### Exemplo de um script {#example-of-a-script}

O script a seguir pode ser usado no workflow para construção do target. For more on this, refer to [Implementation](#implementation).

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

Para obter uma explicação detalhada do script, consulte [Detalhes do script](#details-of-the-script).

### Implementação {#implementation}

1. Abra sua **[!UICONTROL JavaScript code]** atividade.
1. Copie o script oferecido no [Exemplo de um script](#example-of-a-script) na **[!UICONTROL JavaScript code]** janela.

   ![](assets/use_case_abtesting_configscript_002.png)

1. In the **[!UICONTROL Label]** field, enter the name of the script, i.e.

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Feche a **[!UICONTROL JavaScript code]** atividade.
1. Salve seu workflow.

### Detalhes do script {#details-of-the-script}

Esta seção detalha as várias partes do script e seu modo operacional.

* A primeira parte do script é uma query. The **queryDef** command lets you recover from the **NmsDelivery** table the deliveries created by executing the targeting workflow and to sort them based on their estimated rate of opens, then the information from the delivery with the highest rate of opens is recovered.

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* A delivery com a taxa mais alta de abertura é duplicada.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* O rótulo da delivery duplicada é modificado e a palavra **final** é adicionada a ele.

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* A delivery é copiada no painel de campanha.

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* A delivery é salva no banco de dados.

   ```
   // save the delivery in database
   delivery.save()
   ```

* O identificador único da delivery duplicada é armazenado na variável do workflow.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

### Outros critérios de seleção {#other-selection-criteria}

O exemplo acima permite selecionar o conteúdo de uma delivery com base na taxa de abertura de e-mails. É possível adaptá-la se baseando em outros indicadores específicos de delivery:

* Melhor rendimento de cliques: `[indicators/@recipientClickRatio]`,
* Taxa de reatividade mais alta (e-mail aberto e cliques na mensagem): `[indicators/@reactivity]`,
* Taxa de reclamação mais baixa: `[indicators/@refusedRatio]` (use o valor falso para o atributo sortDesc),
* Maior taxa de conversão: `[indicators/@transactionRatio]`,
* Número de páginas visitadas após a recepção de uma mensagem: `[indicators/@totalWebPage]`,
* Taxa de cancelamento de subscrição mais baixa: `[indicators/@optOutRatio]`,
* Valor da transação: `[indicators/@amount]`.

## Step 6: Defining the final delivery {#step-6--defining-the-final-delivery}

Depois que o script for criado para selecionar o vencedor do teste A/B, é possível definir os parâmetros da delivery final.

1. Conecte a **[!UICONTROL JavaScript code]** atividade à **[!UICONTROL Delivery]** atividade restante.
1. Open the **[!UICONTROL Delivery]** activity.
1. Uncheck the **[!UICONTROL Generate an outbound transition]** option to finish the workflow with this activity.
1. Deixe as outras opções em seus valores padrão.

   ![](assets/ab_test_final_delivery.png)

By preparing the delivery specified in the transition (defined via the **[!UICONTROL Javascript Code]** activity), you will be then able to approve it and to start the sending, as described in the next step.

## Etapa 7: Iniciar o fluxo de trabalho {#step-7--starting-the-workflow}

1. Clique **[!UICONTROL Start]** no fluxo de trabalho.

   ![](assets/use_case_abtesting_startwkfl_001.png)

1. Aprove o target e o conteúdo para as remessas A e B via painel de campanha.
1. Confirme a delivery.
1. Aguarde até o final do período de 5 dias para descobrir qual conteúdo foi calculado após os resultados da abertura da delivery.

   ![](assets/use_case_abtesting_startwkfl_002.png)

   Nesse caso, o template B foi escolhido.

1. Após o conteúdo da terceira delivery ser determinado, aprove o target e o conteúdo.

## Etapa 8: Analisar o resultado {#step-8--analyzing-the-result}

Depois que as deliveries forem enviadas, é possível verificar quais recipients receberam e se eles abriram ou não a entrega.

* To find out which recipients have been targeted, open a delivery via the campaign dashboard and click the **[!UICONTROL Delivery]** tab.

   ![](assets/use_case_abtesting_analysis_001.png)

* To find out whether the delivery has been opened, go to the **[!UICONTROL Tracking]** tab.

   ![](assets/use_case_abtesting_analysis_002.png)

* Compare com o outro fornecimento.

   ![](assets/use_case_abtesting_analysis_003.png)

No nosso exemplo, a delivery B pontuou a maior taxa de abertura. Isso significa que o conteúdo B será usado para a delivery final.

![](assets/use_case_abtesting_analysis_004.png)

