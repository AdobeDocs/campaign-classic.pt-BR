---
product: campaign
title: Atividade de fluxo de trabalho de SMS de entrada para infraestrutura mid-sourcing
description: Atividade de fluxo de trabalho de SMS de entrada para infraestrutura mid-sourcing
feature: Technote, SMS
exl-id: 756039b2-5f57-4dc5-8166-a421206b886b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 5%

---

# Atividade de fluxo de trabalho de SMS de entrada para infraestrutura mid-sourcing {#inbound-sms}

## Limitações {#limitations}

* Esse caso de uso se aplica somente à instância de marketing em que você coleta dados de SMS nas instâncias de Mid-sourcing.
* Não implemente esse caso de uso na instância Mid-sourcing.
* Somente um fluxo de trabalho personalizado por conta externa de Mid-sourcing.

## Implementação {#implementation}

1. Adicione uma extensão à `nms:inSMS` na sua instância de marketing. A extensão adicionará um novo atributo à variável `nms:inSMS` esquema e rastreia a chave primária do registro inSMS proveniente da instância Mid-sourcing.

   ```xml
   <element img="nms:miniatures/mini-sms.png" label="Incoming SMS"
          labelSingular="Incoming SMS" name="inSMS">
   <dbindex name="midInSMSId" unique="false">
     <keyfield xpath="@extAccount-id"/>
     <keyfield xpath="@midInSMSId"/>
   </dbindex>
   
   <attribute label="External Mid SMS ID" name="midInSMSId" type="long"/>
   </element>
   ```

1. Para aplicar as modificações feitas nos esquemas, inicie o assistente de atualização de banco de dados. Este assistente pode ser acessado via **Ferramentas** > **Avançado** > **Atualizar estrutura do banco de dados**. Ele verifica se a estrutura física do banco de dados corresponde à sua descrição lógica e executa os scripts de atualização SQL. [Saiba mais](../../configuration/using/updating-the-database-structure.md)

1. Interrompa e faça backup do fluxo de trabalho que contém a **Atividade de SMS de entrada**.

   Fazer backup do ponteiro de opção correspondente com o seguinte formato `SMS_MO_INDEX_{internal name of the workflow}_{name of the insms workflow activity}_{internal name of the external account to access the mid}`.

[Saiba mais sobre backup](../../production/using/backup.md)

1. (**OPCIONAL**) se já estiver usando uma atividade Scheduler, abra o workflow e reconfigure-o da seguinte maneira:

   1. Replicar as configurações atuais do **Agendar** guia do seu **SMS de entrada** atividade no seu externo **Scheduler** atividade.

   1. Desative a configuração atual no **Agendar** guia de **SMS de entrada** atividade.

      ![](assets/inbound_sms_1.png)

1. Atualize o **SMS de entrada** script personalizado.

   Substitua o bloco abaixo. Observe que esse script pode variar se você personalizou esse código anteriormente.

   ```Javascript
   var lastSynchKey = getOption('SMS_MO_INDEX_WKF1105_inSmsUS_smsmidus');
   
   var smsId = application.getNewIds(1);
   
   xtk.session.Write(<inSMS xtkschema="nms:inSMS" _operation="insert"
       id={smsId}
       origin={smsMessage.origin}
       message={smsMessage.message}
       providerId={smsMessage.messageId}/>);
   
   return 2;
   ```

   Com o novo script personalizado a seguir para atualizar dados no SMS com base em uma chave composta, combinando a chave primária do registro Mid-sourcing e a ID de conta externa do roteamento de SMS de marketing.

   Siga os pré-requisitos abaixo:

   * Insira o valor real para `<EXTERNAL_ACCOUNT_ID>`, por exemplo, `var iExtAccountId=72733155`.
   * Mantenha os seguintes elementos no script personalizado:
      * `_operation="insertOrUpdate"`
      * `_key="@midInSMSId,@extAccount-id"`
      * `midInSMSId={smsMessage.id}`
      * `inSms.@["extAccount-id"] = iExtAccountId;{}`

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL ACCOUNT ID>
   var iExtAccountId=<EXTERNAL_ACCOUNT_ID>;
   
   var inSms = <inSMS xtkschema="nms:inSMS" _operation="insertOrUpdate"
   
               _key="@midInSMSId,@extAccount-id"
               midInSMSId={smsMessage.id}
               message={smsMessage.message}
               origin={smsMessage.origin}
               providerId={smsMessage.providerId}
               alias={smsMessage.alias}
               messageDate = {smsMessage.messageDate}
               receivalDate = {smsMessage.receivalDate}
               deliveryDate = {smsMessage.deliveryDate}
               largeAccount = {smsMessage.largeAccount}
               countryCode = {smsMessage.countryCode}
               operatorCode = {smsMessage.operatorCode}
               linkedSmsId={smsMessage.linkedSmsId}
               separator = {smsMessage.separator}/>
   
   inSms.@["extAccount-id"] = iExtAccountId;
   
   xtk.session.Write(inSms);
   
   return 2;
   ```

1. Atualize o script de inicialização avançada do SMS de Entrada com o script a seguir.

   O script redefinirá o ponteiro da chave primária para 24 horas antes. O workflow tentará reprocessar todos os dados no SMS da instância Mid-sourcing nas 24 horas anteriores e adicionar quaisquer dados ausentes à instância de Marketing.

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL_ACCOUNT_ID>
   // please enter real pointer option name to replace '<POINTER_OPTION_NAME>'
   // OPTION NAME format: SMS_MO_INDEX_{internal name of the workflow}_inSms_{internal name of the external account to access the mid}
   
   var queryDef = xtk.queryDef.create(
       <queryDef operation="getIfExists" schema="nms:inSMS" lineCount="1">
       <select>
           <node expr="@midInSMSId" alias="@midInSMSId"/>
       </select>
       <where>
           <condition expr="@midInSMSId != 0"/>
           <condition expr={"@created > SubHours(GetDate(), 24)"}/>
           <condition expr={"[@extAccount-id]=<EXTERNAL_ACCOUNT_ID>"}/>
       </where>
       <orderBy>
           <node expr="@midInSMSId"/>
       </orderBy>
       </queryDef>);
   
   var res = parseInt(queryDef.ExecuteQuery().@midInSMSId.toString());
   
   if( !isNaN(res) )
   setOption('<POINTER_OPTION_NAME>', res);
   ```

   >[!WARNING]
   >
   > * Se várias contas de roteamento SMS estiverem vinculadas à mesma instância Mid-sourcing, somente um único workflow por instância Mid-sourcing será permitido.
   > * Você pode usar qualquer ID de conta externa. A função da chave externa é manter a integridade da reconciliação de dados em cenários que envolvem diferentes servidores Mid-sourcing, nos quais a ID SMS Mid-sourcing pode ser idêntica em outras instâncias Mid-sourcing.
   > * Se houver vários workflows inSMS por instância de Mid-sourcing, a duplicação de dados pode ocorrer, pois a ID SMS de Mid-sourcing permanece constante, enquanto as IDs de conta externa variam.

1. Salve e reinicie o workflow.
