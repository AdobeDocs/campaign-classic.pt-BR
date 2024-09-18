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
source-git-commit: fd4a815bca23b94590012c4883cfaa9c29b6f118
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 4%

---

# Configurar Apache Tomcat {#configuring-tomcat}

O Adobe Campaign usa um **servlet Web incorporado chamado Apache Tomcat** para processar solicitações HTTP/HTTPS entre o aplicativo e qualquer interface externa (incluindo o Console do Cliente, links de URL rastreados, chamadas SOAP e outros). Geralmente, há um servidor Web externo (geralmente o IIS ou Apache) na frente disso para qualquer instância do Adobe Campaign voltada para o exterior.

Saiba mais sobre o Tomcat no Campaign e como localizar sua versão do Tomcat em [esta página](../../production/using/locate-tomcat-version.md).

>[!AVAILABILITY]
>
>
>* A partir do Campaign v7.4.1, Tomcat 10.1 será a versão padrão.
>
>* O Adobe Campaign Classic não usa os protocolos WebSocket e HTTP2.
>



## Porta padrão para o Apache Tomcat {#default-port-for-tomcat}


>[!NOTE]
>
>Este procedimento é restrito a **implantações locais**.
>

Quando a porta de escuta 8080 do servidor Tomcat já estiver ocupada com outro aplicativo necessário para sua configuração, você precisará substituir a porta 8080 por uma porta livre (8090 por exemplo). Para alterá-lo, edite o arquivo **server.xml** salvo no diretório **/tomcat-X/conf** da pasta de instalação do Adobe Campaign.

Em seguida, modifique a porta das páginas de retransmissão JSP. Para fazer isso, altere o arquivo **serverConf.xml** salvo no diretório **/conf** do diretório de instalação do Adobe Campaign.

```xml
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mapear uma pasta no Apache Tomcat {#mapping-a-folder-in-tomcat}


>[!NOTE]
>
>Este procedimento é restrito a **implantações locais**.
>

Para definir configurações específicas do cliente, você pode criar um arquivo **user_contexts.xml** na pasta **/tomcat-X/conf**, que também contém o arquivo **contexts.xml**.

Esse arquivo conterá o seguinte tipo de informação:

```xml
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Se necessário, essa operação pode ser reproduzida no lado do servidor.

## Ocultar o relatório de erros do Tomcat {#hide-tomcat-error-report}


>[!NOTE]
>
>Este procedimento é restrito a **implantações locais**.
>
>Essa alteração não é mais necessária a partir do Campaign v7.4.1.
>

Por motivos de segurança, recomendamos que você oculte o relatório de erros do Tomcat. Siga estas etapas:

1. Abra o arquivo **server.xml** localizado no diretório **/tomcat-X/conf** da pasta de instalação do Adobe Campaign: `/usr/local/neolane/nl6/tomcat-X/conf`
1. Adicione o seguinte elemento na parte inferior após todos os elementos de contexto existentes:

   ```xml
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Reinicie os servidores Web nlserver e Apache.
