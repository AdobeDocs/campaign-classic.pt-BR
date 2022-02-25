---
product: campaign
title: Definir o conteúdo de email no Adobe Campaign Classic
description: Saiba como definir o conteúdo de email ao usar o Adobe Campaign Classic.
feature: Email Design
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: ht
source-wordcount: '1990'
ht-degree: 100%

---

# Definir o conteúdo do email {#defining-the-email-content}

![](../../assets/common.svg)

## Remetente {#sender}

Para definir o nome e o endereço do remetente que aparecerá no cabeçalho das mensagens enviadas, clique no link **[!UICONTROL From]**.

![](assets/s_ncs_user_wizard_email02.png)

Todas as informações necessárias para criação dos cabeçalhos de mensagens de email devem ser inseridas nessa janela. Essas informações podem ser personalizadas. Para fazer isso, use os botões à direita dos campos de entrada para inserir campos de personalização.

Para saber como inserir e usar campos de personalização, consulte a seção [Sobre personalização](about-personalization.md).

>[!NOTE]
>
>* O endereço do remetente será usado para respostas por padrão.
>* Os parâmetros do cabeçalho não devem ficar vazios. Por padrão, eles contêm a entrada de valores ao configurar o assistente de implantação. Para obter mais informações, consulte o [Guia de Instalação](../../installation/using/deploying-an-instance.md).
>* O endereço do remetente é obrigatório para possibilitar o envio de um email (padrão RFC).
>* O Adobe Campaign verifica a sintaxe dos endereços de email inseridos.


>[!IMPORTANT]
>
>No contexto das verificações implementadas pelos Provedores de Serviços de Internet (ISPs) para combater emails não solicitados (spam), a Adobe recomenda criar contas de email que correspondam aos endereços especificados para deliveries e respostas. Verifique com o administrador do sistema de mensagens.

## Assunto da mensagem {#message-subject}

O assunto da mensagem é configurado no campo correspondente. Você pode inseri-lo diretamente no campo ou clicar no link **[!UICONTROL Subject]** para inserir um script. O link de personalização permite inserir campos de banco de dados no assunto.

>[!IMPORTANT]
>
>O assunto da mensagem é obrigatório.

![](assets/s_ncs_user_wizard_email_object.png)

O conteúdo do campo será substituído pelo valor no perfil do recipient quando a mensagem for enviada.

Por exemplo, na mensagem acima, o assunto da mensagem é personalizado para cada recipient com dados do seu perfil.

>[!NOTE]
>
>O uso de campos de personalização é apresentado em [Sobre personalização](about-personalization.md).

Também é possível inserir emoticons na linha do assunto com a janela pop-up **[!UICONTROL Insert emoticon]**.

## Conteúdo da mensagem {#message-content}

>[!IMPORTANT]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

O conteúdo da mensagem é definido na seção inferior da janela de configuração de delivery.

