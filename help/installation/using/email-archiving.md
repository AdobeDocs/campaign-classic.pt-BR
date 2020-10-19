---
title: Arquivamento de email
seo-title: Arquivamento de email
description: Arquivamento de email
seo-description: null
page-status-flag: never-activated
uuid: a5ed0659-be61-4d73-98e7-db3da24d92f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: d6467875-949b-4b47-940f-620efd4db5e0
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 2%

---


# Cco de email {#email-archiving}

Você pode configurar o Adobe Campaign para manter uma cópia dos emails enviados da sua plataforma.

No entanto, a própria Adobe Campaign não gerencia arquivos arquivados. Ela permite que você envie as mensagens de sua escolha para um endereço dedicado, de onde elas podem ser processadas e arquivadas usando um sistema externo.

Para fazer isso, os arquivos .eml correspondentes aos emails enviados são transferidos para um servidor remoto, como um servidor de email SMTP. O destino de arquivamento é um endereço de email Cco (invisível para os recipient do delivery) que você deve especificar.

## Recommendations e limitações {#recommendations-and-limitations}

* O recurso CCO de email é opcional. Verifique o contrato de licença.
* Para arquiteturas **** hospedadas e híbridas, entre em contato com o executivo da sua conta para ativá-la. O endereço de e-mail CCO de sua escolha deve ser fornecido à equipe do Adobe que o configurará para você.
* Para instalações **** no local, siga as diretrizes abaixo para ativá-la - consulte as seções [Ativando e-mail CCO (no local)](#activating-email-archiving--on-premise-) e [Configurando o endereço de e-mail CCO (no local)](#configuring-the-bcc-email-address--on-premise-) .
* Você só pode usar um endereço de email Cco.
* Depois que o e-mail BCC for configurado, verifique se o recurso está ativado no template do delivery ou no delivery por meio da **[!UICONTROL Email BCC]** opção. Para obter mais informações, consulte [esta seção](../../delivery/using/sending-messages.md#archiving-emails).
* Somente emails enviados com êxito são levados em conta, mas não rejeições.
* O sistema de arquivamento de e-mails foi alterado com o Adobe Campaign 17.2 (build 8795). Se você já estava usando o arquivamento de e-mail, é necessário atualizar manualmente para o novo sistema de e-mail CCO. Para obter mais informações, consulte a seção [Mover para a nova Cco](#updated-email-archiving-system--bcc-) de email.

## Ativando Cco de email (no local) {#activating-email-archiving--on-premise-}

Para ativar o arquivamento de e-mails em Cco quando a Adobe Campaign estiver instalada no local, siga as etapas abaixo.

### Pasta local {#local-folder}

Para permitir a transferência de e-mails enviados para um endereço de e-mail Cco, as cópias brutas exatas de e-mails enviados devem primeiro ser salvas como arquivos .eml para uma pasta local.

O caminho para a pasta local deve ser especificado no arquivo **config-`<instance>`.xml** , da configuração. Por exemplo:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>É responsabilidade da equipe que implementa o projeto garantir que as configurações de segurança permitam acesso à pasta definida pelos parâmetros **dataLogPath** .

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
>Em uma instância mid-sourcing, o diretório dos emails BCC está localizado no servidor mid-sourcing.
>
>A deliveryID e a BroadlogID vêm do servidor de mid-sourcing quando o status dos e-mails não é enviado. Depois que o status é alterado para **[!UICONTROL Sent]**, essas IDs vêm do servidor de marketing.

### Parameters {#parameters}

Depois que o caminho da pasta local for definido, adicione e edite os seguintes elementos conforme desejado no arquivo de **configuração`<instance name>.xml`** . Abaixo estão os valores padrão:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: formato usado ao compactar os arquivos .eml. Os valores possíveis são:

   **0**: sem compactação (valor padrão)

   **1**: compactação (formato .zip)

* **compressBatchSize**: número de arquivos .eml adicionados a um arquivo (arquivo .zip).
* **archiveType**: estratégia de arquivamento a ser usada. Os valores possíveis são:

   **0**: cópias brutas de emails enviados são salvas no formato .eml para a pasta **dataLogPath** (valor padrão). Uma cópia de arquivamento do **`<deliveryid>-<broadlogid>-sent.eml`** arquivo é salva na pasta **dataLogPath/archive** . O caminho do arquivo de email enviado se torna **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: cópias brutas de emails enviados são salvas no formato .eml na pasta **dataLogPath** e são enviadas para o endereço de email Cco pelo SMTP. Depois que as cópias de e-mail são enviadas para o endereço BCC, o nome do arquivo de arquivamento se torna **`<deliveryid>-<broadlogid>-sent-archived.eml`** e o arquivo é movido para a pasta **dataLogPath/archive** . O caminho do arquivo de e-mail enviado e arquivado por Cco é então **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: número de dias em que os arquivos .eml são mantidos para arquivamento. Após esse atraso, eles são movidos automaticamente para a pasta **dataLogPath/archive** para compactação. Por padrão, os arquivos .eml expiram após dois dias.
* **purgeArchivesDelay**: número de dias em que os arquivos são mantidos na pasta **dataLogPath/`<archives>`** . Após esse período, são permanentemente apagados. A limpeza começa quando o MTA é iniciado. Por padrão, é realizado a cada sete dias.
* **pollDelay**: frequência de verificação (em segundos) de novos emails enviados recebidos para a pasta **dataLogPath** . Por exemplo, se esse parâmetro estiver definido como 60, significa que a cada minuto, o processo de arquivamento passa pelos arquivos .eml dentro das pastas **dataLogPath/`<date and time>`** , aplica uma expurgação se necessário e envia cópias de email para o endereço BCC e/ou compacta os arquivos arquivados sempre que necessário.
* **acquisitionLimit**: número de arquivos .eml processados simultaneamente antes que o processo de arquivamento seja aplicado novamente de acordo com o parâmetro **pollDelay** . Por exemplo, se você definir o parâmetro **acquisitionLimit** como 100 enquanto o parâmetro **pollDelay** estiver definido como 60, 100 arquivos .eml por minuto serão processados.
* **smtpNbConnection**: número de conexões SMTP com o endereço de email BCC.

Certifique-se de ajustar esses parâmetros de acordo com a throughput de envio do email. Por exemplo, em uma configuração em que o MTA está enviando 30.000 emails por hora, você pode definir o parâmetro **pollDelay** como 600, o parâmetro **acquisitionLimit** como 5000 e o parâmetro **smtpNbConnection** como 2. Isso significa que, usando 2 conexões SMTP, 5.000 emails serão enviados para o endereço BCC a cada 10 minutos.

## Configurar o endereço de email CCO (no local) {#configuring-the-bcc-email-address--on-premise-}

>[!CAUTION]
>
>Por motivos de privacidade, os emails CCO devem ser processados por um sistema de arquivamento capaz de armazenar informações de identificação pessoal (PII) seguras.

No arquivo **config-`<instance name>.xml`** , use os seguintes parâmetros para definir o servidor de email SMTP para o qual os arquivos armazenados serão transferidos:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: arquivamento de destino de públicos alvos
* **smtpEnableTLS**: usando uma conexão SMTP segura (protocolo TLS/SSL)
* **smtpRelayAddress**: endereço de retransmissão a ser usado
* **smtpRelayPort**: porta de retransmissão a ser usada

>[!NOTE]
>
>Se você estiver usando um relé SMTP, as alterações nos emails feitas pelo relé não serão levadas em conta no processo de arquivamento.
>
>Além disso, o relé atribui um **[!UICONTROL Sent]** status a todos os emails, incluindo aqueles que não são enviados. Portanto, todas as mensagens são arquivadas.

## Mudar para a nova Cco de Correio Eletrônico {#updated-email-archiving-system--bcc-}

>[!CAUTION]
>
>O sistema de arquivamento de e-mails (BCC) foi alterado com o Adobe Campaign 17.2 (build 8795). Se você estiver atualizando de uma versão mais antiga e já estiver usando recursos de arquivamento de e-mail, é necessário atualizar manualmente para o novo sistema de arquivamento de e-mails (BCC).

Para fazer isso, faça as seguintes alterações no **`config-<instance>.xml`** arquivo:

1. Remova o parâmetro **zipPath** do **`<archiving>`** nó.
1. Defina o parâmetro **compressionFormat** como **1** , se necessário.
1. Defina o parâmetro **archiveType** como **1**.

Depois que o e-mail BCC estiver configurado, selecione a **[!UICONTROL Email BCC]** opção no template do delivery ou no delivery. Para obter mais informações, consulte [esta seção](../../delivery/using/sending-messages.md#archiving-emails).

## Práticas recomendadas de Cco de email {#best-practices}

* **Caixa de correio** de endereço CCO: verifique se ele tem capacidade de recepção suficiente para arquivar todos os emails enviados pelo MTA.
* **MTA mutualização**: o recurso de arquivamento CCO funciona no nível MTA. Ele permite que você duplicado cada email enviado pelo MTA. Como o MTA pode ser mutualizado em várias instâncias (dev, test ou prod, por exemplo) ou até mesmo em vários clientes (em um ambiente mid-sourcing), a configuração desse recurso afeta a segurança:

   * Se você compartilhar um MTA com vários clientes e um deles tiver essa opção ativada, esse cliente acessará todos os emails dos outros clientes que compartilham o mesmo MTA. Para evitar tal situação, use um MTA diferente para cada cliente.
   * Se você usar o mesmo MTA em várias instâncias (desenvolvimento, teste, prod) para um único cliente, as mensagens enviadas de todas as três instâncias serão duplicadas pela opção dataLogPath.

* **Emails por conexão**: O arquivamento de e-mails em Cco opera abrindo uma conexão e tentando enviar todos os e-mails por essa conexão. O Adobe recomenda verificar com seu contato técnico interno o número de emails aceitos em uma determinada conexão. O aumento desse número pode ter um grande impacto na throughput do BCC.
* **IPs** de envio CCO: atualmente, os emails Cco não são enviados pelos proxies MTA normais. Em vez disso, uma conexão direta é aberta do servidor MTA para o servidor de email de destino. Isso significa que talvez seja necessário adicionar outros IPs à lista de permissões na rede, dependendo da configuração do servidor de email.

