---
product: campaign
title: Configuração do Campaign Tomcat
description: Configuração do Campaign Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 1%

---

# Configurar o Apache Tomcat {#configuring-tomcat}

![](../../assets/v7-only.svg)

A Adobe Campaign usa uma **servlet da Web incorporado chamado Apache Tomcat** para processar solicitações HTTP/HTTPS entre o aplicativo e qualquer interface externa (incluindo Console do cliente, links de URL rastreados, chamadas SOAP e outras). Geralmente, há um servidor da Web externo (geralmente IIS ou Apache) na frente disso para qualquer instância do Adobe Campaign voltada para o exterior.

Saiba mais sobre o Tomcat no Campaign e como localizar a versão do Tomcat no [esta página](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Este procedimento restringe-se a **no local** implantações.

## Porta padrão para Apache Tomcat {#default-port-for-tomcat}

Quando a porta de escuta 8080 do servidor Tomcat já estiver ocupada com outro aplicativo necessário para sua configuração, é necessário substituir a porta 8080 por uma gratuita (8090 por exemplo). Para alterá-lo, edite o **server.xml** arquivo salvo no **/tomcat-8/conf** diretório da pasta de instalação do Adobe Campaign.

Em seguida, modifique a porta das páginas de retransmissão JSP. Para fazer isso, altere a **serverConf.xml** arquivo salvo no **/conf** diretório do diretório de instalação do Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mapear uma pasta no Apache Tomcat {#mapping-a-folder-in-tomcat}

Para definir configurações específicas do cliente, é possível criar um **user_contexts.xml** no **/tomcat-8/conf** pasta , que também contém a variável **contexts.xml** arquivo.

Esse arquivo conterá o seguinte tipo de informação:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Se necessário, essa operação pode ser reproduzida no lado do servidor.

## Ocultar o relatório de erro do Tomcat {#hide-tomcat-error-report}

Por motivos de segurança, recomendamos que você oculte o relatório de erro do Tomcat. Estas são as etapas.

1. Abra o **server.xml** localizada na **/tomcat-8/conf** diretório da pasta de instalação do Adobe Campaign:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Adicione o seguinte elemento na parte inferior após todos os elementos de contexto existentes:

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```
1. Reinicie os servidores da Web nlserver e Apache.
