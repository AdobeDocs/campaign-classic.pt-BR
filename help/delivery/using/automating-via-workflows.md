---
product: campaign
title: Automatizar via fluxos de trabalho
description: Saiba como automatizar o gerenciamento de conteúdo por meio de fluxos de trabalho
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Workflows
role: User
exl-id: bc6ebf5d-cc21-4750-9713-2bf259e7d6bf
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 93%

---

# Automatizar com fluxos de trabalho{#automating-via-workflows}

## Atividade de Gerenciamento de conteúdo {#content-management-activity}

Criar, editar e publicar conteúdo pode ser automatizado usando um fluxo de trabalho configurado através da interface do cliente do Adobe Campaign.

A atividade **Content management** é acessada pela barra de ferramentas **[!UICONTROL Tools]** do diagrama de fluxo de trabalho.

As propriedades da atividade são divididas em quatro etapas:

* **[!UICONTROL Content]**: permite inserir conteúdo existente ou criar conteúdo,
* **[!UICONTROL Update content]**: permite modificar o assunto do conteúdo ou atualizar o conteúdo por meio de um fluxo de dados XML,
* **[!UICONTROL Action to execute]**: permite salvar ou gerar conteúdo,
* **[!UICONTROL Transition]**: permite escolher se gera ou não uma transição de saída e a nomeia.

![](assets/d_ncs_content_wf.png)

### Conteúdo {#content}

* **Especificado pela transição**

  O conteúdo a ser usado foi criado anteriormente. Os processos se referem à instância de conteúdo propagada pelo evento de entrada. O identificador de conteúdo é acessado por meio da variável &quot;contentId&quot; do evento.

* **Explícito**

  Permite escolher o conteúdo criado anteriormente.

* **Calculado por um script**

  Seleciona uma instância de conteúdo com base em um modelo JavaScript. O código a ser avaliado permite recuperar o identificador de conteúdo.

* **Novo, criado por meio de um modelo de publicação**

  Cria um novo conteúdo por meio de um modelo de publicação. A instância de conteúdo será salva na pasta &quot;string&quot; preenchida.

### Atualizar o conteúdo {#update-the-content}

* **Assunto**

  Permite modificar o assunto da ação de entrega ao publicar.

* **Acesso aos dados de um feed XML**

  O conteúdo é atualizado de um feed XML de uma fonte externa. Um URL deve ser inserido para que o download de dados ocorra.

  Uma folha de estilos XSL pode ser usada para transformar os dados XML de entrada.

### Ação a ser executada {#action-to-execute}

* **Salvar**

  Salva o conteúdo criado ou modificado. O identificador do conteúdo salvo é propagado na variável &quot;contentId&quot; do evento de saída.

* **Gerar**

  Gera os arquivos de saída para cada um dos modelos de transformação com uma publicação do tipo &quot;Arquivo&quot;. A transição de saída é ativada para cada arquivo gerado, com os seguintes parâmetros: o identificador do conteúdo salvo na variável &quot;contentId&quot; e o nome do arquivo na variável &quot;filename&quot;.

### Transição {#transition}

A opção **Generate an output transition** permite adicionar uma transição de saída à atividade **[!UICONTROL Content management]** para vincular uma nova atividade à execução do fluxo de trabalho. Após verificar essa opção, insira um rótulo para a transição.

## Exemplos {#examples}

### Automatizar a criação e a entrega de conteúdo {#automating-content-creation-and-delivery}

O exemplo a seguir automatiza a criação e a entrega de um bloco de conteúdo.

![](assets/d_ncs_content_workflow2.png)

O conteúdo é configurado através da atividade &quot;Gerenciamento de conteúdo&quot;:

![](assets/d_ncs_content_workflow3.png)

Uma nova instância de conteúdo é criada por meio do modelo de publicação e da pasta de string de conteúdo.

No nosso exemplo, sobrecarregamos o assunto da entrega. Ele será considerado em vez do inserido no modelo **[!UICONTROL Delivery]**.

O conteúdo é preenchido automaticamente por um feed XML vindo do URL inserido:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

O formato de dados não corresponde ao esquema de dados inserido no modelo de publicação (**cus:book** em nosso exemplo); o elemento **`<section>`** deve ser substituído pelo elemento **`<chapter>`**. É necessário aplicar a folha de estilos &quot;cus:book-workflow.xsl&quot; para fazer as alterações necessárias.

Código de origem da folha de estilos XSLT usada:

```
<?xml version="1.0" encoding="utf-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
 <xsl:output indent="yes" method="xml"  encoding="ISO-8859-1"/>

 <xsl:template match="text()|@*"/>

  <xsl:template match="*">
    <xsl:variable name="element.name" select="name(.)"/>
    <xsl:element name="{$element.name}">
      <xsl:copy-of select="text()|@*"/>
      <xsl:apply-templates/>
    </xsl:element>
  </xsl:template>

  <xsl:template match="book">
  <book name="test">
     <xsl:apply-templates/>
    <book>
 </xsl:template>

  <xsl:template match="section">
    <chapter>
      <xsl:for-each select="@*">
        <xsl:copy-of select="."/>
      </xsl:for-each>
       <xsl:apply-templates/>
    </chapter>
  </xsl:template>
  
</xsl:stylesheet>
```

A ação final da atividade é salvar a instância de conteúdo e prosseguir para a próxima tarefa.

O direcionamento é realizado por meio da atividade **Query**.

Uma atividade **AND-join** é adicionada para garantir que a entrega só iniciará quando a consulta do target e as atualizações de conteúdo forem concluídas.

A ação da entrega é configurada por meio da atividade **Entrega**:

![](assets/d_ncs_content_workflow4.png)

