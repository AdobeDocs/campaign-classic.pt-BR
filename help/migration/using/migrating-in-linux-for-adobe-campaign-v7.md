---
product: campaign
title: Migração de uma plataforma Linux para Adobe Campaign v7
description: Saiba como migrar uma plataforma Linux para o Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Migração de uma plataforma Linux para o Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

As etapas de migração no Linux são as seguintes:

1. Pare todos os serviços - [Saiba mais](#service-stop).
1. Salve o banco de dados - [Saiba mais](#back-up-the-database).
1. Desinstalar pacotes de versão anteriores do Adobe Campaign - [Saiba mais](#uninstalling-adobe-campaign-previous-version-packages).
1. Migre a plataforma - [Saiba mais](#deploying-adobe-campaign-v7).
1. Reiniciar serviço - [Saiba mais](#re-starting-services).

## Parada de serviço {#service-stop}

Primeiro, pare todos os processos com acesso ao banco de dados em todas as máquinas em questão.

1. Fazer logon como **root**.
1. Todos os servidores que usam o módulo de redirecionamento (**webmdl** (serviço) precisa ser interrompido. Para o Apache, execute o seguinte comando:

   ```
   /etc/init.d/apache2 stop
   ```

1. Faça logon novamente como **root**.
1. Interrompa os serviços de versão anterior da Adobe Campaign em todos os servidores.

   ```
   /etc/init.d/nlserver6 stop
   ```

<!--
   If you are migrating from v5.11, run the following command:

   ```
   /etc/init.d/nlserver5 stop
   ```

-->

1. Verifique se os serviços da Adobe Campaign estão interrompidos em cada servidor.

   ```
   ps waux | grep nlserver
   ```

   A lista de processos ativos é exibida junto com sua ID (PID).

1. Se um ou mais processos do Adobe Campaign ainda estiverem ativos ou bloqueados após alguns minutos, mate-os.

   ```
   killall nlserver
   ```

1. Se alguns processos ainda estiverem ativos após alguns minutos, você poderá forçá-los a fechar usando o comando :

   ```
   killall -9 nlserver
   ```

## Fazer backup do banco de dados {#back-up-the-database}

<!--

### For Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database. 
1. Log in as **neolane** and make a backup of the **nl5** directory using the following command:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **nl5.back** folder and save it to a secure location other than the server.

1. Edit the **config-`<instance name>`.xml** (in the **nl5.back** folder), to prevent the **mta**, **wfserver**, **stat** etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart** (still as **neolane**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

<!--

### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Make a backup of the Adobe Campaign database. 
1. Log in as **neolane** and make a backup of the **nl6** directory using the following command:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **nl6.back** folder and save it to a secure location other than the server.

1. Edit the **config-`<instance name>`.xml** (in the **nl6.back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart** (still as **Adobe Campaign**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

1. Faça um backup do banco de dados do Adobe Campaign.
1. Fazer logon como **neolane** e faça um backup do **nl6** diretório usando o seguinte comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Como precaução, recomendamos que você compacte a variável **nl6.back** e salve-a em um local seguro diferente do servidor.

## Desinstalar pacotes de versão anteriores do Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

<!--

### For v5 packages {#uninstalling-adobe-campaign-v5-packages}

1. Log in as **root**.
1. Identify the Adobe Campaign packages installed using the following command.

    * In **Debian**:

      ```    
      dpkg -l | grep nl
      ```    
    
      The list of installed packages is displayed:

      ```    
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

    * In **Red Hat**:

      ```    
      rpm -qa | grep nl
      ```

1. Uninstall Adobe Campaign v5 packages.

    * In **Debian**:

      ```    
      dpkg --purge nlserver5 nlthirdparty5
      ```

    * In **Red Hat**:

      ```    
      rprm -ev nlserver5 nlthirdparty5
      ```

-->

Esta seção mostra como desinstalar pacotes do Adobe Campaign v6.1.

1. Fazer logon como **root**.
1. Identifique os pacotes do Adobe Campaign instalados usando o seguinte comando.

   * Em **Debian**:

      ```
      dpkg -l | grep nl
      ```

      A lista de pacotes instalados é exibida:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * Em **Chapéu Vermelho**:

      ```
      rpm -qa | grep nl
      ```

1. Desinstale os pacotes do Adobe Campaign v6.

   * Em **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * Em **Chapéu Vermelho**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Implantar o Adobe Campaign v7 {#deploying-adobe-campaign-v7}

Este é o procedimento para implantar o v7.

<!--

### From Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Deploying Adobe Campaign involves two stages:

* Installing Adobe Campaign v7 packages: this operation must be performed on each server.
* The post upgrade: this command must be started on each instance.

To deploy Adobe Campaign, apply the following steps:

1. Install the most recent Adobe Campaign v7 packages using the following command:

    * In **Debian**:

      ```    
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

    * In **Red Hat**:

      ```    
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```

   >[!IMPORTANT]
   >
   >You must install the packages successfully before going on to the next step.

   >[!NOTE]
   >
   >When migrating from v5.11, Adobe Campaign is installed in the **/usr/local/neolane/nl6/** directory by default.
   >
   >Once the packages are installed, the following message is displayed: **'WdbcTimeZone' option is missing**. This is normal.

1. To make the client console installation program available, copy it into the Adobe Campaign installation directory:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >For more on how to install Adobe Campaign in Linux, refer to [this section](../../installation/using/installing-campaign-standard-packages.md).

1. Modify the **.bashrd** file which matches the **neolane** user. Log on as **neolane** and run the following command:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >When you log in as **neolane**, the following message is displayed: **nl5/env.sh : No such file or directory**. This is normal.

   At the end of the file, replace **nl5/env.sh** with **nl6/env.sh**.

1. Log in as **root** and prepare the instance using the following commands:

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >These commands let you create the Adobe Campaign v6 internal files system: **conf** directory (with the **config-default.xml** and **serverConf.xml** files), **var** directory.

1. Go to the **nl5.back** backup folder and copy (overwrite) the configuration files and sub-folders of each instance. Log in as **neolane** and run the following command:

   >[!IMPORTANT]
   >
   >For the first command below, do not copy the **config-default.xml** file.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. In the Adobe Campaign v7 **serverConf.xml** and **config-default.xml** files, apply the specific configurations that you had for Adobe Campaign v5. For the **serverConf.xml** file, use the **nl5/conf/serverConf.xml.diff** file.

   >[!NOTE]
   >
   >When reporting configurations from Adobe Campaign v5 to Adobe Campaign v7, make sure the paths to the physical directories lead to Adobe Campaign v7 and not Adobe Campaign v5.

1. Since migration is not a generic installation, you need to force the re-starting of the **trackinglogd** service. To do this, open the **nl6/conf/config-default.xml** file and make sure the **trackinglogd** service is activated (only on the tracking/redirection server(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >If the **trackinglogd** service is not started on the tracking server, no tracking information will be forwarded.

1. Reload the Adobe Campaign v7 configuration using the following command:

   ```
   nlserver config -reload
   ```

1. Start the postupgrade process using the following command (still as **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >You must specify which timezone to use as a reference during the postupgrade (using the **-timezone** option). In this case, we are using the Europe/Paris timezone **-timezone: "Europe/Paris"**.

   >[!NOTE]
   >
   >We strongly recommend upgrading your base to "multi timezone". For further information about timezone options, refer to the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

>[!IMPORTANT]
>
>Do not start Adobe Campaign services yet: changes still need to be made in Apache.

### From Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Deploying Adobe Campaign involves two stages:

* Installing Adobe Campaign v7 packages: this operation must be performed on each server.
* The post upgrade: this command must be started on each instance.

To deploy Adobe Campaign, apply the following steps:

1. Install the most recent Adobe Campaign v7 packages using the following command:

    * In **Debian**:

      ```    
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

    * In **Red Hat**:

      ```    
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```

   >[!IMPORTANT]
   >
   >You must install the packages successfully before going on to the next step.

   >[!NOTE]
   >
   >Adobe Campaign v7 is installed in the same directory by default as Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. To make the client console installation program available, copy it into the Adobe Campaign installation directory:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >For more on how to install Adobe Campaign in Linux, refer to [this section](../../installation/using/installing-campaign-standard-packages.md).

1. Since migration is not a generic installation, you need to force the re-starting of the **trackinglogd** service. To do this, open the **nl6/conf/config-default.xml** file and make sure the **trackinglogd** service is activated (only on the tracking/redirection server(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >If the **trackinglogd** service is not started on the tracking server, no tracking information will be forwarded.

1. Go to the **nl6.back** backup folder and copy (overwrite) the configuration files and sub-folders of each instance. Log in as **neolane** and run the following command:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Reload the Adobe Campaign v7 configuration using the following command:

   ```
   nlserver config -reload
   ```

1. Start the postupgrade process using the following command (still as **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >The "multi timezone" mode was only available in v6.02 for PostgreSQL database engines. It is now available no matter what version of database engine is being used. We strongly recommend upgrading your base to "multi timezone". For further information about timezone options, refer to the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

-->

A implantação do Adobe Campaign envolve duas etapas:

* Instalação de pacotes do Adobe Campaign v7: essa operação deve ser executada em cada servidor.
* A atualização posterior: esse comando deve ser iniciado em cada instância.

Para implantar o Adobe Campaign, siga as etapas abaixo:

1. Instale os pacotes mais recentes do Adobe Campaign v7 usando o seguinte comando:

   * Em **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * Em **Chapéu Vermelho**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Você deve instalar os pacotes com êxito antes de passar para a próxima etapa.

   >[!NOTE]
   >
   >O Adobe Campaign v7 está instalado na variável **/usr/local/neolane/nl6/** por padrão.

1. Para disponibilizar o programa de instalação do console do cliente, copie-o no diretório de instalação do Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obter mais informações sobre como instalar o Adobe Campaign no Linux, consulte [esta seção](../../installation/using/installing-campaign-standard-packages.md).

1. Vá para o **nl6.back** pasta de backup e copie (substitua) os arquivos e as subpastas de configuração de cada instância. Fazer logon como **neolane** e execute o seguinte comando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Recarregue a configuração do Adobe Campaign v7 usando o seguinte comando:

   ```
   nlserver config -reload
   ```

1. Inicie o processo pós-atualização usando o seguinte comando (ainda como **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

<!--

## Migrate the redirection server (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>This section only applies when migrating from Adobe Campaign v5.11.

At this stage, Apache needs to be stopped. Refer to: [Service stop](#service-stop).

1. Log in as **root**.
1. Change the Apache environment variables to make them link to the **nl6** directory.

    * In **Debian**:

      ```    
      vi /etc/apache2/envvars
      ```

    * In **Red Hat**:

      ```    
      vi /usr/local/apache2/bin/envvars
      ```

1. Then run the following commands:

    * In **Debian**:

      In the **nlsrv.load** file, replace **nl5** with **nl6**.

      ```    
      vi /etc/apache2/mods-available/nlsrv.load
      ```    
    
      Delete the link of the **nlsrv.conf** file and create a new one.

      ```    
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

    * In **Red Hat**:

      Go to the **/usr/local/apache2/conf** directory, edit the **http.conf** file and replace **nl5** with **nl6** in the following lines.

      In **RHEL 7/Debian 8**:

      ```    
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Go to the **alias.conf** file and replace all **nl5** with **nl6**. To do this in Debian, run the following command:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

-->

<!--

## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. For more information, refer to [Security](../../migration/using/general-configurations.md#security).

-->

## Reiniciar serviços {#re-starting-services}

Este é o procedimento para reiniciar os serviços.

<!--

### For Adobe Campaign v5 {#migrating-from-adobe-campaign-v5_11-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache and Adobe Campaign services on each of the following servers:

1. Tracking and redirection server.
1. Mid-sourcing server.
1. Marketing server.

Before going on to the next step, run a full test of the new installation, make sure there are no regressions and that everything works by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache and Adobe Campaign services on each of the following servers:

1. Tracking and redirection server.
1. Mid-sourcing server.
1. Marketing server.

Fully test the new installation, check that it does not regress and make sure that everything is working correctly by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

-->

Inicie os serviços do Apache e da Adobe Campaign em cada um dos seguintes servidores:

1. Servidor de rastreamento e redirecionamento.
1. Servidor Mid-sourcing.
1. Servidor de marketing.

Teste completamente a nova instalação, verifique se ela não regride e se tudo está funcionando corretamente.

<!--

## Delete the Adobe Campaign previous version {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>This section only applies when migrating from Adobe Campaign v5.11.

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

Delete the **nl5.back** directory. Log in as **neolane** and run the following command:

```
su - neolane
rm -rf nl5.back
```

Re-start the server.

-->
