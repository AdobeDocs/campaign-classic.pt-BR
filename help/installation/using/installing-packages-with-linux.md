---
solution: Campaign Classic
product: campaign
title: Instalação de pacotes com Linux
description: Instalação de pacotes com Linux
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 1%

---


# Instalação de pacotes com Linux{#installing-packages-with-linux}

Para uma plataforma Linux de 32 bits, instale o Adobe Campaign de 32 bits. Para uma plataforma Linux de 64 bits, instale o Adobe Campaign de 64 bits.

Para cada uma dessas versões, a Adobe Campaign vem com um pacote: **nlserver**. Este pacote contém os binários e os arquivos de configuração para uma determinada versão.

Os comandos de instalação permitem que você:

* Copie os arquivos para **/usr/local/neolane**
* Crie uma conta Adobe Campaign Linux (e o grupo associado), que é criada com **/usr/local/neolane** como seu diretório inicial
* Crie um script automático **/etc/init.d/nlserver6** para uso na inicialização ou crie uma unidade do sistema (a partir de 20.1).

>[!NOTE]
>
>O usuário do sistema **neolane** não deve ter sido criado antes da execução do comando. O usuário **neolane** é criado automaticamente durante a instalação.
>
>O diretório **inicial** vinculado ao usuário **neolane** também é criado automaticamente no **[!UICONTROL /usr/local/neolane]**. Verifique se há espaço suficiente no **[!UICONTROL /usr/local]** disco (vários GB).

Você pode executar o comando **ping`hostname`** para garantir que o servidor possa acessar a si mesmo.

## Distribuição baseada em pacotes RPM {#distribution-based-on-rpm--packages}

Para instalar o Adobe Campaign em um sistema operacional RPM (RHEL, CentOS e SUSE), aplique as seguintes etapas:

1. Primeiro, você deve obter o pacote Adobe Campaign.

   O arquivo é nomeado como abaixo, onde **XXXX** é o número do build do Adobe Campaign:

   * **nlserver6-v7-XXXX-0.x86_64.rpm** para v7.
   * **nlserver6-XXXX-0.x86_64.rpm** para v6.1.

   >[!CAUTION]
   >
   >Certifique-se de usar o nome de arquivo correto para sua versão do Adobe Campaign nos exemplos de comando desta seção.

1. Para instalá-lo, conecte-se como **raiz** e execute o seguinte comando (onde **XXXX** é o número de compilação do Adobe Campaign):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   O arquivo rpm tem dependências em pacotes que você pode encontrar nas distribuições CentOS/Red Hat. Se você não quiser usar algumas dessas dependências (por exemplo, se quiser usar o Oracle JDK em vez do OpenJDK), talvez seja necessário usar a opção &quot;nodeps&quot; de rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

O comando &#39;bc&#39;, necessário para executar o netreport (consulte [esta seção](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) para obter mais informações), não está disponível por padrão em todas as distribuições Linux. Para verificar se o comando está disponível, execute o comando &#39;which bc&#39;. Caso contrário, é necessário instalá-lo.

Com o CentOS, você deve instalar o pacote bc.x86_64: conecte-se como **raiz** e execute o seguinte comando:

```
yum install bc.x86_64
```

## Distribuição com base em APT (Debian) {#distribution-based-on-apt--debian-}

### Em Debian 64 bits {#in-debian-64-bits}

Para instalar o Adobe Campaign de 64 bits em um sistema operacional Debian de 64 bits, execute as seguintes etapas:

1. Primeiro, você deve obter o pacote Adobe Campaign.

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** para v7.
   * **nlserver6-XXXX-linux-2.6-amd64.deb** para v6.1.

   **XXXX** é o número do build do Adobe Campaign.

   >[!CAUTION]
   >
   >Certifique-se de usar o nome de arquivo correto para sua versão do Adobe Campaign nos exemplos de comando desta seção.

1. Para instalá-lo, conecte-se como **raiz** e execute o seguinte comando (onde **XXXX** é o número de compilação do Adobe Campaign):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Se houver dependências ausentes, execute o seguinte comando:

   ```
   apt-get install -f
   ```

**Especificações do Debian 8/9**

Ao instalar o Adobe Campaign em um sistema operacional Debian 8/9, considere o seguinte:

* O OpenSSL deve ser instalado previamente.
* Instale libicu52 (Debian 8) ou libicu57 (Debian 9), libprotobuf9 (Debian8) e libc-ares2 com os seguintes comandos:

   ```
   aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 8)
   ```

