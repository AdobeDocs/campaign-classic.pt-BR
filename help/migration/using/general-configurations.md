---
product: campaign
title: Configurações gerais
description: Configurações gerais
feature: Upgrade
audience: migration
content-type: reference
topic-tags: configuration
hide: true
hidefromtoc: true
exl-id: 7aad0e49-8d9c-40c7-9d6a-42fee0ae5870
source-git-commit: 349c3dfd936527e50d7d3e03aa3408b395502da0
workflow-type: tm+mt
source-wordcount: '2558'
ht-degree: 0%

---

# Configurações gerais{#general-configurations}

Esta seção detalha a configuração a ser executada no Adobe Campaign v7 ao migrar de uma v5.11 ou v6.02.

Além disso:

* Se você migrar da v5.11, também deverá concluir a configuração detalhada em [esta seção](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).
* Se você migrar da v6.02, também deverá concluir a configuração detalhada em [esta seção](../../migration/using/configuring-your-platform.md#specific-configurations-in-v6-02).

## Fusos horários {#time-zones}

### Modo multifuso horário {#multi-time-zone-mode}

Na v6.02, o modo &quot;fuso horário múltiplo&quot; só estava disponível para mecanismos de banco de dados PostgreSQL. Agora ele é oferecido independentemente do tipo de mecanismo de banco de dados usado. É altamente recomendável transformar sua base em uma base de &quot;fuso horário múltiplo&quot;.

Para usar o modo TIMESTAMP WITH TIMEZONE, também é necessário adicionar a opção **-userTimestamptz:1** à linha de comando postupgrade.

>[!IMPORTANT]
>
>Se o parâmetro **-usetimestamptz:1** for usado com um mecanismo de banco de dados incompatível, o banco de dados será corrompido e você terá que restaurar um backup do banco de dados e executar novamente o comando acima.

>[!NOTE]
>
>É possível alterar o fuso horário após a migração através do console (**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** nó).
>
>Para obter mais informações sobre o gerenciamento de fuso horário, consulte [esta seção](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

Se você receber um erro **ORA 01805** durante a pós-atualização, isso significa que os arquivos de fuso horário do Oracle entre o servidor de aplicativos e o servidor de banco de dados estão fora de sincronia. Para sincronizá-los novamente, siga as etapas abaixo:

1. Para identificar o arquivo de fuso horário usado, execute o seguinte comando:

   ```
   select * from v$timezone_file
   ```

   Os arquivos de fuso horário geralmente são encontrados na pasta **ORACLE_HOME/oracore/zoneinfo/**.

1. Verifique se os arquivos de fuso horário são idênticos em ambos os servidores.

Para obter mais informações, visite: [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

Um desalinhamento de fuso horário entre cliente e servidor também pode causar alguns atrasos. É por isso que recomendamos usar a mesma versão da biblioteca do Oracle nos lados do cliente e do servidor. Ambos os fusos horários devem ser os mesmos.

Para verificar se ambos os lados estão nos mesmos fusos horários:

1. Verifique a versão do arquivo de fuso horário no lado do cliente executando o seguinte comando:

   ```
   genezi -v
   ```

   genezi é um binário encontrado no repositório **$ORACLE_HOME/bin**.

1. Verifique a versão do arquivo de fuso horário no lado do servidor executando o seguinte comando:

   ```
   select * from v$timezone_file
   ```

1. Para alterar o arquivo de fuso horário no cliente, use a variável de ambiente **ORA_TZFILE**.

## Segurança {#security}

### Zonas de segurança {#security-zones}

>[!IMPORTANT]
>
>Por motivos de segurança, a plataforma Adobe Campaign não é mais acessível por padrão: você deve configurar as zonas de segurança e, portanto, coletar endereços IP de operador.

O Adobe Campaign v7 envolve o conceito de **zonas de segurança**. Cada usuário deve estar associado a uma zona para fazer logon em uma instância e o endereço IP do usuário deve ser incluído nos endereços ou intervalos de endereços definidos na zona de segurança. A configuração das zonas de segurança pode ser feita no arquivo de configuração do servidor do Adobe Campaign. A zona de segurança à qual um usuário está associado deve ser definida no console (**[!UICONTROL Administration > Access management > Operators]**).

**Antes da migração**, peça ajuda ao administrador de rede para definir as zonas de segurança a serem ativadas após a migração.

**Após a pós-atualização** (antes da reinicialização do servidor), você deve configurar as zonas de segurança.

Configuração de zona de segurança encontrada em [esta seção](../../installation/using/security-zones.md).

### Senhas de usuário {#user-passwords}

Na v7, a conexão de operador **interna** e **admin** deve ser protegida por uma senha. É altamente recomendável atribuir senhas a essas contas e a todas as contas de operador, **antes da migração**. Se você não tiver especificado uma senha para **internal**, não poderá se conectar. Para atribuir uma senha a **internal**, digite o seguinte comando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>A senha **interna** deve ser idêntica para todos os servidores de rastreamento. Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier) e [esta seção](../../platform/using/access-management.md).

### Novos recursos na v7 {#new-features-in-v7}

* Usuários sem permissões não podem mais se conectar ao Adobe Campaign. Suas permissões devem ser adicionadas manualmente, por exemplo, criando uma permissão chamada **conectar**.

  Os usuários afetados por essa modificação são identificados e listados durante a pós-atualização.

* O rastreamento não funciona mais se a senha estiver vazia. Se esse for o caso, uma mensagem de erro avisará você e solicitará que você a reconfigure.
* As senhas dos usuários não são mais armazenadas no esquema **xtk:sessionInfo**.
* Permissões administrativas agora são necessárias para usar as funções **`xtk:builder:EvaluateJavaScript`** e **`xtk:builder:EvaluateJavaScriptTemplate`**.

Determinados esquemas prontos para uso foram modificados e agora são acessíveis por padrão apenas com acesso de gravação para operadores com a permissão **admin**:

* ncm:publicação
* nl:monitoring
* nms:calendar
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
* xtk:operatorGroup
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

### Parâmetro Sessiontoken {#sessiontoken-parameter}

Na v5, o parâmetro **sessiontoken** funcionou no lado do cliente (lista de telas do tipo visão geral, editor de links etc.) e no lado do servidor (aplicações web, relatórios, jsp, jssp etc.). Na v7, ele só funciona no lado do servidor. Se quiser voltar à funcionalidade completa como na v5, você deverá modificar os links usando esse parâmetro e passar pela página de conexão:

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
>Se você usar um operador vinculado a uma máscara IP confiável, verifique se ela tem os direitos mínimos e se está em uma zona de segurança no modo **sessionTokenOnly**.

### Funções SQL {#sql-functions}

Chamadas de função SQL desconhecidas não são mais enviadas naturalmente ao servidor. Atualmente, todas as funções SQL devem ser adicionadas ao esquema **xtk:funcList** (para obter mais informações, consulte [esta seção](../../configuration/using/adding-additional-sql-functions.md)). Ao migrar, uma opção é adicionada durante a pós-atualização, permitindo que você mantenha a compatibilidade com funções SQL não declaradas antigas. Se você quiser continuar usando essas funções, verifique se a opção **XtkPassUnknownSQLFunctionsToRDBMS** está realmente definida no nível do nó **[!UICONTROL Administration > Platform > Options]**.

>[!IMPORTANT]
>
>Recomendamos não usar essa opção devido aos riscos de segurança que ela apresenta.

### JSSP {#jssp}

Se você quiser autorizar o acesso a determinadas páginas por meio do protocolo HTTP (não HTTPS), em seus aplicativos Web, por exemplo, independentemente da configuração executada nas zonas de segurança, você deve especificar o parâmetro **httpAllowed=&quot;true&quot;** na regra de retransmissão correspondente.

Se você usa JSSPs anônimos, deve adicionar o parâmetro **httpAllowed=&quot;true&quot;** em uma regra de retransmissão para seu JSSP (arquivo **[!UICONTROL serverConf.xml]**):

Por exemplo:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Sintaxe {#syntax}

### JavaScript {#javascript}

O Adobe Campaign v7 integra um interpretador JavaScript mais recente. No entanto, essa atualização pode levar ao mau funcionamento de determinados scripts. Como o mecanismo anterior era mais permissivo, certas sintaxes funcionariam, o que não é mais o caso com a nova versão do mecanismo.

A sintaxe **[!UICONTROL myObject.@attribute]** agora é válida somente para objetos XML. Essa sintaxe pode ser usada para personalizar deliveries e gestão de conteúdo. Se você usou esse tipo de sintaxe em um objeto não XML, os recursos de personalização não funcionarão mais.

Para todos os outros tipos de objeto, a sintaxe agora é **[!UICONTROL myObject`[`&quot;atributo&quot;`]`]**. Por exemplo, um objeto não XML que usou a seguinte sintaxe: **[!UICONTROL employee.@sn]**, agora deve usar a seguinte sintaxe: **[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

* Sintaxe anterior:

  ```
  employee.@sn
  ```

* Nova sintaxe:

  ```
  employee["sn"]
  ```

Para alterar um valor em um objeto XML, agora é necessário começar atualizando o valor antes de adicionar o nó XML:

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

Não é mais possível usar um atributo XML como chave de tabela.

* Sintaxe anterior:

  ```
  if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
  ```

* Nova sintaxe:

  ```
  if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
  ```

### SQLData {#sqldata}

Para fortalecer a segurança da instância, uma nova sintaxe foi introduzida no Adobe Campaign v7 para substituir a sintaxe baseada em SQLData. Se você usar esses elementos de código com essa sintaxe, será necessário modificá-los. Os principais elementos em causa são:

* Filtragem por subconsulta: a nova sintaxe é baseada no elemento `<subQuery>` para definir uma subconsulta
* Aggregates: a nova sintaxe é &quot;aggregate function(collection)&quot;
* Filtragem por junção: a nova sintaxe é `[schemaName:alias:xPath]`

O esquema queryDef (xtk:queryDef) foi modificado:

* um novo elemento `<subQuery>` está disponível para substituir o SELECT incluído em SQLData
* dois novos valores, &quot;IN&quot; e &quot;NOT IN&quot; são introduzidos para o atributo @setOperator
* um novo elemento `<where>`, que é filho do elemento `<node>`: isso permite fazer &quot;subseleções&quot; em SELECT

Quando um atributo &quot;@expr&quot; é usado, o SQLData pode estar presente. Uma pesquisa pelos seguintes termos pode ser executada: &quot;SQLData&quot;, &quot;aliasSqlTable&quot;, &quot;sql&quot;.

As instâncias do Adobe Campaign v7 são protegidas por padrão. A segurança é fornecida em termos de definições de zonas de segurança no arquivo **[!UICONTROL serverConf.xml]**: o atributo **allowSQLInjection** gerencia a segurança da sintaxe SQL.

Se ocorrer um erro de SQLData durante a execução pós-atualização, você deverá modificar esse atributo para permitir temporariamente o uso de sintaxes baseadas em SQLData, permitindo que você regrave o código. Para fazer isso, a seguinte opção deve ser alterada no arquivo **serverConf.xml**:

```
allowSQLInjection="true"
```

Portanto, reinicie o postupgrade com o seguinte comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Você deve configurar as zonas de segurança (consulte [Segurança](#security)) e, em seguida, reativar a segurança alterando a opção:

```
allowSQLInjection="false"
```

Abaixo você encontrará exemplos comparativos entre a sintaxe antiga e a nova.

**Filtragem por subconsultas**

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

Função agregada (coleção)

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
  >As junções são executadas automaticamente para as funções agregadas. Não é mais necessário especificar a condição WHERE O0.iOperationId=iOperationId.
  >
  >Não é mais possível usar a função &quot;count(&#42;)&quot;. Você deve usar &quot;countall()&quot;.

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

Em um elemento `<subQuery>`, para referenciar um campo &quot;field&quot; do `<queryDef>` principal   use a seguinte sintaxe: `[../@field]`

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

A migração é realizada por meio de uma pós-atualização e os conflitos podem aparecer em relatórios, formulários ou aplicativos da Web. Esses conflitos podem ser resolvidos no console.

Após a sincronização de recursos, o comando **postupgrade** permite detectar se a sincronização gera erros ou avisos.

### Exibir o resultado da sincronização {#view-the-synchronization-result}

O resultado da sincronização pode ser visualizado de duas maneiras:

* Na interface de linha de comando, os erros são materializados por uma divisa tripla **>>** e a sincronização é interrompida automaticamente. Os avisos são materializados por uma divisa dupla **>** e devem ser resolvidos quando a sincronização estiver concluída. No final da pós-atualização, um resumo é exibido no prompt de comando. Por exemplo:

  ```
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     info    log     =========Summary of the update==========
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Se o aviso aborda um conflito de recursos, é necessária atenção do operador para resolvê-lo.

* O arquivo **postupgrade_`<server version number>`_time de postupgrade`>`.log** contém o resultado da sincronização. Ele está disponível por padrão no seguinte diretório: **diretório de instalação/var/`<instance>`postupgrade**. Os erros e avisos são indicados pelos atributos **erro** e **aviso**.

### Resolver um conflito {#resolve-a-conflict}

A resolução de conflitos só deve ser executada por operadores avançados e aqueles que receberam direitos de &#39;Administrador&#39;.

Para resolver um conflito, aplique o seguinte processo:

1. Na estrutura da árvore do Adobe Campaign, coloque o cursor sobre **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**.
1. Selecione o conflito que deseja resolver na lista.

Há três maneiras possíveis de resolver um conflito:

* **[!UICONTROL Declared as resolved]**: requer a intervenção do operador antecipadamente.
* **[!UICONTROL Accept the new version]**: recomendado se os recursos fornecidos com o Adobe Campaign não tiverem sido alterados pelo usuário.
* **[!UICONTROL Keep the current version]**: significa que a atualização foi rejeitada.

  >[!IMPORTANT]
  >
  >Se você selecionar esse modo de resolução, corre o risco de perder patches na nova versão. Por conseguinte, recomenda-se vivamente que esta opção não seja utilizada ou reservada apenas a operadores especializados.

Se você optar por resolver o conflito manualmente, proceda da seguinte maneira:

1. Na seção inferior da janela, procure por **`_conflict_ string`** para localizar as entidades com conflitos. A entidade instalada com a nova versão contém o argumento **new**. A entidade que corresponde à versão anterior contém o argumento **cus**.

   ![](assets/s_ncs_production_conflict002.png)

1. Exclua a versão que você não deseja manter. Exclua o **`_conflict_argument_ string`** da entidade que você está mantendo.

   ![](assets/s_ncs_production_conflict003.png)

1. Vá para o conflito que você teria resolvido. Clique no ícone **[!UICONTROL Actions]** e selecione **[!UICONTROL Declare as resolved]**.
1. Salve as alterações: o conflito agora está resolvido.

<!--
## Tomcat {#tomcat}

The integrated Tomcat server in Adobe Campaign v7 has changed version. Its installation folder (tomcat-6) has therefore also changed (tomcat 7). After the postupgrade, make sure to check that the paths do link to the updated folder (in the **[!UICONTROL serverConf.xml]** file):

```
$(XTK_INSTALL_DIR)/tomcat-X/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-X/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/el-api.jar
```
-->

## Interação {#interaction}

### Pré-requisitos {#prerequisites}

**Antes da pós-atualização**, você deve excluir todas as referências de esquema do 6.02 que não existirão mais na v7.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### Conteúdo da oferta {#offer-content}

Na v7, o conteúdo da oferta foi movido. Na v6.02, o conteúdo estava em cada esquema de representação (**nms:emailOfferView**). Na v7, o conteúdo agora está no schema de ofertas. Após a pós-atualização, o conteúdo não estará visível na interface. Após a pós-atualização, você deve recriar o conteúdo da oferta ou desenvolver um script que move automaticamente o conteúdo do esquema de representação para o esquema de oferta.

>[!IMPORTANT]
>
>Se alguns deliveries usando ofertas configuradas tiverem que ser enviados após a migração, você deverá excluir e recriar todos esses deliveries no v7. Se você não conseguir fazer isso, um &quot;modo de compatibilidade&quot; será oferecido. Esse modo não é recomendado porque você não se beneficiará de todos os novos recursos do Interaction v7. Esse é um modo de transição que permite concluir campanhas em andamento antes da migração real para o 6.1. Para obter mais informações sobre este modo, entre em contato conosco.

Um exemplo de script de movimentação (**interactionTo610_full_XX.js**) está disponível na pasta **Migration** da pasta do Adobe Campaign v7. Este arquivo mostra um exemplo de um script para um cliente usando uma única representação de email por oferta (os campos **[!UICONTROL htmlSource]** e **[!UICONTROL textSource]**). O conteúdo que estava na tabela **NmsEmailOfferView** foi movido para a tabela de ofertas.

>[!NOTE]
>
>Usar esse script não permite que você se beneficie das opções de &quot;gerenciamento de conteúdo&quot; e &quot;funções de renderização&quot;. Para se beneficiar dessas funções, é necessário repensar as ofertas de catálogo, especialmente o conteúdo da oferta e os espaços de configuração.

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

Este é o procedimento a ser seguido após mover o conteúdo da oferta se você tiver apenas um ambiente. Nesse caso, vamos tomar &quot;ENV&quot; como exemplo.

1. Em todos os espaços de oferta de ambiente &quot;ENV&quot;, atualize a lista de campos usados. Por exemplo, para um espaço de ofertas que use apenas o **[!UICONTROL htmlSource]**, você deve adicionar o **[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. No campo **[!UICONTROL Type of Environment]**, na guia **[!UICONTROL General]**, selecione **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. Crie um ambiente de design (&quot;ENV_DESIGN&quot;, por exemplo) e conecte-o ao ambiente online ENV.

   ![](assets/migration_interaction_4.png)

1. Implante todos os espaços de oferta do ambiente &quot;ENV&quot; (clique com o botão direito do mouse > **[!UICONTROL Actions > Deploy]**) e selecione o ambiente &quot;ENV_DESIGN&quot;.

   ![](assets/migration_interaction_5.png)

1. Faça o mesmo para todas as ofertas de ambientes &quot;ENV&quot;.
1. Ative todas as ofertas de ambiente &quot;ENV_DESIGN&quot; nos canais relevantes.
1. Teste fazer uma oferta entrar em funcionamento. Se você não encontrar problemas, execute tarefas pendentes na tarefa de fluxo de trabalho mais recente **[!UICONTROL Offer notification]** (offerMgt) para ativar todas as ofertas.

   ![](assets/migration_interaction_6.png)

1. Realize testes abrangentes.

   >[!NOTE]
   >
   >Os nomes das categorias e ofertas online são modificados após serem ativadas. No canal de entrada, atualize todas as referências a ofertas e categorias.

## Relatórios {#reports}

### Relatórios padrão {#standard-reports}

Todos os relatórios padrão atualmente usam o mecanismo de renderização v6.x. Se você tiver adicionado JavaScript a esses relatórios, alguns elementos podem não funcionar mais. Na verdade, a versão antiga do JavaScript não é compatível com o mecanismo de renderização v6.x. Portanto, você deve verificar o código JavaScript e adaptá-lo posteriormente. Você deve testar cada relatório, principalmente a função de exportação.

### Relatórios personalizados {#personalized-reports}

<!--If you want to have the blue banner from v7 (allowing you access to the tabs), you must republish reports. If you encounter problems, you can force the v6.0 rendering engine. To do this, go to **[!UICONTROL Properties]** within the report, click **[!UICONTROL Rendering]** and choose the **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** rendering engine.

![](assets/migration_reports_1.png)
-->
Para se beneficiar das novas funcionalidades do relatório, é necessário republicar os relatórios. Nesse caso, verifique todos os scripts e os altere se necessário. Em relação à exportação de PDF, se você tiver adicionado um script específico para o Open Office, ele não funcionará mais com o novo mecanismo de exportação de PDF (PhantomJS).

## Aplicações web {#web-applications}

Há duas famílias de aplicativos Web:

* aplicações Web identificadas (vistos em conjunto, formulários de aprovação, desenvolvimentos internos da extranet),
* aplicações web anônimas (formulários web ou de questionário).

### Aplicativos web identificados {#identified-web-applications}

Assim como para os relatórios ([saiba mais](#reports)), se você tiver adicionado o JavaScript, deverá verificar e adaptar, se necessário. Se quiser se beneficiar do banner azul v7 (contendo as guias azuis), você deverá republicar o aplicativo web.

Os métodos de conexão da aplicação web foram alterados na v7. Se você encontrar problemas de conexão nos aplicativos Web identificados, ative temporariamente as opções **allowUserPassword** e **sessionTokenOnly** no arquivo **serverConf.xml**. Após a pós-atualização, modifique esses valores de opção:

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

Portanto, reinicie o postupgrade com o seguinte comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Teste as aplicações web no mecanismo de renderização da v6.x, antes de publicá-las. Em seguida, desative essas duas opções.

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### Aplicativos web anônimos {#anonymous-web-applications}

Se encontrar problemas, publique novamente o aplicativo web.
