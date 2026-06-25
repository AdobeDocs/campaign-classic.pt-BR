---
product: campaign
title: Usar modelos de entrega
description: Usar modelos de entrega
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Delivery Templates
hide: true
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
TQID: https://experienceleague.adobe.com/99urg-HfXdZVnSsbFPzG9d2RkmxkPoYGNDEojWHmux4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 598
ht-degree: 100%

---

# Usar modelos {#use-templates}



Os modelos da entrega oferecem mais eficiência ao fornecer cenários prontos para os tipos mais comuns de atividades. Com modelos, os profissionais de marketing podem implantar novas campanhas com personalização mínima em um período de tempo menor.

Saiba mais sobre modelos da entrega [nesta seção](about-templates.md).

## Introdução a modelos de entrega {#gs-templates}

Um [modelo da entrega](about-templates.md) permite definir uma única vez um conjunto de propriedades técnicas e funcionais que atendam às suas necessidades e que possam ser reutilizadas para entregas futuras. Você pode economizar tempo e padronizar entregas quando necessário.

Quando você gerencia várias marcas no Adobe Campaign, a Adobe recomenda ter um subdomínio por marca. Por exemplo, um banco pode ter vários subdomínios correspondentes a cada uma de suas agências regionais. Se um banco for proprietário do domínio bluebank.com, seus subdomínios podem ser @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com etc. Ter um modelo de entrega por subdomínio permite usar sempre os parâmetros pré-configurados certos para cada marca, o que evita erros e economiza tempo.

**Dica**: para evitar erros de configuração, recomendamos duplicar um modelo nativo e alterar suas propriedades em vez de criar um novo modelo.

## Configurar endereços

* O endereço do remetente é obrigatório para o envio de um email.

* Alguns ISPs (provedores de serviço de internet) verificam a validade do endereço do remetente antes de aceitarem mensagens.

* Um endereço formado incorretamente pode resultar na rejeição pelo servidor de recebimento. Você precisa ter certeza de que o endereço informado está correto.

* O endereço deve identificar explicitamente o remetente. O domínio deve ser de propriedade e registrado pelo remetente.

* A Adobe recomenda a criação de contas de email que correspondam aos endereços especificados para entrega e respostas. Verifique com o administrador do sistema de mensagens.

Para configurar endereços na interface do Campaign, siga os passos abaixo:

1. No [modelo da entrega](about-templates.md), clique no link **[!UICONTROL From]**. Na janela **[!UICONTROL Email header parameters]**, preencha os seguintes campos:

   ![](assets/d_best_practices_email_header.png)

1. No campo **[!UICONTROL Sender address]**, verifique se o domínio de endereço é o mesmo que o subdomínio que você delegou à Adobe. Você pode alterar a parte anterior a “@&#39;” mas não o endereço do domínio.

1. No campo **[!UICONTROL From]**, use um nome facilmente identificável pelos destinatários, como o nome da sua marca, para aumentar a taxa de abertura das entregas. Para melhorar ainda mais a experiência do destinatário, você pode adicionar o nome de uma pessoa, por exemplo “Emma da Megastore”.

1. Nos campos **[!UICONTROL Reply address text]**, o endereço do remetente é usado por padrão para respostas. No entanto, a Adobe recomenda o uso de um endereço real, como o atendimento ao cliente da sua marca. Nesse caso, se um destinatário enviar uma resposta, o atendimento ao cliente poderá resolvê-lo.

### Configurar um grupo de controle

Depois que a entrega é enviada, você pode comparar o comportamento dos destinatários excluídos com os destinatários que receberam a entrega. Você pode então medir a eficiência de suas campanhas. Saiba mais sobre grupos de controle [nesta seção](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Para configurar um grupo de controle, clique no link **[!UICONTROL To]**. Na janela **[!UICONTROL Select target]**, selecione a guia **[!UICONTROL Control group]**. Você pode extrair uma fatia do público-alvo, por exemplo, uma amostra aleatória de 5%.

![](assets/d_best_practices_control_group.png)

## Usar tipologias para aplicar filtros ou regras de controle

Uma tipologia contém regras de verificação aplicadas durante a fase de análise, antes de enviar qualquer mensagem.

Na guia **[!UICONTROL Typology]** das propriedades do modelo, altere a tipologia padrão de acordo com suas necessidades.

Por exemplo, para controlar melhor o tráfego de saída, você pode definir quais endereços IP podem ser usados, estabelecendo uma afinidade por subdomínio e criando uma tipologia por afinidade. As afinidades são definidas no arquivo de configuração da instância. Entre em contato com o administrador do Adobe Campaign.

Para obter mais informações sobre tipologias, consulte [esta seção](../../campaign-opt/using/about-campaign-typologies.md).
