---
solution: Campaign Classic
product: campaign
title: 'Migração para o Adobe Campaign v7 no Linux '
description: 'Migração para o Adobe Campaign v7 no Linux '
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---


# Migração para o Adobe Campaign v7 no Linux {#migrating-in-linux-for-adobe-campaign-v}

## Procedimento geral {#general-procedure}

As etapas de migração no Linux são as seguintes:

1. Parar serviços: consulte Parada [de serviço](#service-stop).
1. Salve o banco de dados: consulte [Fazer backup do banco de dados e da instalação](#back-up-the-database-and-the-existing-installation)existente.
1. Desinstale os pacotes de versão anteriores do Adobe Campaign: consulte [Desinstalação dos pacotes](#uninstalling-adobe-campaign-previous-version-packages)da versão anterior do Adobe Campaign.
1. Migre a plataforma: consulte [Implantação do Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Restart do serviço: consulte [Reinicializando serviços](#re-starting-services).

## Parada de serviço {#service-stop}

Em primeiro lugar, interromper todos os processos com acesso à base de dados em todas as máquinas em causa.

1. Faça logon como **raiz**.
1. Todos os servidores que usam o módulo de redirecionamento (serviço **webmdl** ) precisam ser interrompidos. Para o Apache, execute o seguinte comando:

   ```
   /etc/init.d/apache2 stop
   ```

1. Faça logon novamente como **raiz**.
1. Pare os serviços de versão anterior da Adobe Campaign em todos os servidores.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Se você estiver migrando da v5.11, execute o seguinte comando:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Certifique-se de que os serviços da Adobe Campaign sejam interrompidos em cada servidor.

   ```
   ps waux | grep nlserver
   ```

   A lista dos processos ativos é exibida junto com sua ID (PID).

1. Se um ou mais processos do Adobe Campaign ainda estiverem ativos ou bloqueados após alguns minutos, mate-os.

   ```
   killall nlserver
   ```

1. Se alguns processos ainda estiverem ativos após alguns minutos, você pode forçá-los a fechar usando o comando:

   ```
   killall -9 nlserver
   ```

## Faça backup do banco de dados e da instalação existente {#back-up-the-database-and-the-existing-installation}

O procedimento depende da versão anterior do Adobe Campaign.

### Migração do Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Faça um backup do banco de dados Adobe Campaign.
1. Faça logon como **neolane** e faça um backup do diretório **nl5** usando o seguinte comando:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Como precaução, recomendamos que você compacte a pasta **nl5.back** e salve-a em um local seguro diferente do servidor.

1. Edite o **config-`<instance name>`.xml** (na pasta **nl5.back** ) para impedir o **mta**, o **wfserver**, **** stat, etc. de iniciar automaticamente. Por exemplo, substitua **autoStart** por **_autoStart** (ainda como **neolane**).

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

### Migração do Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Faça um backup do banco de dados Adobe Campaign.
1. Faça logon como **neolane** e faça um backup do diretório **nl6** usando o seguinte comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Como precaução, recomendamos que você compacte a pasta **nl6.back** e salve-a em um local seguro diferente do servidor.

1. Edite o **config-`<instance name>`.xml** (na pasta **nl6.back** ) para impedir o **mta**, o **wfserver**, **** stat, etc. de iniciar automaticamente. Por exemplo, substitua **autoStart** por **_autoStart** (ainda como **Adobe Campaign**).

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

### Migração do Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Faça um backup do banco de dados Adobe Campaign.
1. Faça logon como **neolane** e faça um backup do diretório **nl6** usando o seguinte comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Como precaução, recomendamos que você compacte a pasta **nl6.back** e salve-a em um local seguro diferente do servidor.

## Desinstalação dos pacotes de versão anterior do Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

O procedimento depende da versão anterior do Adobe Campaign.

### Desinstalação de pacotes Adobe Campaign v5 {#uninstalling-adobe-campaign-v5-packages}

1. Faça logon como **raiz**.
1. Identifique os pacotes Adobe Campaign instalados usando o seguinte comando.

   * Em **Debian**:

      ```
      dpkg -l | grep nl
      ```

      A lista dos pacotes instalados é exibida:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * Em Chapéu **Vermelho**:

      ```
      rpm -qa | grep nl
      ```

1. Desinstale os pacotes Adobe Campaign v5.

   * Em **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * Em Chapéu **Vermelho**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Desinstalação de pacotes Adobe Campaign v6 {#uninstalling-adobe-campaign-v6-packages}

Esta seção mostra como desinstalar os pacotes Adobe Campaign v6.02 ou v6.1.

1. Faça logon como **raiz**.
1. Identifique os pacotes Adobe Campaign instalados usando o seguinte comando.

   * Em **Debian**:

      ```
      dpkg -l | grep nl
      ```

      A lista dos pacotes instalados é exibida:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * Em Chapéu **Vermelho**:

      ```
      rpm -qa | grep nl
      ```

1. Desinstale os pacotes Adobe Campaign v6.

   * Em **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * Em Chapéu **Vermelho**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Implantação do Adobe Campaign v7 {#deploying-adobe-campaign-v7}

O procedimento depende da versão anterior do Adobe Campaign.

### Migração do Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

A implantação do Adobe Campaign envolve duas etapas:

* Instalação de pacotes Adobe Campaign v7: esta operação deve ser executada em cada servidor.
* A atualização posterior: esse comando deve ser iniciado em cada instância.

Para implantar o Adobe Campaign, aplique as seguintes etapas:

1. Instale os pacotes mais recentes do Adobe Campaign v7 usando o seguinte comando:

   * Em **Debian**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * Em Chapéu **Vermelho**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >É necessário instalar os pacotes com êxito antes de passar para a próxima etapa.

   >[!NOTE]
   >
   >Ao migrar da v5.11, o Adobe Campaign é instalado no diretório **/usr/local/neolane/nl6/** por padrão.
   >
   >Depois que os pacotes forem instalados, a seguinte mensagem será exibida: **A opção &#39;WdbcTimeZone&#39; está ausente**. Isto é normal.

1. Para disponibilizar o programa de instalação do console do cliente, copie-o no diretório de instalação do Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obter mais informações sobre como instalar o Adobe Campaign no Linux, consulte [esta seção](../../installation/using/installing-campaign-standard-packages.md).

1. Modifique o arquivo **.bashrd** que corresponde ao usuário **neolane** . Faça logon como **neolane** e execute o seguinte comando:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Quando você faz logon como **neolane**, a seguinte mensagem é exibida: **nl5/env.sh : Esse arquivo ou diretório** não existe. Isto é normal.

   No final do arquivo, substitua **nl5/env.sh** por **nl6/env.sh**.

1. Faça logon como **raiz** e prepare a instância usando os seguintes comandos:

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
   >Esses comandos permitem criar o sistema de arquivos internos Adobe Campaign v6: **diretório conf** (com os arquivos **config-default.xml** e **serverConf.xml** ), diretório **var** .

1. Vá para a pasta de backup **nl5.back** e copie (substitua) os arquivos e as subpastas de configuração de cada instância. Faça logon como **neolane** e execute o seguinte comando:

   >[!IMPORTANT]
   >
   >Para o primeiro comando abaixo, não copie o arquivo **config-default.xml** .

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. Nos arquivos Adobe Campaign v7 **serverConf.xml** e **config-default.xml** , aplique as configurações específicas que você tinha para Adobe Campaign v5. Para o arquivo **serverConf.xml** , use o arquivo **nl5/conf/serverConf.xml.diff** .

   >[!NOTE]
   >
   >Quando as configurações de relatórios do Adobe Campaign v5 para o Adobe Campaign v7, verifique se os caminhos para os diretórios físicos levam ao Adobe Campaign v7 e não ao Adobe Campaign v5.

1. Como a migração não é uma instalação genérica, é necessário forçar a reinicialização do serviço **trackinglogd** . Para fazer isso, abra o arquivo **nl6/conf/config-default.xml** e verifique se o serviço **trackinglogd** está ativado (somente nos servidores de rastreamento/redirecionamento):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Se o serviço **trackinglogd** não for iniciado no servidor de rastreamento, nenhuma informação de rastreamento será encaminhada.

1. Recarregue a configuração do Adobe Campaign v7 usando o seguinte comando:

   ```
   nlserver config -reload
   ```

1. Start o processo pós-atualização usando o seguinte comando (ainda como **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >Você deve especificar qual fuso horário usar como referência durante a pós-atualização (usando a opção **-fuso horário** ). Neste caso, estamos a utilizar o fuso horário Europa/Paris **-: &quot;Europa/Paris&quot;**.

   >[!NOTE]
   >
   >Recomendamos que você atualize sua base para &quot;vários fusos horários&quot;. Para obter mais informações sobre opções de fuso horário, consulte a seção [Fusos](../../migration/using/general-configurations.md#time-zones) horários.

>[!IMPORTANT]
>
>Ainda não start os serviços da Adobe Campaign: ainda é necessário fazer alterações no Apache.

### Migração do Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

A implantação do Adobe Campaign envolve duas etapas:

* Instalação de pacotes Adobe Campaign v7: esta operação deve ser executada em cada servidor.
* A atualização posterior: esse comando deve ser iniciado em cada instância.

Para implantar o Adobe Campaign, aplique as seguintes etapas:

1. Instale os pacotes mais recentes do Adobe Campaign v7 usando o seguinte comando:

   * Em **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * Em Chapéu **Vermelho**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >É necessário instalar os pacotes com êxito antes de passar para a próxima etapa.

   >[!NOTE]
   >
   >O Adobe Campaign v7 é instalado no mesmo diretório por padrão que o Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. Para disponibilizar o programa de instalação do console do cliente, copie-o no diretório de instalação do Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obter mais informações sobre como instalar o Adobe Campaign no Linux, consulte [esta seção](../../installation/using/installing-campaign-standard-packages.md).

1. Como a migração não é uma instalação genérica, é necessário forçar a reinicialização do serviço **trackinglogd** . Para fazer isso, abra o arquivo **nl6/conf/config-default.xml** e verifique se o serviço **trackinglogd** está ativado (somente nos servidores de rastreamento/redirecionamento):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Se o serviço **trackinglogd** não for iniciado no servidor de rastreamento, nenhuma informação de rastreamento será encaminhada.

1. Vá para a pasta de backup **nl6.back** e copie (substitua) os arquivos e as subpastas de configuração de cada instância. Faça logon como **neolane** e execute o seguinte comando:

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

1. Start o processo pós-atualização usando o seguinte comando (ainda como **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >O modo &quot;multifuso horário&quot; estava disponível somente na v6.02 para mecanismos de banco de dados PostgreSQL. Agora ele está disponível independentemente da versão do mecanismo de banco de dados que está sendo usada. Recomendamos que você atualize sua base para &quot;vários fusos horários&quot;. Para obter mais informações sobre opções de fuso horário, consulte a seção [Fusos](../../migration/using/general-configurations.md#time-zones) horários.

### Migração do Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

A implantação do Adobe Campaign envolve duas etapas:

* Instalação de pacotes Adobe Campaign v7: esta operação deve ser executada em cada servidor.
* A atualização posterior: esse comando deve ser iniciado em cada instância.

Para implantar o Adobe Campaign, aplique as seguintes etapas:

1. Instale os pacotes mais recentes do Adobe Campaign v7 usando o seguinte comando:

   * Em **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * Em Chapéu **Vermelho**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >É necessário instalar os pacotes com êxito antes de passar para a próxima etapa.

   >[!NOTE]
   >
   >O Adobe Campaign v7 é instalado no diretório **/usr/local/neolane/nl6/** por padrão.

1. Para disponibilizar o programa de instalação do console do cliente, copie-o no diretório de instalação do Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obter mais informações sobre como instalar o Adobe Campaign no Linux, consulte [esta seção](../../installation/using/installing-campaign-standard-packages.md).

1. Vá para a pasta de backup **nl6.back** e copie (substitua) os arquivos e as subpastas de configuração de cada instância. Faça logon como **neolane** e execute o seguinte comando:

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

1. Start o processo pós-atualização usando o seguinte comando (ainda como **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migração do servidor de redirecionamento (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Esta seção só se aplica ao migrar do Adobe Campaign v5.11.

Nessa fase, o Apache precisa ser parado. Consulte: [Parada](#service-stop)de serviço.

1. Faça logon como **raiz**.
1. Altere as variáveis de ambiente do Apache para torná-las vinculadas ao diretório **nl6** .

   * Em **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * Em Chapéu **Vermelho**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Em seguida, execute os seguintes comandos:

   * Em **Debian**:

      No arquivo **nlsrv.load** , substitua **nl5** por **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Exclua o link do arquivo **nlsrv.conf** e crie um novo.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * Em Chapéu **Vermelho**:

      Vá para o diretório **/usr/local/apache2/conf** , edite o arquivo **http.conf** e substitua **nl5** por **nl6** nas seguintes linhas.

      No **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Vá para o arquivo **alias.conf** e substitua todos os arquivos **nl5** por **nl6**. Para fazer isso no Debian, execute o seguinte comando:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Zonas de segurança {#security-zones}

Se você estiver migrando da v6.02 ou versão anterior, é necessário configurar as zonas de segurança antes de iniciar os serviços. Para obter mais informações, consulte [Segurança](../../migration/using/general-configurations.md#security).

## Reiniciando serviços {#re-starting-services}

O procedimento depende da versão anterior do Adobe Campaign.

### Migração do Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

Nos arquivos **config-`<instance name>`.xml** , reative a inicialização automática do **mta**, **wfserver**, **stat** etc. serviços.

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

Serviços Apache e Adobe Campaign do start em cada um dos seguintes servidores:

1. Servidor de rastreamento e redirecionamento.
1. Servidor Mid-sourcing.
1. Servidor de marketing.

Antes de passar para a próxima etapa, execute um teste completo da nova instalação, certifique-se de que não há regressões e que tudo funciona seguindo todas as recomendações da seção Configurações [](../../migration/using/general-configurations.md) gerais.

### Migração do Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

Nos arquivos **config-`<instance name>`.xml** , reative a inicialização automática do **mta**, **wfserver**, **stat** etc. serviços.

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

Serviços Apache e Adobe Campaign do start em cada um dos seguintes servidores:

1. Servidor de rastreamento e redirecionamento.
1. Servidor Mid-sourcing.
1. Servidor de marketing.

Teste completamente a nova instalação, verifique se ela não regride e se tudo está funcionando corretamente seguindo todas as recomendações da seção Configurações [](../../migration/using/general-configurations.md) gerais.

### Migração do Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Serviços Apache e Adobe Campaign do start em cada um dos seguintes servidores:

1. Servidor de rastreamento e redirecionamento.
1. Servidor Mid-sourcing.
1. Servidor de marketing.

Teste completamente a nova instalação, verifique se ela não regride e se tudo está funcionando corretamente seguindo todas as recomendações da seção Configurações [](../../migration/using/general-configurations.md) gerais.

## Exclusão e limpeza do Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Esta seção só se aplica ao migrar do Adobe Campaign v5.11.

Antes de excluir e limpar a instalação do Adobe Campaign v5, você deve aplicar as seguintes recomendações:

* Obtenha as equipes funcionais para executar uma verificação completa da nova instalação.
* Desinstale o Adobe Campaign v5 somente depois de ter certeza de que nenhuma reversão é necessária.

Exclua o diretório **nl5.back** . Faça logon como **neolane** e execute o seguinte comando:

```
su - neolane
rm -rf nl5.back
```

Restart o servidor.
