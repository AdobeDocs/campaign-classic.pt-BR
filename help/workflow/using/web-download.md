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
translation-type: ht
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Download da Web{#web-download}

A atividade de **download da Web** inicia o download de um arquivo em uma URL explícita, uma conta externa ou uma instância do Adobe Campaign. O protocolo HTTP é usado. Isso pode ser um download GET ou POST.

## Propriedades {#properties}

1. **Seleção do arquivo Web**

   Para especificar o arquivo a ser baixado, você pode inserir a URL do arquivo, usar a conta HTTP externa onde o arquivo está armazenado ou carregar o arquivo por meio de uma instância do Adobe Campaign. Os parâmetros disponíveis são detalhados abaixo:

   * Para inserir diretamente a URL do arquivo a ser baixado, selecione a opção **[!UICONTROL Explicit URL]** e especifique a URL no campo apropriado. Esta URL pode ser construída com dados variáveis.

      ![](assets/download_web_edit.png)

   * Para usar uma **[!UICONTROL External account]**, selecione a conta na lista suspensa e especifique o arquivo a ser baixado.

      Contas externas são configuradas no nó **[!UICONTROL Administration > Platform > External accounts]** da árvore do Adobe Campaign. Os parâmetros da conta podem ser editados por meio do ícone **[!UICONTROL Edit link]**.

      ![](assets/download_web_edit_external.png)

   * Para baixar o arquivo da instância do Adobe Campaign, selecione a opção **[!UICONTROL Adobe Campaign Instance]**.

      ![](assets/download_web_edit_instance.png)

1. **Historização de arquivo**

   O link **[!UICONTROL File historization settings...]** permite especificar o diretório de armazenamento de arquivos e a frequência de limpeza desse diretório.

   ![](assets/download_web_edit_hist.png)

   As seguintes opções estão disponíveis:

   * **[!UICONTROL Use a default storage directory]**: o arquivo é sempre movido antes de ser processado. Se essa opção estiver marcada, o arquivo será movido para o diretório de armazenamento padrão (o diretório **vars** da pasta de instalação do Adobe Campaign). Para especificar um diretório de armazenamento, desmarque a caixa e digite seu caminho no campo **[!UICONTROL Storage directory]**
   * **[!UICONTROL Number of files]**: digite o número máximo de arquivos a serem mantidos no diretório de armazenamento.
   * **[!UICONTROL Maximum size (in Mb)]**: digite a capacidade máxima do diretório de armazenamento (em megabytes).
   Todo arquivo é mantido por 24 horas antes de ser sujeito às regras de limpeza definidas. A limpeza ocorre antes do início da atividade e, portanto, não leva em consideração o arquivo do workflow em andamento.

   Os arquivos são excluídos em função de sua data de criação (mais antiga a mais recente). Os arquivos mais antigos são limpos até que ambas as regras de limpeza sejam verificadas. Portanto, se um limite 100 arquivos for definido, isso significa que o diretório de armazenamento sempre conterá os 100 arquivos mais recentes antes do início do workflow, bem como aqueles que estão sendo processados no workflow em andamento.

   Se você não quiser mais definir um limite para as opções **[!UICONTROL Number of files]** e **[!UICONTROL Maximum size (in Mb)]**, digite 0 como um valor.

1. **Parâmetros avançados**

   O link **[!UICONTROL Advanced parameters...]** permite especificar as seguintes opções adicionais:

   ![](assets/download_web_edit_advanced.png)

   A opção **[!UICONTROL Process errors]** é detalhada em [Processamento de erros](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Parâmetros de output {#output-parameters}

* filename

   Nome completo do arquivo baixado.

