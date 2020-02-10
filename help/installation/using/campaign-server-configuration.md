---
title: Configuração do servidor de campanha
seo-title: Configuração do servidor de campanha
description: Configuração do servidor de campanha
seo-description: null
page-status-flag: never-activated
uuid: a1fadad2-e888-4dd8-bc1f-04df16ba7d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: f296676e-3bf1-47da-8239-f5ae54e52fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# Configuração do servidor de campanha{#campaign-server-configuration}

As seções a seguir detalham as configurações obrigatórias do servidor, o que garantirá o funcionamento eficiente do Adobe Campaign para a maioria das configurações.

Configurações adicionais são oferecidas em [Configuração do servidor](../../installation/using/configuring-campaign-server.md)Campaign.

>[!NOTE]
>
>As configurações do lado do servidor só podem ser executadas pela Adobe para implantações hospedadas pela Adobe. Para saber mais sobre as diferentes implantações, consulte a seção Modelos [de](../../installation/using/hosting-models.md) hospedagem ou este [artigo](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

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
* **serverConf.xml**: configuração geral para todas as instâncias. Este arquivo combina os parâmetros técnicos do servidor do Adobe Campaign: eles são compartilhados por todas as instâncias. A descrição de alguns desses parâmetros é detalhada abaixo. Consulte o arquivo para exibir todos os parâmetros disponíveis. Os diferentes nós e parâmetros e listados nesta [seção](../../installation/using/the-server-configuration-file.md).

Você pode configurar o diretório de armazenamento (diretório **var** ) dos dados do Adobe Campaign (registros, downloads, redirecionamentos etc.). Para fazer isso, use a variável do sistema **XTK_VAR_DIR** :

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

* **várias instâncias**: um único processo é iniciado para todas as instâncias. É o caso dos processos **web**, **syslogd** e **trackinglogd** .

   A ativação pode ser configurada a partir do arquivo **config-default.xml** .

   Declaração de um servidor do Adobe Campaign para acessar consoles de cliente e para redirecionamento (rastreamento):

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

   Declarar um servidor para entrega, executar instâncias de fluxo de trabalho e recuperar e-mails de rejeição:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Configurações de entrega {#delivery-settings}

Os parâmetros de entrega devem ser configurados na pasta **serverConf.xml** .

* **Configuração** DNS: especifique o domínio de entrega e os endereços IP (ou host) dos servidores DNS usados para responder a consultas DNS do tipo MX feitas pelo módulo MTA a partir de **`<dnsconfig>`** agora.

   >[!NOTE]
   >
   >O parâmetro **nameServers** é essencial para uma instalação no Windows. Para uma instalação no Linux, ela deve ficar vazia.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Os outros parâmetros de entrega disponíveis neste arquivo são apresentados em [Personalizando parâmetros](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)de entrega.

Consulte também [Enviabilidade](../../installation/using/email-deliverability.md)por email.
