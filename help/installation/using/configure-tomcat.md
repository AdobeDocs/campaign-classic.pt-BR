---
product: campaign
title: Configuração do Tomcat da campanha
description: Configuração do Tomcat da campanha
feature: Installation, Instance Settings
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 2%

---

# Configurar Apache Tomcat {#configuring-tomcat}



O Adobe Campaign usa um **servlet web incorporado chamado Apache Tomcat** para processar solicitações HTTP/HTTPS entre o aplicativo e qualquer interface externa (incluindo o Console do cliente, links de URL rastreados, chamadas SOAP e outros). Geralmente, há um servidor Web externo (geralmente o IIS ou Apache) na frente disso para qualquer instância do Adobe Campaign voltada para o exterior.

Saiba mais sobre o Tomcat no Campaign e como localizar sua versão do Tomcat no [esta página](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Este procedimento é limitado a **no local** implantações.
>

## Porta padrão para o Apache Tomcat {#default-port-for-tomcat}

Quando a porta de escuta 8080 do servidor Tomcat já estiver ocupada com outro aplicativo necessário para sua configuração, você precisará substituir a porta 8080 por uma porta livre (8090 por exemplo). Para alterá-lo, edite o **server.xml** arquivo salvo na **/tomcat-8/conf** diretório da pasta de instalação do Adobe Campaign.

Em seguida, modifique a porta das páginas de retransmissão JSP. Para fazer isso, altere a variável **serverConf.xml** arquivo salvo na **/conf** diretório do diretório de instalação do Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mapear uma pasta no Apache Tomcat {#mapping-a-folder-in-tomcat}

Para definir configurações específicas do cliente, você pode criar um **user_contexts.xml** arquivo no **/tomcat-8/conf** pasta, que também contém a **contexts.xml** arquivo.

Esse arquivo conterá o seguinte tipo de informação:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Se necessário, essa operação pode ser reproduzida no lado do servidor.

## Ocultar o relatório de erros do Tomcat {#hide-tomcat-error-report}

Por motivos de segurança, recomendamos que você oculte o relatório de erros do Tomcat. Estas são as etapas.

1. Abra o **server.xml** arquivo localizado na **/tomcat-8/conf** diretório da pasta de instalação do Adobe Campaign:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Adicione o seguinte elemento na parte inferior após todos os elementos de contexto existentes:

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Reinicie os servidores Web nlserver e Apache.
