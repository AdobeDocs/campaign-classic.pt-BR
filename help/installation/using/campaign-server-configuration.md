---
solution: Campaign Classic
product: campaign
title: Configuração do servidor do Campaign
description: Configuração do servidor do Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 2%

---


# Configuração do servidor do Campaign{#campaign-server-configuration}

As seções a seguir detalham as configurações obrigatórias do servidor, o que garantirá o funcionamento eficiente da Adobe Campaign para a maioria das configurações.

Configurações adicionais são oferecidas em [Configuração do servidor](../../installation/using/configuring-campaign-server.md)de Campanha.

>[!NOTE]
>
>As configurações do lado do servidor só podem ser executadas por Adobe para implantações hospedadas pelo Adobe. Para saber mais sobre as diferentes implantações, consulte a seção Modelos [de](../../installation/using/hosting-models.md) hospedagem ou [a matriz](../../installation/using/capability-matrix.md)de recursos.

## Identificador interno {#internal-identifier}

O identificador **interno** é um logon técnico a ser usado para fins de instalação, administração e manutenção. Esse logon não está associado a uma instância.

Os operadores conectados usando esse logon terão todos os direitos em todas as instâncias. Este logon não terá uma senha no caso de uma nova instalação. É necessário definir essa senha manualmente.

Use o seguinte comando:

```
nlserver config -internalpassword
```

As seguintes informações são exibidas. Digite e confirme a senha:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Arquivos de configuração {#configuration-files}

Os arquivos de configuração são armazenados na pasta **conf** da pasta de instalação do Adobe Campaign. A configuração é distribuída por dois arquivos:

* **`config-<instance>.xml`** (onde **instância** é o nome da instância): configuração específica da instância. Se você compartilhar seu servidor entre várias instâncias, insira os parâmetros específicos de cada instância em seu arquivo relevante.
* **serverConf.xml**: configuração geral para todas as instâncias. Este arquivo combina os parâmetros técnicos do servidor Adobe Campaign: eles são compartilhados por todas as instâncias. A descrição de alguns desses parâmetros é detalhada abaixo. Consulte o próprio arquivo para visualização de todos os parâmetros disponíveis. Os diferentes nós e parâmetros e listados nesta [seção](../../installation/using/the-server-configuration-file.md).

Você pode configurar o diretório do armazenamento (diretório **var** ) dos dados do Adobe Campaign (registros, downloads, redirecionamentos etc.). Para fazer isso, use a variável do sistema **XTK_VAR_DIR** :

* No Windows, indique o seguinte valor na variável do sistema **XTK_VAR_DIR**

   ```
   D:\log\AdobeCampaign
   ```

* No Linux, vá para o arquivo **customer.sh** e indique: **exporte XTK_VAR_DIR=/app/log/AdobeCampaign**.

   For more on this, refer to [Personalizing parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Ativação de processos {#enabling-processes}

Os processos do Adobe Campaign no servidor são ativados (e desativados) por meio dos arquivos e **config-default.xml** e **`config-<instance>.xml`** arquivos.

Para aplicar as alterações a esses arquivos, se o serviço Adobe Campaign for iniciado, você deverá executar o comando **nlserver config -reload** .

Há dois tipos de processos: várias instâncias e instância única.

* **várias instâncias**: um único processo é iniciado para todas as instâncias. Esse é o caso dos processos **web**, **syslogd** e **trackinglogd** .

   A ativação pode ser configurada a partir do arquivo **config-default.xml** .

   Declaração de um servidor Adobe Campaign para acessar consoles de cliente e para redirecionamento (rastreamento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   Neste exemplo, o arquivo é editado usando um comando **vi** no Linux. Ele pode ser editado usando qualquer editor **.txt** ou **.xml** .

* **mono-instância**: um processo é iniciado para cada instância (módulos: **mta**, **wfserver**, **inMail**, **sms** e **stat**).

   A ativação pode ser configurada usando o arquivo de configuração da instância:

   ```
   config-<instance>.xml
   ```

   Declarar um servidor para o delivery, executar instâncias de fluxo de trabalho e recuperar e-mails de rejeição:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Configurações do delivery {#delivery-settings}

Os parâmetros do delivery devem ser configurados na pasta **serverConf.xml** .

* **Configuração** DNS: especifique o domínio do delivery e os endereços IP (ou host) dos servidores DNS usados para responder a query DNS do tipo MX feitos pelo módulo MTA a partir de **`<dnsconfig>`** agora.

   >[!NOTE]
   >
   >O parâmetro **nameServers** é essencial para uma instalação no Windows. Para uma instalação no Linux, ela deve ficar vazia.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Os outros parâmetros de delivery disponíveis neste arquivo são apresentados em [Personalizando parâmetros](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)de delivery.

Consulte também [Enviabilidade](../../installation/using/email-deliverability.md)por email.
