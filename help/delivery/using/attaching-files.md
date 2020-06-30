---
title: Anexo de arquivos
seo-title: Anexo de arquivos
description: Anexo de arquivos
seo-description: null
page-status-flag: never-activated
uuid: a4dc1908-a6ef-4bc8-a310-605fc80c34ca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: f3666c12-5e6f-452e-b1d6-b69a7e9f6f6e
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: b60b5fad24c1237981f66315e7cf585c79f82641
workflow-type: ht
source-wordcount: '949'
ht-degree: 100%

---


# Anexo de arquivos{#attaching-files}

## Sobre anexos de email {#about-email-attachments}

Você pode anexar um ou mais arquivos a um delivery de email.

>[!NOTE]
>
>Para evitar problemas de desempenho, é recomendável não incluir mais de um anexo por email. O limite recomendado pode ser configurado na [lista de opções do Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

Há dois casos possíveis:

* Selecione um arquivo para anexar ao delivery como está.
* Personalize o conteúdo do anexo para cada recipient. Nesse caso, você precisa criar um **anexo calculado**: o nome do anexo é computado no momento do delivery de cada mensagem, dependendo do recipient. O conteúdo também pode ser personalizado e convertido em formato PDF no momento do delivery, se você tiver a opção **Impressão digital de variáveis**.

>[!NOTE]
>
>Esse tipo de configuração é geralmente executada nos templates do delivery. Para obter mais informações, consulte [Sobre templates](../../delivery/using/about-templates.md).

## Anexo de arquivo local {#attaching-a-local-file}

Para anexar um arquivo local a um delivery, siga as etapas abaixo.

>[!NOTE]
>
>Você pode anexar vários arquivos a um delivery. Os anexos podem estar em qualquer formato, inclusive no formato zipado.

1. Clique no link **[!UICONTROL Attachments]**.
1. Clique no botão **[!UICONTROL Add]**.
1. Clique em **[!UICONTROL File...]** para selecionar o arquivo a ser anexado ao delivery.

   ![](assets/s_ncs_user_wizard_email_attachement.png)

Você também pode arrastar e soltar diretamente o arquivo no campo **[!UICONTROL Attachments]** do delivery, ou usar o ícone **[!UICONTROL Attach]** na barra de ferramentas do assistente do delivery,

![](assets/s_ncs_user_wizard_add_file_ico.png)

Após selecionar o documento, ele será carregado imediatamente no servidor para estar disponível no momento do delivery. Está listado no campo **[!UICONTROL Attachments]**.

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## Criação de anexos calculados {#creating-a-calculated-attachment}

Quando você cria um anexo calculado, o nome do anexo pode ser computado durante a análise ou a delivery de cada mensagem e pode depender do recipient. Ele também pode ser personalizado e convertido em PDF.

![](assets/s_ncs_user_wizard_attachment.png)

Para criar um anexo personalizado, siga estas etapas:

1. Clique no link **[!UICONTROL Attachments]**.
1. Clique no botão **[!UICONTROL Add]** e selecione **[!UICONTROL Calculated attachment]**.
1. Selecione o tipo de cálculo na lista suspensa **[!UICONTROL Type]**:

![](assets/s_ncs_user_wizard_email01_136.png)

As seguintes opções estão disponíveis:

* **O nome do arquivo é especificado ao criar o template do delivery**
* **O conteúdo do arquivo é personalizado e convertido em PDF durante o delivery de cada mensagem**
* **O nome do arquivo é computado durante a análise de delivery (não pode depender do perfil do recipient)**
* **O nome do arquivo é computado no momento do delivery para cada recipient (pode depender do recipient)**

### Anexo de arquivo local {#attach-a-local-file}

Se o anexo for um arquivo local, selecione a opção: **[!UICONTROL File name is specified when creating the delivery template]**. O arquivo é selecionado no local e carregado no servidor. Siga as etapas abaixo:

1. Selecione o arquivo a ser carregado no campo **[!UICONTROL Local file]**.
1. Especifique o rótulo se necessário. O rótulo substitui o nome do arquivo quando visualizado em sistemas de mensagens. Se nada for especificado, o nome do arquivo será usado por padrão.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. Se necessário, selecione **[!UICONTROL Upload file on the server]** e clique em **[!UICONTROL Update on server]** para iniciar a transferência.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

O arquivo está então disponível no servidor para ser anexado aos diferentes deliveries criados a partir desse template.

### Anexar uma mensagem personalizada {#attach-a-personalized-message}

A opção **[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]** permite selecionar um arquivo com campos de personalização, como o sobrenome e o nome do recipient pretendido.

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

Para este tipo de anexo, sigas as seguintes etapas de configuração:

1. Selecione o arquivo a ser carregado.

   >[!NOTE]
   >
   >O arquivo de origem deve ser criado no LibreOffice. A instância deve ser configurada com os pré-requisitos detalhados [nesta seção](../../installation/using/before-starting.md).

1. Especifique o rótulo se necessário.
1. Selecione **[!UICONTROL Upload file on the server]** e clique em **[!UICONTROL Update on server]** para iniciar a transferência.
1. Você pode exibir uma pré-visualização. Para fazer isso, selecione um recipient.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. Analise seu delivery e, em seguida, inicie-o.

   Cada recipient recebe um PDF personalizado anexado ao delivery.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

>[!NOTE]
>
>Para evitar problemas de desempenho, se incluir imagens baixadas em tempo real de um URL personalizado como anexo, cada tamanho de imagem não deve exceder 100.000 bytes por padrão. Esse limite recomendado pode ser configurado na [ lista das opções do Campaign Classic ](../../installation/using/configuring-campaign-options.md#delivery).

### Anexo de arquivo calculado {#attach-a-calculated-file}

Você pode calcular o nome do anexo durante a preparação do delivery. Para fazer isso, selecione a opção.**[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**

>[!NOTE]
>
>Essa opção é usada somente quando o delivery é enviado por um processo externo ou um workflow.

1. Especifique o rótulo que deseja aplicar ao anexo.
1. Especifique o caminho de acesso do arquivo e seu nome exato na janela de definição.

   >[!IMPORTANT]
   >
   >O arquivo deve estar presente no servidor.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. Analise e inicie seu delivery.

   A computação do nome de arquivo pode ser vista no log de análise.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### Anexo de arquivo personalizado {#attach-a-personalized-file}

Ao selecionar o anexo, você pode escolher a opção **[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**. Em seguida, você pode mapear os dados de personalização do recipient com o nome do arquivo a ser enviado.

>[!NOTE]
>
>Essa opção é usada somente quando o delivery é enviado por um processo externo ou um workflow.

1. Especifique o rótulo que deseja aplicar ao anexo.
1. Especifique o caminho de acesso do arquivo e seu nome exato na janela de definição. Se o nome do arquivo for personalizado, você poderá usar os Campos de personalização para os valores relevantes.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!IMPORTANT]
   >
   >O arquivo deve estar presente no servidor.

1. Analise e inicie seu delivery.

   No exemplo abaixo, o arquivo anexado foi escolhido de acordo com seu nome definido nos campos de mesclagem.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### Configurações do anexo {#attachment-settings}

Para as duas primeiras opções, escolha **[!UICONTROL Upload file on the server]** ao selecionar a opção apropriada. O link **[!UICONTROL Update the file on the server]** permite iniciar o upload.

![](assets/s_ncs_user_wizard_email01_137.png)

Uma mensagem informa que o arquivo foi carregado no servidor:

![](assets/s_ncs_user_wizard_email01_1371.png)

Para uma alteração de arquivo, uma mensagem de aviso é exibida:

![](assets/s_ncs_user_wizard_email01_1372.png)

A guia **[!UICONTROL Advanced]** permite definir opções avançadas em arquivos anexados:

* Você pode definir opções de filtro para evitar o envio do arquivo anexado a todos os recipients. A opção **[!UICONTROL Enable filtering of recipients who will receive the attachment]** ativa um campo de entrada usado para definir um script de seleção de recipient, que deve ser inserido em JavaScript.
* Você pode criar um script do nome do arquivo para personalizá-lo.

   Insira seu texto na janela e use os campos de personalização disponíveis na lista suspensa. No exemplo a seguir, o nome do arquivo é personalizado para conter a data de hoje e o nome do recipient.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
