---
product: campaign
title: Descompactação ou descriptografia de um arquivo
description: Saiba como descompactar ou descriptografar um arquivo no Campaign antes do processamento
feature: Workflows, Encryption
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 100%

---


# Descompactar ou descriptografar um arquivo {#unzipping-or-decrypting-a-file-before-processing}

O Adobe Campaign permite importar arquivos compactados ou criptografados. Antes de serem lidos em uma atividade [Data loading (file)](../../workflow/using/data-loading-file.md), é possível definir um pré-processamento para descompactar ou descriptografar o arquivo.

>[!IMPORTANT]
>
>Não é possível descompactar arquivos com mais de 4 GB.

Para fazer isso:

1. Use o [Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=pt-BR#decrypting-data) para gerar um par de chaves públicas/privadas para permitir a descriptografia de arquivos.

   >[!NOTE]
   >
   >O Painel de controle é acessível a todos os usuários administradores. As etapas para conceder acesso de Administrador a um usuário estão detalhadas [nesta página](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=pt-BR#discover-control-panel).
   >
   >Observe que sua instância deve estar hospedada no AWS e atualizada com a [build mais recente disponível](../../rn/using/rn-overview.md). Saiba como verificar a versão [nesta seção](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Para verificar se sua instância está hospedada no AWS, siga as etapas detalhadas [nesta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=pt-BR).

1. Caso a instalação do Adobe Campaign seja no local, instale o utilitário que deseja usar (por exemplo: GPG, GZIP) e as chaves necessárias (chave de criptografia) no servidor de aplicativos.

   Caso sua instalação do Adobe Campaign seja hospedada pela Adobe, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para que os utilitários necessários sejam instalados no servidor.

Em seguida, você pode usar os comandos de pré-processamento desejados em seus workflows:

1. Adicione e configure uma atividade **[!UICONTROL File transfer]** no workflow.
1. Adicione uma atividade **[!UICONTROL Data loading (file)]** e defina o formato do arquivo.
1. Marque a opção **[!UICONTROL Pre-process the file]**.
1. Selecione o comando de pré-processamento que deseja aplicar.
1. Adicione outras atividades para gerenciar dados provenientes do arquivo.
1. Salve e execute seu workflow.

Um exemplo é apresentado no caso de uso abaixo.

**Tópicos relacionados:**

* [Atividade de carregamento de dados (arquivo)](../../workflow/using/data-loading-file.md).
* [Compactar ou criptografar um arquivo](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Caso de uso: importação de dados criptografados usando uma chave gerada pelo Painel de controle {#use-case-gpg-decrypt}

Nesse caso de uso, criaremos um fluxo de trabalho para importar dados que foram criptografados em um sistema externo usando uma chave gerada no Painel de controle.

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](#video)

As etapas para executar esse caso de uso são as seguintes:

1. Use o Painel de controle para gerar um par de chaves (público/privado). As etapas detalhadas estão disponíveis na [documentação do Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=pt-BR#decrypting-data).

   * A chave pública será compartilhada com o sistema externo, que a usará para criptografar os dados que serão enviados para o Campaign.
   * A chave privada será usada pelo Campaign Classic para descriptografar os dados criptografados recebidos.

   ![](assets/gpg_generate.png)

1. No sistema externo, use a chave pública baixada a partir do Painel de controle para criptografar os dados que serão importados para o Campaign Classic.

1. No Campaign Classic, crie um workflow para importar os dados criptografados e descriptografá-los usando a chave privada instalada por meio do Painel de controle. Para fazer isso, criaremos um workflow da seguinte maneira:

   ![](assets/gpg_import_workflow.png)

   * Atividade **[!UICONTROL File transfer]**: transfere o arquivo de uma fonte externa para o Campaign Classic. Neste exemplo, queremos transferir o arquivo de um servidor SFTP.
   * Atividade **[!UICONTROL Data loading (file)]**: carrega os dados do arquivo no banco de dados e os decodifica usando a chave privada gerada no Painel de controle.

1. Abra a atividade **[!UICONTROL File transfer]** e especifique a conta externa da qual deseja importar o arquivo .gpg criptografado.

   ![](assets/gpg_key_transfer.png)

   Os conceitos globais sobre como configurar a atividade estão disponíveis [nesta seção](../../workflow/using/file-transfer.md).

1. Abra a atividade **[!UICONTROL Data loading (file)]** e configure-a de acordo com suas necessidades. Os conceitos globais sobre como configurar a atividade estão disponíveis [nesta seção](../../workflow/using/data-loading-file.md).

   Adicione um estágio de pré-processamento à atividade para descriptografar os dados recebidos. Para fazer isso, selecione a opção **[!UICONTROL Pre-process the file]** e **[!UICONTROL Decrypt]** na lista suspensa **[!UICONTROL Command]**:

   ![](assets/gpg_load.png)

   >[!NOTE]
   >
   >Se forem necessárias alterações nos comandos disponíveis, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para ajustar as configurações de preProcessCommand.
   >
   >Se estiver trabalhando com uma implantação híbrida, você poderá configurar esses comandos diretamente do arquivo de configuração do servidor (serverConf.xml). [Saiba como configurar comandos de pré-processamento no arquivo de configuração do servidor](../../installation/using/the-server-configuration-file.md#preprocesscommand)

1. Clique em **[!UICONTROL OK]** para confirmar a configuração da atividade.

1. Agora você pode executar o workflow. Depois de executado, você pode verificar nos logs do workflow se a descriptografia foi executada e se os dados do arquivo foram importados.

   ![](assets/gpg_run.png)

## Tutorial em vídeo {#video}

Este vídeo mostra como usar uma chave GPG para descriptografar dados.

>[!VIDEO](https://video.tv.adobe.com/v/41363?quality=12&captions=por_br)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
