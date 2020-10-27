---
title: Limites de conexão
seo-title: Limites de conexão
description: Limites de conexão
seo-description: null
page-status-flag: never-activated
uuid: a4b6959a-0f5b-41a2-b4c3-d7d6613d1a18
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f3db77db-94cc-4d75-a59b-2dddce776759
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 5%

---


# Limites de conexão{#connection-thresholds}

Para servidores muito carregados, o limite de conexão pode ser excedido. Em qualquer evento, é útil descobrir porquê.

Há três limiares diferentes:

1. O limite de conexão com a Web, configurado no servidor da Web. Para modificá-la, entre em contato com o administrador do sistema.
1. O limite de conexão do banco de dados. Para modificá-la, entre em contato com o administrador do banco de dados.
1. O limite de conexão Adobe Campaign, disponível em dois lugares:

   * Lado Tomcat: todos os query chegando no cliente Adobe Campaign Tomcat.

      Esse limite é configurado no arquivo **nl6/tomcat-8/conf/server.xml** . O atributo **maxThreads** permite aumentar o limite do número de query processados por vez. Pode ser alterado para 250, por exemplo.

      ```
      <Connector protocol="HTTP/1.1" port="8080"
                     maxThreads="75"
                     minSpareThreads="5"
                     enableLookups="true" redirectPort="8443"
                     acceptCount="100" connectionTimeout="20000"
                     disableUploadTimeout="true" />
          <Engine name="Tomcat-Standalone" defaultHost="localhost">
            <Host name="localhost" appBase="./"
                  unpackWARs="true" autoDeploy="true">
      ```

   * Banco de dados: conjunto de todas as conexões abertas ao mesmo tempo no banco de dados por um processo.

      Esse limite é configurado no arquivo **nl6/conf/serverConf.xml**. O atributo **maxCnx** localizado no pool **de** fontes de dados permite aumentar o limite de query processados simultaneamente.

      ```
          <!-- Data source
               -->
            <dataSource name="default">
              <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
              <sqlParams funcPrefix="">
                <postConnectSQL/>
              </sqlParams>
              <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
            </dataSource>
      ```

