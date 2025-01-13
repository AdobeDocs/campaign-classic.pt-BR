---
product: campaign
title: Como usar os dados de workflow
description: Saiba como usar os dados de workflow
feature: Workflows, Data Management
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '409'
ht-degree: 100%

---

# Como usar os dados de workflow{#how-to-use-workflow-data}



## Atualização do banco de dados {#updating-the-database}

Todos os dados coletados podem ser usados para atualizar o banco de dados ou nas entregas. Por exemplo, você pode enriquecer as possibilidades de personalização do conteúdo da mensagem (incluir o número de contratos na mensagem, especificar o carrinho de compras comum do ano passado, etc.) ou detalhar o público alvo (enviar uma mensagem aos cotitulares do contrato, ter como target os mil melhores assinantes dos serviços online e etc.). Esses dados também podem ser exportados ou arquivados em uma lista.

### Atualizações diretas e listas {#lists-and-direct-updates}

Os dados do banco de dados do Adobe Campaign e as listas existentes podem ser atualizados usando duas atividades dedicadas:

* A atividade de **[!UICONTROL List update]** permite armazenar worktables em um DataList.

  Você pode selecionar uma lista existente ou criar uma. Nesse caso, o nome e possivelmente a pasta de registro são calculados.

  ![](assets/s_user_create_list.png)

  Consulte [Atualização da lista](list-update.md).

* A atividade **[!UICONTROL Update data]** realiza uma atualização em massa dos campos no banco de dados.

  Para mais informações, consulte [Atualização de dados](update-data.md).

### Gestão de assinatura/cancelamento de assinatura {#subscription-unsubscription-management}

Para saber mais sobre assinatura e cancelamento de assinatura de destinatários em um serviço de informação por meio de um workflow, consulte [Serviços de assinatura](subscription-services.md).

## Envio por workflow {#sending-via-a-workflow}

### Atividade de entrega {#delivery-activity}

A atividade de entrega é detalhada em [Entrega](delivery.md).

### Enriquecimento e direcionamento de entregas {#enriching-and-targeting-deliveries}

As entregas podem processar dados de workflows para personalizar o conteúdo ou dentro da estrutura de seleção do público alvo.

Por exemplo, dentro da estrutura de uma entrega de mala direta, você pode incluir os dados adicionais, obtidos da manipulação de dados realizada no workflow, no arquivo de extração:

![](assets/s_advuser_add_data_postal_mail.png)

Além dos campos de personalização habituais, você pode adicionar campos de personalização a partir de estágios do workflow ao conteúdo da entrega. Os dados adicionais definidos nas atividades do fluxo de trabalho podem ser mantidos e acessados no assistente de entrega, conforme mostrado no exemplo abaixo, para definir o nome do arquivo de saída dentro da estrutura de entrega de correspondência direta:

![](assets/s_advuser_using_additional_data.png)

Os dados contidos na tabela de workflow são identificados pelo seu nome: ele é sempre composto pelo link **targetData** . Para obter mais informações, consulte [Dados de target](data-life-cycle.md#target-data).

Dentro da estrutura de entrega de email, os campos de personalização também podem usar dados da extensão do target executada nos estágios de workflows para construção do target, conforme mostrado no exemplo abaixo:

![](assets/s_advuser_add_data_email.png)

Se um código de segmento for especificado em uma atividade de target, ele será adicionado a uma coluna específica da tabela de workflow e será oferecido junto com os campos de personalização. Para exibir todos os campos de personalização, clique no link **[!UICONTROL Target extension > Other...]** que está acessível por meio do botão de personalização.

![](assets/s_advuser_segment_code_select.png)
