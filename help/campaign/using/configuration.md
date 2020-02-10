---
title: Configuração
seo-title: Configuração
description: Configuração
seo-description: null
page-status-flag: never-activated
uuid: 59503b54-ad49-4b00-8ffb-52e6f6c62070
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: ed4afa5e-c184-4c8e-a086-41d87b863190
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Configuração{#configuration}

Esta seção destina-se às pessoas responsáveis pela configuração do gestor de resposta. Ele assume uma certa quantidade de conhecimento sobre a extensão de schemas, definição de workflows e programação SQL.

Isso permite o entendimento de como adaptar o modelo de dados padrão à natureza específica de uma tabela de transações para o Adobe Campaign com a tabela de individuais. Esta tabela pode coincidir com a tabela de individuais disponíveis no Adobe Campaign ou com uma tabela diferente.

The measurement hypothesis is launched by the operation process workflow ( **[!UICONTROL operationMgt]** ). Cada hipótese representa um processo separado que é executado de forma assíncrona com um status de execução (Editando, Pendente, Concluído, Falhou, etc.) e controlado por um programador que gerencia as limitações de prioridade, a restrição do número de processos simultâneos, a página de baixa atividade e a execução automática com frequência.

## Configurar schemas {#configuring-schemas}

>[!CAUTION]
>
>Os schemas padrão do aplicativo não devem ser modificados, mas é possível usar o mecanismo de extensão. Caso contrário, os schemas modificados não serão considerados no momento das atualizações futuras do aplicativo. Isso pode resultar no mau funcionamento durante o uso do Adobe Campaign.

É necessária a integração de aplicativos antes de usar o módulo de reação para definir as várias tabelas (transações, detalhes de transações) que devem ser mensuradas e suas relações com os envios, as ofertas e os individuais.

### Schemas padrão {#standard-schemas}

The out-of-the-box **[!UICONTROL nms:remaMatch]** schema contains the reaction log table, i.e. the relation between individuals, hypothesis and transaction table. Esse schema deve ser usado como um schema de herança para a tabela de destino final dos logs de reação.

The **[!UICONTROL nms:remaMatchRcp]** schema also comes as a standard, it contains the storage of reaction logs for Adobe Campaign recipients ( **[!UICONTROL nms:recipient]** ). Para ser usado, é necessário estender para realizar o mapeamento para uma tabela de transação (onde contém compras, etc.).

### Tabelas e detalhes de transações {#transaction-tables-and-transaction-details}

A tabela de transações deve incluir os links diretos para os individuais.

Também é possível adicionar uma tabela contendo os detalhes da transação. Isso não está diretamente vinculado aos individuais.

Por exemplo, uma tabela de transação está vinculada a um contato (tabela de recebimento) e uma tabela de linhas está vinculada apenas à tabela de recebimento (tabela de detalhes). Então é possível configurar a hipótese diretamente no nível em que a tabela de linha de recebimento está vinculada à tabela de recebimento.

>[!NOTE]
>
>Se desejar manter o identificador do recebimento que descreve o comportamento esperado na hipótese, é possível estender o template da tabela nms:remaMatchRcp para adicionar o identificador a ele (nesse caso, nenhum cálculo de ROI é vinculado a esses campos).

É altamente recomendável adicionar uma data de evento.

O schema a seguir mostra associações entre diferentes tabelas após a conclusão da configuração:

![](assets/response_data_model.png)

### Gestor de resposta com os recipients do Adobe Campaign {#response-management-with-adobe-campaign-recipients}

In this example, we will integrate a table of purchases in our response management module using the Adobe Campaign recipient table ( **[!UICONTROL nms:recipient]** ).

The table of response logs on a **[!UICONTROL nms:remaMatchRcp]** recipient is extended to add a link to the purchase table schema. In the following example, the purchase table is called **demo:purchase**.

1. Pelo Adobe Campaign Explorer, selecione **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**.
1. Clique com o botão direito do mouse em **Destinatário** e selecione **[!UICONTROL Actions]** e **[!UICONTROL Modify the options of the targeting dimensions]**.

   ![](assets/delivery_mapping1.png)

1. Você pode personalizar o **[!UICONTROL Extension namespace]** na próxima janela e clicar em **[!UICONTROL Next]**.

   ![](assets/delivery_mapping2.png)

1. Na **[!UICONTROL Response management]** categoria, verifique se a **[!UICONTROL Generate a storage schema for reactions]** caixa está marcada.

   Then click **[!UICONTROL Define additional fields...]** to select the related transaction tables and add the desired fields to the extension of the nms:remaMatchRcp schema.

   ![](assets/delivery_mapping3.png)

O schema criado tem a seguinte aparência:

```
<srcSchema _cs="Reactions (Recipients) (cus)" entitySchema="xtk:srcSchema" extendedSchema="nms:remaMatchRcp" 
img="nms:remaMatch.png" implements="xtk:persist" label="Reactions (Recipients)" mappingType="sql"
name="remaMatchRcp" namespace="cus">  
 <element label="Reactions (Recipients)" name="remaMatchRcp">    
  <key internal="true" name="match">      
   <keyfield xlink="hypothesis"/>      
   <keyfield xlink="broadLog"/>      
   <keyfield xlink="proposition"/>    
  </key>    
  <attribute label="Quantity" name="quantity" type="long"/>    
  <element name="purchase" target="demo:purchase" type="link"/>    
  <element name="hypothesis" revLabel="Reactions (Recipients)" revLink="remaMatchRcp"/>    
  <element applicableIf="HasPackage('nms:coreInteraction')" label="Proposition" name="proposition" target="nms:propositionRcp" type="link"/>   
  <element desc="Message (Delivery log)" label="Message" name="broadLog" target="nms:broadLogRcp" type="link"/>    
  <element label="Respondent" name="responder" target="nms:recipient" type="link"/>  
 </element>  
 <createdBy _cs="Administrator (admin)"/>  
 <modifiedBy _cs="Administrator (admin)"/>
</srcSchema>
```

### Gestor de respostas com uma tabela de recipient personalizada {#response-management-with-a-personalized-recipient-table}

Neste exemplo, uma tabela de compra é integrada ao módulo de gestor de resposta com uma tabela de individuais que não é a tabela de recipient disponível no Adobe Campaign.

* Creating a new response log schema derived from the **[!UICONTROL nms:remaMatch]** schema.

   Since the table of individuals is different from the table of Adobe Campaign recipients, it is necessary to create a new schema of the response logs based on the **[!UICONTROL nms:remaMatch]** schema. Em seguida, insira os links para os logs do delivery e a tabela de compras.

   In the following example, we will use the **demo:broadLogPers** schema and the **demo:purchase** transaction table:

   ```
   <srcSchema desc="Linking of a recipient transaction to a hypothesis"    
   img="nms:remaMatch.png" label="Responses on persons" labelSingular="Responses on a person" name="remaMatchPers" namespace="nms">
     <element name="remaMatchPers" template="nms:remaMatch">
       <key internal="true" name="match">
         <keyfield xlink="hypothesis"/>
        <keyfield xlink="purchase"/>
       </key>
   
       <element name="hypothesis" revLabel="Response logs for persons" revLink="remaMatchPers"/>
       <element applicableIf="HasPackage('nms:interaction')" label="Proposition" name="proposition"
                target="demo:propositionPers" type="link"/>
       <element label="Delivery log" name="broadLog" target="demo:broadLogPers" type="link"/>
     </element>
   </srcSchema>
   ```

* Modifying the hypothesis form in the **[!UICONTROL nms:remaHypothesis]** schema.

   Por padrão, a lista de logs de resposta é visível nos logs de recipient. Portanto, é possível modificar o formulário de hipótese para exibir os novos logs de resposta criados durante a etapa anterior.

   Por exemplo:

   ```
    <container type="visibleGroup" visibleIf="[context/@remaMatchStorage]= 'demo:remaMatchPers'">
                 <input hideEditButtons="true" img="nms:remaMatch.png" nolabel="true" refresh="true"
                  toolbarCaption="Responses generated by the hypothesis" type="linklist"
                  xpath="remaMatchPers">
             <input xpath="[.]"/>
             <input xpath="@controlGroup"/>
           </input>
      </container> 
   ```

## Gerenciar indicadores {#managing-indicators}

O módulo Gestor de Resposta contém uma lista de indicadores predefinidos. No entanto, é possível adicionar outros indicadores de mensuração personalizados.

Para isso, é possível estender a tabela de hipótese ao inserir dois campos para cada indicador novo:

* o primeiro para a população do target,
* o segundo para o grupo de controle.

Por exemplo:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:remaHypothesis" label="Measurement hypothesis" 
md5="1D4DED54FF8EC2432AED6736EDE6F547" name="remaHypothesis" namespace="demo" xtkschema="xtk:srcSchema">  
    <element name="remaHypothesis">    
        <element name="indicators">      
            <!-- Quantity -->      
            <attribute label="Total contacted" name="contactReactedTotalQuantity" type="long"/>
            <attribute label="Total number of people in the control group" name="proofReactedTotalquantity" type="long"/> 
        </element> 
    </element>
</srcSchema>
```

