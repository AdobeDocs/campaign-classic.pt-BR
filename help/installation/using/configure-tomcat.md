---
product: campaign
title: Configuração do Tomcat da campanha
description: Configuração do Tomcat da campanha
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
TQID: 'https://experienceleague.adobe.com/LaGsFkomGXlahM-Do7Vwfc4OMH0UAXRiiSRq5Q-9Wto'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 6%
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
