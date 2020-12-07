---
solution: Campaign Classic
product: campaign
title: Templates de publicação
description: Templates de publicação
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '824'
ht-degree: 100%

---


# Templates de publicação{#publication-templates}

## Sobre os templates de publicação {#about-publication-templates}

O template de publicação é o cartão de identidade do conteúdo a ser publicado. Ele referencia os recursos usados no processo de publicação, ou seja:

* o schema de dados,
* o formulário de entrada,
* os modelos de transformação para cada documento de saída.

## Identificação de um template de publicação {#identification-of-a-publication-template}

Um template de publicação é identificado por seu nome e namespace.

A chave de identificação de uma folha de estilos é uma cadeia de caracteres formada pelo namespace e pelo nome separados por dois pontos, por exemplo: **cus:newsletter**.

>[!NOTE]
>
>Na prática, é recomendável usar a mesma chave para o schema, o formulário e o template de publicação.

## Criação e configuração do template {#creating-and-configuring-the-template}

Os templates de publicação são armazenados por padrão no nó **[!UICONTROL Administration > Configuration > Publication templates]**. Para criar um novo modelo, clique no botão **[!UICONTROL New]** acima da lista de templates.

Para configurar o template de publicação, preencha o nome do template (ou seja, a chave de identificação que consiste no nome e no namespace), seu rótulo, o schema de dados e o formulário de entrada ao qual ele está vinculado.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>O rótulo aparecerá sempre que o conteúdo for criado com base nesse template de publicação.

A opção **Verificar o status para validar a geração de conteúdo** força uma verificação do status &quot;Validado&quot; das instâncias de conteúdo para autorizar a geração de arquivo. Para obter mais informações, consulte [Publicação](#publication),

Um modelo de transformação deve ser adicionado para cada documento de saída. É possível criar quantos modelos de transformação forem necessários.

O campo **[!UICONTROL Name of template]** é um rótulo gratuito que descreve o tipo de renderização na saída. Para cada modelo de transformação, as configurações de publicação estão disponíveis nas guias.

### Renderização {#rendering}

Na guia **[!UICONTROL Rendering]**, escolha:

* o tipo de renderização usado para projetar o documento de saída: folha de estilo XSL ou template do JavaScript,
* o formato do documento de saída: HTML, Text, XML ou RTF,
* o template que contém os dados de construção, isto é, a folha de estilos ou template de JavaScript a ser utilizado.

### Publicação {#publication}

Se o tipo selecionado for **[!UICONTROL File]**, a publicação envolve a geração do documento de saída na forma de um arquivo.

![](assets/d_ncs_content_model2.png)

As seguintes opções de publicação estão disponíveis:

* O conjunto de caracteres de codificação do arquivo de saída pode ser forçado por meio do campo **[!UICONTROL Encoding]**. O conjunto de caracteres Latin 1 (1252) é usado por padrão.
* A opção **[!UICONTROL Multi-file generation]** ativa um modo de publicação de documento especial. Essa opção consiste em preencher uma tag de particionamento no início de cada página do documento de saída. A geração do conteúdo produzirá um arquivo para cada tag de particionamento preenchida. Esse modo é usado para gerar mini sites a partir de um bloco de conteúdo. Para obter mais informações, consulte [Geração de vários arquivos](#multi-file-generation).
* O campo **[!UICONTROL Location]** contém o nome do arquivo de saída. O nome pode ser composto de variáveis para gerar um nome de arquivo automático.

   Uma variável é preenchida com o seguinte formato: **`$(<xpath>)`**, onde **`<xpath>`** é o caminho de um campo do esquema de dados do modelo de publicação.

   O nome de um arquivo pode consistir em um campo tipo data. Para formatar corretamente esse campo, use a função **$date-format**, usando o caminho do campo e o formato de saída como parâmetros.

   Por padrão, o formato de construção do nome do arquivo usa as variáveis nos campos &quot;@name&quot; e &quot;@date&quot;:

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   O nome do arquivo gerado terá esta aparência: ct_news12_20110901.htm.

   >[!NOTE]
   >
   >Para obter mais informações sobre a geração de conteúdo, consulte [Criação de uma instância de conteúdo](../../delivery/using/using-a-content-template.md#creating-a-content-instance).

### Delivery {#delivery}

Essa guia permite selecionar um cenário para iniciar um delivery diretamente no conteúdo. O conteúdo do email será preenchido automaticamente com base no formato de saída (HTML ou Texto).

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>Para obter um exemplo de criação de delivery com base em um conteúdo, consulte [Delivery de uma Instância de Conteúdo](../../delivery/using/using-a-content-template.md#delivering-a-content-instance).

### Agregador {#aggregator}

Agregar os dados de um script ou lista de query permite enriquecer o documento XML com os dados de conteúdo. O objetivo é complementar determinadas informações referenciadas por links ou para adicionar elementos do banco de dados.

### Geração de vários arquivos {#multi-file-generation}

Para ativar a geração de múltiplos arquivos, selecione a opção **[!UICONTROL Multi-file generation]** no template de publicação. Essa opção permite especificar tags de particionamento na folha de estilos do início de cada página do documento de saída. A geração do conteúdo produzirá um arquivo para cada tag de particionamento encontrada.

A tag de particionamento a ser integrada na folha de estilos é a seguinte:

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** onde **`<name_of_file>`** é o nome de arquivo da página que deve ser gerada.

**Exemplo:** geração de vários arquivos usando o schema &quot;cus:book&quot;.

O princípio é gerar uma página principal listando os capítulos, com a possibilidade de exibir os detalhes do capítulo em uma página externa

![](assets/d_ncs_content_chunk.png)

A folha de estilos correspondente (&quot;cus:book.xsl&quot;) é como segue:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <xsl:for-each select="chapter">
            <li><a target="_blank" href="chapter{@id}.htm"><xsl:value-of select="@name"/></a></li>  
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

Uma segunda folha de estilos (&quot;cus:chapter.xsl&quot;) é necessária para gerar os detalhes dos capítulos:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Detail of a chapter -->
  <xsl:template match="chapter">
    <!-- Cut tag -->   
    <xsl:comment> #nl:output_replace($(path)/chapter<xsl:value-of select="@id"/>.htm)</xsl:comment>
    
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <xsl:value-of select="page" disable-output-escaping="yes"/>
      </body>
    </html>
  </xsl:template>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <xsl:apply-templates/>
   </xsl:template>
</xsl:stylesheet>
```

A tag de particionamento é preenchida no início da página a ser incluída no arquivo para gerar.

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

O nome do arquivo é construído com a variável **$(path)** contendo o caminho da publicação e **`<xsl:value-of select="@id" />`**, que corresponde ao identificador do capítulo no documento de entrada.

O modelo de publicação deve ser preenchido com as duas folhas de estilos &quot;cus:book.xsl&quot; e &quot;cus:chapter.xsl&quot;.

A opção **[!UICONTROL Multi-file generation]** deve estar ativa no template de transformação do capítulo:

![](assets/d_ncs_content_chunk2.png)

O campo **[!UICONTROL Location]** não é usado na geração de múltiplos arquivos, mas esse campo deve ser preenchido para evitar um erro ao publicar.
