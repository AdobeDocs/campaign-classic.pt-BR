---
title: Adicionar anexos a mensagens transacionais com o Adobe Campaign Classic
description: Saiba como enviar emails transacionais com anexos individuais e/ou personalizados usando o Adobe Campaign Classic
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 24a50fcaad4d9081e5504652eb5b73aa7db1e65f
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 39%

---


# Caso de uso: Envio de emails transacionais com anexos{#transactional-email-with-attachments}

O objetivo deste caso de uso é adicionar anexos de email em tempo real a expedições de saída.

## Etapas principais {#key-steps}

Neste cenário, você aprenderá a enviar emails transacionais com anexos individuais e/ou personalizados. Os anexos não serão carregados previamente no servidor de mensagens transacionais: em vez disso, serão gerados em tempo real.

Ao capturar interações ou detalhes do cliente, talvez seja necessário enviar essas informações novamente ao cliente no final do processo, por exemplo, em um arquivo PDF anexado a um email.

Abaixo estão os principais passos desse cenário:

1. O cliente entra no site, localiza um produto que deseja comprar.
1. O cliente seleciona o produto e personaliza algumas opções.
1. O cliente conclui a transação.
1. Um email é enviado ao cliente confirmando a transação. Como não é recomendado enviar PII (Informações pessoais identificáveis) para fora no email, um PDF seguro é gerado e anexado ao email.
1. O cliente recebe o email e seu anexo contendo os dados relevantes.

Nesse cenário, os anexos não são pré-criados, mas adicionados dinamicamente aos e-mails de saída, o que oferta os seguintes benefícios:

* Isso permite que você personalize o conteúdo do anexo.
* Se o anexo estiver associado a uma transação (como no cenário de exemplo descrito acima), ele pode conter dados dinâmicos que são gerados durante o processo do cliente.
* Anexar arquivos PDF otimiza a segurança, pois é possível criptografá-los e enviá-los por HTTPS.

## Recomendações {#important-notes}

Antes de implementar este cenário, leia atentamente as diretrizes abaixo:

* As instâncias de Mensagens Transacionais não devem ser usadas para armazenar, exportar ou carregar arquivos ou dados. Eles só podem ser usados para dados do evento e informações relacionadas. Elas não devem ser consideradas como um sistema de armazenamento de arquivos.
* Como não há acesso direto às instâncias de Mensagens transacionais ou servidores fora da Adobe, não há forma padrão de enviar esses arquivos nesses servidores (sem acesso FTP).
* Não é correto usar o espaço em disco nas instâncias de Mensagens Transacionais para armazenar arquivos de qualquer tipo, nem mesmo para anexos.
* Você precisa usar outro sistema de disco online para hospedar esses arquivos Você precisa de um acesso FTP a este sistema e deve ser capaz de gravar e excluir arquivos.

## Implementação {#implementation}

O diagrama abaixo mostra as diferentes etapas ao implementar este cenário:

![](assets/message-center-uc1.png)

Para adicionar um anexo de email dinamicamente a um mensagen transacional, siga as etapas abaixo:

1. Start ao criar seu anexo. Para obter mais informações, consulte [esta seção](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Isso permite anexar os arquivos a um email, mesmo se eles não estiverem hospedados na instância de execução.

1. Você pode enviar emails por meio de um gatilho de mensagem SOAP Na chamada SOAP, há um parâmetro de URL (attachmentURL).

   Para saber mais sobre solicitações SOAP, consulte [Descrição do evento](../../message-center/using/event-description.md).

1. When designing your email, click **[!UICONTROL Attachment]**.

1. In the **[!UICONTROL Attachment definition]** screen, enter the SOAP attachment parameter:

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. Quando a mensagem for processada, o sistema obterá o arquivo do local remoto (servidor de terceiros) e o anexará à mensagem individual.

   Como esse parâmetro pode ser uma variável, ele deve aceitar a variável de URL remota totalmente formada do seu arquivo, enviado pela chamada SOAP.

   ![](assets/message-center-uc2.png)
