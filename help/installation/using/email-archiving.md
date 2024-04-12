---
product: campaign
title: Arquivamento de email
description: Arquivamento de email
feature: Installation, Instance Settings, Email
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 3%

---

# Configurar email Cco {#email-archiving}



Você pode configurar o Adobe Campaign para manter uma cópia dos emails enviados da sua plataforma.

No entanto, o próprio Adobe Campaign não gerencia arquivos arquivados. Ela permite enviar as mensagens de sua escolha para um endereço dedicado, de onde elas podem ser processadas e arquivadas usando um sistema externo.

Para fazer isso, os arquivos .eml correspondentes aos emails enviados são transferidos para um servidor remoto, como um servidor de email SMTP. O destino do arquivamento é um endereço de email com CCO (invisível para os recipients do delivery) que você deve especificar.

## Recommendations e limitações {#recommendations-and-limitations}

* O recurso Cco de email é opcional. Verifique o contrato de licença.
* Para **arquiteturas hospedadas e híbridas**, entre em contato com o executivo da sua conta para ativá-la. O endereço de email de CCO de sua escolha deve ser fornecido à equipe do Adobe que irá configurá-lo para você.
* Para **instalações no local**, siga as diretrizes abaixo para ativá-la - consulte a [Ativação do email Cco (no local)](#activating-email-archiving--on-premise-) e [Configuração do endereço de email CCO (no local)](#configuring-the-bcc-email-address--on-premise-) seções.
* Você só pode usar um endereço de email CCO.
* Depois que o email Cco for configurado, verifique se o recurso está ativado no template do delivery ou no delivery por meio do **[!UICONTROL Email BCC]** opção. Para obter mais informações, consulte [esta seção](../../delivery/using/sending-messages.md#archiving-emails).
* Somente os emails enviados com êxito são considerados. As rejeições não são.
* O sistema de arquivamento de emails mudou com o Adobe Campaign 17.2 (build 8795). Se você já estava usando o arquivamento de emails, é necessário atualizar manualmente para o novo sistema de email Cco. Para obter mais informações, consulte [Migrar para o novo Email Cco](#updated-email-archiving-system--bcc-) seção.

## Ativar email Cco (no local) {#activating-email-archiving--on-premise-}

[!BADGE No local e híbrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"}


Para ativar o arquivamento de emails com CCO quando o Adobe Campaign for instalado no local, siga as etapas abaixo.

### Pasta local {#local-folder}

Para permitir a transferência de emails enviados para um endereço de email CCO, cópias brutas exatas de emails enviados devem ser salvas primeiro como arquivos .eml em uma pasta local.

O caminho da pasta local deve ser especificado no campo **config-`<instance>`.xml** arquivo, da configuração. Por exemplo:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>A equipe que implementa o projeto é responsável por garantir que as configurações de segurança permitam acesso à pasta definida por meio do **dataLogPath** parâmetros.

O caminho completo é o seguinte: **`<datalogpath>  YYYY-MM-DDHHh`**. A data e a hora são definidas de acordo com o relógio do servidor MTA (UTC). Por exemplo:

```
C:\emails\2018-12-02\13h
```

O nome do arquivo é **`<deliveryid>-<broadlogid>.eml`** quando o status dos emails não é **[!UICONTROL Sent]**. Quando o status for alterado para **[!UICONTROL Sent]**, o nome do arquivo se torna **`<deliveryid>-<broadlogid>-sent.eml`**. Por exemplo:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>Em uma instância mid-sourcing, o diretório para os emails com CCO está localizado no servidor de mid-sourcing.
>
>O deliveryID e o broadlogID vêm do servidor mid-sourcing quando o status dos emails não é enviado. Quando o status for alterado para **[!UICONTROL Sent]**, essas IDs vêm do servidor de marketing.

### Parâmetros {#parameters}

Depois que o caminho da pasta local for definido, adicione e edite os seguintes elementos, conforme desejado na **config-`<instance name>.xml`** arquivo. Abaixo estão os valores padrão:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="1" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: formato usado ao compactar os arquivos .eml. Os valores possíveis são:

  **0**: sem compactação (valor padrão)

  **1**: compactação (formato .zip)

* **compressBatchSize**: número de arquivos .eml adicionados a um arquivo (arquivo .zip).


* **archivingType**: estratégia de arquivamento a ser usada. O único valor possível é **1**. Cópias brutas de emails enviados são salvas no formato .eml na **dataLogPath** e são enviados ao endereço de email CCO via SMTP. Quando as cópias de email são enviadas para o endereço CCo, o nome do arquivo de arquivamento se torna **`<deliveryid>-<broadlogid>-sent-archived.eml`** e o arquivo for movido para a pasta **dataLogPath/archives** pasta. O caminho do arquivo de email enviado e CCO arquivado é **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

  <!--
  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.-->

* **expirationDelay**: número de dias que os arquivos .eml são mantidos para arquivamento. Após esse atraso, elas são movidas automaticamente para o estado **dataLogPath/archives** pasta para compactação. Por padrão, os arquivos .eml expiram após dois dias.
* **purgeArchivesDelay**: número de dias em que os arquivos são mantidos no **dataLogPath/`<archives>`** pasta. Após esse período, eles são excluídos permanentemente. A limpeza começa quando o MTA é iniciado. Por padrão, ele é executado a cada sete dias.
* **pollDelay**: verificação da frequência (em segundos) de novos emails enviados recebidos para a **dataLogPath** pasta. Por exemplo, se esse parâmetro for definido como 60, significa que, a cada minuto, o processo de arquivamento passará pelos arquivos .eml dentro do **dataLogPath/`<date and time>`** , aplique uma limpeza se necessário e envie cópias de e-mail para o endereço CCo e/ou compacte os arquivos arquivados sempre que necessário.
* **acquisitionLimit**: número de arquivos .eml processados de uma só vez antes que o processo de arquivamento seja aplicado novamente de acordo com o **pollDelay** parâmetro. Por exemplo, se você definir a variável **acquisitionLimit** parâmetro para 100 enquanto a variável **pollDelay** for definido como 60, 100 arquivos .eml por minuto serão processados.
* **smtpNbConnection**: número de conexões SMTP com o endereço de email CCO.

Ajuste esses parâmetros de acordo com a taxa de transferência de envio de email. Por exemplo, em uma configuração em que o MTA está enviando 30.000 emails por hora, você pode definir o **pollDelay** para 600, o valor **acquisitionLimit** para 5000 e o **smtpNbConnection** para 2. Isso significa que usando duas conexões SMTP, 5.000 emails serão enviados para o endereço CCO a cada 10 minutos.

## Configuração do endereço de email CCO (no local) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE No local e híbrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"}


>[!IMPORTANT]
>
>Por motivos de privacidade, os emails com CCO devem ser processados por um sistema de arquivamento capaz de armazenar informações de identificação pessoal (PII) seguras.

No **config-`<instance name>.xml`** use os seguintes parâmetros para definir o servidor de email SMTP para o qual os arquivos armazenados serão transferidos:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: destino de arquivamento
* **smtpEnableTLS**: usando uma conexão SMTP segura (protocolo TLS/SSL)
* **smtpRelayAddress**: endereço de retransmissão a ser usado
* **smtpRelayPort**: porta de retransmissão a ser usada

>[!NOTE]
>
>Se você estiver usando uma retransmissão SMTP, as alterações nos emails feitas pela retransmissão não serão consideradas no processo de arquivamento.
>
>Além disso, o relé atribui um **[!UICONTROL Sent]** para todos os emails, incluindo aqueles que não foram enviados. Portanto, todas as mensagens são arquivadas.

<!--
## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
-->

## Práticas recomendadas de Cco de email {#best-practices}

* **Caixa de correio de endereço CCO**: verifique se ele tem capacidade de recepção suficiente para arquivar todos os emails enviados pelo MTA.
* **Pool de MTA**: o recurso de arquivamento CCO funciona no nível do MTA. Ele permite duplicar todos os emails enviados pelo MTA. Como o MTA pode ser agrupado em várias instâncias (desenvolvimento, teste ou produção, por exemplo) ou até mesmo em vários clientes (em um ambiente de mid-sourcing), a configuração desse recurso afeta a segurança:

   * Se você compartilhar um MTA com vários clientes e um deles tiver essa opção ativada, esse cliente acessará todos os emails dos outros clientes que compartilham o mesmo MTA. Para evitar essa situação, use um MTA diferente para cada cliente.
   * Se você usar o mesmo MTA em várias instâncias (desenvolvimento, teste, prod) para um único cliente, as mensagens enviadas de todas as três instâncias serão duplicadas pela opção dataLogPath.

* **Emails por conexão**: o arquivamento de emails com CCO opera abrindo uma conexão e tentando enviar todos os emails por meio dessa conexão. A Adobe recomenda verificar com seu contato técnico interno o número de emails aceitos em uma determinada conexão. Aumentar esse número pode ter um grande impacto na taxa de transferência do Cco.
* **IPs de envio com CCO**: no momento, os emails com CCO não são enviados por meio dos proxies MTA normais. Em vez disso, uma conexão direta é aberta do servidor MTA para o servidor de email de destino. Incluir na lista de permissões Isso significa que talvez seja necessário adicionar outros IPs ao arquivo na rede, dependendo da configuração do servidor de email.

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