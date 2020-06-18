---
title: 'Configurações gerais '
seo-title: 'Configurações gerais '
description: 'Configurações gerais '
seo-description: null
page-status-flag: never-activated
uuid: 317a145d-36b0-40fe-a272-ad5e35b0b190
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: f4b1c108-7f71-4aa1-8394-a7f660834c9c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7de74feb61cc8f4b386a6ff86fc58b9c9e9ca1d
workflow-type: tm+mt
source-wordcount: '2822'
ht-degree: 0%

---


# Configurações gerais {#general-configurations}

Esta seção detalha a configuração a ser realizada no Adobe Campaign v7 se você estiver migrando de uma v5.11 ou de uma v6.02.

Além disso:

* Se você migrar da v5.11, também deverá concluir a configuração detalhada nas configurações [Específicas na seção v5.11](../../migration/using/specific-configurations-in-v5-11.md) .
* Se você migrar da v6.02, também deverá concluir a configuração detalhada em Configurações [específicas na seção v6.02](../../migration/using/specific-configurations-in-v6-02.md) .

## Fusos horários {#time-zones}

### Modo de fuso horário múltiplo {#multi-time-zone-mode}

Na v6.02, o modo &quot;fuso horário múltiplo&quot; estava disponível somente para mecanismos de banco de dados PostgreSQL. Agora, ele é oferecido independentemente do tipo de mecanismo de banco de dados usado. Recomendamos que você transforme sua base em uma base de &quot;vários fusos horários&quot;.

Para usar o modo TIMESTAMP WITH TIMEZONE, também é necessário adicionar a opção **-userTimestamptz:1** à linha de comando pós-atualização.

>[!IMPORTANT]
>
>Se o parâmetro **-usetimestamptz:1** for usado com um mecanismo de banco de dados incompatível, seu banco de dados será corrompido e será necessário restaurar um backup do banco de dados e reexecutar o comando acima.

