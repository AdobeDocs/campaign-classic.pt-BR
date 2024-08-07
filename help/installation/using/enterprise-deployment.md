---
product: campaign
title: Implantação empresarial
description: Implantação empresarial
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 6%

---

# Implantação empresarial{#enterprise-deployment}



Essa é a configuração mais completa. Baseia-se na configuração padrão para maior segurança e disponibilidade:

* servidores de redirecionamento dedicados por trás de um balanceador de carga HTTP ou TCP, para escalabilidade e disponibilidade,
* dois servidores de aplicativos para capacidade aprimorada de throughput e failover (tolerância a falhas) e que estão isolados na LAN.

A comunicação geral entre servidores e processos é realizada de acordo com o seguinte esquema:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Com esse tipo de configuração, o throughput esperado pode exceder 100.000 e-mails por hora com largura de banda e ajuste apropriados.

## Recursos {#features}

### Vantagens {#advantages}

* Segurança otimizada: somente os servidores que precisam ser expostos externamente são instalados no computador na DMZ.
* Alta disponibilidade mais fácil de garantir: somente o computador visível externamente precisa ser gerenciado com alta disponibilidade em mente.

### Desvantagens {#disadvantages}

Custos mais altos de hardware e administração.

### Equipamento recomendado {#recommended-equipment}

* Servidores de aplicativos: CPU quad-core de 2 Ghz, 4 GB de RAM, disco rígido SATA RAID 1 de software de 80 GB.
* Servidores de redirecionamento: CPU quad-core de 2 Ghz, 4 GB de RAM, disco rígido SATA RAID 1 de software de 80 GB.

>[!NOTE]
>
>É possível reutilizar um balanceador de carga existente para o tráfego para os servidores de redirecionamento.

## Etapas de instalação e configuração {#installation-and-configuration-steps}

### Pré-requisitos {#prerequisites}

* JDK em ambos os servidores de aplicativos,
* Servidor Web (IIS, Apache) em ambos os frontais,
* Acesso a um servidor de banco de dados em ambos os servidores de aplicativos,
* Caixa de entrada de devolução acessível via POP3,
* Criação de dois aliases DNS no balanceador de carga:

   * a primeira exposta ao público para rastreamento e apontamento do balanceador de carga em um endereço IP virtual (VIP) e que é então distribuída aos dois servidores frontais,
   * o segundo é exposto aos usuários internos para acesso por meio do console e aponta para um balanceador de carga em um endereço IP virtual (VIP) e que é então distribuído aos dois servidores de aplicativos.

