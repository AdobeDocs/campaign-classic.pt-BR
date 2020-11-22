---
solution: Campaign Classic
product: campaign
title: Recursos e princípios do gerenciador de conteúdo
description: Recursos e princípios do gerenciador de conteúdo
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 100%

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