As mensagens são enviadas em formato de texto ou HTML por padrão, de acordo com a preferência do recipient. Recomendamos a criação de conteúdo nos dois formatos para garantir que as mensagens possam ser exibidas corretamente em qualquer sistema de email. Para obter mais informações, consulte [Seleção de formatos de mensagem](#selecting-message-formats).

* Para importar um conteúdo HTML, clique no botão **[!UICONTROL Open]**. Também é possível colar o código-fonte diretamente na subguia **[!UICONTROL Source]**.

   Se estiver usando o [Editor de Conteúdo Digital](../../web/using/about-campaign-html-editor.md) (DCE), consulte [Seleção de um template de conteúdo](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

   >[!IMPORTANT]
   >
   >O conteúdo HTML deve ser criado antes, e depois importado para o Adobe Campaign. O editor de HTML não foi desenvolvido para criação de conteúdo.

   A subguia **[!UICONTROL Preview]** permite visualizar a renderização de cada conteúdo para um recipient. Os campos de personalização e os elementos condicionais do conteúdo são substituídos pelas informações correspondentes para o perfil selecionado.

   Os botões da barra de ferramentas fornecem acesso aos parâmetros padrão de ações e formatação da página HTML.

   ![](assets/s_ncs_user_wizard_email01_138.png)

   Você pode inserir imagens em mensagens de um arquivo local ou de uma biblioteca de imagens no Adobe Campaign. Para fazer isso, clique no ícone **[!UICONTROL Image]** e selecione a opção apropriada.

   ![](assets/s_ncs_user_wizard_email01_18.png)

   As imagens da biblioteca podem ser acessadas através da pasta **[!UICONTROL Resources>Online>Public resources]** na árvore de pastas. Consulte também [Adicionar imagens](#adding-images).

   O último botão na barra de ferramentas permite inserir campos de personalização.

   >[!NOTE]
   >
   >O uso de campos de personalização é apresentado em [Sobre personalização](about-personalization.md).

   As guias na parte inferior da página permitem exibir o código HTML da página que está sendo criada e exibir a renderização da mensagem com sua personalização. Para iniciar essa exibição, clique em **[!UICONTROL Preview]** e selecione um recipient usando o botão **[!UICONTROL Test personalization]** na barra de ferramentas. Você pode selecionar um recipient no(s) target(s) definido(s) ou escolher outro.

   ![](assets/s_ncs_user_wizard_email01_139.png)

   Você pode validar a mensagem HTML. Também é possível visualizar o conteúdo do cabeçalho do email.

   ![](assets/s_ncs_user_wizard_email01_140.png)

* Para importar um conteúdo de texto, clique no botão **[!UICONTROL Open]** ou na guia **[!UICONTROL Text Content]** para inserir o conteúdo da mensagem quando exibido no formato de texto. Use os botões da barra de ferramentas para acessar ações no conteúdo. O último botão permite inserir campos de personalização.

   ![](assets/s_ncs_user_wizard_email01_141.png)

   Já para o formato HTML, clique na guia **[!UICONTROL Preview]** na parte inferior da página para exibir a renderização da mensagem com sua personalização.

   ![](assets/s_ncs_user_wizard_email01_142.png)


## Definir o conteúdo interativo {#amp-for-email-format}

O Adobe Campaign possibilita experimentar o novo formato interativo [AMP for email](https://amp.dev/pt_br/about/email/), que permite o envio de emails dinâmicos, sob determinadas condições.

Para obter mais informações, consulte [esta seção](defining-interactive-content.md).

## Utilização de gerenciamento de conteúdo {#using-content-management}

O conteúdo da entrega pode ser definido por meio dos formulários de gerenciamento de conteúdo, diretamente no assistente de entrega. Para fazer isso, você deve consultar o template de publicação do gerenciamento de conteúdo que será usado na guia **[!UICONTROL Advanced]** das propriedades de delivery.

![](assets/s_ncs_content_in_delivery.png)

Uma guia adicional permite inserir conteúdo que será integrado e formatado automaticamente de acordo com as regras de gestão de conteúdo.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>Para obter mais informações sobre o gerenciamento de conteúdo no Adobe Campaign, consulte [esta seção](about-content-management.md).

## Inserir emoticons {#inserting-emoticons}

É possível inserir emoticons no conteúdo de e-mail.

1. Clique no ícone **[!UICONTROL Insert emoticon]**.
1. Selecione um emoticon na janela pop-up.

   ![](assets/emoticon_4.png)

1. Clique no botão **[!UICONTROL Close]** quando terminar.

Para personalizar a lista de emoticons, consulte esta [página](customizing-emoticon-list.md).

## Adição de imagens {#adding-images}

As entregas de email em formato HTML podem conter imagens. No assistente do delivery, você pode importar uma página HTML contendo imagens ou inserir imagens diretamente usando o editor de HTML pelo ícone **[!UICONTROL Image]**.

As imagens podem ser:

* Uma imagem local ou de um servidor
* Uma imagem armazenada na biblioteca de recursos públicos do Adobe Campaign

   Os recursos públicos podem ser acessados por meio do nó **[!UICONTROL Resources > Online]** da hierarquia do Adobe Campaign. Elas são agrupadas em uma biblioteca e podem ser incluídas em mensagens de email, mas também podem ser usadas para campanhas ou tarefas, ou para gestão de conteúdo.

* Um ativo compartilhado com a Adobe Experience Cloud. Consulte [esta seção](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

>[!IMPORTANT]
>
>Para incluir imagens nas mensagens de email usando o assistente do delivery, a instância do Adobe Campaign deve ser configurada para habilitar a gestão de recursos públicos. Esse procedimento pode ser executado no assistente de implantação. Consulte [esta seção](../../installation/using/deploying-an-instance.md) para obter mais informações sobre a configuração.

O assistente do delivery permite adicionar imagens locais ou armazenadas na biblioteca ao conteúdo de mensagens. Para fazer isso, clique no botão **[!UICONTROL Image]** na barra de ferramentas do conteúdo HTML.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>Para que os recipients possam exibir as imagens incluídas nas mensagens recebidas, essas mensagens devem estar disponíveis em um servidor acessível externamente.

Para gerenciar as imagens por meio do assistente do delivery:

1. Clique no ícone **[!UICONTROL Tracking & Images]** na barra de ferramentas.
   ![](assets/s_ncs_user_email_del_img_param.png)

1. Selecione **[!UICONTROL Upload images]** na guia **[!UICONTROL Images]**.
1. Você pode escolher se deseja incluir as imagens na mensagem de email.
   ![](assets/s_ncs_user_email_del_img_upload.png)

* Você pode carregar imagens manualmente sem esperar a fase de análise de delivery. Para fazer isso, clique em **[!UICONTROL Upload the images straightaway...]**.
* Você pode especificar outro caminho para acessar as imagens no servidor de rastreamento. Para fazer isso, insira-o no campo **[!UICONTROL Images URL]**. Esse valor substitui o valor definido nos parâmetros do assistente de instalação.

Quando você abre conteúdo HTML com imagens incluídas no assistente do delivery, aparece uma mensagem com a opção de carregar as imagens imediatamente, de acordo com os parâmetros do delivery.

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
>* Os caminhos de acesso à imagem são modificados durante o carregamento manual ou ao enviar as mensagens.
> 
>* Para evitar problemas de desempenho, se você incluir imagens baixadas imediatamente de um URL personalizado como [anexo](attaching-files.md), cada tamanho de imagem não deve exceder 100.000 bytes por padrão. Esse limite recomendado pode ser configurado na [ lista de opções do Campaign Classic ](../../installation/using/configuring-campaign-options.md#delivery).


**Caso de uso: enviar uma mensagem com imagens**

Veja a seguir um exemplo de delivery com quatro imagens:

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

Essas imagens vêm de um diretório ou site local, como pode ser verificado na guia **[!UICONTROL Source]**.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

Clique no ícone **[!UICONTROL Tracking & Images]** e, em seguida, na guia **[!UICONTROL Images]** para iniciar a detecção de imagens na mensagem.

Para cada imagem detectada, você pode ver seu status:

* Se uma imagem for armazenada no local ou localizada em outro servidor, mesmo que esse servidor seja visível externamente (em um site da Internet, por exemplo), ela será detectada como **[!UICONTROL Not yet online]**.
* As imagens são detectadas como **[!UICONTROL Already online]** se tiverem sido carregadas anteriormente durante a criação de outro delivery.
* No assistente de implantação, é possível definir as URLs nas quais a detecção de imagem não está habilitada: o carregamento dessas imagens será **[!UICONTROL Skipped]**.

>[!NOTE]
>
>As imagens são identificadas pelo seu conteúdo e não pelos caminhos de acesso. Isto significa que uma imagem carregada anteriormente com um nome diferente ou em um diretório diferente será detectada como **[!UICONTROL Already online]**.

Durante a fase de análise, as imagens são carregadas automaticamente no servidor para que sejam acessíveis externamente, exceto para as imagens locais que devem ser carregadas anteriormente.

Você pode trabalhar com antecedência e carregar imagens para que elas possam ser visualizadas por outros operadores do Adobe Campaign. Isso pode ser útil se você trabalhar de forma colaborativa. Para fazer isso, clique em **[!UICONTROL Upload the images straightaway...]** para fazer upload das imagens no servidor.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>As URLs das imagens no email, e seus nomes em particular, são então modificadas.

Quando as imagens estiverem online, você poderá exibir as alterações nos nomes e nos caminhos na guia **[!UICONTROL Source]** da mensagem.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

Se você selecionar **[!UICONTROL Include the images in the email]**, será possível escolher imagens para incluir na coluna correspondente.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>Se imagens locais forem incluídas na mensagem, você deverá confirmar as alterações no código-fonte dela.

## Inserir um código de barras personalizado{#insert-a-barcode}

O módulo de geração de código de barras permite criar vários tipos de códigos de barras que estão em conformidade com muitos padrões comuns, incluindo códigos de barras 2D.

É possível gerar um código de barras de forma dinâmica como um bitmap usando um valor definido por meio de critérios do cliente. Os códigos de barra personalizados podem ser incluídos em campanhas de email. O recipient pode imprimir a mensagem e mostrá-la à empresa emissora para exame (ao verificar, por exemplo).

Para inserir um código de barras em um email, coloque o cursor no conteúdo onde deseja exibi-lo e clique no botão de personalização. Selecione **[!UICONTROL Include > Barcode...]**.

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
1. O campo **[!UICONTROL Value]** permite definir o valor do código de barras. Um valor pode corresponder a uma oferta especial e pode ser a função de um critério, ele pode ser o valor de um campo de banco de dados vinculado aos clientes.

   Este exemplo mostra um código de barras do tipo EAN-8, ao qual foi adicionado o número da conta de um recipient. Para adicionar esse número de conta, clique no botão de personalização à direita do campo **[!UICONTROL Value]** e selecione **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. O campo **[!UICONTROL Height]** permite configurar a altura do código de barras sem alterar sua largura, alterando a quantidade do espaço entre cada barra.

   Não há controle de entrada restritivo dependendo do tipo de código de barras. Se um valor de código de barras estiver incorreto, ele só será visível no modo de **Pré-visualização**, onde o código de barras estará riscado em vermelho.

   >[!NOTE]
   >
   >O valor atribuído a um código de barras depende do seu tipo. Por exemplo, um tipo EAN-8 deve ter exatamente 8 números.
   >
   >O botão de personalização à direita do campo **[!UICONTROL Value]** também permite adicionar dados, além do valor. Isso enriquece o código de barras, desde que o padrão do código de barras o aceite.
   >
   >Por exemplo, se estiver usando um código de barras do tipo GS1-128 e quiser inserir o número da conta de um recipient, além do valor, clique no botão de personalização e selecione **[!UICONTROL Recipient > Account number]**. Se o número da conta do recipient selecionado for inserido corretamente, ele será considerado pelo código de barras.

Após configurar estes elementos, você pode finalizar seu email e enviá-lo. Para evitar erros, sempre verifique se o conteúdo é exibido corretamente antes de executar um delivery clicando na guia **[!UICONTROL Preview]**.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Se o valor de um código de barras estiver incorreto, seu bitmap é exibido riscado em vermelho.

![](assets/barcode_insert_11.png)
