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
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Download da Web{#web-download}

A atividade de **download da Web** inicia o download de um arquivo em uma URL explícita, uma conta externa ou uma instância do Adobe Campaign. O protocolo HTTP é usado. Isso pode ser um download GET ou POST.

## Propriedades {#properties}

1. **Seleção do arquivo Web**

   Para especificar o arquivo a ser baixado, você pode inserir a URL do arquivo, usar a conta HTTP externa onde o arquivo está armazenado ou carregar o arquivo por meio de uma instância do Adobe Campaign. Os parâmetros disponíveis são detalhados abaixo:

   * To directly enter the URL of the file to be downloaded, select the **[!UICONTROL Explicit URL]** option and specify the URL in the appropriate field. Esta URL pode ser construída com dados variáveis.

      ![](assets/download_web_edit.png)

   * To use an **[!UICONTROL External account]**, select the account from the drop-down list, and specify the file to be downloaded.

      External accounts are configured from the **[!UICONTROL Administration > Platform > External accounts]** node of the Adobe Campaign tree. The account parameters can be edited via the **[!UICONTROL Edit link]** icon.

      ![](assets/download_web_edit_external.png)

   * To download the file from the Adobe Campaign instance, select the **[!UICONTROL Adobe Campaign Instance]** option.

      ![](assets/download_web_edit_instance.png)

1. **Historização de arquivo**

   The **[!UICONTROL File historization settings...]** link lets you specify the file storage directory and the purge frequency of this directory.

   ![](assets/download_web_edit_hist.png)

   As seguintes opções estão disponíveis:

   * **[!UICONTROL Use a default storage directory]**: o arquivo é sempre movido antes de ser processado. Se essa opção estiver marcada, o arquivo será movido para o diretório de armazenamento padrão (o diretório **vars** da pasta de instalação do Adobe Campaign). To specify a storage directory, uncheck the box and enter its path in the **[!UICONTROL Storage directory]** field
   * **[!UICONTROL Number of files]**: digite o número máximo de arquivos a serem mantidos no diretório de armazenamento.
   * **[!UICONTROL Maximum size (in Mb)]**: informe a capacidade máxima do diretório de armazenamento (em megabytes).
   Todo arquivo é mantido por 24 horas antes de ser sujeito às regras de limpeza definidas. A limpeza ocorre antes do início da atividade e, portanto, não leva em consideração o arquivo do workflow em andamento.

   Os arquivos são excluídos em função de sua data de criação (mais antiga a mais recente). Os arquivos mais antigos são limpos até que ambas as regras de limpeza sejam verificadas. Portanto, se um limite 100 arquivos for definido, isso significa que o diretório de armazenamento sempre conterá os 100 arquivos mais recentes antes do início do workflow, bem como aqueles que estão sendo processados no workflow em andamento.

   If you no longer want to set a limit for the **[!UICONTROL Number of files]** and **[!UICONTROL Maximum size (in Mb)]** options, enter 0 as a value.

1. **Parâmetros avançados**

   The **[!UICONTROL Advanced parameters...]** link lets you specify the additional options shown below:

   ![](assets/download_web_edit_advanced.png)

   A **[!UICONTROL Process errors]** opção é detalhada em Erros [de](../../workflow/using/monitoring-workflow-execution.md#processing-errors)processamento.

## Parâmetros de output {#output-parameters}

* filename

   Nome completo do arquivo baixado.

