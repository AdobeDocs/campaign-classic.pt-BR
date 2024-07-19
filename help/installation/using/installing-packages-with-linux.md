---
product: campaign
title: Instalação de pacotes com Linux
description: Instalação de pacotes com Linux
feature: Installation, Application Settings
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 1%

---

# Instalação de pacotes com Linux{#installing-packages-with-linux}

O Adobe Campaign vem com o pacote **nlserver** que contém os arquivos binários e de configuração para uma determinada versão.

Os comandos de instalação permitem:

* Copiar os arquivos para **/usr/local/neolane**
* Crie uma conta do Adobe Campaign Linux (e o grupo associado), que é criada com **/usr/local/neolane** como seu diretório inicial
* Crie um script automático **/etc/init.d/nlserver6** para usar na inicialização ou crie uma unidade do sistema

>[!NOTE]
>
>O usuário do sistema **neolane** não deve ter sido criado antes da execução do comando. O usuário **neolane** é criado automaticamente durante a instalação.
>
>O diretório **home** vinculado ao usuário **neolane** também é criado automaticamente em **[!UICONTROL /usr/local/neolane]**. Verifique se há espaço suficiente no disco **[!UICONTROL /usr/local]**.

Você pode executar o comando **ping`hostname`** para verificar se o servidor pode alcançar a si mesmo.

## Distribuição com base em pacotes RPM {#distribution-based-on-rpm--packages}

Para instalar o Adobe Campaign em um sistema operacional RPM (RHEL, CentOS), siga estas etapas:

1. Obtenha o pacote do Adobe Campaign. O nome do arquivo é **nlserver6-v7-XXXX-0.x86_64.rpm**, onde **XXXX** é o número da compilação do Adobe Campaign.

   >[!CAUTION]
   >
   >Certifique-se de usar o nome de arquivo correto para sua versão do Adobe Campaign nos exemplos de comando desta seção.

1. Para instalá-lo, conecte como **raiz** e execute o seguinte comando, onde **XXXX** é o número de compilação do Adobe Campaign:

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   O arquivo rpm depende dos pacotes que podem ser encontrados nas distribuições CentOS/Red Hat. Se você não quiser usar algumas dessas dependências (por exemplo, se você quiser usar o JDK do Oracle em vez do OpenJDK), talvez precise usar a opção &quot;nodeps&quot; de rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

O comando `bc`, obrigatório para executar o [netreport](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts), não está disponível por padrão em todas as distribuições do Linux. Para verificar se o comando está disponível, execute o comando `which bc`. Caso contrário, você precisa instalá-lo.

Com o CentOS, você deve instalar o pacote bc.x86_64: conectar como **raiz** e executar o seguinte comando:

```
yum install bc.x86_64
```

## Distribuição baseada em APT (Debian) {#distribution-based-on-apt--debian-}

Para instalar o Adobe Campaign em um sistema operacional Debian de 64 bits, siga as etapas abaixo:

1. Obtenha o pacote do Adobe Campaign. O nome do arquivo é **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, onde **XXXX** é o número de compilação do Adobe Campaign.

   >[!CAUTION]
   >
   >Certifique-se de usar o nome de arquivo correto para sua versão do Adobe Campaign nos exemplos de comando desta seção.

1. Para instalá-lo, conecte como **raiz** e execute o seguinte comando, onde **XXXX** é o número de compilação do Adobe Campaign:

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Se houver dependências ausentes, execute o seguinte comando:

   ```
   apt-get install -f
   ```


1. Ao instalar o Adobe Campaign em um sistema operacional Debian, considere o seguinte:

* O OpenSSL deve ser instalado com antecedência.
* Instale o libicu e o libc-aresYY, onde XX é a versão, com os seguintes comandos:

  ```
  apt install libicuXX
  ```

  ```
  apt install libc-aresXX
  ```

  ```
  apt install openjdk-XX-jdk
  ```

## Personalização de parâmetros {#personalizing-parameters}

Alguns parâmetros podem ser personalizados através do arquivo **customer.sh**

Se você estiver executando a instalação pela primeira vez, talvez o arquivo **customer.sh** ainda não exista no servidor.

