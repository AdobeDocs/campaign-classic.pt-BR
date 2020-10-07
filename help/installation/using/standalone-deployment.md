---
title: Implantação independente
seo-title: Implantação independente
description: Implantação independente
seo-description: null
page-status-flag: never-activated
uuid: 48ce793e-cb9f-4102-898f-758512cb9bf2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 9834638f-a8bb-4969-9f8d-99b8d9fdb1ca
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 2%

---


# Implantação independente{#standalone-deployment}

Esta configuração inclui todos os componentes no mesmo computador:

* processo de aplicação (Web),
* processo de delivery (mta),
* processo de redirecionamento (localização),
* processo de fluxo de trabalho e tarefas programadas (wfserver),
* processo de envio de correio (inMail),
* processo estatístico (estado).

A comunicação geral entre os processos é feita de acordo com o seguinte schema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Esse tipo de configuração pode ser executado ao gerenciar listas com menos de 100.000 recipient e, por exemplo, com as seguintes camadas de software:

* Linux,
* Apache,
* PostgreSQL,
* Correio.

À medida que o volume cresce, uma variante dessa arquitetura move o servidor de banco de dados para outro computador para melhorar o desempenho.

>[!NOTE]
>
>Um servidor de banco de dados existente também pode ser usado se tiver recursos suficientes.

## Recursos {#features}

### Vantagens {#advantages}

* Custo de configuração totalmente independente e baixo (nenhuma licença faturável é necessária se o software de código aberto listado abaixo for usado).
* Instalação simplificada e configuração de rede.

### Desvantagens {#disadvantages}

* Um computador crítico em caso de incidente.
* Largura de banda limitada ao transmitir mensagens (em nossa experiência, cerca de várias dezenas de milhares de emails por hora).
* Possível atraso do aplicativo ao transmitir.
* O servidor de aplicativos deve estar disponível de fora (enquanto estiver localizado no DMZ, por exemplo), pois hospeda o servidor de redirecionamento.

## Etapas de instalação e configuração {#installation-and-configuration-steps}

### Pré-requisitos {#prerequisites}

* JDK,
* Servidor Web (IIS, Apache),
* Acesso a um servidor de bases de dados,
* Caixa de correio de rejeição acessível via POP3,
* Criação de dois aliases DNS:

   * a primeira exposta ao público para rastreamento e indicação do computador no seu IP público;
   * o segundo alias exposto a usuários internos para acesso ao console e apontando para o mesmo computador.

* Firewall configurado para abrir SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 para Oracle, 5432 para PostgreSQL etc.) portas. Para obter mais informações, consulte Configuração [da](../../installation/using/network-configuration.md)rede.

Nos exemplos a seguir, os parâmetros da instância são:

* Nome da instância: **demonstração**
* Máscara de DNS: **console.campanha.net*** (somente para conexões de console do cliente e para relatórios)
* Banco de dados: **campanha:demo@dbsrv**

### Instalação e configuração (máquina única) {#installing-and-configuring--single-machine-}

Siga as etapas abaixo:

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

   * Para Linux: [Primeiro start do servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Para Windows: [Primeiro start do servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

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

1. Edite o arquivo **config-demo.xml** (criado na etapa anterior ao lado de **config-default.xml**) e certifique-se de que os processos **mta** (delivery), **wfserver** (fluxo de trabalho), **inMail** **** (mensagens de rejeição) e stat (estatísticas) estejam habilitados. Em seguida, configure o endereço do servidor de estatísticas:

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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Edite o arquivo **serverConf.xml** e especifique o domínio do delivery, em seguida, especifique os endereços IP (ou host) dos servidores DNS usados pelo módulo MTA para responder aos query DNS do tipo MX.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >O parâmetro **nameServers** só é usado no Windows.

   For more on this, refer to [Campaign server configuration](../../installation/using/campaign-server-configuration.md).

1. Copie o programa de configuração do console do cliente (**setup-client-7.XX**, **YYY.exe** para v7 ou **setup-client-6.XX**, **YYYY.exe** para v6.1) para a pasta **/datakit/nl/eng/jsp** .

   Para obter mais informações, consulte as seguintes seções:

   * Para Linux: [Disponibilidade do console do cliente para Linux](../../installation/using/client-console-availability-for-linux.md)
   * Para Windows: [Disponibilidade do console do cliente para Windows](../../installation/using/client-console-availability-for-windows.md)

1. Siga o procedimento de integração do servidor Web (IIS, Apache) descrito nas seguintes seções:

   * For Linux: [Integration into a Web server for Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * For Windows: [Integration into a Web server for Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Start o site e teste o redirecionamento usando o URL: https://tracking.campaign.net/r/test.

   O navegador deve exibir a seguinte mensagem:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Para obter mais informações, consulte as seguintes seções:

   * Para Linux: [Iniciar o servidor Web e testar a configuração](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Para Windows: [Iniciar o servidor Web e testar a configuração](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. Teste o módulo da Web **do** nlserver usando o URL: https://console.campaign.net/nl/jsp/logon.jsp

   Esse URL permite que você acesse a página de download do programa de configuração do cliente.

   Digite o logon **interno** e a senha associada ao acessar a página do controle de acesso.

   ![](assets/s_ncs_install_access_client.png)

   Para obter mais informações, consulte as seguintes seções:

   * Para Linux: [Disponibilidade do console do cliente para Linux](../../installation/using/client-console-availability-for-linux.md)
   * Para Windows: [Disponibilidade do console do cliente para Windows](../../installation/using/client-console-availability-for-windows.md)

1. Start do console do cliente Adobe Campaign (da página de download anterior ou iniciado diretamente no servidor para uma instalação do Windows), defina o URL da conexão do servidor como https://console.campaign.net e conecte-se usando o logon **interno** .

   Consulte [Criação de uma instância e logon](../../installation/using/creating-an-instance-and-logging-on.md) e identificador [](../../installation/using/campaign-server-configuration.md#internal-identifier)interno.

   O assistente de criação de banco de dados é exibido quando você faz logon pela primeira vez:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Siga as etapas do assistente e crie o banco de dados associado à instância de conexão.

   For more on this, refer to [Creating and configuring the database](../../installation/using/creating-and-configuring-the-database.md).

   Depois que o banco de dados for criado, faça logoff.

1. Faça logon novamente no console do cliente usando o logon do **administrador** sem uma senha e start o assistente de implantação ( **[!UICONTROL Tools > Advanced]** menu) para concluir a configuração da instância.

   For more on this, refer to [Deploying an instance](../../installation/using/deploying-an-instance.md).

   Os principais parâmetros a serem definidos são os seguintes:

   * Delivery de e-mail: endereços de remetente e resposta e a caixa de correio de erro para o correio de rejeição.
   * Acompanhamento: Preencha o URL externo usado para redirecionamento e o URL interno, clique em **Registro no(s) servidor(es)** de rastreamento e valide-o na instância de **demonstração** do servidor de rastreamento.

      For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Como o servidor Adobe Campaign é usado tanto como o servidor de aplicativos quanto o servidor de redirecionamento, o URL interno usado para coletar logs de rastreamento e transferir URLs é uma conexão interna direta com o Tomcat (https://localhost:8080).

   * Gerenciamento de rejeição: Informe os parâmetros para lidar com o email de rejeição (não leve em conta a seção de emails **** de rejeição não processados).
   * Acesso de: Forneça os dois URLs para relatórios, Formulários web e mirrores page.

      ![](assets/d_ncs_install_web_url.png)

