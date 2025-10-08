---
product: campaign
title: Configurar a árvore de navegação do explorador do Campaign
feature: Application Settings
description: Saiba como configurar a árvore de navegação do Campaign Explorer
role: Data Engineer, Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 0%

---

# Configurar a árvore de navegação do explorador do Campaign{#configuration}

Como usuário especialista, você pode adicionar pastas à árvore do explorador e personalizá-la.

Saiba mais sobre a interface do usuário do Campaign na [documentação do Adobe Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

Os tipos de pastas usados pela lista de navegação são descritos em um documento XML que obedece à gramática do esquema **xtk:navtree**.

O documento XML está estruturado da seguinte maneira:

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

O documento XML contém o elemento raiz **`<navtree>`** com os atributos **name** e **namespace** para especificar o nome e o namespace do documento. O nome e o namespace compõem a chave de identificação do documento.

Os comandos globais do aplicativo são declarados no documento do elemento **`<commands>`**.

A declaração de tipos de arquivo está estruturada no documento com os seguintes elementos: **`<model>`** e **`<nodemodel>`**.

## Comandos globais {#global-commands}

Um comando global permite iniciar uma ação. Essa ação pode ser um formulário de entrada ou uma chamada SOAP.

Os comandos globais podem ser acessados no menu principal **[!UICONTROL Tools]**.

A estrutura de configuração do comando é a seguinte:

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

A descrição de um comando global é inserida no elemento **`<command>`** com as seguintes propriedades:

* **nome**: nome interno do comando: o nome deve ser inserido e exclusivo
* **rótulo**: rótulo do comando.
* **desc**: descrição visível da barra de status da tela principal.
* **formulário**: formulário a ser iniciado: o valor a ser inserido é a chave de identificação do formulário de entrada (por exemplo, &quot;cus:recipient&quot;)
* **direitos**: lista de direitos nomeados (separados por vírgula) que permite acesso a este comando. A lista de direitos disponíveis pode ser acessada da pasta **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: exibe uma caixa de confirmação antes da execução do comando.

Um elemento **`<command>`** pode conter subelementos **`<command>`**. Nesse caso, o elemento pai permite exibir um submenu composto desses elementos filhos.

Os comandos são exibidos na mesma ordem declarada no documento XML.

Um separador de comandos permite exibir uma barra de separação entre comandos. Ela é identificada pelo valor **&#39;-&#39;** contido no rótulo do comando.

A presença opcional da marca **`<soapcall>`** com seus parâmetros de entrada define a chamada de um método SOAP a ser executado. Para obter mais informações sobre a API do SOAP, consulte a [documentação do Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=pt-BR).

O contexto do formulário pode ser atualizado na inicialização a partir da marca **`<enter>`**. Para obter mais informações sobre essa tag, consulte a documentação nos formulários de entrada.

**Exemplo**:

* Declaração de um comando global para iniciar o formulário &quot;xtk:import&quot;:

  ```
  <command desc="Start the data import assistant" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  Um atalho de teclado é declarado no caractere &#39;I&#39; pela presença de **&amp;** no rótulo do comando.

* Exemplo de submenu com separador:

  ![](assets/d_ncs_integration_navigation_exemple1.png)

  ```
  <command label="Administration" name="admin">
    <command name="cmd1" label="Example 1" form="cus:example1"/>
    <command name="sep" label="-"/>
    <command name="cmd1" label="Example 2" form="cus:example2">
      <enter>
        <set xpath="@type" expr="1"/>
      </enter>
    </command>
  </command>
  ```

* Execução de um método SOAP:

  ```
  <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
    <soapCall name="Execute" service="xtk:sql"/>
  </command>
  ```

## Tipo de pasta {#folder-type}

Um tipo de pasta permite que você dê acesso aos dados de um esquema. A visualização associada à pasta consiste em uma lista e um formulário de entrada.

A estrutura de configuração do tipo de pasta é a seguinte:

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

A declaração de tipo de pasta deve ser inserida em um elemento **`<model>`**. Esse elemento permite definir uma organização hierárquica visível no menu **[!UICONTROL Add new folder]**. Um elemento **`<model>`** deve conter elementos **`<nodemodel>`** e outros elementos **`<model>`**.

Os atributos **name** e **label** preenchem o nome interno do elemento e o rótulo exibido no menu **[!UICONTROL Add new folder]**.

O elemento **`<nodemodel>`** contém a descrição do tipo de pasta com as seguintes propriedades:

* **nome**: nome interno
* **rótulo**: rótulo usado no menu **[!UICONTROL Add new folder]** e como rótulo padrão ao inserir uma pasta.
* **img**: imagem padrão na inserção da pasta.
* **hiddenCommands**: lista de comandos (separados por vírgula) a serem mascarados. Valores possíveis: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; e &quot;adbdup&quot;.
* **newFolderShortCuts**: lista de atalhos nos modelos (**`<nodemodel>`** separados por vírgula) na criação da pasta.
* **insertRight**, **editRight**, **deleteRight**: direitos para inserir, editar e excluir pastas.

O elemento **`<view>`** sob o elemento **`<nodemodel>`** contém a configuração da lista associada ao modo de exibição. O esquema da lista é inserido no atributo **schema** do elemento **`<view>`**.

Para editar os registros da lista, o formulário de entrada com o mesmo nome do schema de lista é usado implicitamente. O atributo **type** no elemento **`<view>`** afeta a exibição do formulário. Os valores possíveis são:

* **listdet**: exibe o formulário na parte inferior da lista.
* **lista**: exibe somente a lista. O formulário é iniciado clicando duas vezes em ou usando o &quot;Open&quot; no menu ao selecionar a lista.
* **formulário**: exibe um formulário somente leitura.
* **editForm**: exibe um formulário no modo de edição.

>[!NOTE]
>
>O nome do formulário de entrada pode ser sobrecarregado digitando o atributo **formulário** no elemento **`<view>`**.

A configuração padrão das colunas da lista é inserida por meio do elemento **`<columns>`**. Uma coluna é declarada em um elemento **`<node>`** contendo o atributo **xpath** com o campo a ser referenciado em seu esquema como seu valor.

**Exemplo**: declaração de um tipo de pasta no esquema &quot;nms:recipient&quot;.

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

O menu de inserção de pasta correspondente:

![](assets/d_ncs_integration_navigation_exemple2.png)

A filtragem e a classificação podem ser aplicadas quando a lista está sendo carregada:

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### Comandos de atalho {#shortcut-commands}

Um comando de atalho permite iniciar uma ação ao selecionar a lista. A ação pode ser um formulário de entrada ou uma chamada SOAP.

Os comandos podem ser acessados no menu **[!UICONTROL Action]** da lista ou no botão de menu associado.

A estrutura de configuração do comando é a seguinte:

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

A descrição de um comando é inserida no elemento **`<command>`** com as seguintes propriedades:

* **nome**: nome interno do comando: o nome deve ser inserido e exclusivo.
* **rótulo**: rótulo do comando.
* **desc**: descrição visível da barra de status da tela principal.
* **formulário**: formulário a ser iniciado: o valor a ser inserido é a chave de identificação do formulário de entrada (por exemplo, &quot;cus:recipient&quot;).
* **direitos**: lista de direitos nomeados (separados por vírgula) que permite acesso a este comando. A lista de direitos disponíveis pode ser acessada da pasta **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: exibe uma caixa de confirmação antes da execução do comando
* **monoSelection**: força a seleção mono (seleção múltipla por padrão).
* **refreshView**: força o recarregamento da lista após a execução do comando.
* **enabledIf**: ativa o comando dependendo da expressão inserida.
* **img**: insere uma imagem que permite acesso ao comando a partir da barra de ferramentas da lista.

Um elemento **`<command>`** pode conter subelementos **`<command>`**. Nesse caso, o elemento pai permite exibir um submenu composto desses elementos filhos.

Os comandos são exibidos na mesma ordem declarada no documento XML.

Um separador de comandos permite exibir uma barra de separação entre comandos. Ela é identificada pelo valor **&#39;-&#39;** contido no rótulo do comando.

A presença opcional da marca **`<soapcall>`** com seus parâmetros de entrada define a chamada de um método SOAP a ser executado. Para obter mais informações sobre as APIs do SOAP, consulte a [documentação do Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=pt-BR).

O contexto do formulário pode ser atualizado na inicialização por meio da marca **`<enter>`**. Para obter mais informações sobre essa tag, consulte a documentação do formulário de entrada.

**Exemplo**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>
```

### Pasta vinculada {#linked-folder}

Há dois tipos de operações de gerenciamento de pastas:

1. A pasta é uma visualização: a lista exibe todos os registros associados ao schema, com a possibilidade de filtragem do sistema inserida nas propriedades da pasta.
1. A pasta está vinculada: os registros na lista são filtrados implicitamente no link da pasta.

Para uma pasta vinculada, o atributo **folderLink** no elemento **`<nodemodel>`** deve ser preenchido. Este atributo contém o nome do link na pasta configurada no schema de dados.

Exemplo de declaração de uma pasta vinculada no schema de dados:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

A configuração de **`<nodemodel>`** no link da pasta chamada &quot;folder&quot; é a seguinte:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
