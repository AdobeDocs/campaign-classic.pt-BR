---
title: Recursos e princípios do gerenciador de conteúdo
seo-title: Recursos e princípios do gerenciador de conteúdo
description: Recursos e princípios do gerenciador de conteúdo
seo-description: null
page-status-flag: never-activated
uuid: 3560e392-129a-471d-a211-05481cdda224
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: b22b3abb-6fe5-4f4d-93fc-0d00d426edb6
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Recursos e princípios do gerenciador de conteúdo{#content-manager-resources-and-principles}

É necessário definir um template de publicação, que contenha modelos de transformação para cada conteúdo.

Um bloco de conteúdo é estruturado em um documento XML para armazenamento de dados. Uma interface de edição é usada para inserir o conteúdo do console do cliente Adobe Campaign ou através de um navegador da Web. O conteúdo também pode ser inserido automaticamente via captura de fluxo XML ou dados agregados em um banco de dados.

Combinar o documento XML e as folhas de estilos de template XSL ou JavaScript gera automaticamente a projeção do template de publicação em vários formatos (HTML, texto).

![](assets/d_ncs_content_process.png)

Os seguintes recursos são necessários para a configuração de conteúdo:

* Schemas de dados: descrição da estrutura de conteúdo XML. Para obter mais informações, consulte [Schemas de dados](../../delivery/using/data-schemas.md).
* Formulários de entrada de dados: construção de telas de entrada de dados. Para obter mais informações, consulte [Formulários de entrada](../../delivery/using/input-forms.md).
* Imagens: imagens usadas em formulários de entrada de dados. Para obter mais informações, consulte [Gestão de imagens](../../delivery/using/formatting.md#image-management).
* Folhas de estilos: formatação de documentos de saída usando a linguagem XSLT. Para obter mais informações, consulte [Formatação](../../delivery/using/formatting.md).
* Templates JavaScript: formatação de documentos de saída usando a linguagem JavaScript. Para obter mais informações, consulte [Templates de publicação](../../delivery/using/publication-templates.md).
* Códigos JavaScript: códigos JavaScript para agregação de dados. Para obter mais informações, consulte [Agregador](../../delivery/using/publication-templates.md#aggregator).
* Templates de publicação: definição de templates de publicação. Para obter mais informações, consulte [Templates de publicação](../../delivery/using/publication-templates.md).
* Conteúdo: instâncias de conteúdo a serem criadas e publicadas. Para obter mais informações, consulte [Uso de um template de conteúdo](../../delivery/using/using-a-content-template.md).