Uma nova ação da entrega é criada com base em um modelo.

O template da entrega da atividade é usado para selecionar os modelos de transformação do template de publicação. A geração de conteúdo leva em consideração todos os modelos HTML e Texto sem os modelos da entrega ou aqueles referenciados com o mesmo que a atividade.

O target a ser enviado é digitado por meio do evento de entrada.

O conteúdo de entrega é preenchido por meio do evento de entrada.

A última etapa para concluir a atividade é preparar e depois iniciar a entrega.

### Criar conteúdo para publicação posterior {#creating-content-and-publishing-it-later}

Este exemplo cria um bloco de conteúdo e uma publicação de arquivo de lançamento após um atraso específico.

![](assets/d_ncs_content_workflow5.png)

A primeira tarefa de **Gerenciamento de conteúdo** cria uma instância de conteúdo.

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>A guia **[!UICONTROL Publication]** da janela dos modelos de transformação deve ser preenchida com o local do target a ser gerado.

Uma atividade de espera é adicionada para pausar a próxima transição por uma semana.

![](assets/d_ncs_content_workflow7.png)

O conteúdo é inserido manualmente durante esse período de tempo.

A próxima tarefa inicia a geração de conteúdo.

![](assets/d_ncs_content_workflow8.png)

O conteúdo a ser publicado é inserido por meio da transição de entrada.

A ação final é gerar esse conteúdo forçando o diretório de publicação.

A atividade **Código JavaScript** recupera o nome completo de cada arquivo gerado.

![](assets/d_ncs_content_workflow9.png)

### Criar a entrega e seu conteúdo {#creating-the-delivery-and-its-content}

Esse exemplo usa o mesmo conceito do primeiro exemplo, mas cria a ação de entrega na primeira etapa.

![](assets/d_ncs_content_workflow10.png)

A primeira tarefa **Criar entrega** cria a ação de entrega.

A atividade fork permite o início do cálculo do alvo e a criação da instância de conteúdo ao mesmo tempo.

Depois que as tarefas são executadas, a caixa AND-join ativa a tarefa **Delivery** para iniciar a entrega criada anteriormente no conteúdo e direcionamento.

![](assets/d_ncs_content_workflow11.png)

A ação da entrega a ser iniciada é preenchida pela transição.

O target a ser entregue é digitado por meio do evento de entrada.

O conteúdo de entrega é preenchido por meio do evento de entrada.

A ação final da atividade é preparar e iniciar a entrega.

### Importar conteúdo do FTP {#importing-content-from-ftp}

Se o seu conteúdo da entrega estiver disponível em um arquivo HTML localizado em servidores FTP ou SFTP, é possível carregá-los facilmente nas entregas do Adobe Campaign. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/load-delivery-content.html){target="_blank"}.


### Importar conteúdo do conector do Amazon Simple Storage Service (S3)  {#importing-content-from-amazon-simple-storage-service--s3--connector}

Se o conteúdo da entrega estiver localizado nos buckets do Amazon Simple Storage Service (S3), é possível carregá-los facilmente nas entregas do Adobe Campaign. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/deliveries/load-delivery-content.html){target="_blank"}.


## Atualização semiautomática {#semi-automatic-update}

Os dados de conteúdo podem ser atualizados no modo &quot;semiautomático&quot;. Os dados são recuperados de um feed XML via URL.

A ativação da recuperação de dados é realizada manualmente por meio do formulário de entrada.

O objetivo é declarar um campo de tipo **`<input>`** **editBtn** no formulário. Esse controle inclui uma zona de edição e um botão para iniciar o processamento.

A zona de edição permite que você preencha dados variáveis usados para construir o URL do feed XML de dados a serem recuperados.

O botão executa o método SOAP **GetAndTransform** preenchido na tag **`<input>`**.

A declaração de controle no formulário é a seguinte:

```
<input type="editbtn" xpath="<path>">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="<url>" type="string"/>
      <param exprIn="'xtk:xslt|<style sheet>'" type="string"/>
      <param type="DOMElement" xpathOut="<output path>"/>
    </soapCall>
  </enter>
</input>
```

O método **GetAndTransform** deve ser declarado no elemento **`<enter>`** da tag **`<input>`**. Essa tag assume como parâmetros p URL de recuperação de dados XML de uma expressão construída dinamicamente. O segundo parâmetro da função é opcional e faz referência a uma folha de estilos usada para uma transformação intermediária quando os dados XML de entrada não estão no mesmo formato do conteúdo.

A saída atualiza o conteúdo com base no caminho inserido no último parâmetro.

**Exemplo**: para ilustrar este exemplo, começamos do esquema &quot;cus:book&quot;.

Um formulário de entrada de controle de edição de atualização semiautomático é adicionado:

![](assets/d_ncs_content_exemple9.png)

```
<input label="File name" type="editbtn" xpath="/tmp/@name">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="'https://myserver.adobe.com/incoming/' + [/tmp/@name] + '.xml'" type="string"/>
      <param exprIn="'xtk:xslt|cus:book-workflow.xsl'" type="string"/>
      <param type="DOMElement" xpathOut="."/>
    </soapCall>
  </enter>
</input>
```

A zona de edição permite a inserção do nome do arquivo a ser recuperado. O URL é construído com base neste nome, por exemplo: https://myserver.adobe.com/incomin/data.xml

O formato dos dados a serem recuperados é o mesmo do exemplo 1 da automação do fluxo de trabalho. Usaremos a folha de estilos &quot;cus:book-workflow.xsl&quot; vista neste exemplo.

O resultado da execução do trabalho atualiza a instância do conteúdo do caminho &#39;.&#39;.
