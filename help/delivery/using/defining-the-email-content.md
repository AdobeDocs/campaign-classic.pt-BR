---
title: Definição do conteúdo de email no Adobe Campaign Classic
description: Saiba como definir o conteúdo de email ao usar o Adobe Campaign Classic.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 30803bde7be6073895fcea4b6c70655a27111f55

---


# Definição do conteúdo do email{#defining-the-email-content}

## Remetente {#sender}

To define the name and address of the sender which will appear in the header of messages sent, click the **[!UICONTROL From]** link.

![](assets/s_ncs_user_wizard_email02.png)

Todas as informações necessárias para criação dos cabeçalhos de mensagens de email devem ser inseridas nessa janela. Essas informações podem ser personalizadas. Para fazer isso, use os botões à direita dos campos de entrada para inserir campos de personalização.

To find out how to insert and use personalization fields, refer to [About personalization](../../delivery/using/about-personalization.md) section.

>[!NOTE]
>
>* O endereço do remetente será usado para respostas por padrão.
>* Os parâmetros do cabeçalho não devem ficar vazios. Por padrão, eles contêm a entrada de valores ao configurar o assistente de implantação. Para obter mais informações, consulte o [Guia de Instalação](../../installation/using/deploying-an-instance.md).
>* O endereço do remetente é obrigatório para possibilitar o envio de um email (padrão RFC).
>* O Adobe Campaign verifica a sintaxe dos endereços de email inseridos.


>[!CAUTION]
>
>No contexto das verificações implementadas pelos Provedores de Serviços de Internet (ISPs) para combater emails não solicitados (spam), a Adobe recomenda criar contas de email que correspondam aos endereços especificados para deliveries e respostas. Verifique com o administrador do sistema de mensagens.

## Assunto da mensagem {#message-subject}

O assunto da mensagem é configurado no campo correspondente. You can enter it directly in the field or click the **[!UICONTROL Subject]** link to enter a script. O link de personalização permite inserir campos de banco de dados no assunto.

>[!CAUTION]
>
>O assunto da mensagem é obrigatório.

![](assets/s_ncs_user_wizard_email_object.png)

O conteúdo do campo será substituído pelo valor no perfil do recipient quando a mensagem for enviada.

Por exemplo, na mensagem acima, o assunto da mensagem é personalizado para cada recipient com dados do seu perfil.

>[!NOTE]
>
>The use of personalization fields is presented in [About personalization](../../delivery/using/about-personalization.md).

## Conteúdo da mensagem {#message-content}

>[!CAUTION]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

O conteúdo da mensagem é definido na seção inferior da janela de configuração de delivery.

