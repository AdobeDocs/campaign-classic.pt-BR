---
solution: Campaign Classic
product: campaign
title: Configuração
description: Configuração
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 2%

---


# Configuração{#configuration}

Os tipos de pastas usados pela lista de navegação são descritos em um documento XML que obedece à gramática do schema **xtk:navtree** .

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

O documento XML contém o elemento **`<navtree>`** raiz com os atributos **name** e **namespace** para especificar o nome e a namespace do documento. O nome e a namespace compõem a chave de identificação do documento.

Os comandos globais do aplicativo são declarados no documento a partir do **`<commands>`** elemento.

A declaração de tipos de arquivos está estruturada no documento com os seguintes elementos: **`<model>`** e **`<nodemodel>`**.

## Comandos globais {#global-commands}

Um comando global permite que você inicie uma ação. Essa ação pode ser um formulário de entrada ou uma chamada SOAP.

Os comandos globais podem ser acessados a partir do **[!UICONTROL Tools]** menu principal.

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

A descrição de um comando global é inserida no **`<command>`** elemento com as seguintes propriedades:

* **name**: nome interno do comando: o nome deve ser inserido e exclusivo
* **rótulo**: rótulo do comando.
* **desc**: descrição visível na barra de status da tela principal.
* **formulário**: formulário a ser lançado: o valor a ser inserido é a chave de identificação do formulário de entrada (por exemplo, &quot;cus:recipient&quot;)
* **direitos**: lista de direitos nomeados (separados por vírgula) que permite o acesso a esse comando. A lista de direitos disponíveis pode ser acessada na **[!UICONTROL Administration > Access management > Named rights]** pasta.
* **promptLabel**: exibe uma caixa de confirmação antes da execução do comando.

Um **`<command>`** elemento pode conter **`<command>`** subelementos. Nesse caso, o elemento pai permite exibir um submenu composto desses elementos filho.

Os comandos são exibidos na mesma ordem em que são declarados no documento XML.

Um separador de comando permite exibir uma barra de separação entre comandos. É identificado pelo valor **&#39;-&#39;** contido no rótulo do comando.

A presença opcional da **`<soapcall>`** tag com seus parâmetros de entrada define a chamada de um método SOAP a ser executado. Para obter mais informações sobre a API SOAP, consulte a documentação [JSAPI da](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)Campanha.

O contexto do formulário pode ser atualizado na inicialização a partir da **`<enter>`** tag . Para obter mais informações sobre essa tag, consulte a documentação sobre formulários de entrada.

**Exemplo**:

* Declaração de um comando global para iniciar o formulário &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   Um atalho de teclado é declarado no caractere &#39;I&#39; pela presença de **&amp;** no rótulo do comando.

* Exemplo de um submenu com um separador:

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

Um tipo de pasta permite que você dê acesso aos dados de um schema. A visualização associada à pasta consiste em uma lista e um formulário de entrada.

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

A declaração de tipo de pasta deve ser inserida em um **`<model>`** elemento. Esse elemento permite definir uma organização hierárquica visível no **[!UICONTROL Add new folder]** menu. Um **`<model>`** elemento deve conter **`<nodemodel>`** elementos e outros **`<model>`** elementos.

Os atributos de **nome** e **rótulo** preenchem o nome interno do elemento e o rótulo exibido no **[!UICONTROL Add new folder]** menu.

O **`<nodemodel>`** elemento contém a descrição do tipo de pasta com as seguintes propriedades:

* **name**: nome interno
* **rótulo**: rótulo usado no **[!UICONTROL Add new folder]** menu e como um rótulo padrão ao inserir uma pasta.
* **img**: imagem padrão na inserção de pasta.
* **hiddenCommands**: lista de comandos (separados por vírgula) a serem mascarados. Valores possíveis: &quot;insert&quot;, &quot;delete&quot;, &quot;update&quot; e &quot;duplicado&quot;.
* **newFolderShortCuts**: lista de atalhos em modelos (**`<nodemodel>`** separados por vírgula) na criação de pastas.
* **insertRight**, **editRight**, **deleteRight**: direitos para inserir, editar e excluir pastas.

O **`<view>`** elemento sob o **`<nodemodel>`** elemento contém a configuração da lista associada à visualização. O schema da lista é inserido no atributo **schema** do **`<view>`** elemento.

Para editar os registros da lista, o formulário de entrada com o mesmo nome do schema da lista é implicitamente usado. O atributo **type** no **`<view>`** elemento afeta a exibição do formulário. Os valores possíveis são:

* **lista**: exibe o formulário na parte inferior da lista.
* **lista**: exibe a lista sozinha. O formulário é iniciado clicando com o duplo ou usando &quot;Abrir&quot; no menu ao selecionar a lista.
* **formulário**: exibe um formulário somente leitura.
* **editForm**: exibe um formulário no modo de edição.

>[!NOTE]
>
>O nome do formulário de entrada pode ser sobrecarregado inserindo o atributo de **formulário** no **`<view>`** elemento .

A configuração padrão das colunas de lista é inserida por meio do **`<columns>`** elemento. Uma coluna é declarada em um **`<node>`** elemento que contém o atributo **xpath** com o campo a ser referenciado em seu schema como seu valor.

**Exemplo**: declaração de um tipo de pasta no schema &quot;nms:recipient&quot;.

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

Os comandos podem ser acessados a partir do **[!UICONTROL Action]** menu da lista ou do botão de menu associado.

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

A descrição de um comando é inserida no **`<command>`** elemento com as seguintes propriedades:

* **name**: nome interno do comando: o nome deve ser inserido e exclusivo.
* **rótulo**: rótulo do comando.
* **desc**: descrição visível na barra de status da tela principal.
* **formulário**: formulário a ser lançado: o valor a ser inserido é a chave de identificação do formulário de entrada (por exemplo, &quot;cus:recipient&quot;).
* **direitos**: lista de direitos nomeados (separados por vírgula) que permite o acesso a esse comando. A lista de direitos disponíveis pode ser acessada na **[!UICONTROL Administration > Access management > Named rights]** pasta.
* **promptLabel**: exibe uma caixa de confirmação antes da execução do comando
* **monoSelection**: força a seleção mono (seleção múltipla por padrão).
* **refreshView**: força o recarregamento da lista após a execução do comando.
* **enabledIf**: ativa o comando, dependendo da expressão inserida.
* **img**: insere uma imagem que permite o acesso ao comando na barra de ferramentas lista.

Um **`<command>`** elemento pode conter **`<command>`** subelementos. Nesse caso, o elemento pai permite exibir um submenu composto desses elementos filho.

Os comandos são exibidos na mesma ordem em que são declarados no documento XML.

Um separador de comando permite exibir uma barra de separação entre comandos. É identificado pelo valor **&#39;-&#39;** contido no rótulo do comando.

A presença opcional da **`<soapcall>`** tag com seus parâmetros de entrada define a chamada de um método SOAP a ser executado. Para obter mais informações sobre APIs SOAP, consulte a documentação [JSAPI da](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)Campanha.

O contexto do formulário pode ser atualizado na inicialização por meio da **`<enter>`** tag . Para obter mais informações sobre essa tag, consulte a documentação do formulário de entrada.

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
1. A pasta está vinculada: os registros na lista são implicitamente filtrados no link da pasta.

Para uma pasta vinculada, o atributo **folderLink** no **`<nodemodel>`** elemento deve ser preenchido. Este atributo contém o nome do link na pasta configurada no schema de dados.

Exemplo de declaração de uma pasta vinculada no schema de dados:

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

A configuração da pasta &quot;folder&quot; **`<nodemodel>`** no link é a seguinte:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