>[!NOTE]
>
>É possível alterar o fuso horário após a migração por meio do console (**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** nó).
>
>For more on time zone management, refer to [this section](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

Se você receber um erro **ORA 01805** durante o pós-upgrade, isso significa que os arquivos de fuso horário Oracle entre o servidor de aplicativos e o servidor de banco de dados estão dessincronizados. Para sincronizá-los novamente, aplique as seguintes etapas:

1. Para identificar o arquivo de fuso horário usado, execute o seguinte comando:

   ```
   select * from v$timezone_file
   ```

   Os arquivos de fuso horário geralmente são encontrados na pasta **ORACLE_HOME/oracore/zoneinfo/** .

1. Verifique se os arquivos de fuso horário são idênticos em ambos os servidores.

Para obter mais informações, visite: [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

Um desalinhamento de fuso horário entre o cliente e o servidor também pode causar alguns atrasos. É por isso que recomendamos usar a mesma versão da biblioteca Oracle nos lados cliente e servidor, os dois fusos horários devem ser os mesmos.

Para verificar se os dois lados estão no mesmo fuso horário:

1. Verifique a versão do arquivo de fuso horário no lado do cliente executando o seguinte comando:

   ```
   genezi -v
   ```

   genezi é um binário encontrado no repositório **$ORACLE_HOME/bin** .

1. Verifique a versão do arquivo de fuso horário no lado do servidor executando o seguinte comando:

   ```
   select * from v$timezone_file
   ```

1. Para alterar o arquivo de fuso horário no lado do cliente, use a variável de ambiente **ORA_TZFILE** .

## Segurança {#security}

### Zonas de segurança {#security-zones}

>[!IMPORTANT]
>
>Por motivos de segurança, a plataforma Adobe Campaign não está mais acessível por padrão: você deve configurar as zonas de segurança e, portanto, coletar endereços IP do operador.

Adobe Campaign v7 envolve o conceito de zonas **de** segurança. Cada usuário deve estar associado a uma zona para fazer logon em uma instância e o endereço IP do usuário deve ser incluído nos endereços ou intervalos de endereços definidos na zona de segurança. A configuração das zonas de segurança pode ser feita no arquivo de configuração do servidor Adobe Campaign. A zona de segurança à qual um usuário está associado deve ser definida no console (**[!UICONTROL Administration > Access management > Operators]**).

**Antes da migração**, peça ao administrador da rede para ajudá-lo a definir as zonas de segurança a serem ativadas após a migração.

**Após a pós-atualização** (antes da reinicialização do servidor), você deve configurar as zonas de segurança.

A configuração da zona de segurança foi encontrada [nesta seção](../../installation/using/configuring-campaign-server.md#defining-security-zones).

### Senhas de usuário {#user-passwords}

Na v7, a conexão do operador **interno** e do **administrador** deve ser protegida por uma senha. Recomendamos atribuir senhas a essas contas e a todas as contas de operadores, **antes da migração**. Se você não tiver especificado uma senha para **interno**, não poderá se conectar. Para atribuir uma senha a **interno**, digite o seguinte comando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>A senha **interna** deve ser idêntica para todos os servidores de rastreamento. Para obter mais informações, consulte [esta seção](../../installation/using/campaign-server-configuration.md#internal-identifier) e [esta seção](../../platform/using/access-management.md#about-permissions).

### Novos recursos na v7 {#new-features-in-v7}

* Usuários sem permissões não podem mais se conectar ao Adobe Campaign. Suas permissões devem ser adicionadas manualmente, por exemplo, criando uma permissão chamada **connect**.

   Os usuários afetados por essa modificação são identificados e listados durante a pós-atualização.

* O rastreamento não funciona mais se a senha estiver vazia. Se esse for o caso, uma mensagem de erro informará você e solicitará que você a reconfigure.
* As senhas de usuário não são mais armazenadas no schema **xtk:sessionInfo** .
* As permissões de administração agora são necessárias para usar as funções **xtk:builder:EvaluateJavaScript** e **xtk:builder:EvaluateJavaScriptTemplate** .

Determinados schemas prontos para uso foram modificados e agora estão agora, por padrão, acessíveis somente com acesso de gravação para operadores com a permissão de **administrador** :

* ncm:publicação
* nl:monitoramento
* nms:calendário
* xtk:builder
* xtk:conexões
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operadorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

### Parâmetro de sessiontoken {#sessiontoken-parameter}

Na v5, o parâmetro do **sessiontoken** funcionava em ambos os lados do cliente (lista de telas de tipo de visão geral, editor de links etc.) e servidor (aplicativos da Web, relatórios, jsp, jssp etc.). Na v7, funciona apenas no lado do servidor. Se você quiser voltar à funcionalidade completa como na v5, você deve modificar os links usando esse parâmetro e passar pela página de conexão:

Exemplo de link:

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

Novo link usando a página de conexão:

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>Se você usar um operador vinculado a uma máscara IP confiável, verifique se ele tem os direitos mínimos e se está em uma zona de segurança no modo **sessionTokenOnly** .

### Funções SQL {#sql-functions}

Chamadas de função SQL desconhecidas não são mais enviadas naturalmente para o servidor. Atualmente, todas as funções SQL devem ser adicionadas ao schema **xtk:funcList** (para obter mais informações, consulte [esta seção](../../configuration/using/adding-additional-sql-functions.md)). Ao migrar, uma opção é adicionada durante a pós-atualização que permite manter a compatibilidade com funções SQL antigas não declaradas. Se você deseja continuar usando essas funções, verifique se a opção **XtkPassUnknownSQLFunctionsToRDBMS** está definida no nível do **[!UICONTROL Administration > Platform > Options]** nó.

>[!IMPORTANT]
>
>Recomendamos vivamente que esta opção não seja utilizada devido aos riscos de segurança que apresenta.

### JSSP {#jssp}

Se você deseja autorizar o acesso a determinadas páginas por meio do protocolo HTTP (não HTTPS), em seus aplicativos da Web, por exemplo, independentemente da configuração realizada nas zonas de segurança, você deve especificar o parâmetro **httpAllowed=&quot;true&quot;** na regra de retransmissão correspondente.

Se você usar JSSPs anônimos, deverá adicionar o parâmetro **httpAllowed=&quot;true&quot;** em uma regra de retransmissão para seu JSSP (**[!UICONTROL serverConf.xml]** arquivo):

Por exemplo:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blocklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Sintaxe {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7 integra um interpretador JavaScript mais recente. No entanto, essa atualização pode resultar em alguns scripts que não funcionam. Como o mecanismo anterior era mais permissivo, certas sintaxes funcionavam, o que já não acontece com a nova versão do mecanismo.

A **[!UICONTROL myObject.@attribute]** sintaxe agora só é válida para objetos XML. Essa sintaxe pode ser usada para personalizar delivery e gestões de conteúdo. Se você usou esse tipo de sintaxe em um objeto não XML, os recursos de personalização não funcionarão mais.

Para todos os outros tipos de objetos, a sintaxe agora é **[!UICONTROL myObject`[`&quot;attribute&quot;`]`]**. Por exemplo, um objeto não XML que usou a seguinte sintaxe:**[!UICONTROL employee.@sn]**, agora deve usar a seguinte sintaxe:**[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

* Sintaxe anterior:

   ```
   employee.@sn
   ```

* Nova sintaxe:

   ```
   employee["sn"]
   ```

Para alterar um valor em um objeto XML, agora é necessário start atualizando o valor antes de adicionar o nó XML:

* Código JavaScript antigo:

   ```
   var cellStyle = node.style.copy();
   this.styles.appendChild(cellStyle);
   cellStyle.@width = column.@width;
   ```

* Novo código JavaScript:

   ```
   var cellStyle = node.style.copy();
   cellStyle.@width = column.@width;
   this.styles.appendChild(cellStyle);
   ```

Não é mais possível usar um atributo XML como uma chave de tabela.

* Sintaxe anterior:

   ```
   if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
   ```

* Nova sintaxe:

   ```
   if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
   ```

### SQLData {#sqldata}

Para reforçar a segurança da instância, uma nova sintaxe foi introduzida no Adobe Campaign v7 para substituir a sintaxe baseada no SQLData. Se você usar esses elementos de código com essa sintaxe, será necessário modificá-los. Os principais elementos em causa são:

* Filtragem por subquery: a nova sintaxe se baseia no `<subQuery>` elemento para definir um subquery
* Agregações: a nova sintaxe é &quot;função de agregação(coleção)&quot;
* Filtragem por junção: a nova sintaxe é `[schemaName:alias:xPath]`

O schema queryDef (xtk:queryDef) foi modificado:

* um novo `<subQuery>` elemento está disponível para substituir a SELECT incluída no SQLData
* dois novos valores, &quot;IN&quot; e &quot;NOT IN&quot; são introduzidos para o atributo @setOperador
* um novo `<where>` elemento, que é um filho do `<node>` elemento: isso permite que você faça &quot;subseleções&quot; em SELECT

Quando um atributo &quot;@expr&quot; é usado, o SQLData pode estar presente. É possível pesquisar os seguintes termos: &quot;SQLData&quot;, &quot;aliasSqlTable&quot;, &quot;sql&quot;.

As instâncias de Adobe Campaign v7 são protegidas por padrão. A segurança está relacionada com as definições das zonas de segurança do **[!UICONTROL serverConf.xml]** ficheiro: o atributo **allowSQLInjection** gerencia a segurança da sintaxe SQL.

Se ocorrer um erro de SQLData durante a execução pós-atualização, você deve modificar esse atributo para permitir temporariamente o uso de sintaxes baseadas em SQLData, permitindo que você regrave o código. Para fazer isso, a seguinte opção deve ser alterada no arquivo **serverConf.xml** :

```
allowSQLInjection="true"
```

Portanto, reinicie o pós-upgrade com o seguinte comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Você deve configurar as zonas de segurança (consulte [Segurança](#security)) e reativar a segurança alterando a opção:

```
allowSQLInjection="false"
```

Abaixo, você encontrará exemplos comparativos entre a sintaxe antiga e a nova.

**Filtragem por subquery**

* Sintaxe anterior:

   ```
   <condition expr="@id NOT IN ([SQLDATA[SELECT iOperatorId FROM XtkOperatorGroup WHERE iGroupId = $(../@owner-id)]])" enabledIf="$(/ignored/@ownerType)=1"/>
   ```

* Nova sintaxe:

   ```
   <condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
     <subQuery schema="xtk:operatorGroup">
        <select>
          <node expr="[@operator-id]" />
        </select>
        <where>
          <condition expr="[@group-id]=$long(../@owner-id)"/>
        </where>
      </subQuery>
   </condition>
   ```

* Sintaxe anterior:

   ```
   <queryFilter name="dupEmail" label="Emails duplicated in the folder" schema="nms:recipient">
       <where>
         <condition sql="sEmail in (select sEmail from nmsRecipient where iFolderId=$(folderId) group by sEmail having count(sEmail)>1)" internalId="1"/>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

* Nova sintaxe:

   ```
   <queryFilter name="dupEmail" label=" Emails duplicated in the folder " schema="nms:recipient">
       <where>
         <condition expr="@email" setOperator="IN" internalId="1">
           <subQuery schema="nms:recipient">
             <select><node expr="@email"/></select>
             <where><condition expr="[@folder-id]=$(folderId)"/></where>
             <groupBy><node expr="@email"/></groupBy>
             <having><condition expr="count(@email)>1"/></having>
           </subQuery>
         </condition>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

**A agregação**

função de Agregação (coleção)

* Sintaxe anterior:

   ```
   <node sql="(select count(*) from NmsNewsgroup WHERE O0.iOperationId=iOperationId)" alias="@nbMessages"/>
   ```

* Nova sintaxe:

   ```
   <node expr="count([newsgroup/@id])" alias="../@nbMessages"/>
   ```

   >[!NOTE]
   >
   >As articulações são automaticamente realizadas para as funções de agregação. Não é mais necessário especificar a condição WHERE O0.iOperationId=iOperationId.
   >
   >Não é mais possível usar a função &quot;count(*)&quot;. Você deve usar &quot;countall()&quot;.

* Sintaxe anterior:

   ```
   <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
   ```

* Nova sintaxe:

   ```
   <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                     <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
   ```

**Filtros por junções**

`[schemaName:alias:xPath]`

O alias é opcional

* Sintaxe anterior:

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                            aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
   ```

* Nova sintaxe:

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
   ```

**Dicas e truques**

Em um `<subQuery>` elemento, para fazer referência a um campo do `<queryDef>` elemento principal, use a seguinte sintaxe: `[../@field]`

Exemplo:

```
<queryDef operation="select" schema="xtk:jobLog" startPath="/" xtkschema="xtk:queryDef">
  <select>
    <node expr="[job/@pid]" alias="@pid"/>
    <node expr="@id" ordered="true"/>
    <node expr="@logType"/>
  </select>
  <where>
    <condition expr="[@job-id]=99"/>
    <condition expr="@logType" setOperator="IN">
      <subQuery schema="xtk:jobLog">
        <select><node expr="@logType"/></select>
        <where><condition expr="[@job-id]=[../job/@id]"/></where>
        <groupBy><node expr="@logType"/></groupBy>
        <having><condition expr="count(@logType)>1"/></having>
      </subQuery>
    </condition>
  </where>
</queryDef>
```

## Conflitos {#conflicts}

A migração é realizada por meio de uma pós-atualização e os conflitos podem aparecer em relatórios, formulários ou aplicativos da Web. Esses conflitos podem ser resolvidos a partir do console.

Após a sincronização do recurso, o comando **pós-atualização** permite detectar se a sincronização gera erros ou avisos.

### Visualização do resultado da sincronização {#view-the-synchronization-result}

O resultado da sincronização pode ser visualizado de duas formas:

* Na interface da linha de comando, os erros são materializados por uma divisa tripla **>>** e a sincronização é interrompida automaticamente. Os avisos são materializados por uma divisa de duplo **>>** e devem ser resolvidos assim que a sincronização for concluída. No final da pós-atualização, um resumo é exibido no prompt de comando. Por exemplo:

   ```
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Se o aviso disser respeito a um conflito de recursos, o operador deverá ter atenção para resolvê-lo.

* O **pós-upgrade_`<server version number>`_time do arquivo pós-upgrade`>`.log** contém o resultado da sincronização. Está disponível por padrão no seguinte diretório: **diretório de instalação/var/`<instance>`pós-atualização**. Erros e avisos são indicados pelos atributos de **erro** e **aviso** .

### Resolver um conflito {#resolve-a-conflict}

A resolução de conflitos só pode ser efetuada por operadores avançados e por operadores a quem tenham sido concedidos direitos de &quot;Administrador&quot;.

Para resolver um conflito, aplique o seguinte processo:

1. Na estrutura da árvore Adobe Campaign, posicione o cursor sobre **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**.
1. Selecione o conflito que deseja resolver na lista.

Há três maneiras possíveis de resolver um conflito:

* **[!UICONTROL Declared as resolved]**: requer uma intervenção prévia do operador.
* **[!UICONTROL Accept the new version]**: recomendado se os recursos fornecidos com o Adobe Campaign não tiverem sido alterados pelo usuário.
* **[!UICONTROL Keep the current version]**: significa que a atualização foi rejeitada.

   >[!IMPORTANT]
   Se você selecionar esse modo de resolução, corre o risco de perder patches na nova versão. Por conseguinte, recomenda-se vivamente que esta opção não seja utilizada ou reservada apenas aos operadores especializados.

Se você optar por resolver manualmente o conflito, proceda da seguinte forma:

1. Na seção inferior da janela, procure o **`_conflict_ string`** para localizar as entidades com conflitos. A entidade instalada com a nova versão contém o **novo** argumento, a entidade que corresponde à versão anterior contém o argumento **cus** .

   ![](assets/s_ncs_production_conflict002.png)

1. Exclua a versão que não deseja manter. Exclua o nome **`_conflict_argument_ string`** da entidade que você está mantendo.

   ![](assets/s_ncs_production_conflict003.png)

1. Vá ao conflito que você teria resolvido. Click the **[!UICONTROL Actions]** icon and select **[!UICONTROL Declare as resolved]**.
1. Salve as alterações: o conflito está agora resolvido.

## Tomcat {#tomcat}

O servidor Tomcat integrado no Adobe Campaign v7 mudou a versão (Tomcat 7). A pasta de instalação (tomcat-6) também foi alterada (tomcat 7). Após a pós-atualização, verifique se os caminhos estão vinculados à pasta atualizada (no **[!UICONTROL serverConf.xml]** arquivo):

```
$(XTK_INSTALL_DIR)/tomcat-7/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-7/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/el-api.jar
```

## Interação {#interaction}

### Pré-requisitos {#prerequisites}

**Antes da pós-atualização**, você deve excluir todas as referências de schema da versão 6.02 que não existirão mais na v7.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### conteúdo da Oferta {#offer-content}

Na v7, o conteúdo da oferta foi movido. Na v6.02, o conteúdo estava em cada schema de representação (**nms:emailOfferView**). Na v7, o conteúdo agora está no schema da oferta. Após a pós-atualização, o conteúdo não estará visível na interface. Após a pós-atualização, você deve recriar o conteúdo da oferta ou desenvolver um script que move automaticamente o conteúdo do schema de representação para o schema de oferta.

>[!IMPORTANT]
Se alguns delivery que usam ofertas configurados forem enviados após a migração, você deverá excluir e recriar todos esses delivery na v7. Se você não conseguir fazer isso, um &quot;modo de compatibilidade&quot; será oferecido. Este modo não é recomendado porque você não se beneficiará de todos os novos recursos no Interaction v7. Este é um modo de transição que permite concluir as campanhas em andamento antes da migração real para a versão 6.1. Para obter mais informações sobre este modo, entre em contato conosco.

Um exemplo de script de movimento (**interventionTo610_full_XX.js**) está disponível na pasta **Migração** na pasta Adobe Campaign v7. Este arquivo mostra um exemplo de script para um cliente usando uma única representação de email por oferta (os **[!UICONTROL htmlSource]** campos e **[!UICONTROL textSource]** ). O conteúdo que estava na tabela **NmsEmailOfferView** foi movido para a tabela oferta.

>[!NOTE]
O uso desse script não permite que você se beneficie das opções &quot;gestão de conteúdo&quot; e &quot;funções de renderização&quot;. Para se beneficiar dessas funções, é necessário repensar as ofertas do catálogo, especialmente o conteúdo da oferta e os espaços de configuração.

```
loadLibrary("/nl/core/shared/nl.js");

NL.require("/nl/core/shared/xtk.js");

// 1. Restore old emailOfferView schema
logInfo("Restoring old emailOfferView schema");
var oldOfferViewSchemas = <entities schema="xtk:srcSchema"/>;

oldOfferViewSchemas.appendChild(
  <srcSchema img="nms:offerView.png"
             label="Email offer representations"
             labelSingular="Email offer representation"
             name="emailOfferView" namespace="nlmig"
             genAccessors="false" implements="xtk:persist">
    <element name="emailOfferView" template="nms:offerView" sqltable="NmsEmailOfferView">
      <element name="offer" revLabel="Email representation" revIntegrity="owncopy"/>
      <element   name="htmlSource"      type="html" label="HTML content"  xml="true"/>
      <element   name="textSource"      type="CDATA" label="Text content" xml="true"/>
      <element   name="htmlSource_jst"  type="CDATA" label="HTML script"  desc="HTML content calculation script."  xml="true" advanced="true"/>
      <element   name="textSource_jst"  type="CDATA" label="Text script" desc="Text content calculation script." xml="true" advanced="true"/>
    </element>
  </srcSchema>);

var oldOfferViewsPkg = <builder><package buildNumber="*">{oldOfferViewSchemas}</package></builder>;
xtk.builder.InstallPackage(oldOfferViewsPkg);

// 2. Migrate data from old emailOfferView table to nms:offer
logInfo("Moving data from old EmailOfferView table to NmsOffer");
var OFFER_STATUS_VALIDATED = 3;

var queryDef = xtk.queryDef.create(
  <queryDef operation="select" schema="nlmig:emailOfferView">
    <select>
      <node expr="[@offer-id]"/>
      <node expr="[@space-id]"/>
      <node expr="htmlSource_jst"/>
      <node expr="textSource_jst"/>
    </select>
  </queryDef>);
var res = queryDef.ExecuteQuery();

var processedOffers = {};
for each( var emailOfferView in res.emailOfferView )
{
  if( processedOffers[String(emailOfferView.@["offer-id"])] != undefined )
  {
    logWarning("Found 2 or more eff fffffmail representations for offer " + String(emailOfferView.@["offer-id"]) + ". Only keep the first one here.");
    continue;
  }
  xtk.session.Write(
    <offer id={emailOfferView.@["offer-id"]} status={OFFER_STATUS_VALIDATED} xtkschema="nms:offer">
      <view>
        {emailOfferView.mdSource_jst}
        {emailOfferView.textSource_jst}
      </view>
    </offer>
  );
  processedOffers[String(emailOfferView.@["offer-id"])] = 1;
}

// 3. Get rid of emailOfferView schema now that data has been moved.
logInfo("Deleting EmailOfferView schema");
xtk.session.Write(<srcSchema xtkschema="xtk:srcSchema" name="emailOfferView" namespace="nlmig" _operation="delete"/>);

logInfo("Done");
```

### Testes e configuração {#tests-and-configuration}

Este é o procedimento a ser seguido depois de ter movido o conteúdo da oferta se você tiver apenas um ambiente. Neste caso vamos pegar &quot;ENV&quot; como exemplo.

1. Em todos os espaços de ofertas de ambiente &quot;ENV&quot;, atualize a lista dos campos usados. Por exemplo, para um espaço de ofertas que usa somente o **[!UICONTROL htmlSource]**, é necessário adicionar o **[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. No **[!UICONTROL Type of Environment]** campo dentro da **[!UICONTROL General]** guia, selecione **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. Crie um ambiente de design (&quot;ENV_DESIGN&quot;, por exemplo) e conecte-o ao ambiente online ENV.

   ![](assets/migration_interaction_4.png)

1. Implante todos os espaços de ofertas do ambiente &quot;ENV&quot; (clique com o botão direito do mouse em > **[!UICONTROL Actions > Deploy]**) e selecione o ambiente &quot;ENV_DESIGN&quot;.

   ![](assets/migration_interaction_5.png)

1. Faça o mesmo para todas as ofertas ambientes &quot;ENV&quot;.
1. Ative todas as ofertas do ambiente &quot;ENV_DESIGN&quot; nos canais relevantes.
1. Teste para fazer uma oferta. Se você não encontrar nenhum problema, execute tarefas pendentes na tarefa de fluxo de trabalho mais recente **[!UICONTROL Offer notification]** (offerMgt) para ativar todas as ofertas.

   ![](assets/migration_interaction_6.png)

1. Execute testes abrangentes.

   >[!NOTE]
   Os nomes das categorias e ofertas online são modificados depois de serem colocados no ar. No canal recebido, atualize todas as referências ao oferta e categoria.

## Relatórios {#reports}

### Relatórios padrão {#standard-reports}

Todos os relatórios padrão usam atualmente o mecanismo de renderização v6.x. Se você adicionou JavaScript a esses relatórios, alguns elementos podem não funcionar mais. Na verdade, a versão antiga do JavaScript não é compatível com o mecanismo de renderização v6.x. Portanto, você deve verificar o código JavaScript e adaptá-lo posteriormente. Você deve testar cada relatório, especialmente a função de exportação.

### Relatórios personalizados {#personalized-reports}

Se você quiser ter o banner azul da v7 (permitindo o acesso aos universos), é necessário republicar os relatórios. Se encontrar problemas, você pode forçar o mecanismo de renderização v6.0. Para fazer isso, vá para **[!UICONTROL Properties]** dentro do relatório, clique em **[!UICONTROL Rendering]** e escolha o mecanismo de **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** renderização.

![](assets/migration_reports_1.png)

Se desejar se beneficiar das novas funcionalidades do relatório, selecione o mecanismo de renderização v.6.x. Nesse caso, verifique todos os scripts e altere-os, se necessário. Em relação à exportação de PDF, se você tiver adicionado um script específico para o OpenOffice, isso não funcionará mais com o novo mecanismo de exportação de PDF (PhantomJS).

## Aplicações web {#web-applications}

Há duas famílias de aplicativos da Web:

* aplicações web identificadas (em conjunto, formulários de aprovação, evolução interna da extranet),
* aplicações web anônimas (formulários web ou questionários).

### Aplicativos da Web identificados {#identified-web-applications}

Assim como os relatórios (consulte [Relatórios](#reports)), se você adicionou JavaScript, é necessário verificar e adaptar, se necessário. Se você quiser se beneficiar do banner azul v7 (contendo os universos), será necessário publicar novamente o aplicativo da Web. Se o código JavaScript estiver funcionando, você pode selecionar o mecanismo de renderização v6.x. Se esse não for o caso, você pode usar o mecanismo de renderização v6.0 enquanto adapta seu código, em seguida, usar o mecanismo de renderização v6.x.

>[!NOTE]
As etapas para selecionar o mecanismo de renderização são as mesmas para selecionar relatórios. Consulte Relatórios [personalizados](#personalized-reports).

Os métodos de conexão de Aplicação web foram alterados na v7. Se você encontrar problemas de conexão em seus aplicativos da Web identificados, será necessário ativar temporariamente as opções **allowUserPassword** e **sessionTokenOnly** no arquivo **serverConf.xml** . Após a pós-atualização, modifique estes valores de opção:

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

Portanto, reinicie o pós-upgrade com o seguinte comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Teste seus aplicativos da Web no mecanismo de renderização v6.x antes de publicá-los. Em seguida, desative essas duas opções.

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### Aplicativos da Web anônimos {#anonymous-web-applications}

Se você encontrar algum problema, publique novamente o aplicativo da Web. Se o problema persistir, você poderá selecionar o mecanismo de renderização v6.0. Se você não tiver adicionado o JavaScript, poderá selecionar o mecanismo de renderização v6.x e se beneficiar de seus novos recursos.

>[!NOTE]
As etapas para selecionar o mecanismo de renderização são as mesmas para selecionar relatórios. Consulte Relatórios [personalizados](#personalized-reports).

## Red-Hat {#red-hat}

Se os schemas prontos para uso tiverem sido excluídos na v6.02 ou na v5.11, talvez não seja mais possível editar seus schemas após a pós-atualização. Se isso acontecer, execute o comando:

```
su - neolane
nlserver config -postupgrade -instance:<instance name> -force
```
