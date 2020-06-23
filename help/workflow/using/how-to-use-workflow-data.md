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
source-git-commit: bb35d2ae2d40aaef3bb381675d0c36ffb100b242
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 49%

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

1. Instale um par de chaves GPG para sua instância usando o Painel [de controle](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >O Painel de controle está disponível para todos os clientes hospedados no AWS (exceto para clientes que hospedam suas instâncias de marketing no local).

1. Se sua instalação do Adobe Campaign for hospedada pela Adobe, entre em contato com o Atendimento ao cliente da Adobe para ter os utilitários necessários instalados no servidor.
1. Se a instalação do Adobe Campaign estiver no local, instale o utilitário que deseja usar (por exemplo: GPG, GZIP) e as chaves necessárias (chave de criptografia) no servidor de aplicativos.

Em seguida, você pode usar comandos ou códigos na **[!UICONTROL Script]** guia da atividade ou em uma **[!UICONTROL JavaScript code]** atividade. Um exemplo é apresentado no caso de uso abaixo.

**Tópicos relacionados:**

* [Descompactação ou descriptografia de um arquivo antes do processamento](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)
* [atividade](../../workflow/using/extraction--file-.md)de extração de dados (arquivo).

### Caso de uso: Criptografar e exportar dados usando uma chave instalada no Painel de controle {#use-case-gpg-encrypt}

Nesse caso de uso, criaremos um fluxo de trabalho para criptografar e exportar dados usando uma chave instalada no Painel de controle.

As etapas para executar esse caso de uso são as seguintes:

1. Gere um par de chaves GPG (público/privado) usando um utilitário GPG e, em seguida, instale a chave pública no Painel de controle. As etapas detalhadas estão disponíveis na documentação [do Painel de](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)controle.

1. No Campaign Classic, crie um fluxo de trabalho para exportar os dados e exportá-los usando a chave privada que foi instalada por meio do Painel de controle. Para fazer isso, criaremos um fluxo de trabalho da seguinte maneira:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** atividade: Neste exemplo, queremos executar um query para público alvo dos dados do banco de dados que queremos exportar.
   * **[!UICONTROL Data extraction (file)]** atividade: Extrai os dados em um arquivo.
   * **[!UICONTROL JavaScript code]** atividade: Criptografa os dados a serem extraídos.
   * **[!UICONTROL File transfer]** atividade: Envia os dados para uma fonte externa (neste exemplo, um servidor SFTP).

1. Configure a **[!UICONTROL Query]** atividade para público alvo dos dados desejados do banco de dados. Para obter mais informações, consulte [esta seção](../../workflow/using/query.md).

1. Abra a **[!UICONTROL Data extraction (file)]** atividade e configure-a de acordo com suas necessidades. Os conceitos globais sobre como configurar a atividade estão disponíveis [nesta seção](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Abra a **[!UICONTROL JavaScript code]** atividade e copie e cole o comando abaixo para criptografar os dados a serem extraídos.

   >[!IMPORTANT]
   >
   >Certifique-se de substituir o valor da **impressão digital** do comando pela impressão digital da chave pública instalada no Painel de controle.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch -yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Abra a **[!UICONTROL File transfer]** atividade e especifique o servidor SFTP para o qual deseja enviar o arquivo. Os conceitos globais sobre como configurar a atividade estão disponíveis [nesta seção](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Agora você pode executar o fluxo de trabalho. Depois de executado, o público alvo de dados pelo query será exportado para o servidor SFTP em um arquivo .gpg criptografado.

   ![](assets/gpg-sftp-encrypt.png)
