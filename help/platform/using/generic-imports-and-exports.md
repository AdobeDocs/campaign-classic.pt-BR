---
title: Importações e exportações genéricas
seo-title: Importações e exportações genéricas
description: Importações e exportações genéricas
seo-description: null
page-status-flag: never-activated
uuid: e98753bb-1f14-4ec7-aa3b-d5e4f1ebaef7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: a21576c7-e94c-4fe1-9e31-d89116e427f6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 80%

---


# Importações e exportações genéricas{#generic-imports-and-exports}

O Adobe Campaign oferece um módulo de exportação de dados que facilita a extração de uma lista de clientes ou clientes potenciais (por exemplo, seguindo uma operação de definição de públicos-alvo) que se tornará parte de um público-alvo.

O Adobe Campaign também oferece um módulo de importação que permite fornecer o banco de dados com dados de arquivos externos.

>[!NOTE]
>
>As exportações e importações são configuradas em modelos dedicados executados através de workflows por meio das atividades de **[!UICONTROL Import]** e **[!UICONTROL Export]**. Elas podem ser repetidas automaticamente de acordo com um agendamento, por exemplo, para automatizar a troca de dados entre vários sistemas de informações. If necessary, you can create an occasional import or export via the **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** node of the Adobe Campaign tree.

É possível:

* Criar um modelo de importação ou exportação e configurá-lo (veja abaixo).
* Criar uma importação ou exportação: consulte [Exportação de dados](../../platform/using/exporting-data.md) ou [Importação de dados](../../platform/using/importing-data.md).
* Iniciar a importação ou exportação e monitorar sua execução. consulte [Rastreio de execução](#execution-tracking).

>[!CAUTION]
>
>A importação de dados no Campaign deve ser realizada por meio de fluxos de trabalho para garantir a consistência dos dados e melhorar a eficiência. Para mais informações, consulte as seções [Importação de dados](../../workflow/using/importing-data.md), [Práticas recomendadas de importação](../../workflow/using/importing-data.md#best-practices-when-importing-data) e [Exemplo de template de importação](../../workflow/using/importing-data.md#setting-up-a-recurring-import).

## Criação de um template de trabalho {#creating-a-job-template}

Import and export templates are stored in the **[!UICONTROL Resources > Templates > Job templates]** directory of the Adobe Campaign tree.

![](assets/s_ncs_user_export_wizard_template.png)

Por padrão, três templates de importação e um template de exportação estão presentes nesse diretório. Eles não devem ser modificados. You can duplicate them to create your own templates or create a new template via the **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** menu.

![](assets/s_ncs_user_export_wizard_template_create.png)

O procedimento para criação de um modelo de processo é apresentado no [Assistente de exportação](../../platform/using/exporting-data.md#export-wizard) e [Assistente de importação](../../platform/using/importing-data.md#import-wizard).

>[!NOTE]
>
>O modelo nativo já **[!UICONTROL Import block list]** está configurado para importar uma lista de endereços de email que foram adicionados à lista de bloqueios.
> 
>The **[!UICONTROL New text import]** and **[!UICONTROL New text export]** templates let you configure an import or export from scratch.

## Criação de uma nova importação/exportação {#creating-a-new-import-export}

Após a configuração do modelo, as operações de importação e exportação podem ser iniciadas em vários contextos no Adobe Campaign.

Todos abrem o assistente de [importação](../../platform/using/importing-data.md) ou [exportação](../../platform/using/exporting-data.md#export-wizard).

* Na seção **[!UICONTROL Profiles and targets]** do espaço de trabalho do Adobe Campaign, clique no link **[!UICONTROL Jobs]**: isso permitirá o acesso à lista de importações e exportações existentes.

   Clique no botão **[!UICONTROL Create]** e selecione o tipo de trabalho que deseja executar.

   ![](assets/s_ncs_user_import_from_home.png)

* Além disso, é possível iniciar importações e exportações na seção Supervision do espaço de trabalho: dois links dedicados permitem que você inicie a importação ou exportação diretamente.

   ![](assets/s_ncs_user_import_from_production.png)

* Importações e exportações também podem ser iniciadas no gerenciador do Adobe Campaign.

   To export/import data, click the **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** node, then the **[!UICONTROL New]** icon, and select **[!UICONTROL Export]** or **[!UICONTROL Import]**. Isso abre o assistente apropriado.

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## Rastreamento da execução {#execution-tracking}

É possível exibir o rastreamento da execução na seção superior deste editor. Para fechar o assistente de exportação e exibir a execução do trabalho, use a lista de trabalhos de importação/exportação.

![](assets/s_ncs_user_export_list_and_details.png)

* A guia **[!UICONTROL Log]** permite visualizar mensagens de log relacionadas à execução.
* A guia **[!UICONTROL Rejects]** contém os registros rejeitados. Consulte o [Comportamento no caso de um erro](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error)

>[!NOTE]
>
>Os status do trabalho de importação/exportação são apresentados em [Job statuses](../../platform/using/importing-data.md#job-statuses).