As mensagens são enviadas em formato de texto ou HTML por padrão, de acordo com a preferência do recipient. Recomendamos a criação de conteúdo nos dois formatos para garantir que as mensagens possam ser exibidas corretamente em qualquer sistema de email. Para obter mais informações, consulte [Selecionar formatos](#selecting-message-formats)de mensagem.

* To import an HTML content, use the **[!UICONTROL Open]** button. You can also paste the source code directly into the **[!UICONTROL Source]** sub-tab.

   Se estiver usando o [Editor de Conteúdo Digital](../../web/using/about-campaign-html-editor.md) (DCE), consulte [Seleção de um template de conteúdo](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

   >[!CAUTION]
   >
   >O conteúdo HTML deve ser criado antes, e depois importado para o Adobe Campaign. O editor de HTML não foi desenvolvido para criação de conteúdo.

   The **[!UICONTROL Preview]** sub-tab lets you view the rendering of each content for a recipient. Os campos de personalização e os elementos condicionais do conteúdo são substituídos pelas informações correspondentes para o perfil selecionado.

   Os botões da barra de ferramentas fornecem acesso aos parâmetros padrão de ações e formatação da página HTML.

   ![](assets/s_ncs_user_wizard_email01_138.png)

   Você pode inserir imagens em mensagens de um arquivo local ou de uma biblioteca de imagens no Adobe Campaign. To do this, click the **[!UICONTROL Image]** icon and select the appropriate option.

   ![](assets/s_ncs_user_wizard_email01_18.png)

   Library images can be accessed via the **[!UICONTROL Resources>Online>Public resources]** folder in the folder tree. Consulte também [Adicionar imagens](#adding-images).

   O último botão na barra de ferramentas permite inserir campos de personalização.

   >[!NOTE]
   >
   >The use of personalization fields is presented in [About personalization](../../delivery/using/about-personalization.md).

   As guias na parte inferior da página permitem exibir o código HTML da página que está sendo criada e exibir a renderização da mensagem com sua personalização. To launch this display, click **[!UICONTROL Preview]** and select a recipient using the **[!UICONTROL Test personalization]** button in the toolbar. Você pode selecionar um recipient no(s) target(s) definido(s) ou escolher outro.

   ![](assets/s_ncs_user_wizard_email01_139.png)

   Você pode validar a mensagem HTML. Também é possível visualizar o conteúdo do cabeçalho do email.

   ![](assets/s_ncs_user_wizard_email01_140.png)

* To import a text content, use the **[!UICONTROL Open]** button, or the **[!UICONTROL Text Content]** tab to enter the content of the message when displayed in text format. Use os botões da barra de ferramentas para acessar ações no conteúdo. O último botão permite inserir campos de personalização.

   ![](assets/s_ncs_user_wizard_email01_141.png)

   As for the HTML format click the **[!UICONTROL Preview]** tab at the bottom of the page to view the rendering of the message with its personalization.

   ![](assets/s_ncs_user_wizard_email01_142.png)

## Seleção dos formatos de mensagem {#selecting-message-formats}

Você pode alterar o formato das mensagens de email enviadas. To do this, edit the delivery properties and click the **[!UICONTROL Delivery]** tab.

![](assets/s_ncs_user_wizard_email_param.png)

Selecione o formato do email na seção inferior da janela:

* **[!UICONTROL Use recipient preferences]** (modo padrão)

   The message format is defined according to the data stored in the recipient profile and stored by default in the **[!UICONTROL email format]** field (@emailFormat). Se um recipient deseja receber mensagens em determinado formato, esse será o formato enviado. Se o campo não estiver preenchido, uma mensagem multipart-alternative será enviada (veja abaixo).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   A mensagem contém os dois formatos: texto e HTML. O formato exibido no recebimento depende da configuração do software de email do recipient (multipart-alternative).

   >[!CAUTION]
   >
   >Essa opção inclui ambas as versões do documento. Portanto, isso afeta a taxa de delivery, porque o tamanho da mensagem é maior.

* **[!UICONTROL Send all messages in text format]**

   A mensagem é enviada em formato de texto. O formato HTML não será enviado, mas usado somente para a mirror page quando o recipient clicar na mensagem.

## Definição de conteúdo interativo {#amp-for-email-format}

O Adobe Campaign permite que você experimente o novo [AMP interativo para o formato de email](https://amp.dev/about/email/) , que permite o envio de emails dinâmicos, sob determinadas condições.

For more on this, see [this section](../../delivery/using/defining-interactive-content.md).

## Uso da gestão de conteúdo {#using-content-management}

O conteúdo do delivery pode ser definido nos formulários de gestão de conteúdo, diretamente no assistente do delivery. To do this, you must reference the publication template of the content management to be used, in the **[!UICONTROL Advanced]** tab of the delivery properties.

![](assets/s_ncs_content_in_delivery.png)

Uma guia adicional permite inserir conteúdo que será integrado e formatado automaticamente de acordo com as regras de gestão de conteúdo.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>For further information about content management in Adobe Campaign, refer to [this section](../../delivery/using/about-content-management.md).

## Adição de imagens {#adding-images}

Os deliveries de email do formato HTML podem conter imagens. From the delivery wizard, you can import an HTML page containing images or insert images directly using the HTML editor via the **[!UICONTROL Image]** icon.

As imagens podem ser:

* Uma imagem local ou de um servidor
* Uma imagem armazenada na biblioteca de recursos públicos do Adobe Campaign

   Public resources are accessible via the **[!UICONTROL Resources > Online]** node of the Adobe Campaign hierarchy. Elas são agrupadas em uma biblioteca e podem ser incluídas em mensagens de email, mas também podem ser usadas para campanhas ou tarefas, ou para gestão de conteúdo.

* Um ativo compartilhado com a Adobe Experience Cloud. Consulte [esta seção](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

>[!CAUTION]
>
>Para incluir imagens nas mensagens de email usando o assistente do delivery, a instância do Adobe Campaign deve ser configurada para habilitar a gestão de recursos públicos. Esse procedimento pode ser executado no assistente de implantação. Consulte [esta seção](../../installation/using/deploying-an-instance.md) para obter mais informações sobre a configuração.

O assistente do delivery permite adicionar imagens locais ou armazenadas na biblioteca ao conteúdo de mensagens. To do this, click the **[!UICONTROL Image]** button in the HTML content toolbar.

![](assets/s_ncs_user_image_from_library.png)

Para que os recipients possam exibir as imagens incluídas nas mensagens recebidas, essas mensagens devem estar disponíveis em um servidor acessível externamente.

To manage images via the delivery wizard, you must click the **[!UICONTROL Tracking & Images]** icon in the toolbar.

![](assets/s_ncs_user_email_del_img_param.png)

Selecione **[!UICONTROL Upload images]** na **[!UICONTROL Images]** guia. Você pode escolher se deseja incluir as imagens na mensagem de email.

![](assets/s_ncs_user_email_del_img_upload.png)

* Você pode carregar imagens manualmente sem esperar a fase de análise de delivery. To do this, click the **[!UICONTROL Upload images now]** link.
* Você pode especificar outro caminho para acessar as imagens no servidor de rastreamento. To do this, enter it in the **[!UICONTROL Image URL]** field. Esse valor substitui o valor definido nos parâmetros do assistente de instalação.

Quando você abre conteúdo HTML com imagens incluídas no assistente do delivery, aparece uma mensagem com a opção de carregar as imagens imediatamente, de acordo com os parâmetros do delivery.

![](assets/s_ncs_user_email_del_img_local.png)

>[!CAUTION]
>
>Os caminhos de acesso à imagem são modificados durante o carregamento manual ou ao enviar as mensagens.

**Exemplo: envio de uma mensagem com imagens{#example--sending-a-message-with-images}**

Veja a seguir um exemplo de delivery com quatro imagens:

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

These images come from a local directory or Web site as you can verify from the **[!UICONTROL Source]** tab.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

Click the **[!UICONTROL Tracking & Images]** icon and then the **[!UICONTROL Images]** tab to start detecting images in the message.

Para cada imagem detectada, você pode ver seu status:

* Se uma imagem for armazenada no local ou localizada em outro servidor, mesmo que esse servidor seja visível externamente (em um site da Internet, por exemplo), ela será detectada como **[!UICONTROL Not yet online]**.
* The images are detected as **[!UICONTROL Already online]** if they were uploaded earlier while creating another delivery.
* In the deployment wizard, you can define URLs for which image detection is not enabled: uploading these images will be **[!UICONTROL Skipped]**.

>[!NOTE]
>
>As imagens são identificadas pelo seu conteúdo e não pelos caminhos de acesso. This means that an image uploaded previously under a different name or in a different directory will be detected as **[!UICONTROL Already online]**.

Durante a fase de análise, as imagens são carregadas automaticamente no servidor para que sejam acessíveis externamente, exceto para as imagens locais que devem ser carregadas anteriormente.

Você pode trabalhar com antecedência e carregar imagens para que elas possam ser visualizadas por outros operadores do Adobe Campaign. Isso pode ser útil se você trabalhar de forma colaborativa. To do this, click **[!UICONTROL Upload the images straightaway...]** to upload the images onto the server.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>As URLs das imagens no email, e seus nomes em particular, são então modificadas.

Once the images are online, you can view changes to their names and paths from the **[!UICONTROL Source]** tab of the message.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

If you select **[!UICONTROL Include the images in the email]**, you can choose which images to include in the corresponding column.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>Se as imagens locais estiverem incluídas na mensagem, você deve confirmar as alterações no código-fonte da mensagem.

## Inserir código de barras em um email{#inserting-a-barcode-in-an-email}

O módulo de geração de código de barras permite criar vários tipos de códigos de barras que estão em conformidade com muitos padrões comuns, incluindo códigos de barras 2D.

É possível gerar um código de barras de forma dinâmica como um bitmap usando um valor definido por meio de critérios do cliente. Os códigos de barra personalizados podem ser incluídos em campanhas de email. O recipient pode imprimir a mensagem e mostrá-la à empresa emissora para exame (ao verificar, por exemplo).

Para inserir um código de barras em um email, coloque o cursor no conteúdo onde deseja exibi-lo e clique no botão de personalização. Select **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Em seguida, configure os seguintes elementos para atender às suas necessidades:

1. Selecione o tipo de código de barras.

   * Para o formato 1D, os seguintes tipos estão disponíveis no Adobe Campaign: Codabar, Code 128, GS1-128 (antigo EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 de 5, POSTNET e Royal Mail (RM4SCC).

      Exemplo de um código de barras 1D:

      ![](assets/barcode_insert_08.png)

   * Os tipos DataMatrix e PDF417 correspondem ao formato 2D.

      Exemplo de um código de barras 2D:

      ![](assets/barcode_insert_09.png)

   * Para inserir um código QR, selecione esse tipo e digite a taxa de correção de erro a ser aplicada. Essa taxa define a quantidade de informações repetidas e a tolerância à deterioração.

      ![](assets/barcode_insert_06.png)

      Exemplo de código QR:

      ![](assets/barcode_insert_12.png)

1. Insira o tamanho do código de barras que deseja inserir no email: a configuração da escala permite aumentar ou reduzir o tamanho do código de barras, de x1 a x10.
1. The **[!UICONTROL Value]** field enables you to define the value of the barcode. Um valor pode corresponder a uma oferta especial e pode ser a função de um critério, ele pode ser o valor de um campo de banco de dados vinculado aos clientes.

   Este exemplo mostra um código de barras do tipo EAN-8, ao qual foi adicionado o número da conta de um recipient. To add this account number, click the personalization button to the right of the **[!UICONTROL Value]** field and select **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. The **[!UICONTROL Height]** field lets you configure the height of the barcode without changing its width, by altering the amount of space between each bar.

   Não há controle de entrada restritivo dependendo do tipo de código de barras. Se um valor de código de barras estiver incorreto, ele só será visível no modo de **Pré-visualização**, onde o código de barras estará riscado em vermelho.

   >[!NOTE]
   >
   >O valor atribuído a um código de barras depende do seu tipo. Por exemplo, um tipo EAN-8 deve ter exatamente 8 números.
   >
   >The personalization button to the right of the **[!UICONTROL Value]** field lets you add data in addition to the value itself. Isso enriquece o código de barras, desde que o padrão do código de barras o aceite.
   >
   >Por exemplo, se você estiver usando um código de barras do tipo GS1-128 e quiser inserir o número da conta de um recipient, além do valor, clique no botão de personalização e selecione **[!UICONTROL Recipient > Account number]**. Se o número da conta do recipient selecionado for inserido corretamente, ele será considerado pelo código de barras.

Após configurar estes elementos, você pode finalizar seu email e enviá-lo. To avoid errors, always make sure your content is displayed correctly before performing a delivery by clicking the **[!UICONTROL Preview]** tab.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Se o valor de um código de barras estiver incorreto, seu bitmap é exibido riscado em vermelho.

![](assets/barcode_insert_11.png)

## Envio de emails em celulares japoneses {#sending-emails-on-japanese-mobiles}

### Formatos de email para celulares japoneses {#email-formats-for-japanese-mobiles}

O Adobe Campaign gerencia três formatos específicos em japonês para email em telefones: **Deco-mail** (DoCoMo mobiles), **Decore Mail** (Softbank mobiles) e **Decoration Mail** (KDDI AU mobiles). Esses formatos impõem restrições específicas de codificação, estrutura e tamanho. Saiba mais sobre limitações e recomendações [nesta seção](#limitations-and-recommendations).

In order for the recipient to correctly receive messages in one of these formats, we recommend selecting **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** or **[!UICONTROL Decoration Mail (KDDI AU)]** in the corresponding profile:

![](assets/deco-mail_03.png)

However, if you leave the **[!UICONTROL Email format]** option as **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** or **[!UICONTROL Text]**, Adobe Campaign will automatically detect (when sending the email) the Japanese format to use so that the message is correctly displayed.

This automatic detection system is based on the list of predefined domains defined in the **[!UICONTROL Management of Email Formats]** mail rule set. Para saber mais sobre gestão de formatos de email, consulte [esta página](../../installation/using/email-deliverability.md#managing-email-formats).

### Limitações e recomendações {#limitations-and-recommendations}

Determinado número de restrições se aplica no envio de emails que serão lidos em um dispositivo móvel operado por um provedor japonês (Softbank, DoCoMo, KDDI AU).

Portanto, você deve:

* Usar somente imagens no formato JPEG ou GIF
* Criar um delivery com seções de texto e HTML que são estritamente inferiores a 10.000 bytes (para KDDI AU e DoCoMo)
* Usar imagens com tamanho total (antes de codificar) abaixo de 100 KB
* Usar até 20 imagens por mensagem
* Usar um formato HTML de tamanho reduzido (um número limitado de tags está disponível para cada operador)

>[!NOTE]
>
>Deve-se considerar as limitações específicas para cada operador ao criar sua mensagem. Consulte:
>
>* Para DoCoMo, consulte [esta página](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html).
>* Para KDDI AU, consulte [esta página](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* Para Softbank, consulte [esta página](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm).


### Teste do conteúdo do email {#testing-the-email-content}

#### Pré-visualização da mensagem {#previewing-the-message}

O Adobe Campaign permite verificar se o formato da mensagem é compatível com um celular japonês.

Após definir seu conteúdo e inserir o assunto do email, você poderá verificar a exibição e a formatação quando a mensagem for criada.

Na **[!UICONTROL Preview]** guia da janela de edição de conteúdo, clicar em **[!UICONTROL More... > Deco-mail diagnostic]** permite:

* Verifique se as tags de conteúdo HTML estão em conformidade com as restrições do formato japonês
* Verifique se o número de imagens na mensagem não excede o limite imposto pelo formato (20 imagens)
* Verifique o tamanho total da mensagem (até 100kB)

   ![](assets/deco-mail_06.png)

#### Execução da regra de tipologia {#running-typology-rule}

In addition to the previewing diagnosis, a second check is carried out when sending a proof or a delivery: a specific typology rule, **[!UICONTROL Deco-mail check]**, is started during the analysis.

>[!CAUTION]
>
>Essa regra de tipologia só é executada se pelo menos um dos destinatários estiver configurado para receber emails no **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** ou **[!UICONTROL Decoration Mail (KDDI AU)]** formato.

Essa regra de tipologia permite verificar se o delivery respeita as [restrições de formato](#limitations-and-recommendations) definidas pelos operadores japoneses, especialmente em relação ao tamanho total do email, ao tamanho das seções HTML e texto, ao número de imagens nas mensagens e às tags no conteúdo HTML.

#### Envio de provas {#sending-proofs}

Você pode enviar provas para testar seu delivery. Quando você envia a prova, se estiver usando endereços de substituição, digite os endereços que correspondem ao formato do email do perfil usado.

For example, you can replace a profile&#39;s address by test@softbank.ne.jp if the email format for this profile was defined beforehand on **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

### Envio de mensagens {#sending-messages}

Para enviar um email para recipients com formatos de email japoneses com o Campaign, há duas opções:

* Criar dois deliveries: um somente para recipients japoneses e outro para outros recipients. Consulte [esta seção](#designing-a-specific-delivery-for-japanese-formats).
* Criar um único delivery e o Adobe Campaign detectará automaticamente o formato a ser usado. Consulte [esta seção](#designing-a-delivery-for-all-formats).

#### Criação de delivery específico para formatos japoneses {#designing-a-specific-delivery-for-japanese-formats}

Você pode criar um workflow que contenha dois deliveries: um para ser lido em um celular japonês e outro para recipients com formato do email padrão.

To do this, use the **[!UICONTROL Split]** activity in your workflow and define the Japanese email formats (Deco-mail, Decoration Mail and Decore Mail) as filtering conditions.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

#### Criação de delivery para todos os formatos {#designing-a-delivery-for-all-formats}

When Adobe Campaign dynamically manages the formats according to the domain (profiles with email formats defined as **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** or **[!UICONTROL Text]** ), you can send the same delivery to all of your recipients.

O contato da mensagem será exibido corretamente para os usuários em celulares japoneses, assim como para os recipients padrão.

>[!CAUTION]
>
>Respeite os recursos especiais associados a cada formato do email japonês (Deco-mail, Decoration Mail e Decore Mail). Para obter mais informações sobre as limitações, consulte [esta seção](#limitations-and-recommendations).
