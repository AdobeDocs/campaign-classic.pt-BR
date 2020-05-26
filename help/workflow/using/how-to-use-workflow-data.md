---
title: Como usar os dados de workflow
seo-title: Como usar os dados de workflow
description: Como usar os dados de workflow
seo-description: null
page-status-flag: never-activated
uuid: ed03f14b-1b53-426e-9213-22cb2f3deb19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: ec3844ca-8d80-4ddc-b08c-f18a6919bb28
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 94%

---


# Como usar os dados de workflow{#how-to-use-workflow-data}

## Atualização do banco de dados {#updating-the-database}

Todos os dados coletados podem ser usados para atualizar o banco de dados ou nos deliveries. Por exemplo, você pode enriquecer as possibilidades de personalização do conteúdo da mensagem (incluir o número de contratos na mensagem, especificar o carrinho de compras comum do ano passado, etc.) ou detalhar o público alvo (enviar uma mensagem aos cotitulares do contrato, ter como target os mil melhores assinantes dos serviços online e etc.). Esses dados também podem ser exportados ou arquivados em uma lista.

### Atualizações diretas e listas {#lists-and-direct-updates}

Os dados do banco de dados do Adobe Campaign e as listas existentes podem ser atualizados usando duas atividades dedicadas:

* A atividade de **[!UICONTROL List update]** permite armazenar worktables em um DataList.

   Você pode selecionar uma lista existente ou criar uma. Nesse caso, o nome e possivelmente a pasta de registro são calculados.

   ![](assets/s_user_create_list.png)

   Consulte [Atualização da lista](../../workflow/using/list-update.md).

* A atividade **[!UICONTROL Update data]** realiza uma atualização em massa dos campos no banco de dados.

   Para obter mais informações, consulte [Atualização de dados](../../workflow/using/update-data.md).

### Gestão de assinatura/unsubscription {#subscription-unsubscription-management}

Para saber mais sobre subscrição e cancelamento de subscrição de recipients de um serviço de informações via workflow, consulte [Serviços de subscrição](../../workflow/using/subscription-services.md).

## Envio por workflow {#sending-via-a-workflow}

### Atividade de delivery {#delivery-activity}

A atividade de delivery é detalhada em [Delivery](../../workflow/using/delivery.md).

### Enriquecimento e target de deliveries {#enriching-and-targeting-deliveries}

Os deliveries podem processar dados de workflows para personalizar o conteúdo ou dentro da estrutura de seleção do público alvo.

Por exemplo, dentro da estrutura de um delivery de mala direta, você pode incluir os dados adicionais, obtidos da manipulação de dados realizada no workflow, no arquivo de extração:

![](assets/s_advuser_add_data_postal_mail.png)

Além dos campos de personalização habituais, você pode adicionar campos de personalização a partir de estágios do workflow ao conteúdo do delivery. Os dados adicionais definidos nas atividades de workflow podem ser mantidos e acessíveis no assistente de delivery, conforme mostrado no exemplo abaixo, para definir o nome do arquivo de output dentro da estrutura de delivery de mala direta:

![](assets/s_advuser_using_additional_data.png)

Os dados contidos na tabela de workflow são identificados pelo seu nome: ele é sempre composto pelo link **targetData** . Para obter mais informações, consulte [Dados de target](../../workflow/using/data-life-cycle.md#target-data).

Dentro da estrutura de delivery de email, os campos de personalização também podem usar dados da extensão do target executada nos estágios de workflows para construção do target, conforme mostrado no exemplo abaixo:

![](assets/s_advuser_add_data_email.png)

Se um código de segmento for especificado em uma atividade de target, ele será adicionado a uma coluna específica da tabela de workflow e será oferecido junto com os campos de personalização. To display all personalization fields, click the **[!UICONTROL Target extension > Other...]** link accessible via the personalization button.

![](assets/s_advuser_segment_code_select.png)

## Exportação de dados {#exporting-data}

### Compactação ou criptografia de um arquivo {#zipping-or-encrypting-a-file}

O Adobe Campaign permite exportar arquivos compactados ou criptografados. When defining an export through a **[!UICONTROL Data extraction (file)]** activity, you can define a post-processing to zip or to encrypt the file.

Para fazer isso:

* Se a sua instalação do Adobe Campaign estiver hospedada pela Adobe: envie uma solicitação para [Suporte](https://support.neolane.net) para ter os utilitários necessários instalados no servidor.
* Se a instalação do Adobe Campaign estiver no local: instale o utilitário que deseja usar (por exemplo: GPG, GZIP) e as chaves necessárias (chave de criptografia) no servidor de aplicativos.

Você pode usar comandos ou código, como:

```
function encryptFile(file) {  
  var systemCommand = “gpg --encrypt --recipient  recipientToEncryptTo ” + file;  
  var result = execCommand(systemCommand, true); 
}
```

Ao importar um arquivo, você também pode descompactar ou descriptografar. Consulte [Descompactação ou descriptografia de um arquivo antes do processamento](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)
