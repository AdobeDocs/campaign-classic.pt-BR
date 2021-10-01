---
product: campaign
title: Recursos e princípios do gerenciador de conteúdo
description: Recursos e princípios do gerenciador de conteúdo
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '238'
ht-degree: 100%

---

# Recursos e princípios do gerenciador de conteúdo{#content-manager-resources-and-principles}

![](../../assets/common.svg)

É necessário definir um template de publicação, que contenha modelos de transformação para cada conteúdo.

Um bloco de conteúdo é estruturado em um documento XML para armazenamento de dados. Uma interface de edição é usada para inserir o conteúdo do console do cliente Adobe Campaign ou através de um navegador da Web. O conteúdo também pode ser inserido automaticamente via captura de fluxo XML ou dados agregados em um banco de dados.

Combinar o documento XML e as folhas de estilos de template XSL ou JavaScript gera automaticamente a projeção do template de publicação em vários formatos (HTML, texto).

![](assets/d_ncs_content_process.png)

Os seguintes recursos são necessários para a configuração de conteúdo:

* Schemas de dados: descrição da estrutura de conteúdo XML. Para obter mais informações, consulte [Schemas de dados](data-schemas.md).
* Formulários de entrada de dados: construção de telas de entrada de dados. Para obter mais informações, consulte [Formulários de entrada](input-forms.md).
* Imagens: imagens usadas em formulários de entrada de dados. Para obter mais informações, consulte [Gestão de imagens](formatting.md#image-management).
* Folhas de estilos: formatação de documentos de saída usando a linguagem XSLT. Para obter mais informações, consulte [Formatação](formatting.md).
* Templates JavaScript: formatação de documentos de saída usando a linguagem JavaScript. Para obter mais informações, consulte [Templates de publicação](publication-templates.md).
* Códigos JavaScript: códigos JavaScript para agregação de dados. Para obter mais informações, consulte [Agregador](publication-templates.md#aggregator).
* Templates de publicação: definição de templates de publicação. Para obter mais informações, consulte [Templates de publicação](publication-templates.md).
* Conteúdo: instâncias de conteúdo a serem criadas e publicadas. Para obter mais informações, consulte [Uso de um template de conteúdo](using-a-content-template.md).
