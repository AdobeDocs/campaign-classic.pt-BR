---
solution: Campaign Classic
product: campaign
title: Limites de conexão
description: Limites de conexão
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

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

