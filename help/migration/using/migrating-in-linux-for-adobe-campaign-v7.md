---
product: campaign
title: Migração de uma plataforma Linux para Adobe Campaign v7
description: Saiba como migrar uma plataforma Linux para o Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 63aca25a8d1ae24ef83849b35a44d1b37cfa5e96
workflow-type: tm+mt
source-wordcount: '1858'
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

   Se você estiver migrando da v5.11, execute o seguinte comando:

   ```
   /etc/init.d/nlserver5 stop
   ```

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

O procedimento depende da versão anterior do Adobe Campaign.

### Para Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Faça um backup do banco de dados do Adobe Campaign.
1. Fazer logon como **neolane** e faça um backup do **nl5** diretório usando o seguinte comando:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Como precaução, recomendamos que você compacte a variável **nl5.back** e salve-a em um local seguro diferente do servidor.

1. Edite o **config-`<instance name>`.xml** na **nl5.back** pasta), para evitar o **mta**, **wfserver**, **stat** etc. de iniciar automaticamente. Por exemplo, substitua **autoStart** com **_autoStart** (ainda como **neolane**).

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

### Para Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Faça um backup do banco de dados do Adobe Campaign.
1. Fazer logon como **neolane** e faça um backup do **nl6** diretório usando o seguinte comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Como precaução, recomendamos que você compacte a variável **nl6.back** e salve-a em um local seguro diferente do servidor.

1. Edite o **config-`<instance name>`.xml** na **nl6.back** para evitar que a variável **mta**, **wfserver**, **stat**, etc. de iniciar automaticamente. Por exemplo, substitua **autoStart** com **_autoStart** (ainda como **Adobe Campaign**).

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

### Para Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

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

O procedimento depende da versão anterior do Adobe Campaign.

### Para pacotes v5 {#uninstalling-adobe-campaign-v5-packages}

1. Fazer logon como **root**.
1. Identifique os pacotes do Adobe Campaign instalados usando o seguinte comando.

   * Em **Debian**:

      ```
      dpkg -l | grep nl
      ```

      A lista de pacotes instalados é exibida:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * Em **Chapéu Vermelho**:

      ```
      rpm -qa | grep nl
      ```

