---
product: campaign
title: Regras de filtro
description: Saiba como usar as regras de filtro
feature: Typology Rules
exl-id: a4d12445-5680-4704-9c67-e43e0ea6631b
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Regras de filtro{#filtering-rules}

![](../../assets/v7-only.svg)

Regras de filtragem permitem definir as mensagens a serem excluídas com base nos critérios definidos em uma query. Essas regras estão vinculadas a uma targeting dimension.

As regras de filtragem podem estar vinculadas a outros tipos de regras (controle, pressão etc.) em tipologias ou agrupadas em uma tipologia **Filtragem** dedicada. Para obter mais informações, consulte [Criação e uso de uma tipologia de filtragem](#creating-and-using-a-filtering-typology).

## Criar uma regra de filtro {#creating-a-filtering-rule}

Por exemplo, você pode filtrar os assinantes do boletim informativo para evitar que as comunicações sejam enviadas a recipients menores de idade.

Para definir esse filtro, aplique as seguintes etapas:

1. Crie uma regra de tipologia **[!UICONTROL Filtering]** aplicável a todos os canais de comunicação.

   ![](assets/campaign_opt_create_filter_01.png)

1. Altere a targeting dimension padrão e selecione as assinaturas (**nms:subscription**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Crie o filtro usando o link **[!UICONTROL Edit the query from the targeting dimension...]**.

   ![](assets/campaign_opt_create_filter_03.png)

1. Vincule essa regra a uma tipologias de campanha e salve-a.

   ![](assets/campaign_opt_create_filter_04.png)

Quando essa regra for usada em um delivery, os assinantes menores de idade serão excluídos automaticamente. Uma mensagem específica indica a regra do aplicativo:

![](assets/campaign_opt_create_filter_05.png)

## Condicionar uma regra de filtro {#conditioning-a-filtering-rule}

Você poderá restringir o campo da aplicação na regra de filtragem com base na entrega ou na estrutura de entrega vinculada.

Para fazer isso, vá para a guia **[!UICONTROL General]** da regra de tipologia, selecione o tipo de restrição a ser aplicado e crie o filtro, conforme mostrado abaixo:

![](assets/campaign_opt_create_filter_06.png)

Nesse caso, mesmo que a regra esteja vinculada a todos os deliveries, ela só será aplicada àqueles que correspondam aos critérios do filtro definido.

>[!NOTE]
>
>As regras de filtragem e tipologia podem ser usadas em um fluxo de trabalho, na atividade **[!UICONTROL Delivery outline]**. Para obter mais informações, consulte [esta seção](../../workflow/using/delivery-outline.md).

## Criar e usar uma tipologia de filtro {#creating-and-using-a-filtering-typology}

É possível criar tipologias **[!UICONTROL Filtering]**: elas contêm apenas regras de filtragem.

![](assets/campaign_opt_create_typo_filtering.png)

Essas tipologias específicas podem ser vinculadas a um delivery quando o target for selecionado: no assistente do delivery, clique no link **[!UICONTROL To]** e, em seguida, na guia **[!UICONTROL Exclusions]**.

![](assets/campaign_opt_apply_typo_filtering.png)

Em seguida, selecione o filtro a ser aplicado ao delivery. Para fazer isso, clique no botão **[!UICONTROL Add]** e selecione as tipologias a serem aplicadas.

Você também poderá vincular regras de filtragem diretamente por meio desta guia, sem que sejam agrupadas em uma tipologia. Para fazer isso, use a seção inferior da janela.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>Somente as regras de filtragem e de tipologia estarão disponíveis na janela de seleção.
>
>Essas configurações podem ser definidas no template de delivery a ser aplicado automaticamente a todos os novos deliveries criados usando o template.

## Regras padrão de exclusão de entrega {#default-deliverability-exclusion-rules}

Duas regras de filtragem estão disponíveis por padrão: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) e **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). Durante a análise de e-mail, essas regras comparam os endereços de e-mail do recipient com os endereços proibidos ou nomes de domínio contidos em uma lista de supressão global criptografada gerenciada na instância de entrega. Se houver algum positivo, a mensagem não será enviada para esse recipient.

Isso evita a inclusão na lista de bloqueios devido a atividades mal-intencionadas, especialmente o uso de um Spamtrap. Por exemplo, se um Spamtrap for usado para se inscrever em um dos seus formulários web, um email de confirmação será enviado automaticamente para esse Spamtrap e resultará na inclusão automática do endereço utilizado à lista de bloqueios.

>[!NOTE]
>
>Os endereços e os nomes de domínio contidos na lista de supressão global estão ocultos. Somente o número de recipients excluídos é indicado nos logs de análise de delivery.
