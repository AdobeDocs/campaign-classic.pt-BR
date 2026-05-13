---
product: campaign
title: Como usar os dados de fluxo de trabalho
description: Saiba como usar os dados de fluxo de trabalho
feature: Workflows, Data Management
hide: true
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
TQID: https://experienceleague.adobe.com/xasYSu6WyHC0T6CpKn51bZ5K7WlspJAbB0R45AeXb8M
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 410
ht-degree: 88%

---

# Como usar os dados de fluxo de trabalho{#how-to-use-workflow-data}



## Atualização do banco de dados {#updating-the-database}

Todos os dados coletados podem ser usados para atualizar o banco de dados ou nas entregas. Por exemplo, você pode enriquecer as possibilidades de personalização do conteúdo da mensagem (incluir o número de contratos na mensagem, especificar o carrinho de compras médio do ano passado etc.) ou detalhar a segmentação de população (enviar uma mensagem aos cotitulares do contrato, direcionar os mil melhores assinantes para serviços online e etc.). Esses dados também podem ser exportados ou arquivados em uma lista.

### Atualizações diretas e listas {#lists-and-direct-updates}

Os dados do banco de dados do Adobe Campaign e as listas existentes podem ser atualizados usando duas atividades dedicadas:

* A atividade de **[!UICONTROL List update]** permite armazenar tabelas de trabalho num DataList.

  Você pode selecionar uma lista existente ou criar uma. Nesse caso, o nome e possivelmente a pasta de registro são calculados.

  ![](assets/s_user_create_list.png)

  Consulte [Atualização da lista](list-update.md).

* A atividade **[!UICONTROL Update data]** realiza uma atualização em massa dos campos no banco de dados.

  Para mais informações, consulte [Atualização de dados](update-data.md).

### Gestão de assinatura/cancelamento de assinatura {#subscription-unsubscription-management}

Para saber mais sobre subscrição e cancelamento de subscrição de destinatários de um serviço de informações via fluxo de trabalho, consulte [Serviços de subscrição](subscription-services.md).

## Envio por fluxo de trabalho {#sending-via-a-workflow}

### Atividade de entrega {#delivery-activity}

A atividade de entrega é detalhada em [Entrega](delivery.md).

### Enriquecimento e direcionamento de entregas {#enriching-and-targeting-deliveries}

As entregas podem processar dados de fluxos de trabalho para personalizar o conteúdo ou dentro da estrutura de seleção da população de destino.

Por exemplo, dentro da estrutura de uma entrega de mala direta, você pode incluir os dados adicionais, obtidos da manipulação de dados realizada no fluxo de trabalho, no arquivo de extração:

![](assets/s_advuser_add_data_postal_mail.png)

Além dos campos de personalização habituais, você pode adicionar campos de personalização a partir de estágios do fluxo de trabalho ao conteúdo da entrega. Os dados adicionais definidos nas atividades do fluxo de trabalho podem ser mantidos e acessados no assistente de entrega, conforme mostrado no exemplo abaixo, para definir o nome do arquivo de saída dentro da estrutura de entrega de correspondência direta:

![](assets/s_advuser_using_additional_data.png)

Os dados contidos na tabela de fluxo de trabalho são identificados pelo seu nome: ele é sempre composto pelo link **targetData** . Para obter mais informações, consulte [Dados de target](data-life-cycle.md#target-data).

Dentro da estrutura de entrega de email, os campos de personalização também podem usar dados da extensão do target executada nos estágios de fluxos de trabalho de segmentação, conforme mostrado no exemplo abaixo:

![](assets/s_advuser_add_data_email.png)

Se um código de segmento for especificado em uma atividade de segmentação, ele será adicionado a uma coluna específica da tabela de fluxo de trabalho e será oferecido junto com os campos de personalização. Para exibir todos os campos de personalização, clique no link **[!UICONTROL Target extension > Other...]** que está acessível por meio do botão de personalização.

![](assets/s_advuser_segment_code_select.png)
