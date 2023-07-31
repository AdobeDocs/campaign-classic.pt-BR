---
product: campaign
title: Compactação ou criptografia de um arquivo
description: Saiba como compactar ou criptografar um arquivo no Campaign antes do processamento
feature: Data Management
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '548'
ht-degree: 100%

---

# Compactar ou criptografar um arquivo {#zipping-or-encrypting-a-file}



O Adobe Campaign permite exportar arquivos compactados ou criptografados. Ao definir uma exportação por meio da atividade **[!UICONTROL Data extraction (file)]**, é possível definir um pós-processamento para compactar ou criptografar o arquivo.

Para fazer isso:

1. Instale um par de chaves GPG para sua instância usando o [Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=pt-BR#encrypting-data).

   >[!NOTE]
   >
   >O Painel de controle é restrito a usuários Administradores e está disponível somente para determinadas versões do Campaign. [Saiba mais](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=pt-BR)
   >

1. Caso sua instalação do Adobe Campaign seja hospedada pela Adobe, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para ter os utilitários necessários instalados no servidor.
1. Caso a instalação do Adobe Campaign seja no local, instale o utilitário que deseja usar (por exemplo: GPG, GZIP) e as chaves necessárias (chave de criptografia) no servidor de aplicativos.

Em seguida, você pode usar comandos ou códigos na guia **[!UICONTROL Script]** da atividade ou em uma atividade **[!UICONTROL JavaScript code]**. Um exemplo é apresentado no caso de uso abaixo.

**Tópicos relacionados:**

* [Descompactar ou descriptografar um arquivo antes do processamento](../../platform/using/unzip-decrypt.md)
* [Atividade de extração de dados (arquivo)](../../workflow/using/extraction--file-.md).

## Caso de uso: criptografar e exportar dados usando uma chave instalada no Painel de controle {#use-case-gpg-encrypt}

Nesse caso de uso, criaremos um fluxo de trabalho para criptografar e exportar dados usando uma chave instalada no Painel de controle.

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](#video)

As etapas para executar esse caso de uso são as seguintes:

1. Gere um par de chaves GPG (público/privado) usando um utilitário GPG e, em seguida, instale a chave pública no Painel de controle. As etapas detalhadas estão disponíveis na [documentação do Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=pt-BR#encrypting-data).

1. Crie um workflow para exportação de dados no Campaign Classic e criptografe-o usando a chave privada que foi instalada através do Painel de controle. Para fazer isso, criaremos um workflow da seguinte maneira:

   ![](assets/gpg-workflow-encrypt.png)

   * Atividade **[!UICONTROL Query]**: neste exemplo, queremos executar um query para direcionar os dados do banco de dados que queremos exportar.
   * Atividade **[!UICONTROL Data extraction (file)]**: extrair os dados em um arquivo.
   * Atividade **[!UICONTROL JavaScript code]**: criptografar os dados que serão extraídos.
   * Atividade **[!UICONTROL File transfer]**: enviar os dados para uma fonte externa (neste exemplo, um servidor SFTP).

1. Configure a atividade **[!UICONTROL Query]** para direcionar os dados desejados a partir do banco de dados. Para obter mais informações, consulte [esta seção](../../workflow/using/query.md).

1. Abra a atividade **[!UICONTROL Data extraction (file)]** e configure-a de acordo com suas necessidades. Os conceitos globais sobre como configurar a atividade estão disponíveis [nesta seção](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Abra a atividade **[!UICONTROL JavaScript code]** e copie e cole o comando abaixo para criptografar os dados que serão extraídos.

   >[!IMPORTANT]
   >
   >Substitua o valor **impressão digital** do comando pela impressão digital da chave pública instalada no Painel de controle.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Abra a atividade **[!UICONTROL File transfer]** e especifique o servidor SFTP para o qual deseja enviar o arquivo. Os conceitos globais sobre como configurar a atividade estão disponíveis [nesta seção](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Agora você pode executar o workflow. Após a execução, o direcionamento de dados pelo query será exportado para o servidor SFTP em um arquivo .gpg criptografado.

## Tutorial em vídeo {#video}

Este vídeo mostra como usar uma chave GPG para criptografar dados e também está disponível em

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
