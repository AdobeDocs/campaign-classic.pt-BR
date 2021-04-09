---
solution: Campaign Classic
product: campaign
title: Configuração do Campaign Tomcat
description: Configuração do Campaign Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 8ab0aab42accbd1253d53e8133f5af0a38c724ea
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Configurar o Apache Tomcat {#configuring-tomcat}

O Adobe Campaign usa um **servlet da Web incorporado chamado Apache Tomcat** para processar solicitações HTTP/HTTPS entre o aplicativo e qualquer interface externa (incluindo Console do cliente, links de URL rastreados, chamadas SOAP e outras). Geralmente, há um servidor da Web externo (geralmente IIS ou Apache) na frente disso para qualquer instância do Adobe Campaign voltada para o exterior.

Saiba mais sobre o Tomcat no Campaign e como localizar a versão do Tomcat em [this page](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Este procedimento está restrito a **implantações locais**.


## Porta padrão para Apache Tomcat {#default-port-for-tomcat}

Quando a porta de escuta 8080 do servidor Tomcat já estiver ocupada com outro aplicativo necessário para sua configuração, é necessário substituir a porta 8080 por uma gratuita (8090 por exemplo). Para alterá-lo, edite o arquivo **server.xml** salvo no diretório **/tomcat-8/conf** da pasta de instalação do Adobe Campaign.

Em seguida, modifique a porta das páginas de retransmissão JSP. Para fazer isso, altere o arquivo **serverConf.xml** salvo no diretório **/conf** do diretório de instalação do Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mapear uma pasta no Apache Tomcat {#mapping-a-folder-in-tomcat}

Para definir configurações específicas do cliente, você pode criar um arquivo **user_contexts.xml** na pasta **/tomcat-8/conf**, que também contém o arquivo **contexts.xml**.

Esse arquivo conterá o seguinte tipo de informação:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Se necessário, essa operação pode ser reproduzida no lado do servidor.
