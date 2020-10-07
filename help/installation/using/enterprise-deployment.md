---
title: Implantação empresarial
seo-title: Implantação empresarial
description: Implantação empresarial
seo-description: null
page-status-flag: never-activated
uuid: 2c2b5cef-86cb-4cb5-801a-ca6afeae90bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 066d0ac1-033c-467b-aa6c-43a97ecd8632
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1265'
ht-degree: 2%

---


# Implantação empresarial{#enterprise-deployment}

Esta é a configuração mais completa. Ele se baseia na configuração padrão para maior segurança e disponibilidade:

* servidores de redirecionamento dedicados atrás de um balanceador de carga HTTP ou TCP, para escalabilidade e disponibilidade,
* dois servidores de aplicativos para melhor throughput e capacidade de failover (tolerância a falhas) e que são isolados na LAN.

A comunicação geral entre servidores e processos é realizada de acordo com o seguinte schema:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Com esse tipo de configuração, o throughput esperado pode exceder 100.000 emails por hora com largura de banda e ajuste adequados.

## Recursos {#features}

### Vantagens {#advantages}

* Segurança otimizada: Somente os servidores que precisam ser expostos ao exterior são instalados no computador no DMZ.
* A alta disponibilidade é mais fácil de garantir: Somente o computador visível do exterior precisa ser gerenciado com alta disponibilidade em mente.

### Desvantagens {#disadvantages}

Custos mais altos de hardware e administração.

### Equipamento recomendado {#recommended-equipment}

* Servidores de aplicativos: CPU quad-core de 2 Ghz, 4 GB de RAM, disco rígido SATA de 80 GB RAID de software.
* Servidores de redirecionamento: CPU quad-core de 2 Ghz, 4 GB de RAM, disco rígido SATA de 80 GB RAID de software.

>[!NOTE]
>
>É possível reutilizar um balanceador de carga existente para tráfego nos servidores de redirecionamento.

## Etapas de instalação e configuração {#installation-and-configuration-steps}

### Pré-requisitos {#prerequisites}

* JDK em ambos os servidores de aplicativos,
* Servidor Web (IIS, Apache) em ambas as frentes,
* Acesso a um servidor de bases de dados em ambos os servidores de aplicações,
* Caixa de correio de rejeição acessível via POP3,
* Criação de dois aliases DNS no balanceador de carga:

   * a primeira exposta ao público para rastreamento e apontamento para o balanceador de carga em um endereço IP virtual (VIP) e que é então distribuída para os dois servidores frontais,
   * a segunda foi exposta aos usuários internos para acesso por meio do console e apontando para um balanceador de carga em um endereço IP virtual (VIP) e que é então distribuída para os dois servidores de aplicativos.

