---
title: Campos de personalização
seo-title: Campos de personalização
description: Campos de personalização
seo-description: null
page-status-flag: never-activated
uuid: 3a94a50e-259e-40c3-ae67-8a2c42e9fad7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 27c8e443-ee6b-4d58-bc2d-81cf8391c5de
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f5062117b5cefbdd2570018f6803f114c14a3fae

---


# Campos de personalização{#personalization-fields}

Os campos de personalização são usados para personalização de primeiro nível do conteúdo das mensagens de delivery. Os campos que você insere em um conteúdo principal mostram onde inserir os dados da fonte de dados selecionada.

Por exemplo, o campo de personalização com a sintaxe **&lt;%= recipient.LastName %>** informa ao Adobe Campaign para inserir o nome do recipient no banco de dados (tabela de recipients).

>[!NOTE]
>
>O conteúdo dos campos de personalização não pode exceder 1024 caracteres.

## Fontes de Dados {#data-sources}

Os campos de personalização podem vir de dois tipos de fonte de dados, de acordo com o modo de delivery selecionado:

* O banco de dados do Adobe Campaign é a fonte de dados. Este é o caso mais comum, com, por exemplo, &#39;campos de personalização de recipient&#39;. Esses são todos os campos definidos na tabela de recipients, sejam os campos padrão (normalmente: sobrenome, nome, endereço, cidade, data de nascimento, etc.) ou campos definidos pelo usuário.
* Um arquivo externo é a fonte de dados. Esses são todos os campos definidos nas colunas do arquivo apresentados como entrada durante um delivery usando os dados encontrados em um arquivo externo.

>[!NOTE]
>
>Uma tag de personalização do Adobe Campaign sempre tem o seguinte formulário **&lt;%=table.field%>**.

## Inserção de um campo de personalização {#inserting-a-personalization-field}

Para inserir campos de personalização, clique no ícone suspenso que está acessível a partir de qualquer campo de edição de cabeçalho, assunto ou corpo de mensagem.

![](assets/s_ncs_user_add_custom_field.png)

Após a seleção de uma fonte de dados (campos de recipient ou campo de arquivo), essa inserção assume o formulário de um comando que será interpretado pelo Adobe Campaign e substituído pelo valor do campo para um determinado recipient. The physical replacement can then be viewed in the **[!UICONTROL Preview]** tab.

## Exemplo de campos de personalização {#personalization-fields-example}

Ao criar um email, iremos inserir o nome do recipient e depois adicionar a data de criação do perfil no corpo da mensagem. Para fazer isso:

1. Criar um novo delivery ou abrir um tipo de delivery de email existente.
1. In the delivery wizard, click **[!UICONTROL Subject]** to edit the subject of the message and enter a subject.
1. Enter &quot; **[!UICONTROL Special offer for]** &quot; and use the button in the toolbar to insert a personalization field. Select **[!UICONTROL Recipients>Title]**.

   ![](assets/s_ncs_user_insert_custom_field.png)

1. Repita a operação para inserir o nome do recipient. Insira espaços entre todos os campos de personalização.
1. Click **[!UICONTROL OK]** to validate.
1. Insira a personalização no corpo da mensagem. Para fazer isso, clique no conteúdo da mensagem e clique no botão de inserção de campo.
1. Select **[!UICONTROL Recipient>Other...]**.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. Select the field with the information to display and click **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. Click the **[!UICONTROL Preview]** tab to view the personalization result. Você deve selecionar um recipient para exibir a mensagem dele.

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >Quando um delivery faz parte de um workflow, você pode usar os dados da tabela de workflow temporário. This data is grouped in the **[!UICONTROL Target extension]** menu. Para obter mais informações, consulte [esta seção](../../workflow/using/executing-a-workflow.md#target-data).

## Otimização da personalização {#optimizing-personalization}

Você pode otimizar a personalização usando uma opção dedicada: **[!UICONTROL Prepare the personalization data with a workflow]**, disponível na **[!UICONTROL Analysis]** guia das propriedades de entrega.

Durante a análise de delivery, essa opção cria e executa automaticamente um workflow que armazena todos os dados vinculados ao Target em uma tabela temporária, incluindo dados de tabelas vinculadas na FDA.

Ao selecionar essa opção, é possível obter um aumento significativo no desempenho para executar a personalização.

Por exemplo, se estiver tendo problemas de desempenho com delivery de um grande número de recipients ao usar muitos campos de personalização e/ou blocos de personalização no conteúdo de suas mensagens, essa opção pode acelerar o manuseio de personalização e, portanto, o delivery de suas mensagens.

Para fazer isso, siga as etapas abaixo:

1. Crie uma campanha. Para obter mais informações, consulte [esta seção](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. In the **[!UICONTROL Targeting and workflows]** tab of your campaign, add a **Query** activity to your workflow. Para obter mais informações sobre o uso dessa atividade, consulte [esta seção](../../workflow/using/query.md).
1. Add an **[!UICONTROL Email delivery]** activity to the workflow and open it. Para obter mais informações sobre o uso dessa atividade, consulte [esta seção](../../workflow/using/delivery.md).
1. Vá até a **[!UICONTROL Analysis]** guia do **[!UICONTROL Delivery properties]** e selecione a **[!UICONTROL Prepare the personalization data with a workflow]** opção.

   ![](assets/perso_optimization.png)

1. Configure o delivery e comece o workflow para iniciar a análise.

Depois que a análise é feita, os dados da personalização são armazenados em uma tabela temporária por meio de um workflow temporário criado em tempo real durante a análise.

Este workflow não está visível na interface do Adobe Campaign. É para ser apenas um meio técnico para armazenar e manipular rapidamente os dados de personalização.

Once the analysis is complete, go to the workflow **[!UICONTROL Properties]** and select the **[!UICONTROL Variables]** tab. Você pode ver o nome da tabela temporária que pode ser usada para fazer uma chamada SQL para exibir os IDs que ela contém.

![](assets/perso_optimization_temp_table.png)

## Tempo limite da fase de personalização {#timing-out-personalization}

Para melhorar a proteção de entrega, é possível definir um período de tempo limite para a fase de personalização.

Na **[!UICONTROL Delivery]** guia do **[!UICONTROL Delivery properties]**, selecione um valor máximo em segundos para a **[!UICONTROL Maximum personalization run time]** opção.

Durante a visualização ou envio, se a fase de personalização exceder o tempo máximo definido neste campo, o processo será abortado com uma mensagem de erro e a entrega falhará.

![](assets/perso_time-out.png)

O valor padrão é de 5 segundos.

Se você definir essa opção como 0, não haverá limite de tempo para a fase de personalização.