---
title: Download da Web
seo-title: Download da Web
description: Download da Web
seo-description: null
page-status-flag: never-activated
uuid: 44039e9c-0cd8-4d3f-b73f-e01c5343835a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 8590cc75-11c8-450d-90e8-56744e12ac70
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 75%

---


# Download da Web{#web-download}

A atividade de **download da Web** inicia o download de um arquivo em uma URL explícita, uma conta externa ou uma instância do Adobe Campaign. O protocolo HTTP é usado. Isso pode ser um download GET ou POST.

## Propriedades {#properties}

1. **Seleção do arquivo Web**

   Para especificar o arquivo a ser baixado, você pode inserir a URL do arquivo, usar a conta HTTP externa onde o arquivo está armazenado ou carregar o arquivo por meio de uma instância do Adobe Campaign. Os parâmetros disponíveis são detalhados abaixo:

   * Para inserir diretamente a URL do arquivo a ser baixado, selecione a opção **[!UICONTROL Explicit URL]** e especifique a URL no campo apropriado. Esta URL pode ser construída com dados variáveis.

      ![](assets/download_web_edit.png)

   * Para usar uma **[!UICONTROL External account]**, selecione a conta na lista suspensa e especifique o arquivo a ser baixado.

      External accounts are configured from the **[!UICONTROL Administration > Platform > External accounts]** node of the Adobe Campaign tree. Os parâmetros da conta podem ser editados por meio do ícone **[!UICONTROL Edit link]**.

      ![](assets/download_web_edit_external.png)

   * To download the file from the Adobe Campaign instance, select the **[!UICONTROL Adobe Campaign Instance]** option.

      ![](assets/download_web_edit_instance.png)

1. **Historização de arquivo**

   The **[!UICONTROL File historization settings...]** link lets you specify the file storage directory and the purge frequency of this directory.

   ![](assets/download_web_edit_hist.png)

   As seguintes opções estão disponíveis:

   * **[!UICONTROL Use a default storage directory]**: o arquivo é sempre movido antes de ser processado. Se essa opção estiver marcada, o arquivo será movido para o diretório de armazenamento padrão (o diretório **vars** da pasta de instalação do Adobe Campaign). Para especificar um diretório de armazenamento, desmarque a caixa e digite seu caminho no campo **[!UICONTROL Storage directory]**
   * **[!UICONTROL Number of files]**: digite o número máximo de arquivos a serem mantidos no diretório de armazenamento.
   * **[!UICONTROL Maximum size (in Mb)]**: digite a capacidade máxima do diretório do armazenamento (em megabytes).
   Todo arquivo é mantido por 24 horas antes de ser sujeito às regras de limpeza definidas. A limpeza ocorre antes do início da atividade e, portanto, não leva em consideração o arquivo do workflow em andamento.

   Os arquivos são excluídos em função de sua data de criação (mais antiga a mais recente). Os arquivos mais antigos são limpos até que ambas as regras de limpeza sejam verificadas. Portanto, se um limite 100 arquivos for definido, isso significa que o diretório de armazenamento sempre conterá os 100 arquivos mais recentes antes do início do workflow, bem como aqueles que estão sendo processados no workflow em andamento.

   If you no longer want to set a limit for the **[!UICONTROL Number of files]** and **[!UICONTROL Maximum size (in Mb)]** options, enter 0 as a value.

1. **Parâmetros avançados**

   The **[!UICONTROL Advanced parameters...]** link lets you specify the additional options shown below:

   ![](assets/download_web_edit_advanced.png)

   The **[!UICONTROL Process errors]** option is detailed in [Processing errors](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Parâmetros de output {#output-parameters}

* nome do arquivo: Nome completo do arquivo baixado.