* Firewall configurado para abrir STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 para Oracle, 5432 para PostgreSQL etc.) portas. Para obter mais informações, consulte a seção Acesso [ao](../../installation/using/network-configuration.md#database-access)banco de dados.

>[!CAUTION]
>
>Se os servidores de aplicativos apontarem para uma única instância do banco de dados, depois de importar um pacote padrão em uma instância, o schema contido no pacote não será carregado na outra instância.
>  
>Se os servidores de aplicativos apontarem para uma única instância do banco de dados, depois de alterar o schema em uma instância, o schema não será carregado na outra instância.
>
>Para recuperar esses problemas, é necessário reinicializar o processo ‘web@default’ na segunda instância em que ocorreu o erro.

### Instalação e configuração do servidor de aplicativos 1 {#installing-and-configuring-the-application-server-1}

Nos exemplos a seguir, os parâmetros da instância são:

* Nome da instância: demonstração
* Máscara de DNS: tracking.campanha.net*, console.campanha.net* (o servidor de aplicativos lida com os URLs das conexões e relatórios do console do cliente e das páginas de mirrores page e unsubscription)
* Idioma: Inglês
* Banco de dados: campanha:demo@dbsrv

As etapas para instalar o primeiro servidor são:

1. Siga o procedimento de instalação do servidor Adobe Campaign: **pacote nlserver** no Linux ou **setup.exe** no Windows.

   Para obter mais informações, consulte [Pré-requisitos de instalação do Campaign no Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) e [Pré-requisitos de instalação do Campaign no Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Depois que o servidor Adobe Campaign for instalado, start o servidor de aplicativos (Web) usando o comando **nlserver web -tomcat** (o módulo Web permite que você start o Tomcat no modo independente de servidor Web acompanhando na porta 8080) e verifique se os start Tomcat estão corretos:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >Na primeira vez que o módulo Web é executado, ele cria os arquivos **config-default.xml** e **serverConf.xml** no diretório **conf** na pasta de instalação. Todos os parâmetros disponíveis no **serverConf.xml** estão listados nesta [seção](../../installation/using/the-server-configuration-file.md).

   Pressione **Ctrl+C** para parar o servidor.

   Para obter mais informações, consulte as seguintes seções:

   * Para Linux: [Primeiro start do servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Para Windows: [Primeiro start do servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Altere a senha **interna** usando o comando:

   ```
   nlserver config -internalpassword
   ```

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Crie a instância de **demonstração** com as máscaras de DNS para rastreamento (neste caso, **tracking.campanha.net**) e acesso aos consoles do cliente (neste caso, **console.campanha.net**). Há duas maneiras de fazer isso:

   * Crie a instância por meio do console:

      ![](assets/install_create_new_connexion.png)

      Para obter mais informações, consulte [Criação de uma instância e logon](../../installation/using/creating-an-instance-and-logging-on.md).

      ou

   * Crie a instância usando linhas de comando:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      For more on this, refer to [Creating an instance](../../installation/using/command-lines.md#creating-an-instance).

1. Edite o arquivo **config-demo.xml** (criado por meio do comando anterior e localizado ao lado do arquivo **config-default.xml** ), verifique se os processos **mta** (delivery), **wfserver** (fluxo de trabalho), **inMail** **** **** (e-mails de retorno) estat (estatísticas) estão habilitados e configure o endereço do app servidor de estatísticas:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Edite o arquivo **serverConf.xml** e especifique o domínio do delivery, em seguida, especifique os endereços IP (ou host) dos servidores DNS usados pelo módulo MTA para responder aos query DNS do tipo MX.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Os parâmetros **nameServers** são usados apenas no Windows.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Copie o programa de configuração do console do cliente (**setup-client-7.XX**, **YYY.exe** para v7 ou **setup-client-6.XX**, **YYYY.exe** para v6.1) para a pasta **/datakit/nl/eng/jsp** .

   Para obter mais informações, consulte as seguintes seções:

   * Para Linux: [Disponibilidade do console do cliente para Linux](../../installation/using/client-console-availability-for-linux.md)
   * Para Windows: [Disponibilidade do console do cliente para Windows](../../installation/using/client-console-availability-for-windows.md).

1. Start o servidor Adobe Campaign (start **net nlserver6** no Windows, start **** /etc/init.d/nlserver6 no Linux) e execute o comando **nlserver pdump** mais uma vez para verificar a presença de todos os módulos habilitados.

   >[!NOTE]
   >
   >A partir do 20.1, recomendamos usar o seguinte comando (para Linux): **start nlserver do systemctl**


   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Esse comando também permite que você saiba a versão e o número da compilação do servidor Adobe Campaign instalado no computador.

1. Teste o módulo da Web **do** nlserver usando o URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Esse URL permite que você acesse a página de download do programa de configuração do cliente.

   Digite o logon **interno** e a senha associada ao acessar a página do controle de acesso.

   ![](assets/s_ncs_install_access_client.png)

   Para obter mais informações, consulte as seguintes seções:

   * Para Linux: [Disponibilidade do console do cliente para Linux](../../installation/using/client-console-availability-for-linux.md)
   * Para Windows: [Disponibilidade do console do cliente para Windows](../../installation/using/client-console-availability-for-windows.md)

### Instalação e configuração do servidor de aplicativos 2 {#installing-and-configuring-the-application-server-2}

Siga as etapas abaixo:

1. Instale o servidor Adobe Campaign.
1. Copie os arquivos da instância criada no servidor de aplicativos 1.

   Mantemos o mesmo nome de instância do servidor de aplicativos 1.

1. Altere o **interno** para o mesmo que o servidor de aplicativos 1.
1. Vincule o banco de dados à instância:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Edite o arquivo **config-demo.xml** (criado por meio do comando anterior e localizado ao lado do arquivo **config-default.xml** ), verifique se os processos **mta** (delivery), **wfserver** (fluxo de trabalho), **inMail** **** **** (e-mails de retorno) estat (estatísticas) estão habilitados e configure o endereço do app servidor de estatísticas:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Edite o arquivo **serverConf.xml** e preencha a configuração DNS do módulo MTA:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >O parâmetro **nameServers** só é usado no Windows.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Start dos servidores Adobe Campaign.

   Para obter mais informações, consulte as seguintes seções:

   * Para Linux: [Primeiro start do servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Para Windows: [Primeiro start do servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Instalação e configuração dos servidores frontais {#installing-and-configuring-the-frontal-servers}

Os procedimentos de instalação e configuração são idênticos em ambos os computadores.

As etapas são as seguintes:

1. Instale o servidor Adobe Campaign,
1. Cumpra o procedimento de integração do servidor Web (IIS, Apache) descrito nas seguintes seções:

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Copie os arquivos **config-demo.xml** e **serverConf.xml** criados durante a instalação. No arquivo **config-demo.xml** , ative o processo **trackinglogd** e desative os processos **mta**, **inmail**, **wfserver** **** e stat.
1. Edite o arquivo **serverConf.xml** e preencha os servidores de rastreamento redundantes nos parâmetros do redirecionamento:

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Start o site e teste o redirecionamento do URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   O navegador deve exibir as seguintes mensagens (dependendo do URL redirecionado pelo balanceador de carga):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   ou

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Para obter mais informações, consulte as seguintes seções:

   * Para Linux: [Iniciar o servidor Web e testar a configuração](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Para Windows: [Abrindo o servidor Web e testando a configuração](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Start o servidor Adobe Campaign.

