---
product: campaign
title: Arquivamento de email
description: Arquivamento de email
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: dccf72b200cad9ba160a496cdd13ba39c5599008
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 3%

---

# Configurar email Cco {#email-archiving}

![](../../assets/v7-only.svg)

Você pode configurar o Adobe Campaign para manter uma cópia dos emails enviados da sua plataforma.

No entanto, o Adobe Campaign em si não gerencia arquivos arquivados. Ele permite enviar as mensagens de sua escolha para um endereço dedicado, de onde elas podem ser processadas e arquivadas usando um sistema externo.

Para fazer isso, os arquivos .eml correspondentes aos emails enviados são transferidos para um servidor remoto, como um servidor de email SMTP. O destino do arquivamento é um endereço de email CCO (invisível para os recipients do delivery) que você deve especificar.

## Recommendations e limitações {#recommendations-and-limitations}

* O recurso Cco de email é opcional. Verifique o contrato de licença.
* Para **arquiteturas hospedadas e híbridas**, entre em contato com o executivo da sua conta para ativá-la. O endereço de email CCO de sua escolha deve ser fornecido à equipe do Adobe que o configurará para você.
* Para **instalações no local**, siga as diretrizes abaixo para ativá-la - consulte as seções [Ativating email BCC (on premise)](#activating-email-archiving--on-premise-) e [Configuring the BCC email address (on premise)](#configuring-the-bcc-email-address--on-premise-) .
* Você só pode usar um endereço de email CCO.
* Depois que o CCO de email estiver configurado, verifique se o recurso está ativado no template do delivery ou no delivery por meio da opção **[!UICONTROL Email BCC]**. Para obter mais informações, consulte [esta seção](../../delivery/using/sending-messages.md#archiving-emails).
* Somente emails enviados com êxito são considerados, as rejeições não são.
* O sistema de arquivamento de email foi alterado com o Adobe Campaign 17.2 (build 8795). Se você já estava usando o arquivamento de email, é necessário atualizar manualmente para o novo sistema CCO de email. Para obter mais informações, consulte a seção [Migração para o novo Cco de email](#updated-email-archiving-system--bcc-) .

## Ativando email Cco (no local) {#activating-email-archiving--on-premise-}

Para ativar o arquivamento de emails CCO quando o Adobe Campaign estiver instalado no local, siga as etapas abaixo.

### Pasta local {#local-folder}

Para permitir a transferência de emails enviados para um endereço de email CCO, as cópias brutas exatas de emails enviados devem primeiro ser salvas como arquivos .eml em uma pasta local.

O caminho para a pasta local deve ser especificado no arquivo **config-`<instance>`.xml**, da configuração. Por exemplo:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>É responsabilidade da equipe que implementa o projeto garantir que as configurações de segurança permitam acesso à pasta definida por meio dos parâmetros **dataLogPath**.

O caminho completo é o seguinte: **`<datalogpath>  YYYY-MM-DDHHh`**. A data e a hora são definidas de acordo com o relógio do servidor MTA (UTC). Por exemplo:

```
C:\emails\2018-12-02\13h
```

O nome do arquivo de arquivamento é **`<deliveryid>-<broadlogid>.eml`** quando o status dos emails não é **[!UICONTROL Sent]**. Depois que o status for alterado para **[!UICONTROL Sent]**, o nome do arquivo se tornará **`<deliveryid>-<broadlogid>-sent.eml`**. Por exemplo:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>Em uma instância mid-sourcing, o diretório dos emails do CCO está localizado no servidor mid-sourcing.
>
>A deliveryID e a broadlogID vêm do servidor mid-sourcing quando o status dos emails não é enviado. Depois que o status é alterado para **[!UICONTROL Sent]**, essas IDs vêm do servidor de marketing.

### Parâmetros {#parameters}

Depois que o caminho da pasta local for definido, adicione e edite os seguintes elementos, conforme desejado, no arquivo **config-`<instance name>.xml`**. Abaixo estão os valores padrão:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: formato usado ao compactar os arquivos .eml. Os valores possíveis são:

   **0**: sem compactação (valor padrão)

   **1**: compactação (formato .zip)

* **compressBatchSize**: número de arquivos .eml adicionados a um arquivo (arquivo .zip).
* **archivingType**: estratégia de arquivamento a ser usada. Os valores possíveis são:

   **0**: cópias brutas de emails enviados são salvas no formato .eml na  **** dataLogPathfolder (valor padrão). Uma cópia de arquivamento do arquivo **`<deliveryid>-<broadlogid>-sent.eml`** é salva na pasta **dataLogPath/archive**. O caminho do arquivo de email enviado torna-se **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: cópias brutas de emails enviados são salvas no formato .eml na pasta  **** dataLogPathfolder e são enviadas para o endereço de email CCO por SMTP. Depois que as cópias de email são enviadas para o endereço CCO, o nome do arquivo de arquivamento se torna **`<deliveryid>-<broadlogid>-sent-archived.eml`** e o arquivo é movido para a pasta **dataLogPath/archive**. O caminho do arquivo de email arquivado e enviado por CCO é então **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: número de dias em que os arquivos .eml são mantidos para arquivamento. Após esse atraso, eles são movidos automaticamente para a pasta **dataLogPath/archive** para compactação. Por padrão, os arquivos .eml expiram após dois dias.
* **purgeArchivesDelay**: número de dias que os arquivos são mantidos na pasta  **dataLogPath/`<archives>`** . Após esse período, são permanentemente excluídas. A limpeza começa quando o MTA é iniciado. Por padrão, é realizado a cada sete dias.
* **pollDelay**: verificar a frequência (em segundos) de novos emails enviados recebidos para a pasta  **** dataLogPathfolder. Por exemplo, se esse parâmetro estiver definido como 60, significa que a cada minuto, o processo de arquivamento passa pelos arquivos .eml dentro das pastas **dataLogPath/`<date and time>`**, aplica uma limpeza, se necessário, e envia cópias de email para o endereço CCO e/ou compacta os arquivos arquivados, sempre que necessário.
* **acquisitionLimit**: número de arquivos .eml processados de uma vez antes que o processo de arquivamento seja aplicado novamente de acordo com o parâmetro  **** pollDelay. Por exemplo, se você definir o parâmetro **acquisitionLimit** como 100 enquanto o parâmetro **pollDelay** estiver definido como 60, 100 arquivos .eml por minuto serão processados.
* **smtpNbConnection**: número de conexões SMTP para o endereço de email CCO.

Certifique-se de ajustar esses parâmetros de acordo com a taxa de transferência de envio de email. Por exemplo, em uma configuração em que o MTA está enviando 30.000 emails por hora, você pode definir o parâmetro **pollDelay** como 600, o parâmetro **acquisitionLimit** como 5000 e o parâmetro **smtpNbConnection** como 2. Significa que, usando 2 conexões SMTP, 5.000 emails serão enviados ao endereço CCO a cada 10 minutos.

## Configuração do endereço de email CCO (no local) {#configuring-the-bcc-email-address--on-premise-}

>[!IMPORTANT]
>
>Por motivos de privacidade, os emails CCO devem ser processados por um sistema de arquivamento capaz de armazenar informações de identificação pessoal (PII) seguras.

No arquivo **config-`<instance name>.xml`**, use os seguintes parâmetros para definir o servidor de email SMTP para o qual os arquivos armazenados serão transferidos:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: arquivamento do destino
* **smtpEnableTLS**: usando uma conexão SMTP segura (protocolo TLS/SSL)
* **smtpRelayAddress**: endereço de retransmissão a ser usado
* **smtpRelayPort**: porta de retransmissão a ser usada

>[!NOTE]
>
>Se você estiver usando uma retransmissão SMTP, as alterações nos emails feitas pela retransmissão não serão consideradas no processo de arquivamento.
>
>Além disso, o retransmissão atribui um status **[!UICONTROL Sent]** a todos os emails, incluindo aqueles que não são enviados. Portanto, todas as mensagens são arquivadas.

## Migração para o novo Cco de email {#updated-email-archiving-system--bcc-}

>[!IMPORTANT]
>
>O sistema de arquivamento de email (CCO) foi alterado com o Adobe Campaign 17.2 (build 8795). Se você estiver atualizando de uma build mais antiga e já estiver usando recursos de arquivamento de email, será necessário atualizar manualmente para o novo sistema de arquivamento de email (CCO).

Para fazer isso, faça as seguintes alterações no arquivo **`config-<instance>.xml`**:

1. Remova o parâmetro **zipPath** do nó **`<archiving>`**.
1. Defina o parâmetro **compressionFormat** para **1** se necessário.
1. Defina o parâmetro **archivingType** para **1**.

Após configurar o Cco do email, selecione a opção **[!UICONTROL Email BCC]** no template do delivery ou no delivery. Para obter mais informações, consulte [esta seção](../../delivery/using/sending-messages.md#archiving-emails).

## Práticas recomendadas de Cco de emails {#best-practices}

* **Caixa de entrada** do endereço CCO: verifique se tem capacidade de recebimento suficiente para arquivar todos os emails enviados pelo MTA.
* **mutualização** de MTA: o recurso de arquivamento do Cco funciona no nível do MTA. Ele permite duplicar cada email enviado pelo MTA. Como o MTA pode ser mutualizado em várias instâncias (desenvolvimento, teste ou produção por exemplo) ou até mesmo em vários clientes (em um ambiente de mid-sourcing), a configuração desse recurso afeta a segurança:

   * Se você compartilhar um MTA com vários clientes e um deles tiver essa opção ativada, esse cliente acessará todos os emails dos outros clientes que compartilham o mesmo MTA. Para evitar essa situação, use um MTA diferente para cada cliente.
   * Se você usar o mesmo MTA em várias instâncias (desenvolvimento, teste, prod) para um único cliente, as mensagens enviadas de todas as três instâncias serão duplicadas pela opção dataLogPath .

* **Emails por conexão**: O arquivamento de emails CCO opera abrindo uma conexão e tentando enviar todos os emails por essa conexão. O Adobe recomenda verificar com seu contato técnico interno o número de emails aceitos em uma determinada conexão. O aumento desse número pode ter um grande impacto na taxa de transferência de Cco.
* **IPs** de envio de Cco: atualmente, os emails do CCO não são enviados pelos proxies MTA normais. Em vez disso, uma conexão direta é aberta do servidor MTA para o servidor de email de destino. Isso significa que talvez seja necessário adicionar outros IPs à lista de permissões na rede, dependendo da configuração do servidor de email.

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->