1. Desinstale os pacotes Adobe Campaign v5.

   * Em **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * Em **Chapéu Vermelho**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Para pacotes v6 {#uninstalling-adobe-campaign-v6-packages}

Esta seção mostra como desinstalar pacotes Adobe Campaign v6.02 ou v6.1.

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

O procedimento depende da versão anterior do Adobe Campaign.

### Do Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

A implantação do Adobe Campaign envolve duas etapas:

* Instalação de pacotes do Adobe Campaign v7: essa operação deve ser executada em cada servidor.
* A atualização posterior: esse comando deve ser iniciado em cada instância.

Para implantar o Adobe Campaign, siga as etapas abaixo:

1. Instale os pacotes mais recentes do Adobe Campaign v7 usando o seguinte comando:

   * Em **Debian**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * Em **Chapéu Vermelho**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >Você deve instalar os pacotes com êxito antes de passar para a próxima etapa.

   >[!NOTE]
   >
   >Ao migrar da v5.11, o Adobe Campaign é instalado no **/usr/local/neolane/nl6/** por padrão.
   >
   >Depois que os pacotes forem instalados, a seguinte mensagem será exibida: **A opção &#39;WdbcTimeZone&#39; está ausente**. Isso é normal.

1. Para disponibilizar o programa de instalação do console do cliente, copie-o no diretório de instalação do Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obter mais informações sobre como instalar o Adobe Campaign no Linux, consulte [esta seção](../../installation/using/installing-campaign-standard-packages.md).

1. Modifique o **.bashrd** que corresponde ao **neolane** usuário. Faça logon como **neolane** e execute o seguinte comando:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Ao fazer logon como **neolane**, a seguinte mensagem é exibida: **nl5/env.sh : Esse arquivo ou diretório não existe**. Isso é normal.

   No final do arquivo, substitua **nl5/env.sh** com **nl6/env.sh**.

1. Fazer logon como **root** e prepare a instância usando os seguintes comandos:

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
   >Esses comandos permitem criar o sistema de arquivos internos Adobe Campaign v6: **conf** diretório (com o **config-default.xml** e **serverConf.xml** arquivos), **var** diretório.

1. Vá para o **nl5.back** pasta de backup e copie (substitua) os arquivos e as subpastas de configuração de cada instância. Fazer logon como **neolane** e execute o seguinte comando:

   >[!IMPORTANT]
   >
   >Para o primeiro comando abaixo, não copie a variável **config-default.xml** arquivo.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. No Adobe Campaign v7 **serverConf.xml** e **config-default.xml** , aplique as configurações específicas que você tinha para o Adobe Campaign v5. Para o **serverConf.xml** use o **nl5/conf/serverConf.xml.diff** arquivo.

   >[!NOTE]
   >
   >Ao relatar configurações do Adobe Campaign v5 para o Adobe Campaign v7, verifique se os caminhos para os diretórios físicos levam ao Adobe Campaign v7 e não ao Adobe Campaign v5.

1. Como a migração não é uma instalação genérica, é necessário forçar o reinício do **trackinglogd** serviço. Para fazer isso, abra o **nl6/conf/config-default.xml** e certifique-se de que **trackinglogd** estiver ativado (somente no(s) servidor(es) de rastreamento/redirecionamento):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Se a variável **trackinglogd** não for iniciado no servidor de rastreamento, nenhuma informação de rastreamento será encaminhada.

1. Recarregue a configuração do Adobe Campaign v7 usando o seguinte comando:

   ```
   nlserver config -reload
   ```

1. Inicie o processo pós-atualização usando o seguinte comando (ainda como **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >Você deve especificar qual fuso horário usar como referência durante a pós-atualização (usando o **-fuso horário** ). Neste caso, estamos a utilizar o fuso horário Europa/Paris **-fuso horário: &quot;Europa/Paris&quot;**.

   >[!NOTE]
   >
   >É altamente recomendável atualizar sua base para &quot;vários fusos horários&quot;. Para obter mais informações sobre as opções de fuso horário, consulte [Fusos horários](../../migration/using/general-configurations.md#time-zones) seção.

>[!IMPORTANT]
>
>Ainda não inicie os serviços da Adobe Campaign: ainda é necessário fazer alterações no Apache.

### Do Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

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
   >O Adobe Campaign v7 é instalado no mesmo diretório por padrão que o Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. Para disponibilizar o programa de instalação do console do cliente, copie-o no diretório de instalação do Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obter mais informações sobre como instalar o Adobe Campaign no Linux, consulte [esta seção](../../installation/using/installing-campaign-standard-packages.md).

1. Como a migração não é uma instalação genérica, é necessário forçar o reinício do **trackinglogd** serviço. Para fazer isso, abra o **nl6/conf/config-default.xml** e certifique-se de que **trackinglogd** estiver ativado (somente no(s) servidor(es) de rastreamento/redirecionamento):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Se a variável **trackinglogd** não for iniciado no servidor de rastreamento, nenhuma informação de rastreamento será encaminhada.

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

   >[!NOTE]
   >
   >O modo &quot;vários fusos horários&quot; estava disponível somente na v6.02 para mecanismos de banco de dados PostgreSQL. Agora ele está disponível independentemente da versão do mecanismo de banco de dados que está sendo usada. É altamente recomendável atualizar sua base para &quot;vários fusos horários&quot;. Para obter mais informações sobre as opções de fuso horário, consulte [Fusos horários](../../migration/using/general-configurations.md#time-zones) seção.

### Do Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

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

## Migrar o servidor de redirecionamento (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Esta seção só se aplica ao migrar do Adobe Campaign v5.11.

Nesse estágio, o Apache precisa ser interrompido. Consulte: [Parada de serviço](#service-stop).

1. Fazer logon como **root**.
1. Altere as variáveis de ambiente do Apache para vinculá-las ao **nl6** diretório.

   * Em **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * Em **Chapéu Vermelho**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Em seguida, execute os seguintes comandos:

   * Em **Debian**:

      No **nlsrv.load** arquivo, substituir **nl5** com **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Exclua o link do **nlsrv.conf** e crie um novo.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * Em **Chapéu Vermelho**:

      Vá para o **/usr/local/apache2/conf** , edite o **http.conf** arquivo e substitua **nl5** com **nl6** nas linhas a seguir.

      Em **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Vá para o **alias.conf** arquivo e substitua tudo **nl5** com **nl6**. Para fazer isso no Debian, execute o seguinte comando:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Zonas de segurança {#security-zones}

Se estiver migrando da v6.02 ou anterior, você deve configurar as zonas de segurança antes de iniciar os serviços. Para obter mais informações, consulte [Segurança](../../migration/using/general-configurations.md#security).

## Reiniciar serviços {#re-starting-services}

O procedimento depende da versão anterior do Adobe Campaign.

### Para Adobe Campaign v5 {#migrating-from-adobe-campaign-v5_11-2}

No **config-`<instance name>`.xml** arquivos, reative a inicialização automática do **mta**, **wfserver**, **stat**, etc. serviços.

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

Inicie os serviços do Apache e da Adobe Campaign em cada um dos seguintes servidores:

1. Servidor de rastreamento e redirecionamento.
1. Servidor Mid-sourcing.
1. Servidor de marketing.

Antes de prosseguir para a próxima etapa, execute um teste completo da nova instalação, verifique se não há regressões e se tudo funciona seguindo todas as recomendações da [Configurações gerais](../../migration/using/general-configurations.md) seção.

### Para Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

No **config-`<instance name>`.xml** arquivos, reative a inicialização automática do **mta**, **wfserver**, **stat**, etc. serviços.

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

Inicie os serviços do Apache e da Adobe Campaign em cada um dos seguintes servidores:

1. Servidor de rastreamento e redirecionamento.
1. Servidor Mid-sourcing.
1. Servidor de marketing.

Teste completamente a nova instalação, verifique se ela não regride e se tudo está funcionando corretamente seguindo todas as recomendações da [Configurações gerais](../../migration/using/general-configurations.md) seção.

### Para Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Inicie os serviços do Apache e da Adobe Campaign em cada um dos seguintes servidores:

1. Servidor de rastreamento e redirecionamento.
1. Servidor Mid-sourcing.
1. Servidor de marketing.

Teste completamente a nova instalação, verifique se ela não regride e se tudo está funcionando corretamente seguindo todas as recomendações da [Configurações gerais](../../migration/using/general-configurations.md) seção.

## Excluir a versão anterior do Adobe Campaign {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Esta seção só se aplica ao migrar do Adobe Campaign v5.11.

Antes de excluir e limpar a instalação do Adobe Campaign v5, você deve aplicar as seguintes recomendações:

* Obtenha as equipes funcionais para executar uma verificação completa da nova instalação.
* Desinstale o Adobe Campaign v5 somente depois de ter certeza de que nenhuma reversão será necessária.

Exclua o **nl5.back** diretório. Fazer logon como **neolane** e execute o seguinte comando:

```
su - neolane
rm -rf nl5.back
```

Reinicie o servidor.
