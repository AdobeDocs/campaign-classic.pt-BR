---
title: Usar templates do delivery
seo-title: Usar templates do delivery
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 24%

---


# Usar modelos {#use-templates}

Os templates do delivery permitem maior eficiência ao fornecer cenários prontos para os tipos mais comuns de atividades. Com modelos, os profissionais de marketing podem implantar novas campanhas com personalização mínima em um período de tempo menor.

Saiba mais sobre templates do delivery [nesta seção](../../delivery/using/creating-a-delivery-template.md).

## Introdução aos templates do delivery {#gs-templates}

Um [template do delivery](../../delivery/using/creating-a-delivery-template.md) permite que você defina uma vez um conjunto de propriedades técnicas e funcionais que atendam às suas necessidades e que possam ser reutilizadas para delivery futuros. Você pode economizar tempo e padronizar delivery quando necessário.

Quando você gerencia várias marcas no Adobe Campaign, a Adobe recomenda ter um subdomínio por marca. Por exemplo, um banco pode ter vários subdomínios correspondentes a cada uma de suas agências regionais. Se um banco possuir o domínio bluebank.com, seus subdomínios poderão ser @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Ter um modelo de entrega por subdomínio permite usar sempre os parâmetros pré-configurados certos para cada marca, o que evita erros e economiza tempo.

**Dica**:  Para evitar erros de configuração no Campaign Standard, recomendamos que você duplicado um modelo nativo e altere suas propriedades em vez de criar um novo modelo.

## Configurar endereços

* O endereço do remetente é obrigatório para permitir o envio de um email.

* Alguns ISPs (Internet Provedores de serviço) verificam a validade do endereço do remetente antes de aceitarem mensagens.

* Um endereço mal formado pode resultar na rejeição pelo servidor de recebimento. Tem de se certificar de que é fornecido o endereço correto.

* O endereço deve identificar explicitamente o remetente. O domínio deve ser de propriedade e registrado no remetente.

* O Adobe recomenda criar contas de email que correspondam aos endereços especificados para delivery e respostas. Verifique com o administrador do sistema de mensagens.

Para configurar endereços na interface de Campanha, siga as etapas abaixo:

1. No [template do delivery](../../delivery/using/creating-a-delivery-template.md), clique no **[!UICONTROL From]** link. Na **[!UICONTROL Email header parameters]** janela, preencha os seguintes campos:

   ![](assets/d_best_practices_email_header.png)

1. No **[!UICONTROL Sender address]** campo, verifique se o domínio de endereço é o mesmo que o subdomínio que você delegou ao Adobe. Você pode alterar a parte anterior a &#39;@&#39;, mas não o endereço do domínio.

1. No **[!UICONTROL From]** campo, use um nome facilmente identificável pelos recipient, como o nome da sua marca, para aumentar a taxa de abertura dos delivery. Para melhorar ainda mais a experiência do recipient, adicione o nome de uma pessoa, por exemplo &quot;Emma from Megastore&quot;.

1. Nos **[!UICONTROL Reply address text]** arquivos, o endereço do remetente é usado por padrão para respostas. Entretanto, a Adobe recomenda usar um endereço real existente, como o atendimento ao cliente da sua marca. Nesse caso, se um destinatário enviar uma resposta, o atendimento ao cliente poderá resolvê-lo.

### Configurar um grupo de controle

Depois que a entrega é enviada, você pode comparar o comportamento dos destinatários excluídos com os destinatários que receberam a entrega. Você pode então medir a eficiência de suas campanhas. Saiba mais sobre grupos de controle [nesta seção](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Para configurar um grupo de controle, clique no **[!UICONTROL To]** link. Na **[!UICONTROL Select target]** janela, selecione a **[!UICONTROL Control group]** guia. Você pode extrair uma parte do público alvo, por exemplo, uma amostra aleatória de 5%.

![](assets/d_best_practices_control_group.png)

## Usar tipologias para aplicar filtros ou regras de controle

Uma tipologia contém regras de verificação aplicadas durante a fase de análise, antes de enviar qualquer mensagem.

Na **[!UICONTROL Typology]** guia das propriedades do modelo, altere a tipologia padrão de acordo com suas necessidades.

Por exemplo, para controlar melhor o tráfego de saída, você pode definir quais endereços IP podem ser usados definindo uma afinidade por subdomínio e criando uma tipologia por afinidade. As afinidades são definidas no arquivo de configuração da instância. Entre em contato com o administrador da Adobe Campaign.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).
