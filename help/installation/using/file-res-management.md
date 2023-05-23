---
product: campaign
title: Gerenciamento de arquivos e recursos
description: Saiba como configurar o gerenciamento de arquivos e recursos no Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Gerenciamento de arquivos e recursos{#file-and-resmanagement}



## Limitar formato de arquivo de upload {#limiting-uploadable-files}

Use o **uploadWhiteList** para restringir os tipos de arquivos disponíveis para upload no servidor do Adobe Campaign.

Este atributo está disponível no **dataStore** elemento do **serverConf.xml** arquivo. Todos os parâmetros disponíveis no **serverConf.xml** estão listados neste [seção](../../installation/using/the-server-configuration-file.md).

O valor padrão desse atributo é **.+** e permite carregar qualquer tipo de arquivo.

Para limitar os formatos possíveis, substitua o valor do atributo por uma expressão Java regular válida. É possível inserir vários valores separando-os por vírgula.

Por exemplo: **uploadWhiteList=&quot;.&#42;.png.&#42;.jpg&quot;** O permitirá o upload de formatos PNG e JPG no servidor. Nenhum outro formato será aceito.

Você também pode impedir que arquivos importantes sejam carregados configurando o Servidor Web. [Saiba mais](web-server-configuration.md)

>[!NOTE]
>
>A variável **uploadWhiteList** o atributo restringe os tipos de arquivo disponíveis para upload no servidor do Adobe Campaign. No entanto, quando o modo de publicação é **Servidor(es) de rastreamento** ou **Outros servidores do Adobe Campaign**, o **uploadWhitelist** O atributo também deve ser atualizado nesses servidores.

## Configuração de conexão proxy {#proxy-connection-configuration}

Você pode conectar o servidor do Campaign a um sistema externo por meio de um proxy, usando um **Transferência de arquivo** atividade de workflow, por exemplo. Para isso, é necessário configurar o **proxyConfig** seção do **serverConf.xml** por meio de um comando específico. Todos os parâmetros disponíveis no **serverConf.xml** estão listados neste [seção](../../installation/using/the-server-configuration-file.md).

As seguintes conexões proxy são possíveis: HTTP, HTTPS, FTP, SFTP. Observe que a partir da versão 20.2 do Campaign, os parâmetros de protocolo HTTP e HTTPS serão **não está mais disponível**. Esses parâmetros ainda são mencionados abaixo, pois permanecem disponíveis em builds anteriores, incluindo a 9032.

>[!CAUTION]
>
>Somente o modo de autenticação básico é suportado. Não há suporte para autenticação NTLM.
>
>Proxies SOCKS não são suportados.

Você pode usar o seguinte comando:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

os parâmetros de protocolo podem ser &quot;http&quot;, &quot;https&quot; ou &quot;ftp&quot;.

Se estiver configurando o FTP na mesma porta do tráfego HTTP/HTTPS, você poderá usar o seguinte:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

As opções &quot;http&quot; e &quot;https&quot; só são usadas quando o parâmetro de protocolo é &quot;ftp&quot; e indicam se o tunelamento na porta especificada será executado por HTTPS ou por HTTP.

Se você usar portas diferentes para tráfego FTP/SFTP e HTTP/HTTPS no servidor proxy, deverá definir o parâmetro de protocolo ‘ftp’.


Por exemplo:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Em seguida, digite a senha.

As conexões HTTP são definidas no parâmetro proxyHTTP:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

As conexões HTTPS são definidas no parâmetro proxyHTTPS:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

As conexões FTP/FTPS são definidas no parâmetro proxyFTP:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Se você usar o mesmo proxy para vários tipos de conexão, somente proxyHTTP será definido com useSingleProxy definido como &quot;1&quot; ou &quot;true&quot;.

Se você tiver conexões internas que devem passar pelo proxy, adicione-as no parâmetro de substituição.

Se você quiser desativar temporariamente a conexão proxy, defina o parâmetro ativado como &quot;false&quot; ou &quot;0&quot;.

Se você precisar usar o conector HTTP/2 do iOS por meio de um proxy, os seguintes modos de proxy HTTP serão compatíveis:

* HTTP sem autenticação
* Autenticação básica HTTP

Para ativar o modo proxy, a seguinte alteração deve ser feita no `serverconf.xml` arquivo:

```
<nmac useHTTPProxy="true">
```

Para obter mais informações sobre esse conector HTTP/2 do iOS, consulte [página](../../delivery/using/about-mobile-app-channel.md).

## Gerenciar recursos públicos {#managing-public-resources}

Para serem disponibilizadas publicamente, as imagens usadas em emails e recursos públicos vinculados a campanhas devem estar presentes em um servidor acessível externamente. Eles podem estar disponíveis para recipients ou operadores externos. [Saiba mais](../../installation/using/deploying-an-instance.md#managing-public-resources).

Os recursos públicos são armazenados no **/var/res/instance** diretório do diretório de instalação do Adobe Campaign.

O URL correspondente é: **http://server/res/instance** onde **instância** é o nome da instância de rastreamento.

Você pode especificar outro diretório adicionando um nó à **conf-`<instance>`.xml** arquivo para configurar o armazenamento no servidor. Isso significa adicionar as seguintes linhas:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

Nesse caso, o novo URL para os recursos públicos fornecido na parte superior da janela do assistente de implantação deve apontar para essa pasta.
