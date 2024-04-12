---
product: campaign
title: Integração em um servidor Web para Linux
description: Saiba como integrar o Campaign a um servidor Web (Linux)
feature: Installation, Instance Settings
badge-v7-prem: label="No local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 4%

---

# Integração em um servidor Web para Linux{#integration-into-a-web-server-for-linux}



O Adobe Campaign inclui o Apache Tomcat, que atua como ponto de entrada no servidor de aplicativos via HTTP (e SOAP).

Você pode usar esse servidor Tomcat integrado para atender a solicitações HTTP.

Neste caso:

* a porta de escuta padrão é 8080. Para alterá-lo, consulte [nesta seção](configure-tomcat.md).
* Os consoles clientes se conectam usando um URL como:

  ```
  http://<computer>:8080
  ```

No entanto, por motivos de segurança e administração, recomendamos usar um servidor Web dedicado como principal ponto de entrada para o tráfego HTTP quando o computador que executa o Adobe Campaign estiver exposto na Internet e você desejar abrir o acesso ao console fora da rede.

Um servidor da Web também permite garantir a confidencialidade dos dados com o protocolo HTTPs.

Da mesma forma, você deve usar um servidor Web quando quiser usar a funcionalidade de rastreamento, que só está disponível como um módulo de extensão para um servidor Web.

>[!NOTE]
>
>Se você não usar a funcionalidade de rastreamento, poderá executar uma instalação padrão do Apache ou do IIS com um redirecionamento para o Campaign. O módulo de extensão do servidor Web de rastreamento não é necessário.

## Configuração do servidor Web Apache com Debian {#configuring-the-apache-web-server-with-debian}

Esse processo se aplica se você tiver instalado o Apache em uma distribuição baseada no APT.

Siga as etapas abaixo:

1. Desative os módulos carregados por padrão usando o seguinte comando:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Certifique-se de que o **alias**, **authz_host** e **mime** Os módulos do ainda estão ativados. Para fazer isso, use o seguinte comando:

   ```
   a2enmod  alias authz_host mime
   ```

1. Criar o arquivo **nlsrv.load** in **/etc/apache2/mods-available** e insira o seguinte conteúdo:

   No Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Criar o arquivo **nlsrv.conf** in **/etc/apache2/mods-available** usando o seguinte comando:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Ative esse módulo com o seguinte comando:

   ```
    a2enmod nlsrv
   ```

   Se você estiver usando a variável **mod_rewrite** para páginas do Adobe Campaign, é necessário renomear o **nlsrv.load** e **nlsrv.conf** arquivos para **zz-nlsrv.load** e **zz-nlsrv.conf**. Para ativar o módulo, execute o seguinte comando:

   ```
   a2enmod zz-nlsrv
   ```

1. Edite o **/etc/apache2/envvars** adicione as seguintes linhas:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Salve as alterações.

1. Em seguida, adicione usuários do Adobe Campaign ao grupo de usuários do Apache e vice-versa usando o seguinte tipo de comando:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Reiniciar o Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## Configuração do Apache Web Server no RHEL {#configuring-apache-web-server-in-rhel}

Este procedimento se aplica se você tiver instalado e protegido o Apache em um pacote baseado em RPM (RHEL, CentOS e Suse).

Siga as etapas abaixo:

1. No `httpd.conf` ative os seguintes módulos Apache:

   ```
   alias
   authz_host
   mime
   ```

1. Desative os seguintes módulos:

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

   Comente as funções vinculadas aos módulos desativados:

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. Crie um arquivo de configuração específico do Adobe Campaign no `/etc/httpd/conf.d/` pasta. Por exemplo `CampaignApache.conf`

1. Para **RHEL7**, adicione as seguintes instruções no arquivo:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. Para **RHEL7**:

   Adicione o `/etc/systemd/system/httpd.service` arquivo com o seguinte conteúdo:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Atualize o módulo usado pelo systemd:

   ```
   systemctl daemon-reload
   ```

1. Em seguida, adicione operadores do Adobe Campaign ao grupo de operadores do Apache e vice-versa, executando o comando:

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   Os nomes de grupo a serem usados dependem da forma como o Apache é configurado.

1. Execute o Apache e o servidor do Adobe Campaign.

   Para RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Iniciar o servidor Web e testar a configuração{#launching-the-web-server-and-testing-the-configuration}

Agora você pode testar a configuração iniciando o Apache. O módulo Adobe Campaign agora deve exibir seu banner no console (dois banners em determinados sistemas operacionais):

```
 /etc/init.d/apache start
```

As seguintes informações são exibidas:

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Em seguida, verifique se ele responde enviando um URL de teste.

Você pode testar isso na linha de comando executando:

```
 telnet localhost 80  
```

Você deve obter:

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

Em seguida, digite:

```
GET /r/test
```

As seguintes informações são exibidas:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

Você também pode solicitar o URL `https://myserver.adobe.com/r/test` de um navegador da Web.
