---
product: campaign
title: Enviar emails transacionais com anexos
description: Saiba como enviar emails transacionais com anexos individuais e/ou personalizados usando o Adobe Campaign
feature: Transactional Messaging
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: ht
source-wordcount: '624'
ht-degree: 100%

---

# Caso de uso: enviar emails transacionais com anexos {#transactional-email-with-attachments}

![](../../assets/v7-only.svg)

O objetivo deste caso de uso é adicionar anexos de email, em tempo real, a expedições de saída.

## Principais etapas {#key-steps}

Neste cenário, veremos como enviar emails transacionais com anexos individuais/personalizados. Os anexos não serão carregados previamente no servidor de mensagens transacionais, serão gerados em tempo real.

Ao capturar interações ou detalhes do cliente, talvez seja necessário enviar essas informações novamente ao cliente no final do processo, por exemplo, em um arquivo PDF anexado a um email.

Abaixo estão as principais etapas desse cenário:

1. O cliente entra no site, localiza um produto que deseja comprar.
1. O cliente seleciona o produto e personaliza algumas opções.
1. O cliente conclui a transação.
1. Um email é enviado ao cliente confirmando a transação. Como não é recomendado enviar PII (Informações pessoais identificáveis) no email, um PDF seguro é gerado e anexado ao email.
1. O cliente recebe o email e seu anexo contendo todos os dados relevantes.

Nesse cenário, os anexos não são pré-criados, mas adicionados instantaneamente aos emails de saída, que oferecem os seguintes benefícios:

* Assim, também é possível personalizar o conteúdo do anexo.
* Além disso, se o anexo estiver associado a uma transação (como no exemplo acima), talvez seja necessário que ele contenha dados dinâmicos gerados durante o processo do cliente.
* Anexar arquivos PDF otimiza a segurança, pois é possível criptografá-los e enviá-los por HTTPS.

>[!NOTE]
>
>Para evitar problemas de desempenho, se você incluir imagens baixadas online de um URL personalizado como anexo, cada tamanho de imagem não deverá exceder 100.000 bytes por padrão. Esse limite recomendado pode ser configurado na [ lista das opções do Campaign Classic ](../../installation/using/configuring-campaign-options.md#delivery).

## Recomendações {#important-notes}

Antes de implementar este cenário, leia atentamente as diretrizes abaixo:

* As instâncias de mensagens transacionais não devem ser usadas para armazenar, exportar ou carregar arquivos ou dados. Eles só podem ser usados para dados do evento e informações relacionadas. Elas não devem ser consideradas como um sistema de armazenamento de arquivos.
* Como não há acesso direto às instâncias de Mensagens transacionais ou servidores fora da Adobe, não há forma padrão de enviar esses arquivos nesses servidores (sem acesso ao FTP).
* Não é contratualmente correto usar o espaço em disco nas instâncias de mensagens transacionais para armazenar arquivos de qualquer tipo, nem mesmo anexos.
* Você precisa usar outro sistema de disco online para hospedar esses arquivos Você precisa de um acesso FTP para este sistema e ser capaz de gravar e excluir arquivos.

>[!NOTE]
>
>Para evitar problemas de desempenho, é recomendável não incluir mais de um anexo por email. O limite recomendado pode ser configurado na [lista de opções do Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

## Implementação {#implementation}

O diagrama abaixo mostra as diferentes etapas ao implementar este cenário:

![](assets/message-center-uc1.png)

Para adicionar um anexo de email rapidamente a uma mensagem transacional, siga as etapas abaixo:

1. Comece criando seu anexo. Para obter mais informações, consulte [esta seção](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Isso permite anexar os arquivos a um email, mesmo se eles não estiverem hospedados na instância de execução.

1. Você pode enviar emails por meio de um gatilho de mensagem SOAP Na chamada SOAP, há um parâmetro de URL (attachmentURL).

   Para saber mais sobre solicitações SOAP, consulte [Descrição do evento](../../message-center/using/event-description.md).

1. Ao criar o email, clique em **[!UICONTROL Attachment]**.

1. Na tela **[!UICONTROL Attachment definition]**, digite o parâmetro de anexo SOAP:

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. Quando a mensagem é processada, o sistema obtém o arquivo do local remoto (servidor de terceiros) e o anexa à mensagem individual.

   Como esse parâmetro pode ser uma variável, ele deve aceitar a variável de URL remota totalmente formada do seu arquivo, enviado pela chamada SOAP.

   ![](assets/message-center-uc2.png)
