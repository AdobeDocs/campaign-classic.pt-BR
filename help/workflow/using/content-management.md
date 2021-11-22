---
product: campaign
title: Gestão de conteúdo
description: Gestão de conteúdo
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 100%

---

# Gestão de conteúdo{#content-management}

![](../../assets/common.svg)

Uma atividade de **Gestão de conteúdo** permite criar e manipular um conteúdo e gerar arquivos com base nesse conteúdo. Esse conteúdo pode ser entregue por meio de uma atividade de &#39;Delivery&#39;.

>[!CAUTION]
>
>A gestão de conteúdo é um módulo opcional do Adobe Campaign. Verifique o contrato de licença.

As propriedades da atividade são divididas em três etapas:

* **Seleção de conteúdo**: o conteúdo pode ter sido criado anteriormente ou pode ser criado através da atividade.
* **Atualização de conteúdo**: a tarefa pode modificar o assunto do conteúdo ou importar todo o conteúdo XML.
* **Ação**: o conteúdo resultante pode ser salvo ou gerado.

   ![](assets/content_mgmt_edit.png)

   Para obter mais informações sobre como configurar e usar a gestão de conteúdo no Adobe Campaign, consulte esta [seção](../../delivery/using/about-content-management.md).

1. **Conteúdo**

   * **[!UICONTROL Specified in the transition]**

      Essa opção permite usar o conteúdo especificado na transição, ou seja, o evento que ativa o gerenciamento de conteúdo deve conter uma variável **[!UICONTROL contentId]**. Essa variável pode ter sido definida por uma gestão de conteúdo anterior ou por qualquer script.

   * **[!UICONTROL Explicit]**

      Essa opção permite selecionar um conteúdo já criado, por meio do campo **[!UICONTROL Content]**. Este campo fica visível somente quando a opção **[!UICONTROL Explicit]** é selecionada.

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      O identificador de conteúdo é calculado por um script. O campo **[!UICONTROL Script]** permite definir um template JavaScript avaliando o identificador (chave primária) do conteúdo. Este campo fica visível somente quando a opção **[!UICONTROL Calculated by a script]** é selecionada.

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      Cria um novo conteúdo a partir de um template de publicação. Esse novo conteúdo será salvo no arquivo especificado no campo **[!UICONTROL String]**. O campo **[!UICONTROL Template]** especifica o template de publicação a ser usado para criar o conteúdo.

      ![](assets/content_mgmt_new.png)

1. **Atualização de conteúdo**

   * **[!UICONTROL Subject]**

      Este campo permite modificar o assunto do conteúdo.

   * **[!UICONTROL Access to data from an XML feed]**

      Essa opção permite construir o conteúdo de um documento XML baixado por meio de uma folha de estilos XSL. Quando essa opção é selecionada, o campo **[!UICONTROL URL]** especifica a URL de download de conteúdo XML. A **[!UICONTROL XSL stylesheet]** permite que você especifique a folha de estilos a ser usada para transformar o documento XML baixado. Esse campo é opcional.

      ![](assets/content_mgmt_xmlcontent.png)

1. **Ação a ser executada**

   * **[!UICONTROL Save]**

      Essa opção salva o conteúdo criado ou modificado.

      A transição de saída é ativada apenas uma vez, com o conteúdo salvo na variável **[!UICONTROL contentId]** como um parâmetro.

   * **[!UICONTROL Generate]**

      Essa opção salva o conteúdo e gera os arquivos de output para cada template de transformação com uma publicação de tipo &#39;Arquivo&#39;.

      ![](assets/content_mgmt_generate.png)

      A transição de saída é ativada para cada arquivo gerado com o identificador do conteúdo salvo na variável **[!UICONTROL contentId]** como seu parâmetro e o nome do arquivo na variável **[!UICONTROL filename]**.

## Parâmetros de entrada {#input-parameters}

* contentId

Identificador do conteúdo a ser usado se a opção **[!UICONTROL Specified in the transition]** estiver habilitada.

## Parâmetros de saída {#output-parameters}

* contentId

   Identificador de conteúdo.

* filename

   Nome completo do arquivo gerado se a ação selecionada for **[!UICONTROL Generate]**.

## Exemplos {#examples}

Os exemplos são apresentados nesta [seção](../../delivery/using/automating-via-workflows.md#examples).
