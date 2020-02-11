---
title: Envio de um email com o Adobe Campaign Classic
description: Saiba mais sobre os parâmetros específicos para fornecer emails no Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 791f7a54-3225-46ca-ad6f-6c32e9c62d75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: e2dd8161-fe38-48bf-a288-8ec328b2660e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c800c20fff89b97f6fa38b3c659ca765765e157

---


# Envio de um email{#sending-an-email}

To approve your email and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

O processo detalhado da validação e envio de um delivery é apresentado nas seções abaixo:

* [Validando o dleivery](../../delivery/using/steps-validating-the-delivery.md)
* [Enviando o delivery](../../delivery/using/steps-sending-the-delivery.md)

As seções abaixo detalham os parâmetros específicos ao envio de emails.

## Arquivamento de emails {#archiving-emails}

O Adobe Campaign permite que você armazene emails em um sistema externo por meio do CCo simplesmente adicionando um endereço de email do CCo ao seu destino de mensagem. Uma vez ativada a opção, uma cópia exata de todas as mensagens enviadas será mantida para este delivery.

Para obter mais informações sobre a configuração do campo de email CCo, consulte [esta seção](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Este recurso é opcional. Verifique seu contrato de licença e entre em contato com o executivo da sua conta para ativá-lo.

Ao criar um novo delivery ou template do delivery, o CCo não é habilitado por padrão, mesmo que a opção tenha sido adquirida. Você deve habilitá-lo manualmente em cada delivery ou template onde deseja usá-lo.

Para fazer isso, siga as etapas abaixo:

1. Vá até **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** ou **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Selecione o delivery de sua escolha ou duplique o template do delivery **de email** integrado e selecione o template duplicado.
1. Clique no botão **Propriedades**.
1. Select the **[!UICONTROL Delivery]** tab.
1. Marque a caixa **Arquivar emails** para manter uma cópia de todas as mensagens enviadas para esse delivery ou para cada delivery com base nesse template.

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >If the emails sent to the BCC address are opened and clicked through, this will be taken into account in the **[!UICONTROL Total opens]** and **[!UICONTROL Clicks]** from the send analysis, which could cause some miscalculations.

## Geração da mirror page {#generating-the-mirror-page}

A mirror page é uma página HTML acessível online através de um navegador da Web. Seu conteúdo é idêntico ao email.

Por padrão, a mirror page é gerada se o link for inserido no conteúdo do email. For more on personalization blocks insertion, refer to [Personalization blocks](../../delivery/using/personalization-blocks.md).

In the delivery properties, the **[!UICONTROL Mode]** field of the **[!UICONTROL Validity]** tab lets you modify the generation mode for this page.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>Um conteúdo HTML deve ter sido definido para o delivery da mirror page a ser criada.

Além do modo padrão, as seguintes opções também estão disponíveis:

* **[!UICONTROL Force the generation of the mirror page]** : mesmo se nenhum link para a página espelhada for inserido na entrega, a página espelhada será criada.
* **[!UICONTROL Do not generate the mirror page]** : nenhuma página espelhada é gerada, mesmo se o link estiver presente na entrega.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** : essa opção permite acessar o conteúdo da página espelhada, com informações de personalização, na janela do log de entrega. To do this, after the end of the delivery, click the **[!UICONTROL Delivery]** tab and select the line of the recipient whose mirror page you wish to view. Clique no **[!UICONTROL Display the mirror page for this message...]** link.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Gestão de emails de devolução {#managing-bounce-emails}

The **[!UICONTROL SMTP]** tab of the delivery parameters lets you configure the management of bounce mails.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Por padrão, os emails devolvido são recebidos na caixa de erro padrão da plataforma, mas você pode definir um endereço de erro específico para o delivery.

Você também pode definir um endereço específico nessa tela para investigar os motivos para a devolução dos emails quando não puderem ser qualificados automaticamente pelo aplicativo. Para cada um desses campos, o ícone &#39;adicionar campos personalizados&#39; permite adicionar parâmetros de personalização.

## Codificação de caracteres {#character-encoding}

Na **[!UICONTROL SMTP]** guia dos parâmetros de entrega, a **[!UICONTROL Character encoding]** seção permite definir uma codificação específica.

A codificação padrão é UTF-8. Se alguns dos provedores de email de seus destinatários não oferecerem suporte à codificação padrão UTF-8, você pode definir uma codificação específica para exibir corretamente os caracteres especiais aos destinatários dos seus emails.

Por exemplo, você deseja enviar um email contendo caracteres japoneses. Para garantir que todos os caracteres sejam exibidos corretamente para seus destinatários no Japão, é possível usar uma codificação que ofereça suporte aos caracteres japoneses em vez do padrão UTF-8.

Para fazer isso, selecione a **[!UICONTROL Force the encoding used for messages]** opção na seção **[!UICONTROL Character encoding]** e escolha uma codificação na lista suspensa que é exibida.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Adição de cabeçalhos SMTP {#adding-smtp-headers}

É possível adicionar cabeçalhos SMTP aos seus deliveries. To do this, use the relevant section of the **[!UICONTROL SMTP]** tab in the delivery.

The script entered in this window must reference one header per line in the following form: **name:value**.

Os valores são codificados automaticamente se necessário.

>[!CAUTION]
>
>Adicionar um script para inserir cabeçalhos SMTP adicionais é apenas para usuários avançados.
>
>A sintaxe desse script deve estar em conformidade com os requisitos desse tipo de conteúdo: não há espaço não utilizado, nenhuma linha vazia, etc.
