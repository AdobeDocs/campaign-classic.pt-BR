---
title: Geração de documentos personalizados em PDF
seo-title: Geração de documentos personalizados em PDF
description: Geração de documentos personalizados em PDF
seo-description: null
page-status-flag: never-activated
uuid: d4c27523-bff3-457a-ba60-e2747a2b3166
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 8dfc5e7c-c762-46ba-bbda-a7251354cb47
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Geração de documentos personalizados em PDF{#generating-personalized-pdf-documents}

## Sobre documentos PDF variáveis {#about-variable-pdf-documents}

O Adobe Campaign permite gerar documentos variáveis em PDF (para anexos de email, delivery de mala direta) de documentos do LibreOffice ou do Microsoft Word.

As seguintes extensões são suportadas: &quot;.docx&quot;, &quot;.doc&quot; e &quot;.odt&quot;.

Para personalizar seus documentos, as mesmas funcionalidades JavaScript de personalização de email estão disponíveis.

É necessário ativar a **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** opção. Essa opção é acessível quando você anexa o arquivo ao email de delivery. For more on attaching a calculated file, refer to the [Attaching files](../../delivery/using/attaching-files.md) section.

Exemplo de personalização de cabeçalho de fatura:

![](assets/s_ncs_pdf_simple.png)

Para gerar tabelas dinâmicas ou incluir imagens via URL, você precisa seguir um processo específico.

## Geração de tabelas dinâmicas {#generating-dynamic-tables}

O procedimento para gerar tabelas dinâmicas é da seguinte maneira:

* Crie uma tabela com três linhas e quantas colunas forem necessárias, então configure seu layout (bordas, etc.).
* Coloque o cursor na tabela e clique no **[!UICONTROL Table > Table properties]** menu. Go to the **[!UICONTROL Table]** tab and enter a name beginning with **NlJsTable**.
* Na primeira célula da primeira linha, defina um loop (&quot;para&quot;, por exemplo) que permite a iteração nos valores que você deseja exibir na tabela.
* Em cada célula da segunda linha da tabela, insira os scripts que retornam os valores para exibição.
* Feche o loop na terceira e última linha da tabela.

   Exemplo de definição de tabela dinâmica:

   ![](assets/s_ncs_pdf_table.png)

## Inserir imagens externas {#inserting-external-images}

A inserção de imagens externas é útil se, por exemplo, você deseja personalizar um documento com uma imagem cujo URL é inserido em um campo do recipient.

Para fazer isso, você precisa configurar um bloco de personalização e, em seguida, incluir uma chamada para o bloco de personalização no anexo.

**Exemplo: inserir um logotipo personalizado de acordo com o país do recipient**

**Etapa 1: criar o anexo:**

* Insira a chamada para o bloco de personalização: **&lt;%@ include view=&quot;blockname&quot; %>**.
* Insira seu conteúdo (personalizado ou não) no corpo do arquivo.

![](assets/s_ncs_open_office_blocdeperso.png)

**Etapa 2: criar o bloco de personalização:**

* Vá para o **[!UICONTROL Resources > Campaign management > Personalization blocks]** menu do console do Adobe Campaign.
* Crie um novo bloco de personalização &quot;Meu logotipo&quot; com &quot;Meu_Logotipo&quot; como um nome interno.
* Clique no **[!UICONTROL Advanced parameters...]** link e marque a **[!UICONTROL "The content of the block is included in an attachment"]** opção. Isso permite copiar a definição do bloco de personalização diretamente para o conteúdo do arquivo OpenOffice.

   ![](assets/s_ncs_pdf_bloc_option.png)

   Você precisa diferenciar dois tipos de declarações no bloco de personalização:

   * The Adobe Campaign code of the personalization fields for which the &quot;open&quot; and &quot;closed&quot; chevrons must be replaced with escape characters (respectively `&lt;` and `&gt;`).
   * O código OpenOffice XML inteiro será copiado para o documento OpenOffice.

No exemplo, o bloco de personalização tem esta aparência:

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

Dependendo do país do recipient, a personalização fica visível no documento vinculado ao delivery:

![](assets/s_ncs_pdf_result.png)