* Firewall configurado para abrir STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 para Oracle, 5432 para PostgreSQL etc.) portas. Para obter mais informações, consulte a seção [Acesso ao banco de dados](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Se os servidores de aplicações apontarem para uma única instância de banco de dados, após importar um pacote padrão em uma instância, o schema contido no pacote não será carregado na outra instância.
>  
>Se os servidores da aplicação apontarem para uma única instância do banco de dados, após alterar o esquema em uma instância, o esquema não será carregado na outra instância.
>
>Para recuperar esses problemas, é necessário reinicializar o processo &quot;web@default&quot; na segunda instância em que ocorreu o erro.

### Instalando e configurando o servidor de aplicativos 1 {#installing-and-configuring-the-application-server-1}

Nos exemplos a seguir, os parâmetros da instância são:

* Nome da instância: demo
* Máscara DNS: tracking.campaign.net&#42;, console.campaign.net&#42; (o servidor de aplicativos manipula as URLs para conexões e relatórios do console do cliente e para páginas de mirror pages e unsubscription)
* Idioma: inglês
* Banco de dados: campaign:demo@dbsrv

As etapas para instalar o primeiro servidor são:

1. Siga o procedimento de instalação do servidor Adobe Campaign: pacote **nlserver** no Linux ou **setup.exe** no Windows.

   Para obter mais informações, consulte [Pré-requisitos da instalação do Campaign no Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) e [Pré-requisitos da instalação do Campaign no Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Depois que o servidor Adobe Campaign estiver instalado, inicie o servidor de aplicativos (web) usando o comando **nlserver web -tomcat** (o módulo Web permite que você inicie o Tomcat no modo de servidor Web independente escutando na porta 8080) e verifique se o Tomcat é iniciado corretamente:

   ```sql
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >Na primeira vez que o módulo Web é executado, ele cria os arquivos **config-default.xml** e **serverConf.xml** no diretório **conf** na pasta de instalação. Todos os parâmetros disponíveis no **serverConf.xml** estão listados nesta [seção](../../installation/using/the-server-configuration-file.md).

   Pressione **Ctrl+C** para parar o servidor.

   Para obter mais informações, consulte estas seções:

   * Para Linux: [Primeira inicialização do servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Para Windows: [Primeira inicialização do servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Altere a senha **interna** usando o comando:

   ```
   nlserver config -internalpassword
   ```

   Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Crie a instância **demo** com as máscaras de DNS para rastreamento (neste caso, **tracking.campaign.net**) e acesso aos consoles de cliente (neste caso, **console.campaign.net**). Há duas maneiras de fazer isso:

   * Crie a instância por meio do console:

     ![](assets/install_create_new_connexion.png)

     Para obter mais informações, consulte [Criação de uma instância e logon](../../installation/using/creating-an-instance-and-logging-on.md).

     ou

   * Crie a instância usando linhas de comando:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Para obter mais informações, consulte [Criação de uma instância](../../installation/using/command-lines.md#creating-an-instance).

1. Edite o arquivo **config-demo.xml** (criado por meio do comando anterior e localizado ao lado do arquivo **config-default.xml**), verifique se os processos **mta** (entrega), **wfserver** (fluxo de trabalho), **inMail** (emails de reassociação) e **stat** (estatísticas) estão habilitados e configure o endereço do servidor de estatísticas do **app**:

   ```xml
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

   Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Edite o arquivo **serverConf.xml**, especifique o domínio de entrega e os endereços IP (ou host) dos servidores DNS usados pelo módulo MTA para responder consultas DNS do tipo MX.

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Os parâmetros **nameServers** são usados apenas no Windows.

   Para obter mais informações, consulte [Configuração do servidor do Campaign](../../installation/using/configuring-campaign-server.md).

1. Copie o programa de instalação do console do cliente **setup-client-7.XX**, **YYYY.exe** para a pasta **/datakit/nl/eng/jsp**. [Saiba mais](../../installation/using/client-console-availability-for-windows.md).

1. Inicie o servidor do Adobe Campaign (**net start nlserver6** no Windows, **/etc/init.d/nlserver6 start** no Linux) e execute o comando **nlserver dump** mais uma vez para verificar a presença de todos os módulos habilitados.

   >[!NOTE]
   >
   >A partir da versão 20.1, recomendamos usar o seguinte comando (para Linux): **systemctl start nlserver**


   ```sql
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Esse comando também permite saber a versão e o número da build do servidor Adobe Campaign instalado no computador.

1. Teste o módulo da Web **nlserver** usando a URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Este URL permite que você acesse a página de download do programa de configuração do cliente. [Saiba mais](../../installation/using/client-console-availability-for-windows.md).

   Insira o logon **interno** e a senha associada quando você acessar a página de controle de acesso.

   ![](assets/s_ncs_install_access_client.png)

### Instalando e configurando o servidor de aplicativos 2 {#installing-and-configuring-the-application-server-2}

Siga as etapas abaixo:

1. Instale o servidor do Adobe Campaign.
1. Copie os arquivos da instância criada no servidor de aplicativos 1.

   Mantemos o mesmo nome de instância do servidor de aplicativos 1.

1. Altere o **internal** para o mesmo que o servidor de aplicativos 1.
1. Vincule o banco de dados à instância:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Edite o arquivo **config-demo.xml** (criado por meio do comando anterior e localizado ao lado do arquivo **config-default.xml**), verifique se os processos **mta** (entrega), **wfserver** (fluxo de trabalho), **inMail** (emails de reassociação) e **stat** (estatísticas) estão habilitados e configure o endereço do servidor de estatísticas do **app**:

   ```xml
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

   Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Edite o arquivo **serverConf.xml** e preencha a configuração DNS do módulo MTA:

   ```xml
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >O parâmetro **nameServers** é usado apenas no Windows.

   Para obter mais informações, consulte [Configuração do servidor do Campaign](../../installation/using/configuring-campaign-server.md).

1. Inicie os servidores do Adobe Campaign.

   Para obter mais informações, consulte estas seções:

   * Para Linux: [Primeira inicialização do servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Para Windows: [Primeira inicialização do servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Instalação e configuração dos servidores frontais {#installing-and-configuring-the-frontal-servers}

Os procedimentos de instalação e configuração são idênticos em ambos os computadores.

As etapas são as seguintes:

1. Instalar o servidor do Adobe Campaign,
1. Siga o procedimento de integração do servidor Web (IIS, Apache) descrito nas seguintes seções:

   * Para Linux: [Integração em um servidor Web para Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Para Windows: [Integração em um servidor Web para Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Copie os arquivos **config-demo.xml** e **serverConf.xml** criados durante a instalação. No arquivo **config-demo.xml**, ative o processo **trackinglogd** e desative os processos **mta**, **inmail**, **wfserver** e **stat**.
1. Edite o arquivo **serverConf.xml** e preencha os servidores de rastreamento redundantes nos parâmetros do redirecionamento:

   ```xml
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Inicie o site e teste o redirecionamento da URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   O navegador deve exibir as seguintes mensagens (dependendo do URL redirecionado pelo balanceador de carga):

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   ou

   ```xml
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Para obter mais informações, consulte estas seções:

   * Para Linux: [Iniciando o servidor Web e testando a configuração](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Para Windows: [Iniciar o servidor Web e testar a configuração](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Inicie o servidor do Adobe Campaign.
