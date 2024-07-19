---
product: campaign
title: Implantação independente
description: Implantação independente
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 5%

---

# Implantação independente{#standalone-deployment}



Essa configuração inclui todos os componentes no mesmo computador:

* processo de aplicação (web),
* processo de entrega (mta),
* processo de redirecionamento (rastreamento),
* processo de fluxo de trabalho e tarefas agendadas (wfserver),
* processo de rejeição de emails (inMail),
* processo de estatísticas (stat).

A comunicação geral entre os processos é realizada de acordo com o seguinte schema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Esse tipo de configuração pode ser executado ao gerenciar listas de menos de 100.000 recipients e com, por exemplo, as seguintes camadas de software:

* Linux
* Apache,
* PostgreSQL,
* Qmail.

À medida que o volume cresce, uma variante dessa arquitetura move o servidor de banco de dados para outro computador para melhorar o desempenho.

>[!NOTE]
>
>Um servidor de banco de dados existente também pode ser usado se tiver recursos suficientes.

## Recursos {#features}

### Vantagens {#advantages}

* Totalmente independente e com baixo custo de configuração (nenhuma licença faturável é necessária se o software de código aberto listado abaixo for usado).
* Instalação simplificada e configuração de rede.

### Desvantagens {#disadvantages}

* Um computador crítico em caso de incidente.
* Largura de banda limitada ao transmitir mensagens (em nossa experiência, em torno de várias dezenas de milhares de emails por hora).
* Possível lentidão do aplicativo durante a transmissão.
* O servidor de aplicativos deve estar disponível externamente (enquanto estiver localizado na DMZ, por exemplo), pois ele hospeda o servidor de redirecionamento.

## Etapas de instalação e configuração {#installation-and-configuration-steps}

### Pré-requisitos {#prerequisites}

* JDK,
* servidor Web (IIS, Apache),
* Acesso a um servidor de banco de dados,
* Caixa de entrada de devolução acessível via POP3,
* Criação de dois aliases DNS:

   * a primeira a ser exposta ao público para rastrear e apontar para o computador no seu IP público;
   * o segundo alias exposto aos usuários internos para acesso ao console e apontando para o mesmo computador.

* Firewall configurado para abrir SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 para Oracle, 5432 para PostgreSQL etc.) portas. Para obter mais informações, consulte [Configuração de rede](../../installation/using/network-configuration.md).

Nos exemplos a seguir, os parâmetros da instância são:

* Nome da instância: **demonstração**
* Máscara DNS: **console.campaign.net&#42;** (somente para conexões de console do cliente e relatórios)
* Banco de dados: **campaign:demo@dbsrv**

### Instalação e configuração (computador único) {#installing-and-configuring--single-machine-}

Siga as etapas abaixo:

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

   * Para Linux: [Primeira inicialização do servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Para Windows: [Primeira inicialização do servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. Altere a senha **interna** usando o comando:

   ```
   nlserver config -internalpassword
   ```

   Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Crie a instância **demo** com as máscaras de DNS para rastreamento (neste caso, **tracking.campaign.net**) e acesso aos consoles de cliente (neste caso, **console.campaign.net**). Há duas maneiras de fazer isso:

   * Crie a instância por meio do console:

     ![](assets/install_create_new_connexion.png)

     Para obter mais informações, consulte [Criar uma instância e fazer logon](../../installation/using/creating-an-instance-and-logging-on.md).

     ou

   * Crie a instância usando linhas de comando:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Para obter mais informações, consulte [Criação de uma instância](../../installation/using/command-lines.md#creating-an-instance).

1. Edite o arquivo **config-demo.xml** (criado na etapa anterior ao lado de **config-default.xml**) e verifique se os processos **mta** (entrega), **wfserver** (fluxo de trabalho), **inMail** (emails devolvidos) e **stat** (estatísticas) estão habilitados. Em seguida, configure o endereço do servidor de estatísticas:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Para obter mais informações, consulte [esta seção](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Edite o arquivo **serverConf.xml**, especifique o domínio de entrega e os endereços IP (ou host) dos servidores DNS usados pelo módulo MTA para responder consultas DNS do tipo MX.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >O parâmetro **nameServers** é usado apenas no Windows.

   Para obter mais informações, consulte [Configuração do servidor do Campaign](../../installation/using/configuring-campaign-server.md).

1. Copie o programa de instalação do console do cliente **setup-client-7.XXX.exe** para a pasta **/datakit/nl/eng/jsp**. [Saiba mais](../../installation/using/client-console-availability-for-windows.md).

1. Siga o procedimento de integração do servidor Web (IIS, Apache) descrito nas seguintes seções:

   * Para Linux: [Integração em um servidor Web para Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Para Windows: [Integração em um servidor Web para Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Inicie o site e teste o redirecionamento usando o URL: https://tracking.campaign.net/r/test.

   O navegador deve exibir a seguinte mensagem:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Para obter mais informações, consulte estas seções:

   * Para Linux: [Iniciar o servidor Web e testar a configuração](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Para Windows: [Iniciar o servidor Web e testar a configuração](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. Teste o módulo da Web **nlserver** usando a URL: https://console.campaign.net/nl/jsp/logon.jsp

   Este URL permite que você acesse a página de download do programa de configuração do cliente.

   Insira o logon **interno** e a senha associada quando você acessar a página de controle de acesso. [Saiba mais](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. Inicie o console do cliente Adobe Campaign (na página de download anterior ou iniciado diretamente no servidor para uma instalação do Windows), defina a URL de conexão do servidor como https://console.campaign.net e conecte-se usando o logon **interno**.

   Consulte [esta página](../../installation/using/creating-an-instance-and-logging-on.md) e [esta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).

   O assistente de criação de banco de dados é exibido quando você efetua login pela primeira vez:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Siga as etapas do assistente e crie o banco de dados associado à instância de conexão.

   Para obter mais informações, consulte [Criação e configuração do banco de dados](../../installation/using/creating-and-configuring-the-database.md).

   Depois que o banco de dados for criado, faça logoff.

1. Faça logon novamente no console do cliente usando o logon **admin** sem senha e inicie o assistente de implantação (menu **[!UICONTROL Tools > Advanced]**) para concluir a configuração da instância.

   Para obter mais informações, consulte [Implantando uma instância](../../installation/using/deploying-an-instance.md).

   Os principais parâmetros a serem definidos são os seguintes:

   * Delivery de email: endereços de remetente e resposta e a caixa de correio de erro para emails devolvidos.
   * Rastreamento: preencha a URL externa usada para redirecionamento e a URL interna, clique em **Registro no(s) servidor(es) de rastreamento** e valide-a na instância **demo** do servidor de rastreamento.

     Para obter mais informações, consulte [Configuração de rastreamento](../../installation/using/deploying-an-instance.md#tracking-configuration).

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     Como o servidor do Adobe Campaign é usado como o servidor de aplicativos e o servidor de redirecionamento, o URL interno usado para coletar logs de rastreamento e transferir URLs é uma conexão interna direta com o Tomcat (https://localhost:8080).

   * Gerenciamento de rejeição: insira os parâmetros para manipular emails de rejeição (não considere a seção **Emails de rejeição não processados**).
   * Acesso de: forneça os dois URLs para relatórios, formulários web e mirror pages.

     ![](assets/d_ncs_install_web_url.png)
