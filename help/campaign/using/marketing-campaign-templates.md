---
title: Modelos de campanha de marketing
seo-title: Modelos de campanha de marketing
description: Modelos de campanha de marketing
seo-description: Modelos de campanha de marketing
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Modelos de Campanha de marketing {#campaign-templates}

Os modelos de campanha estão centralizados no **[!UICONTROL Resources > Templates > Campaign templates]** nó. Um template de parâmetro é fornecido como padrão. Ele permite criar uma nova campanha usando todos os módulos disponíveis (Documentos, tarefas, seed addresses, etc.), mas os módulos oferecidos dependem dos seus direitos e da configuração da plataforma Adobe Campaign.

## Criar ou duplicar um template de campanha {#creating-or-duplicating-a-campaign-template}

Para criar um novo template, execute as seguintes etapas:

1. Abra o **Gerenciador** de Campanha.
1. Em **Resources > Templates > Campaign templates**, clique em **New** na barra de ferramentas acima da lista de templates.

   ![](assets/create_campaign_template_1.png)

1. Insira o rótulo do seu novo template de campanha.
1. Clique em **Save** e abra seu template novamente.
1. Na guia **Edit**, insira o **Internal name** e outros valores, caso seja necessário.
1. Selecione **Advanced campaign settings** para adicionar um workflow ao seu template de campanha.

   ![](assets/create_campaign_template_2.png)

1. Altere o valor de **Targeting and workflows** para **Yes**.

   ![](assets/create_campaign_template_3.png)

1. Na guia **Targeting and workflows**, clique em **Add a workflow...**.

   ![](assets/create_campaign_template_4.png)

1. Complete o campo **Label** e clique em **Ok**.
1. Crie o workflow de acordo com suas necessidades.
1. Clique em **Save**. Agora, seu template está pronto para ser usado em uma campanha.

Você também pode duplicar o template padrão para reutilizar e adaptar a configuração.

The various tabs and sub-tabs of the campaign template allow you to access its settings, described in [General configuration](#general-configuration).

![](assets/s_ncs_user_new_op_template_duplicate.png)

## Configuração de um template de campanha {#configuring-a-campaign-template}

As campanhas são baseadas em modelos que compartilham um conjunto de parâmetros predefinidos.

In a default configuration, the campaign templates are centralized in the **[!UICONTROL Resources > Templates > Campaign templates]** node of the Adobe Campaign tree.

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>The tree is displayed when you click the **[!UICONTROL Explorer]** icon on the home page.

Um modelo predefinido é fornecido para criar uma campanha para a qual nenhuma configuração específica foi definida. Você pode criar e configurar seus templates de campanha e, em seguida, criar campanhas a partir desses templates.

The creation and configuration of campaign templates are presented in [Campaign templates](#campaign-templates).

Para obter mais informações sobre a criação da campanha, consulte o vídeo [Criação de uma campanha e de um e-mail](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html).

## Configuração dos módulos disponíveis {#configuration-of-the-available-modules}

### Seleção do módulo {#module-selection}

The **[!UICONTROL Advanced campaign settings...]** link lets you enable and disable jobs for the campaigns based on this template. Selecione as funções que deseja habilitar nas campanhas criadas com base neste template.

![](assets/s_ncs_user_op_template_tab1.3.png)

Se uma funcionalidade não estiver selecionada, os elementos relativos ao processo (menus, ícones, opções, guias, subguias etc.) não aparecerão na interface do template ou em campanhas baseadas nesse template. As guias à esquerda dos detalhes da campanha geralmente coincidem com os processos selecionados no template. For example, if **Expenses and objectives** is not selected, the corresponding **[!UICONTROL Budget]** tab will not be shown in campaigns based on this template.

Além disso, os atalhos para as janelas de configuração são adicionados ao painel de campanha. Quando uma funcionalidade é habilitada, um link direto dá acesso a ela a partir do painel de campanha.

Por exemplo, com a configuração abaixo:

![](assets/s_ncs_user_op_template_tab1.4.png)

The following links are displayed in the campaign dashboard (the **[!UICONTROL Add a task]** link is missing):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

E somente as seguintes guias serão exibidas:

![](assets/s_ncs_user_op_template_tab1.4ex.png)

No entanto, com esse tipo de configuração:

![](assets/s_ncs_user_op_template_tab2.2ex.png)

Os links e as guias a seguir serão exibidos:

![](assets/s_ncs_user_op_template_tab2.3ex.png)

### Tipologia de módulos habilitados {#typology-of-enabled-modules}

* **Grupo de controle**

   Quando este módulo está selecionado, uma guia adicional é adicionada às configurações avançadas do template e às campanhas baseadas nesse template. A configuração pode ser definida por meio do template ou individualmente para cada campanha.

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **Seed addresses**

   Quando este módulo está selecionado, uma guia adicional é adicionada às configurações avançadas do template e às campanhas baseadas nesse template. A configuração pode ser definida por meio do template ou individualmente para cada campanha.

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **Documentos**

   When this module is selected, an additional tab is added to the **[!UICONTROL Edition]** tab of the template and the campaigns based on this template. Os documentos anexados podem ser adicionados a partir do template ou individualmente para cada campanha.

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **Estrutura**

   When this module is selected, a **[!UICONTROL Delivery outlines]** sub-tab is added to the **[!UICONTROL Documents]** tab in order to define delivery outlines for the campaign.

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **Construção do target e workflows**

   When you select the **[!UICONTROL Targeting and workflows]** module, a tab is added to let you create one or more workflows for campaigns based on this template. Os workflows também podem ser configurados individualmente para cada campanha com base nesse template.

   ![](assets/s_ncs_user_op_template_activate_5.png)

   Quando este módulo é habilitado, uma guia é adicionada às configurações avançadas da campanha para definir a sequência de execução do processo.

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **Aprovação**

   If you select the **[!UICONTROL Approval]**, you can select the processes to approve as well as the operators in charge of approvals.

   ![](assets/s_ncs_user_op_template_activate_5b.png)

* **Despesas e metas**

   When this module is selected, a **[!UICONTROL Budget]** tab is added to the details of the template and campaigns based on this template so that the associated budget can be selected.

   ![](assets/s_ncs_user_op_template_activate_7.png)

### Aprovação de tarefas {#approval-of-jobs}

You may choose whether or not to enable process approval via the **[!UICONTROL Approvals]** tab of the templates advanced settings section. As tarefas para as quais a aprovação é selecionada devem ser aprovadas para que o delivery de mensagens seja autorizado.

Você deve associar um operador de revisor ou grupo de operadores a cada aprovação habilitada.

## Configuração geral {#general-configuration}

### Propriedades do template {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

Ao criar um template de campanha, você precisa inserir as seguintes informações:

* Insira o **rótulo** do template: este rótulo será atribuído por padrão para todas as campanhas criadas através deste template.
* Selecione a **natureza** da campanha na lista suspensa. The values available in this list are those saved in the **[!UICONTROL natureOp]** enumeration.

   >[!NOTE]
   >
   >Para obter mais informações sobre enumerações, consulte a seção [Introdução](../../platform/using/managing-enumerations.md).

* Selecione o **tipo de campanha**: exclusiva, recorrente ou periódica. Por padrão, os templates de campanha se aplicam a campanhas exclusivas. As campanhas recorrentes e periódicas são detalhadas aqui: Campanhas [recorrentes e periódicas](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns).
* Especifique a duração da campanha, ou seja, o número de dias em que a campanha ocorrerá. Ao criar uma campanha com base nesse template, as datas de início e término da campanha serão preenchidas automaticamente.

   Se a campanha for recorrente, você deverá especificar as datas de início e término da campanha diretamente no template.

* Especifique o **programa relacionado** do template: campanhas baseadas neste template serão vinculadas ao programa selecionado.

### Parâmetros de execução do template {#template-execution-parameters}

O **[!UICONTROL Advanced campaign settings...]** link permite configurar as opções avançadas do modelo para processar o destino de entrega (grupo de controle, endereços semente etc.) e a configuração da medição da campanha e da execução do fluxo de trabalho.

![](assets/s_ncs_user_op_template_tab1.2.png)

## Programação reversa de campanha {#campaign-reverse-scheduling}

Você pode criar uma agenda reversa para uma campanha, por exemplo, para preparar um evento cuja data é conhecida antecipadamente. Os templates de campanha agora permitem calcular a data de início de uma tarefa com base na data de término de uma campanha.

Na caixa de configuração da tarefa, vá para a **[!UICONTROL Implementation schedule]** área e marque a **[!UICONTROL The start date is calculated based on the campaign end date]** caixa. (Aqui, &quot;start date&quot; é a data de início da tarefa). Go to the **[!UICONTROL Start]** field and enter an interval: the task will start this long before the campaign end date. Se você inserir um período mais longo do que a campanha deve durar, a tarefa começará antes da campanha.

![](assets/mrm_task_in_template_start_date.png)

Quando você cria uma campanha usando este template, a data de início da tarefa será calculada automaticamente. No entanto, você sempre pode alterá-lo mais tarde.
