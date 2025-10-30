---
product: campaign
title: Parâmetros de email
description: Saiba mais sobre as opções e configurações específicas da entrega por email
feature: Email
role: User, Developer, Data Engineer
hide: true
hidefromtoc: true
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
source-git-commit: 0507e0372a81351adc145dafdd3cbe5d5422dc00
workflow-type: ht
source-wordcount: '905'
ht-degree: 100%

---

# Parâmetros de email {#email-parameters}

Esta seção apresenta as opções e os parâmetros específicos da entrega de email.

## CCO de email {#email-bcc}

O Adobe Campaign permite que você armazene emails em um sistema externo por meio do CCO simplesmente adicionando um endereço de email de CCO ao seu target de mensagem.

Uma vez ativada a opção, uma cópia exata de todas as mensagens enviadas será mantida para essa entrega.

Para obter mais informações sobre a configuração e práticas recomendadas de Cco de email, consulte [esta seção](../../installation/using/email-archiving.md).

>[!NOTE]
>
>A Cco de email é um recurso opcional. Verifique seu contrato de licença e entre em contato com o executivo da sua conta para ativá-la.

Ao criar uma nova entrega ou template da entrega, o Email Cc não é ativado por padrão. Você precisa habilitá-lo manualmente no nível da entrega de email ou do template da entrega.

>[!NOTE]
>
>Se estiver usando o Email CCO com [MTA aprimorado](sending-with-enhanced-mta.md), essa opção será habilitada automaticamente para todas as entregas.

Para habilitar o Cco de Email para um template da entrega de email, siga as etapas abaixo:

1. Acesse **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** ou **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Selecione a entrega de sua escolha ou duplique o modelo de entrega **de email** integrado e selecione o modelo duplicado.
1. Clique no botão **Propriedades**.
1. Selecione a guia **[!UICONTROL Delivery]**.
1. Verifique a opção **Email Cco**. Uma cópia de todas as mensagens enviadas para cada entrega com base neste modelo será enviada para o endereço Cco de email que foi configurado.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>Se os emails enviados para o endereço CCo forem abertos e clicados, isso será considerado no **[!UICONTROL Total opens]** e **[!UICONTROL Clicks]** da análise de envio, o que poderá causar alguns erros de cálculo.

## Seleção dos formatos de mensagem {#selecting-message-formats}

Você pode alterar o formato das mensagens de email enviadas. Para fazer isso, edite as propriedades da entrega e clique na guia **[!UICONTROL Delivery]**.

![](assets/s_ncs_user_wizard_email_param.png)

Selecione o formato do email na seção inferior da janela:

* **[!UICONTROL Use recipient preferences]** (modo padrão)

  O formato da mensagem é definido de acordo com os dados armazenados no perfil do destinatário e armazenado por padrão no campo **[!UICONTROL email format]** (@emailFormat). Se um destinatário deseja receber mensagens em determinado formato, esse será o formato enviado. Se o campo não estiver preenchido, uma mensagem multipart-alternative será enviada (veja abaixo).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

  A mensagem contém os dois formatos: texto e HTML. O formato exibido no recebimento depende da configuração do software de email do destinatário (multipart-alternative).

  >[!IMPORTANT]
  >
  >Essa opção inclui ambas as versões do documento. Portanto, isso afeta a taxa de entrega, porque o tamanho da mensagem é maior.

* **[!UICONTROL Send all messages in text format]**

  A mensagem é enviada em formato de texto. O formato HTML não será enviado, mas usado somente para a mirror page quando o destinatário clicar na mensagem.

>[!NOTE]
>
>Para obter mais informações sobre como definir o conteúdo de email, consulte [esta seção](defining-the-email-content.md).

## Geração da mirror page {#generating-mirror-page}

A mirror page é uma página HTML acessível online através de um navegador da Web. Seu conteúdo é idêntico ao email.

Por padrão, a mirror page é gerada se o link for inserido no conteúdo do email. Para obter mais informações sobre a inserção de blocos de personalização, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html?lang=pt-BR){target="_blank"}.

Nas propriedades de entrega, o campo **[!UICONTROL Mode]** da guia **[!UICONTROL Validity]** permite modificar o modo de geração desta página.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>Um conteúdo HTML deve ter sido definido para a entrega da mirror page a ser criada.

Além do modo padrão, as seguintes opções também estão disponíveis:

* **[!UICONTROL Force the generation of the mirror page]**: mesmo se nenhum link para a mirror page for inserido na entrega, ela será criada.
* **[!UICONTROL Do not generate the mirror page]**: nenhuma mirror page será gerada, mesmo se o link estiver presente na entrega.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**: essa opção permite acessar o conteúdo da mirror page, com informações de personalização, na janela de log da entrega. Para fazer isso, após o fim da entrega, clique na guia **[!UICONTROL Delivery]** e selecione a linha do destinatário cuja mirror page você deseja exibir. Clique no link **[!UICONTROL Display the mirror page for this message...]**.

  ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Codificação de caracteres {#character-encoding}

Na guia **[!UICONTROL SMTP]** dos parâmetros da entrega, a seção **[!UICONTROL Character encoding]** permite definir uma codificação específica.

A codificação padrão é UTF-8. Se alguns dos provedores de email de seus destinatários não oferecerem suporte à codificação padrão UTF-8, você pode definir uma codificação específica para exibir corretamente os caracteres especiais aos destinatários dos seus emails.

Por exemplo, você deseja enviar um email contendo caracteres japoneses. Para garantir que todos os caracteres sejam exibidos corretamente para seus destinatários no Japão, é possível usar uma codificação que ofereça suporte aos caracteres japoneses em vez do padrão UTF-8.

Para fazer isso, selecione a opção **[!UICONTROL Force the encoding used for messages]** na seção **[!UICONTROL Character encoding]** e escolha uma codificação na lista suspensa que é exibida.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Gerenciamento de emails rejeitados {#managing-bounce-emails}

A guia **[!UICONTROL SMTP]** dos parâmetros de entrega permite configurar a gestão de emails devolvidos.

Por padrão, os emails devolvidos são recebidos na [caixa de erro padrão da plataforma](../../installation/using/deploying-an-instance.md#parameters-for-delivered-emails-parameters-for-delivered-emails), mas é possível definir um endereço de erros específico para uma entrega.

Você também pode definir um endereço específico nessa tela para investigar os motivos para a devolução dos emails quando não puderem ser qualificados automaticamente pelo aplicativo. Para cada um desses campos, o ícone **Adicionar campos personalizados** permite adicionar parâmetros de personalização.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Para obter mais informações sobre gerenciamento de rejeição de emails, consulte [esta seção](understanding-delivery-failures.md#bounce-mail-management).

## Adição de cabeçalhos SMTP {#adding-smtp-headers}

É possível adicionar cabeçalhos SMTP às entregas Para fazer isso, use a seção relevante da guia **[!UICONTROL SMTP]** na entrega.

O script inserido nessa janela deve referenciar um cabeçalho por linha no seguinte formulário: **nome:value**.

Os valores são codificados automaticamente se necessário.

>[!IMPORTANT]
>
>Adicionar um script para inserir cabeçalhos SMTP adicionais é apenas para usuários avançados.
>
>A sintaxe desse script deve estar em conformidade com os requisitos desse tipo de conteúdo: não há espaço não utilizado, nenhuma linha vazia, etc.