* Instale o JDK7 com o seguinte comando:

   ```
   aptitude install openjdk-7-jdk (Debian 8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## Personalização de parâmetros {#personalizing-parameters}

Alguns parâmetros podem ser personalizados pelo arquivo **customer.sh**

Se você estiver executando a instalação pela primeira vez, o arquivo **customer.sh** talvez ainda não exista no servidor. Crie-o e verifique se ele tem direitos de execução. Se esse não for o caso, digite o seguinte comando:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Codificação do servidor {#server-encoding}

Por padrão, o servidor é iniciado em um ambiente iso8859-15. No entanto, o servidor pode ser iniciado em um ambiente UTF-8.

>[!CAUTION]
>
>Essa alteração afeta as interações com o sistema de arquivos (arquivos carregados por meio de um fluxo de trabalho ou um script JavaScript) e na codificação do arquivo. Portanto, recomendamos usar o ambiente padrão.

No entanto, para criar uma instância **** japonesa, é necessário usar um ambiente UTF-8.

Para ativar o ambiente UTF-8, use o seguinte comando:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Idioma padrão do servidor {#default-language-for-the-server}

A instalação suporta inglês e francês. O inglês é usado por padrão.

Para alternar para francês, digite os seguintes comandos:

```
su - neolane
vi nl6/customer.sh
```

e adicione a seguinte linha:

```
export neolane_LANG=fra
```

Para garantir que as mensagens do sistema sejam lidas corretamente, os consoles devem estar em uma página de código correspondente ao idioma (ISO-8859-1 ou -15 para francês).

### Variáveis de ambiente {#environment-variables}

As variáveis de ambiente a seguir devem ser definidas corretamente.

Determinadas combinações exigem alterações no ambiente usado para executar o Adobe Campaign. Um arquivo (`/usr/local/neolane/nl6/customer.sh`) específico pode ser criado e editado para adicionar modificações específicas ao ambiente Adobe Campaign.

Se necessário, edite o arquivo **customer.sh** usando o comando **vi customer.sh** e adapte a configuração ou adicione linhas ausentes:

* Para o cliente Oracle:

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   O conteúdo da variável de ambiente ORACLE_HOME corresponde ao diretório de instalação do Oracle.

   O conteúdo da variável TNS_ADMIN deve corresponder ao local do arquivo **tnsnames.ora** .

* LibreOffice:

   Para executar o Adobe Campaign em uma versão existente do LibreOffice, são necessárias configurações adicionais: é necessário especificar os caminhos de acesso para o diretório de instalação. Por exemplo:

   * Debian

      São fornecidos valores padrão para OOO_INSTALL_DIR, OOO_BASIS_INSTALL_DIR, OOO_URE_INSTALL_DIR. Você pode substituí-los em **customer.sh** se o layout da instalação do LibreOffice for diferente:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

   * CentOs

      Use os seguintes valores padrão:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* Para o Java Development Kit (JDK):

   Por padrão, o script de configuração do ambiente Adobe Campaign (`~/nl6/env.sh`) pesquisa o diretório de instalação do JDK. Como esse comportamento não é 100% confiável, é necessário especificar qual JDK deve ser usado. Para fazer isso, você pode forçar a variável de ambiente **JDK_HOME** usando o seguinte comando:

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >Este é um exemplo. Verifique se a versão do JDK usada corresponde ao nome do diretório.

   Para testar a configuração do JDK, faça logon como o usuário do sistema Adobe Campaign com o seguinte comando:

   ```
   su - neolane
   ```

É necessário reiniciar o serviço Adobe Campaign para que as alterações sejam consideradas.

Os comandos são os seguintes:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

A partir do 20.1, recomendamos usar os seguintes comandos:

```
systemctl stop nlserver
systemctl start nlserver
```

### Cliente oracle em Linux {#oracle-client-in-linux}

Ao usar o Oracle com o Adobe Campaign, é necessário configurar as camadas do cliente Oracle no Linux.

* Usar o cliente completo
* Definição de TNS

   As definições de TNS devem ser adicionadas durante a fase de instalação. Para fazer isso, use os seguintes comandos:

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* Variáveis de ambiente

   Consulte as variáveis [do](../../installation/using/installing-packages-with-linux.md#environment-variables)Ambiente.

* Configuração para Adobe Campaign

   Para finalizar a instalação do cliente Oracle para Adobe Campaign, é necessário criar um link simbólico para o arquivo **.so** usado pela Adobe Campaign.

   Para fazer isso, use os seguintes comandos:

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

Se você encontrar um problema, verifique se os pacotes listados na documentação [de instalação do](https://www.oracle.com/pls/db112/portal.portal_db?selected=11) Oracle estão instalados corretamente.

## Verificações de instalação {#installation-checks}

Agora é possível executar um teste de instalação inicial usando os seguintes comandos:

```
su - neolane
nlserver pdump
```

Quando o Adobe Campaign não é iniciado, a resposta é:

```
no task
```

## Primeiro start do servidor {#first-start-up-of-the-server}

Quando o teste de instalação estiver concluído, digite o seguinte comando:

```
nlserver web
```

As seguintes informações são exibidas:

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Esses comandos permitem criar arquivos de configuração **config-default.xml** e **serverConf.xml** . Todos os parâmetros disponíveis no **serverConf.xml** estão listados nesta [seção](../../installation/using/the-server-configuration-file.md).

Pressione **Ctrl+C** para parar o processo e, em seguida, digite o seguinte comando:

```
nlserver start web
```

As seguintes informações são exibidas:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Para pará-lo, digite:

```
nlserver stop web
```

As seguintes informações são exibidas:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Senha do identificador interno {#password-for-the-internal-identifier}

O servidor Adobe Campaign define um logon técnico chamado **interno** que tem todos os direitos em todas as instâncias. Logo após a instalação, o logon não tem uma senha. É obrigatório definir um.

Consulte o identificador [interno](../../installation/using/campaign-server-configuration.md#internal-identifier)da seção.