Crie-o e verifique se ele tem direitos de execução. Se esse não for o caso, insira o seguinte comando:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Codificação do servidor {#server-encoding}

Por padrão, o servidor é iniciado em um ambiente iso8859-15. No entanto, o servidor pode ser iniciado em um ambiente UTF-8.

>[!CAUTION]
>
>Essa alteração afeta as interações com o sistema de arquivos (arquivos carregados por um fluxo de trabalho ou um script do JavaScript) e na codificação do arquivo. Portanto, recomendamos usar o ambiente padrão.

Para criar uma **instância japonesa**, você deve usar um ambiente UTF-8.

Para habilitar o ambiente UTF-8, use o seguinte comando:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Variáveis de ambiente {#environment-variables}

As variáveis de ambiente a seguir devem ser definidas corretamente.

Determinadas combinações exigem alterações no ambiente usado para executar o Adobe Campaign. Um arquivo específico (`/usr/local/neolane/nl6/customer.sh`) pode ser criado e editado para adicionar modificações específicas ao ambiente do Adobe Campaign.

Se necessário, edite o arquivo **customer.sh** usando o comando **vi customer.sh** e adapte a configuração ou adicione linhas ausentes:

* Para o cliente Oracle:

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  O conteúdo da variável de ambiente ORACLE_HOME corresponde ao diretório de instalação do Oracle.

  O conteúdo da variável TNS_ADMIN deve corresponder ao local do arquivo **tnsnames.ora**.

* Para o LibreOffice:

  Para executar o Adobe Campaign em uma versão existente do LibreOffice, configurações adicionais são necessárias: você precisa especificar os caminhos de acesso para o diretório de instalação. Por exemplo:

   * Debian

     São fornecidos valores default para OOO_INSTALL_DIR e OOO_BASIS_INSTALL_DIR. Você pode substituí-los em **customer.sh** se o layout da instalação do LibreOffice for diferente:

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
     export OOO_INSTALL_DIR=/usr/lib/libreoffice/
     ```

   * CentOs

     Use os seguintes valores padrão:

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
     export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
     ```

* Para Java Development Kit (JDK):

  Por padrão, o script de configuração do ambiente Adobe Campaign (`~/nl6/env.sh`) procura o diretório de instalação do JDK. No entanto, é recomendável especificar qual JDK precisa ser usado. Para fazer isso, você pode forçar a variável de ambiente **JDK_HOME** usando o seguinte comando:

  ```
  export JDK_HOME=/usr/java/jdkX.Y.Z
  ```

  >[!NOTE]
  >
  >Verifique se a versão do JDK usada corresponde ao nome do diretório.

  Para testar a configuração do JDK, faça logon como o usuário do sistema do Adobe Campaign com o seguinte comando:

  ```
  su - neolane
  ```

Você deve reiniciar o serviço Adobe Campaign para que as alterações sejam consideradas.

Os comandos são os seguintes:

```
systemctl stop nlserver
systemctl start nlserver
```

### Cliente Oracle no Linux {#oracle-client-in-linux}

Ao usar o Oracle com o Adobe Campaign, é necessário configurar as camadas de cliente do Oracle no Linux.

* Usar o cliente completo
* Definição de TNS

  As definições TNS devem ser adicionadas durante a fase de instalação. Para fazer isso, use os seguintes comandos:

  ```
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* Variáveis de ambiente

  Consulte [Variáveis de ambiente](#environment-variables).

* Configuração do Adobe Campaign

  Para finalizar a instalação do cliente do Oracle para Adobe Campaign, você precisa criar um link simbólico para o arquivo **.so** usado pelo Adobe Campaign.

  Para fazer isso, use os seguintes comandos:

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

Em caso de problema, verifique se os pacotes listados na documentação de instalação do Oracle estão instalados corretamente.

## Verificações de instalação {#installation-checks}

Agora você pode executar um teste de instalação inicial usando os seguintes comandos:

```
su - neolane
nlserver pdump
```

Quando o Adobe Campaign não é iniciado, a resposta é:

```
no task
```

## Primeira inicialização do servidor {#first-start-up-of-the-server}

Quando o teste de instalação estiver concluído, digite o seguinte comando:

```
nlserver web
```

As seguintes informações são exibidas:

```sql
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Esses comandos permitem criar arquivos de configuração do **config-default.xml** e do **serverConf.xml**. Todos os parâmetros disponíveis no **serverConf.xml** estão listados nesta [seção](../../installation/using/the-server-configuration-file.md).

Pressione **Ctrl+C** para parar o processo e digite o seguinte comando:

```
nlserver start web
```

As seguintes informações são exibidas:

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Para interrompê-lo, digite:

```
nlserver stop web
```

As seguintes informações são exibidas:

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Senha do identificador interno {#password-for-the-internal-identifier}

O servidor do Adobe Campaign define um logon técnico chamado **interno** que tem todos os direitos em todas as instâncias. Logo após a instalação, o login não terá uma senha. É obrigatório definir um.

Saiba mais [nesta seção](../../installation/using/configuring-campaign-server.md#internal-identifier).
